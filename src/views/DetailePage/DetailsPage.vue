<template>
<div>
    <seach />


    <!-- <el-steps :active="1" class="centered-steps">
        <el-step title="预览" description="选择您的设备" />
        <el-step title="回收" description="设备信息" />
        <el-step title="选择" description="Some description" />
        <el-step title="成功！" description="Some description" />
    </el-steps> -->
    <el-header style="margin-top: 20px;">
        <el-steps :active="1" align-center>
    <el-step title="Step 1" description="Some description" />
    <el-step title="Step 2" description="Some description" />
    <el-step title="Step 3" description="Some description" />
    <el-step title="Step 4" description="Some description" />
  </el-steps>
    </el-header>

    <div class="product-details">
      
      <div class="left-section">
        
        <div class="display">
          <div class="product-image">
            <el-image
            style="width: 300px; height: 300px;"
            :src="product.currentimageUrl"
            :zoom-rate="1.2"
            :preview-src-list="product.srcList"
            :initial-index="0"
            fit="cover" 
            alt="Product Image"
          />
          </div>
        </div>
  
        <el-carousel :interval="4000" type="card" height="200px" v-model="activeIndex">
          <el-carousel-item v-for="image in product.imageList" :key="image.id">
            <img :src="image.url" alt="Carousel Image" @click="changeImage(image.url)">
          </el-carousel-item>
        </el-carousel>
  
      </div>
  
      <div class="right-section">
  
        <el-card class="box-card"> <!--  产品信息-->
  
          <template #header>
            <div class="card-header">
              <h2 class="product-name">{{ product.name }}</h2>
            </div>
          </template>
  
          <!-- <p class="product-description">{{ product.description }}</p>    产品描述的表单 -->
  
          <!-- 产品具体描述信息 -->
          <el-descriptions
            direction="vertical"
            :column="4"
            :size="size"
            border
          >
  
            <el-descriptions-item label="设备类别">{{ product.type }}</el-descriptions-item>
            <el-descriptions-item label="设备型号">{{ product.name }}</el-descriptions-item>
            <el-descriptions-item label="使用时长">两年</el-descriptions-item>
            <el-descriptions-item label="市场价格">{{product.price}}</el-descriptions-item>
  
            
  
            <el-descriptions-item label="其他信息"
              >{{product.description}}
            </el-descriptions-item>
  
          </el-descriptions>
  
  
          <div class="container">
            <div class="button-group">
              <el-button class="button" type="primary" @click="goToRecyclePage">回收界面</el-button>
              <span style="width:90px;"></span>
              <el-button class="button" type="success" @click="goToRepairPage">维修界面</el-button>
            </div>
          </div>
  
        </el-card>
        
      </div>
    </div>
  </div>

</template>
  
  <script>
  import header from '/src/components/header.vue'
  export default {
    name:'DetailsPage',
    data() {
      return {
        product: {
          type:'Phone',
          name: 'iphone11',
          description: '高性能手机',
          price:'100$',
          currentimageUrl:require('/public/p.jpg'), // 图片路径根据实际情况进行调整
          imageList: [
            { id: 1, url: require('/public/p.jpg') }, // 图片路径根据实际情况进行调整
            { id: 2, url: require('/public/p.jpg') }, 
            { id: 3, url: require('/public/p.jpg') }, 
            { id: 4, url: require('/public/p.jpg') }, 
            { id: 5, url: require('/public/p.jpg') } 
          ],
          srcList : [
          '/public/p.jpg',
          '/public/p.jpg',
          '/public/p.jpg',
          '/public/p.jpg',
          '/public/p.jpg',
  ]
        }, 
        activeIndex:0
      };
    },
    methods: {
      goToRecyclePage() {
        // 进入回收界面的逻辑
        this.$router.push('/RecoveryPage');
      },
      goToRepairPage() {
        // 进入维修界面的逻辑
        this.$router.push('/RepairPage');
      },
      changeImage(imageUrl){
        this.product.currentimageUrl = imageUrl;
        this.activeIndex = this.product.imageList.findIndex(image => image.url === imageUrl);
      },
  
    },
    watch:{
      activeIndex(newIndex) {
        this.product.currentimageUrl = this.product.imageList[newIndex].url;
      }
    },
    components: {
        "seach": header,
    }
  };
  </script>
  
  
  
  <style>
  .left-section {
    flex: 1;
    margin-right: 20px;
  }
  
  .container {
    display: flex;
    justify-content: center;
  }
  
  .display{
    display: flex;
    overflow-x: auto; /* 横向滚动 */
    justify-content: center;
    margin-top: 100px;
    margin-bottom: 100px;
  }
  
  .product-image {
    width: 300px; /* 统一的正方形尺寸 */
    height: 300px;
    flex-shrink: 0; /* 防止缩小 */
  }
  
  .product-image img{
    width: 100%;
    height: 100%;
    object-fit: cover; /* 填充容器并裁剪 */
  }
  
  .box-card{
    justify-content: center;
    height: 600px;
    width: 700px;
    margin-top: 100px;
    left: 10%;
  }
  
  .product-details {
    display: flex;
    justify-content: center;
    align-items: flex-start;
  }
  
  .el-carousel__item h3 {
    color: #475669;
    opacity: 0.75;
    line-height: 200px;
    margin: 0;
    text-align: center;
  }
  
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  
  .el-carousel__item:nth-child(2n + 1) {
    background-color: #d3dce6;
  }
  
  .image-list {
    display: flex;
    overflow-x: auto; /* 横向滚动 */
  }
  
  .image-item {
    width: 200px; /* 统一的正方形尺寸 */
    height: 200px;
    margin-right: 10px; /* 图片间的间距 */
    flex-shrink: 0; /* 防止缩小 */
  }
  
  .image-item img {
    width: 100%;
    height: 100%;
    object-fit: cover; /* 填充容器并裁剪 */
  }
  

  .right-section {
    flex: 1;
  }
  
  .el-descriptions {
    margin-top: 20px;
  }
  
  .product-name {
    text-align: center;
    font-size: 24px;
    margin-bottom: 10px;
  }
  
  .product-description {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .container {
    display: flex;
    justify-content: center;
    margin-top: 100px;
  }
  
  .button-group {
    display: flex;
    justify-content: center;
  }
  
  .button{
    width: 150px;
    height: 75px;
  }
  
  .demo-image__error .image-slot {
    font-size: 30px;
  }
  .demo-image__error .image-slot .el-icon {
    font-size: 30px;
  }
  .demo-image__error .el-image {
    width: 100%;
    height: 200px;
  }

  </style>
  