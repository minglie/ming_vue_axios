<template>
    <!-- 所有的内容要被根节点包含起来 -->
    <div id="home">

            <button @click="test01()">test01</button>
            <button @click="test02()">test02</button>
            <button @click="test03()">test03</button>
            <button @click="test04()">test04</button>
            <button @click="test05()">test05</button>
            <button @click="test06()">test06</button>
            <button @click="test07()">test07</button>
            <button @click="test08()">test08</button>
        
    </div>

</template>


<script>


   import axios from 'axios';

let host='http://minglie.vaiwan.com';

    export default{
        data(){
            return {               
                list:[]
            }
        },
        methods:{
/**
 * 两种get
 */
            test01(){
                var api=host+'/test01';
                axios.get(api).then((response)=>{
                   let r=response.data;
                    console.log(r)
                }).catch((error)=>{
                    console.log(error);
                })
                //////////////////////////
                 axios({
                     method:'get',
                     url:api,
                     params:{id:12}

                 }).then((response)=>{
                   let r=response.data;
                    console.log(r)
                }).catch((error)=>{
                    console.log(error);
                })
            },

             test02(){
                let formData=new FormData();
                formData.append("name","zs");
                axios.post(host+"/formData",formData).
                then((response)=>{
                   let r=response.data;
                    console.log(r)
                }).catch((error)=>{
                    console.log(error);
                })
            },

            test03(){
                  var api=host+'/test01';
                axios.all([
                    axios.get(api)  ,
                   axios.get(api)  
                ]).then(axios.spread((res1, res2) => {
                    console.log(res1);
                    console.log(res2);
                }));
            },

            test04(){
                  var api=host+'/test01';
                axios.all([
                    axios.get(api)  ,
                   axios.get(api)  
                ]).then(axios.spread((res1, res2) => {
                    console.log(res1);
                    console.log(res2);
                }));
            }

        },
        mounted(){  /*生命周期函数*/

           // this.getData();

        }
       

    }

</script>

<style lang="scss" scoped>

    /*css  局部作用域  scoped*/

    h2{

        color:red
    }

    
</style>