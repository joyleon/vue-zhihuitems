<template>
  <div id="datalist">
    <div class="hd">现在一共有：<strong class="item_count">{{items.length}}</strong> 个条目</div>
    <div class="list">
      <div class="row" v-for='item in items' track-by="$index" ><div>{{item.name}}<input v-model=item.name v-show=item.isEdit /></div><a href="javascript:;" v-on:click="delateItem($index)" >删除</a><a href="javascript:;" v-on:click="editItem($index)" v-show=!item.isEdit >修改</a><a href="javascript:;" v-on:click="storeItem($index)"  v-show=item.isEdit >保存</a></div>
    </div>
    <div class="ft"><a href="javascript:;" v-on:click="addItem" >新增条目</a></div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isEdit:false,
      items:[
        {name:'这是第一条',isEdit:false},
        {name:'这是第二条',isEdit:false},
        {name:'花儿为什么这么红',isEdit:false},
        {name:'你知道小月月是哪个不？',isEdit:false},
        {name:'人生就是一个杯具',isEdit:false}
      ]
    }
  },
  methods:{
    addItem:function(){
      this.items.push({name:'未命名',isEdit:false});
    },
    editItem:function(index){
      this.items[index].isEdit = true;
    },
    storeItem:function(index){
      this.items[index].isEdit = false;
    },
    delateItem:function(index){
      this.items.splice(index,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{padding:0;margin:0;}
a{outline:none;text-decoration:none;}
body{font: 14px/1.5 arial}
.w960{width:560px;margin:0 auto;}
.hd{background: #059ed3;color:#fff;}
.hd,.ft{padding:5px;}
.ft{background:#ccc;text-align:right;}
.row{padding:5px;border-bottom:solid 1px #eee;}
.row div{display:inline}
.row a{float:right;}
.ft a{color:green;font-weight:bold}
code{display:block;border:solid 1px #666;padding:10px;background:#ffffc0;}
h3{margin:10px 0;color:#ff9900;}
input{border:solid 1px #c0c0c0;line-height:1.5em;height:1.5em}
</style>
