<!-- eslint-disable vue/no-deprecated-slot-attribute -->
<template>
    <el-container>
        <!--搜索栏部分-->
        <el-header>
            <seach />
        </el-header>
        <el-container>
            <!--边栏部分-->
            <el-aside width="200px">
                <div class="side">
                    <el-aside>
                        <el-row class="tac">
                            <el-col :span="26">
                                <el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen"
                                    @close="handleClose">
                                    <el-menu-item index="1">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator one</span>
                                    </el-menu-item> <el-menu-item index="2">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator two</span>
                                    </el-menu-item> <el-menu-item index="3">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator three</span>
                                    </el-menu-item> <el-menu-item index="4">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator four</span>
                                    </el-menu-item>
                                    <el-menu-item index="5">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator Five</span>
                                    </el-menu-item>
                                    <el-menu-item index="6">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator Six</span>
                                    </el-menu-item>
                                    <el-menu-item index="7">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator Seven</span>
                                    </el-menu-item>
                                    <el-menu-item index="8">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator Eight</span>
                                    </el-menu-item>
                                    <el-menu-item index="9">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator Nine</span>
                                    </el-menu-item>
                                    <el-menu-item index="10">
                                        <el-icon>
                                            <setting />
                                        </el-icon>
                                        <span>Navigator Ten</span>
                                    </el-menu-item>
                                </el-menu>
                            </el-col>
                        </el-row>
                    </el-aside>
                </div>
            </el-aside>
            <el-container>
                <!--具体部分-->
                <el-main>
                    <el-row> <el-col v-for="item in list" :key="item.id" @click="change(item.id)" :span="4" :offset="1">
                        
                        
                            <!-- <el-card :body-style="{ padding: '0px' }" shadow="hover" >
                                <div @click="goToDetailsPage">
                                <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png"
                                    class="image" />
                                <div style="padding: 14px">
                                    <span>Yummy hamburger</span>
                                    <div class="bottom">
                                        <time class="time">{{ currentDate }}</time>
                                    </div>
                                </div>
                            </div>
                            </el-card> -->

                            <el-card :body-style="{ padding: '0px' }" shadow="hover">
                                <div @click="goToDetailsPage">
                                    <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image" />
                                    <div style="padding: 14px">
                                    <span>Yummy hamburger</span>
                                    <div class="bottom">
                                        <time class="time">{{ currentDate }}</time>
                                    </div>
                                    </div>
                                </div>
                            </el-card>
                                                  
                        </el-col>
                    </el-row>
                </el-main>
                <!--机型部分-->

                <el-footer>
                    <el-col :span="5" :offset="4">
                        <el-pagination background layout="prev, pager, next" :total="100" />
                    </el-col>
                    <!--
                    <div class="type" >
                        <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" :ellipsis="false"
                            @select="handleSelect">
                            <el-col :span="4" >
                                <el-menu-item index="1">笔记本</el-menu-item>
                            </el-col>
                            <el-col :span="4">
                                <el-menu-item index="2">手机</el-menu-item>
                            </el-col>
                            <el-col :span="4">
                                <el-menu-item index="3">平板</el-menu-item>
                            </el-col>
                            <el-col :span="4">
                                <el-menu-item index="4">耳机</el-menu-item>
                            </el-col>
                            <el-col :span="4">
                                <el-menu-item index="5">手表</el-menu-item>
                            </el-col>
                            <el-col :span="4">
                                <el-menu-item index="6">智能眼镜</el-menu-item>
                            </el-col>
                        </el-menu>
                    </div>-->
                </el-footer>
            </el-container>
        </el-container>
    </el-container>
    <!--导航栏部分-->
</template>

<script>
import header from '../components/header.vue'
import { ref } from 'vue'
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: "evaluatepage",

    data() {
        return {
            key: undefined,
            list: [
                { id: 1, },
                { id: 2, },
                { id: 3, },
                { id: 4, },
                { id: 5, },
                { id: 6, },
                { id: 7, },
                { id: 8, },
            ],
            currentDate: ref(new Date()),

        }
    },
    components: {
        
        "seach": header,
    },
    methods: {
        change(key) {
            this.key = key;
            console.log(this.key);
        },
        goToDetailsPage() {
        console.log("到这")
        this.$router.push({ name: 'DetailsPage' });
        }
    },
    
}
</script>


<style scoped>
.time {
    font-size: 12px;
    color: #999;
}

.bottom {
    margin-top: 13px;
    line-height: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.button {
    padding: 0;
    min-height: auto;
}

.image {
    width: 100%;
    display: block;
}

.el-row {
    margin-bottom: 20px;
}

.type {
    flex-grow: 1;
}
</style>

