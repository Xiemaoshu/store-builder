<template>
  <div id="chuchuang_p">
    <div class="chuchuang_head">
      <p class="chuchuang_title">产品展示</p>
      <!-- <a class="chuchuang_more" href="" title="更多产品">更多产品 <i class="el-icon-d-arrow-right"></i></a> -->
    </div>
    <div class="chuchuang_con">
      <div class="product_item" :class="{has_bottom: length>4, has_bottom2: length>10 && index >3 && (length-4)%6 >0 && (length - (length-4)%6 >= index) || (length>10 && index >3 && (length-4)%6 ===0 && (parseInt((length-4)/6)*6)>index+1)}" v-for="(item, index) in list" :key="index">
        <div class="product_cart">
          <router-link :to="{path: '/detail' , query: {goodsId: item.id}}" class="product_img" target="_blank">
            <div class="product_img_box">
              <img class="product_img_con" :src="item.smallPic">
            </div>
          </router-link>
          <div class="product_info">
            <div class="product_title">
              <router-link :to="{path: '/detail' , query: {goodsId: item.id}}" class="product_word"><span>{{item.goodsName}}</span></router-link>
            </div>
          </div>
        </div>
        <router-link
          :to="{path: '/3D/3Dshow',query:{ id: item.threeId,homeShops: storeId,goodsId: item.id}}"
          v-if="item.threeId"
          target="_blank"
          class="t3D_play"
          title="商品支持3D展示">
          <img src="static/img/detail_play_3D.png">
        </router-link>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'chuchuang_p',
  props: {
    list: {
      type: Array
    },
    storeId: {
      type: String
    }
  },
  data () {
    return {
      length: this.list.length
    }
  }
}

</script>
<style lang="scss" scoped>
/* 主题颜色 #141414 */
  #chuchuang_p {
    width: 1226px;
  }
  .chuchuang_head {
    display: flex;
    align-item: center;
    justify-content: space-between;
    border: 1px solid #dbe3ef;
    border-top: 2px solid transparent;
    border-top-color: #141414;
    border-bottom: none;
    line-height: 30px;
    padding: 12px 20px;
    .chuchuang_title {
      font-size: 22px;
      line-height: inherit;
      font-weight: 400;
      color: #141414;
    }
    .chuchuang_more {
      font-size: 14px;
      color: #333;
      color: #2192d9;
      &:hover {
        text-decoration: underline;
        color: #ef7026;
      }
    }
  }
  .chuchuang_con {
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    border: 1px solid #dbe3ef;
  }
  .product_item {
    width: 25%;
    border-right: 1px solid #dbe3ef;
    position: relative;
    padding: 18px 15px;
    text-align: center;
    overflow: hidden;
    &:nth-child(-n+4).has_bottom {
      border-bottom: 1px solid #dbe3ef;
    }
    &:nth-child(n).has_bottom2 {
      border-bottom: 1px solid #dbe3ef;
    }
    &:nth-child(6n+4) {
      border-right: 1px solid transparent;
    }
    .product_cart {
      width: 160px;
      display: inline-block;
      vertical-align: top;
      font-size: 14px;
      line-height: 16px;
      text-align: left;
      .product_img {
        margin-bottom: 13px;
        display: block;
        .product_img_box {
          width: 100%;
          height: 100%;
          overflow: hidden;
          position: relative;
          .product_img_con {
            display: block;
            max-width: 100%;
            max-height: 100%;
          }
        }
      }
      .product_info {
        color: #666;
        overflow: hidden;
        width: 100%;
        .product_title {
          width: 100%;
          max-height: 38px;
          white-space: normal;
          line-height: 20px;
          word-break: break-all;
          overflow: hidden;
          text-overflow: ellipsis;
          -webkit-box-orient: vertical;
          display: -webkit-box;
          -webkit-line-clamp: 2;
          .product_word {
            color: #333;
            word-break: break-all;
            &:hover {
              color: #ef7026;
              text-decoration:underline;
            }
          }
        }
        .product_price {
          color: #333;
          font-weight: 700;
          margin-top: 5px;
          white-space: nowrap;
          overflow: hidden;
          text-overflow: ellipsis;
          text-align: center;
        }
      }
    }
    .t3D_play {
      position: absolute;
      bottom: 8px;
      z-index: 100;
      font-size: 36px;
      color: #404040;
      border-radius: 50%;
      line-height: 35px;
      width: 45px;
      height: 45px;
      left: initial;
      right: 6px;
      border: 1px solid transparent;
      cursor: pointer;
      &:hover {
        border: 1px solid rgba(64, 64, 64, 0.33);
      }
      &>img {
        max-width: 100%;
        max-height: 100%;
      }
    }
  }
  .product_item {
    &:nth-child(n+5) {
      width: 16.667%;
    }
  }
</style>
