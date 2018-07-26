<template>
    <div class='shopmall'>
        <!-- search bar -->
        <div class='search-bar'>
            <van-row>
                <van-col span='3'><img :src="searchicon" alt="" width='50%'></van-col>
                <van-col span='16'>
                    <input type="text" class="search-input">
                </van-col>
                <van-col span='5'> <van-button size="mini">查找</van-button></van-col>
            </van-row>
        </div>
        <!-- swiper area -->
        <div class="swiper-area">
            <van-swipe :autoplay="2000">
                <van-swipe-item v-for="(banner,index) in bannerpicarray" :key="index">
                    <!-- <img :src="banner.imageUrl" width="100%"/> -->
                    <img v-lazy="banner.image" width="100%"/>
                </van-swipe-item>
            </van-swipe>
        </div>
        <!-- cstegoru 分类 -->
        <div class="type-bar">
            <div v-for="(cate,index) in category " :key='index'>
                <img v-lazy='cate.image' width='90%' alt="">
                <span>{{cate.mallCategoryName}}</span>
            </div>
        </div>
        <!-- banner 广告 -->
        <div class="ad-banner">
            <img v-lazy='adbanner' alt="" width="100%">
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name:'ShoppingMall',
    data(){
        return{
            msg:'monkeykg',
            searchicon:require('../../assets/images/position.png'),
            bannerpicarray:[
                // {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic001.jpg'},
                // {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic002.jpg'},
                // {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic003.jpg'},
            ],
            category:[],
            adbanner:'',
        }
    },
    created(){
        axios({
            url:'https://easy-mock.com/mock/5af2ca7c98fb450b11cb102f/kg/vueshpop',
            method:'get',
        }).then(response=>{
            console.dir(response)
            if(response.status==200){
                this.category=response.data.data.category;
                this.adbanner=response.data.data.advertesPicture.PICTURE_ADDRESS;
                this.bannerpicarray=response.data.data.slides;
            }
        }).catch(error=>{
            console.log(error)
        })
    }
}
</script>
<style lang="less">
    .shopmall{
        font-size:0.2rem;
        .search-bar{
            height:0.825rem;
            background: #e5017d;
            line-height: 0.825rem;
            & img{
                display:inline-block;
                margin-top:25%;
                margin-left:25%;
            }
            .search-input{
                width:100%;
                height:0.4875rem;
                border:none;
                border-bottom:1px solid #fff;
                background-color: #e5017d;
                color:#fff;
            }
            .van-col--5{
                text-align: center;
            }
        }
        .type-bar{
            display:flex;
            flex-direction: row;
            flex-wrap:nowrap;
            padding: 0 0.1rem 0.1rem 0.1rem;
            background: #fff;
            &>div{
                padding:0.1rem;
                text-align: center;
                flex:1;
            }
        }
    }
</style>

