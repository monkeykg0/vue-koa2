<template>
    <div class='shopmall'>
        <!-- search bar -->
        <div class='search-bar'>
            <van-row>
                <van-col span='3'>icon</van-col>
                <van-col span='16'>search input</van-col>
                <van-col span='5'> button</van-col>
            </van-row>
        </div>
    </div>
</template>
<script>
export default {
    name:'ShoppingMall',
    data(){
        return{
            msg:'monkeykg'
        }
    }
}
</script>
<style lang="less">
    .shopmall{
        font-size:0.2rem;
        .search-bar{
            height:0.5rem;
            background: #e5017d;
            line-height: 0.5rem;
        }
    }
</style>

