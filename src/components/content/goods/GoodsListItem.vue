<template>
  <div class="goods-list-item" @click="itemClick">
    <img :src="goodsItem.show.img" alt="" @load="imageLoad">
    <div class="info-goods">
      <p>{{goodsItem.title}}</p>
      <span class="price">{{goodsItem.price}}</span>
      <span class="collect">{{goodsItem.cfav}}</span>
    </div>
  </div>
</template>

<script>
  export default {
    name: "GoodListItem",
    props:{
      goodsItem:{
        type:Object,
        default(){
          return {}
        }
      }
    },
    methods:{
      imageLoad() {
        this.$bus.$emit('itemImageLoad')
      },
      itemClick(){
        this.$router.push("/detail/" + this.goodsItem.iid)
      }
    }
  }
</script>

<style scoped>
  .goods-list-item{
    width: 48%;
    font-size: 12px;

  }
  .goods-list-item img {
    width: 100%;
    border-radius: 5px;
  }
  .info-goods {
    padding: 6px;
    text-align: center;
  }
  .info-goods p {
    margin-bottom: 3px;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .info-goods .price {
    color: var(--color-high-text);
    margin-right: 20px;
  }
  .info-goods .collect {
    position: relative;
  }
  .info-goods .collect::before{
    /*display: inline-block;*/
    content: "";
    position: absolute;
    top: -1px;
    left: -15px;
    width: 14px;
    height: 14px;
    background: url("~assets/img/common/collect.svg") 0 0/14px 14px;
  }
</style>