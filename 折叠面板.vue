<template>
  <div class="box">
    <div class="main" v-for="item in list" :key="item.title" @click="click">
      <div class="title">{{item.title}}<Icon  type="ios-arrow-forward" /></div>
      <div class="text" style="height:0px">{{item.text}}</div>
    </div>

  </div>

</template>

<script>
export default {
  data() {
    return {
      list: [
        { title: "11", text: "dddddddddddddddd" },
        { title: "12", text: "dddddddddddddddd" },
        { title: "13", text: "dddddddddddddddd" },
        { title: "14", text: "dddddddddddddddd" },
        { title: "15", text: "dddddddddddddddd" }
      ]
    };
  },
  created(){
  },
  methods: {
    click(e) {
      let textBox = e.target.parentNode.children[1];
      let icon=e.target.parentNode.children[0].children[0]
      let tHeight = textBox.scrollHeight;
      let h = parseInt(textBox.style.height);
      console.log(h)
      if (h <= 0) {
          icon.classList.add("rotatedown")
          textBox.classList.add("to")
        let timer = setInterval(() => {
          h += 3;
          textBox.style.height = h + "px";
          if (h >= tHeight) {
            clearInterval(timer);
            textBox.style.height = tHeight + "px";
          }
        }, 20);
      }else{
          icon.classList.remove("rotatedown")
          let timer = setInterval(() => {
          h -= 3;
        textBox.style.height = h + "px";
          if (h <=0) {
              textBox.style.height = 0+ "px";
            clearInterval(timer);
          }

        }, 20);
      }

    }
  }
};
</script>

<style lang="scss" scoped>
.box {
  width: 400px;
}
.main {
  margin-bottom: 10px;
  background-color: #ccc;
}
.title{
    i{
        transition: all 0.5s;
    }
}
.rotatedown{
    transform: rotate(90deg)
}
.text {
    font-size: 20px;
  height: 0px;
  overflow: hidden;
}
</style>