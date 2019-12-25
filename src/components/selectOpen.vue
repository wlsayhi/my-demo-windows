<template>
    <div class="open">
       <div>
         <p>打开</p>
         <p>删除</p>
         <p>重命名</p>
       </div>
    </div>
</template>
           
<script>
export default{
   name: 'selectOpen'          
}
</script>
<style lang="scss" scoped>
  .open {
    position: absolute;
    top: 20px;
    left:50px;
    z-index: 1;

    div {
      width: 80px;
      height: 120px;
      line-height: 30px;
      padding-top: 10px;
      background: #f0f0f0;
      border: 1px solid #eee;
      cursor: default;

      p {
        padding-left: 20px;

        &:hover {
          background: #fff;
        }
      }
    } 
  }
     
</style>