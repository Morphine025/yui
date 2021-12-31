<script>
import {ref} from 'vue'
  export default {

  setup(){
    
  let list=[{names:'旁氏洗发露',price:99,effect:'防脱'}
  // ,{names:'旁氏洗发露',price:99,effect:'去屑'}
  ]
  let addes=ref([])
  let num=ref(addes.value.length+1)
    let arr=JSON.parse(JSON.stringify(addes.value))
  let add=(v)=>{
    console.log(v.names);

    console.log(addes.value.length);
    if(addes.value.length==0){
      addes.value.push(v)
    }else{
      num.value++
    }
    console.log(num);

  }
 let  delet=()=>{
   console.log("11");
      console.log(addes.value);
   addes.value.shift()
   console.log(addes.value);
  }


    return {
      list,add,addes,num,delet
    }
  },


}


</script>

<template>
  <!-- {{list}} -->
        <div class="car" style="margin-bottom:50px;">
            <h2>商品列表</h2>
            <div class="good">
                <table><tr><td width=30%>商品名称</td><td width=20%>单价</td><td width=20%>功效</td><td width=30%>操作</td></tr></table>
            </div>
            <div class="goods"  v-for="(item,index) in list" :key="index">
                <table><tr><td width=30%>{{item.names}}</td><td width=20%>{{item.price}}</td><td width=20%>{{item.effect}}</td><td width=30%><a><button class="btn1" style="width:100px;" @click="add(item)">加入购物车</button></a></td></tr></table>
            </div>

    </div>

    <div class="car"  v-for="(item,index) in addes" :key="index">
            <h2>购物车</h2>
            <div class="good">
                <table><tr><td width=30%>商品名称</td><td width=20%>单价</td><td width=20%>数量</td><td width=30%>操作</td></tr></table>
            </div>
            <!-- {{addes}} -->
            <div class="goods">
                <table><tr><td width=30%>{{item.names}}</td><td width=20%>{{item.price}}</td><td width=20%><input type="number" v-model="num" style="width: 50px;height:20px;" min="1"/></td><td width=30%><a><button class="btn1" @click="delet">删除</button></a></td></tr></table>
            </div>
            <!-- {{num}} -->
            <!-- <div class="goods">
                <table><tr><td width=30%>旁氏洗发露</td><td width=20%>99</td><td width=20%><input type="number" value="1" style="width: 50px;height:20px;" min="1"/></td><td width=30%><a><button class="btn1">删除</button></a></td></tr></table>
            </div> -->
            <div class="goods2">
                <table><tr><td width=300></td><td width=30%>小计：{{item.price*num}}</td><td width=30%>总数：{{num}}</td></tr></table>
            </div>
            <div class="goods1">
                <table><tr><td width=50%><button class="btn2">确认购买</button></td><td><button class="btn3">全部清空</button></td></tr></table>
            </div>
    </div>
</template>

<style scoped>
            body{
                overflow: hidden;
                text-align: center;
            }
            .car{
                width:60%;
                border: 1px solid #F88020;
                border-radius: 18px;
                margin-left: 300px;
            }
            .car .good{
                background-color: #F88020;
                height:55px;
                font-size: 22px;
                color:white;
                line-height: 55px;
                font-weight: 200;
                border-radius: 18px 18px 0 0;
                margin-bottom: 20px;
                
            }
            .car .good table{
                width:100%;
            }
            .car .goods{
                height:45px;
                line-height: 45px;
                font-size: 20px;
                font-weight: 200;
            }
            .car .goods table{
                width:100%;
            }
            .car .goods table .btn1{
                width: 70px;
                height:28px;
                border: 2px solid #46B3E6;
                background-color: white;
                color: #46B3E6;
                border-radius: 4px;
                font-weight: 600;
            }
            .car .goods table button:hover{
                background-color: #46B3E6;
                color: white;
            }
            .car .goods1{
                margin-top: 10px;
                background-color:pink ;
                height:50px;
                font-size: 19px;
                color:white;
                line-height: 50px;
                font-weight: 200;
                border-radius:0 0 10px 10px ;
            }
            .car .goods2{
                border-top: 1px solid #F88020;
                margin-top: 10px;
                height:50px;
                font-size: 19px;
                line-height: 50px;
                font-weight: 200;
                border-radius:0 0 10px 10px ;
            }
            .car .goods1 table{
                width:100%;
            }
            .car .goods1 .btn2{
                width: 80px;
                height:28px;
                border: 2px solid #21BF73;
                background-color: white;
                color: #21BF73;
                border-radius: 4px;
                font-weight: 600;
            }
            .car .goods1 .btn2:hover{
                color:white;
                background-color: #21BF73;
            }
            .car .goods1 .btn3{
                width: 80px;
                height:30px;
                border: 2px solid #FF0000;
                background-color: white;
                color: #FF0000;
                border-radius: 4px;
                font-weight: 600;
            }
            .car .goods1 .btn3:hover{
                color:white;
                background-color:#FF0000 ;
            }
</style>
