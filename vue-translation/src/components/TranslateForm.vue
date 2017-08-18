<template>
  <div id="translateForm" class="row">
    <div class="col-md-6 col-md-offset-3">
      <form id="transForm" v-on:submit="formSubmit" class="well form-inline">
         <input type="text" v-model="textToTranslate" placeholder="输入需要翻译的内容" class="form-control">
          <select class="form-control" v-model="language">
            <option value="en">英语</option>
            <option value="ru">俄语</option>
            <option value="ko">韩语</option>
            <option value="ja">日语</option>
          </select>
          <input type="submit" value="翻译" class="btn btn-primary">
      </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data:function() {
        return {
          textToTranslate:"",
          language:""
        }
    
  },
  methods:{
    formSubmit:function (e) {
      this.$emit("formSubmit",this.textToTranslate,this.language);
      e.preventDefault();
    }
  },
  created:function(){
    this.language="en";
  }

}
</script>

<style>
#transForm{
  border-radius: 10px;
  border:1px solid #ccc;
}
</style>
