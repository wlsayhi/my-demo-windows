<template>
    <div>
      <canvas ref="canvasText">
          你的浏览器不支持 canvas
      </canvas>
    </div>
</template>
           
<script>
export default{
     data () {
         return {
             ctx: null,
         }
     },
     props: {
         text: {
             type: String,
             default: '请输入搜索内容'
         }
     },        
     mounted() {
         let canvas = this.$refs.canvasText;
         console.log(canvas,'cc');
         this.ctx = canvas.getContext('2d');
         for(let i=0; i<100; i++) {
             this.getGraph(Math.floor(Math.random()*1000), Math.floor(Math.random()*100), canvas)
         }
     },
     watch: {
         text(val) {
         }
     },
     methods: {
         getGraph(x, y, canvas) {
             this.draw(x, y, canvas)
         },
         //绘制圆球
         draw(x, y, canvas) {
            //  this.ctx.clearRect(0,0,canvas.width,canvas.height);
            //  this.ctx.save()
             this.ctx.beginPath();
             this.ctx.fillStyle = 'rgb' + this.rgb();   
             this.ctx.arc(x,y,2,0*Math.PI/180,360*Math.PI/180);
             this.ctx.fill()
            console.log('来了');
            
            //  requestAnimationFrame(this.draw);
         },
         rgb(){//rgb颜色随机
			var r = Math.floor(Math.random()*256);
			var g = Math.floor(Math.random()*256);
			var b = Math.floor(Math.random()*256);
			var rgb = '('+r+','+g+','+b+')';
			return rgb;
         },
         //动画
         move() {

         },
     },
}
</script>
<style scoped>
  canvas {
    width: 100%;
    height: 100%;
    position : absolute;
    position: fixed;
    top: 0;
    left: 0;
    margin: 0 auto;
    z-index: 9;
  }          
</style>