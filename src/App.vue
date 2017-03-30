<template>
    <div id="app">
        <div id="pageContain">
            <!-- 首页简介 -->
            <div class="page section1  current">
                <div class="contain">
                    <div class="myavatar"><img class="z-depth-3" :src="myInfo.avatar"></div>
                    <h1 class="myname">{{myInfo.name}}</h1>
                    <p class="subtitle">{{myInfo.description}}</p>
                    <h5>{{myInfo.position}}</h5>
                    <a data-target="modal1" class="modal-trigger btn mybtn">简&nbsp;&nbsp;介</a>
                    <!-- Modal Structure -->
                    <div id="modal1" class="modal mydatas">
                        <div class="modal-content">
                            <h6>基本资料</h6>
                            <div class="row">
                                <span v-for="item in myInfo.infos" class="col s12">{{item}}</span>
                            </div>
                        </div>
                        <div class="modal-footer">
                            <a href="#!" class=" modal-action modal-close waves-effect waves-green btn-flat">关闭</a>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 个人技能 -->
            <div class="page section2">
                <div class="contain">
                    <h4 class="text-center">个人技能</h4>
                    <div class="myskills text-center">
                        <a v-for="item in myInfo.skills" :class="{'stress':item.type===1}">{{item.text}}</a>
                    </div>
                </div>
            </div>
            <!-- 工作经验 -->
            <div class="page section3">
                <div class="contain">
                    <h4 class="text-center">工作经验</h4>
                    <div class="experience">
                        <div class="time-line"></div>
                        <div class="work-content">
                            <div v-for="(item, index) in myInfo.works" class="word-items">
                                <div class="work-item">
                                    <div class="year-flag rel">
                                        {{item.year}}
                                        <i class="mdi-action-query-builder"></i>
                                    </div>
                                </div>
                                <div class="work-item">
                                    <div class="mouth-flag rel">
                                        <span>{{item.month}}</span>
                                        <i class="mdi-image-panorama-fisheye"></i>
                                    </div>
                                    <div class="work-box" :class="classMap[index]">
                                        <p>{{item.description}}</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- 个人作品 -->
            <div class="page section4 ">
                <div class="contain">
                    <h4 class="text-center">个人作品/项目</h4>
                    <div class="p4subtitle">
                        <!-- （以下所有页面都是我做的） -->
                    </div>
                    <ul class="collection row">
                        <li class="collection-item col s11 m5 avatar" v-for="(item, index) in myInfo.production1">
                            <a target="_blank" :href="item.link">
                                <i class="circle" :class="productionMap1[index]"></i>
                                <span class="title">{{item.title}}</span>
                            </a>
                            <p>{{item.description}}
                                <br>
                                <a target="_blank" :href="item.link">{{item.text}}</a>
                            </p>
                            <a href="#" class="secondary-content"><i class="mdi-action-grade"></i></a>
                        </li>
                    </ul>
                </div>
            </div>
            <div class="page section4 ">
                <div class="contain">
                    <h4 class="text-center">个人作品/项目</h4>
                    <div class="p4subtitle">
                        <!-- （以下所有页面都是我做的） -->
                    </div>
                    <ul class="collection row">
                        <li class="collection-item col s11 m5 avatar" v-for="(item, index) in myInfo.production2">
                            <a target="_blank" :href="item.link">
                                <i class="circle" :class="productionMap2[index]"></i>
                                <span class="title">{{item.title}}</span>
                            </a>
                            <p>{{item.description}}
                                <br>
                                <a target="_blank" :href="item.link">{{item.text}}</a>
                            </p>
                            <a href="#" class="secondary-content"><i class="mdi-action-grade"></i></a>
                        </li>
                    </ul>
                </div>
            </div>
            <!-- 求职意向 -->
            <div class="page section5">
                <div class="contain">
                    <h4 class="text-center">求职意向</h4>
                    <div class="expect">
                        <p v-for="item in myInfo.hope"><i class="mdi-action-label-outline"></i>{{item}}</p>
                    </div>
                </div>
            </div>
            <!-- 联系方式 -->
            <div class="page section6">
                <div class="contain">
                    <h4 class="text-center">联系方式/社交</h4>
                    <div class="callme">
                        <p v-for="item in myInfo.callme">{{item.title}}<a :href="item.link">{{item.text}}</a></p>
                    </div>
                    <div class="social">
                        <a href="tel:18576689103" class="call-item"><img src="../static/images/call_phone.png"></a>
                        <a target="_blank" href="https://www.zhihu.com/people/dbdl" class="call-item"><img src="../static/images/call_zhihu.png"></a>
                        <a target="_blank" href="http://wpa.qq.com/msgrd?v=3&uin=734436664&site=qq&menu=yes" class="call-item"><img src="../static/images/call_qq.png"></a>
                        <a target="_blank" href="http://huaban.com/eleyvzru6h/" class="call-item"><img src="../static/images/call_huaban.png"></a>
                        <a target="_blank" href="https://github.com/biao734436664" class="call-item"><img src="../static/images/call_github.png"></a>
                        <a class="call-item modal-trigger" href="#modal-wx"><img src="../static/images/call_wx.png"></a>
                        <div id="modal-wx" class="modal">
                            <div class="modal-content">
                                <h5>扫一扫，添加好友</h5>
                                <p class="text-center"><img src="../static/images/weixin.jpg"></p>
                            </div>
                            <div class="modal-footer">
                                <a href="#!" class="modal-action modal-close waves-effect waves-green btn-flat">确定</a>
                            </div>
                        </div>
                    </div>
                    <div class="text-center">
                        <a href="../static/mengdebiao_resume.pdf" class="waves-effect waves-light btn btn-download"><i class="mdi-file-file-download left"></i>下载简历</a>
                        <a id="mobile-btn" class="waves-effect waves-light teal btn modal-trigger btn-download" href="#modal-mobile"><i class="mdi-hardware-phone-iphone left"></i>手机查看</a>
                        <div id="modal-mobile" class="modal">
                            <div class="modal-content">
                                <h5>扫一扫，手机查看(我不会告诉你微信上浏览效果更佳！)</h5>
                                <p class="text-center"><img src="../static/images/mobile.png"></p>
                            </div>
                            <div class="modal-footer">
                                <a href="#!" class="modal-action modal-close waves-effect waves-green btn-flat">确定</a>
                            </div>
                        </div>
                    </div>
                    <div class="share">
                        给彼此一个机会，还彼此一个精彩！
                    </div>
                </div>
            </div>
        </div>
        <!-- 右侧导航 -->
        <ul id="navBar">
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
            <li></li>
        </ul>
    </div>
</template>
<script>
export default {
    name: 'resume',
    data() {
        return {
            myInfo: Object
        }
    },
    created() {
        let url = '../static/data.json';
        this.$http.get(url).then(response => {
            this.myInfo = response.data.myInfo;
            console.log('成功')
            this.$nextTick(() => {
                this._silderFullPage();
            });
        }, response => {
            console.log('失败')
        })

        this.classMap = ['wow_01', 'wow_02', 'wow_04', 'wow_05'];
        this.productionMap1 = ['mdi-action-stars', 'mdi-action-receipt', 'mdi-navigation-apps', 'mdi-action-shopping-basket'];
        this.productionMap2 = ['mdi-hardware-phone-android', 'mdi-action-face-unlock', 'mdi-action-shopping-cart', 'mdi-action-dashboard'];
    },
    methods: {
        _silderFullPage() {
            this.runPage = new FullPage({
                id: 'pageContain', // 外层包裹id
                slideTime: 800, // 每页切换时间(毫秒)
                continuous: false, // 是否循环(即能从最后页跳到第一页面)
                effect: { // 效果参数
                    transform: {
                        translate: 'Y', // 'X'|'Y'|'XY'|'none'
                        scale: [.1, 1], // 缩放 [scalefrom, scaleto] 表示 [起始缩放比例, 结束时缩放比例]
                        rotate: [60, 0] // 旋转 [rotatefrom, rotateto] 表示 [起始旋转角度, 结束时旋转角度]
                    },
                    opacity: [0, 1] // 透明度 [opacityfrom, opacityto] 表示 [起始透明度, 结束时透明度]
                },
                mode: 'wheel,touch,nav:navBar', // 转换模式:'滚轮,触摸,导航条:导航条id'
                easing: 'ease-in-out' // easing('ease','ease-in','ease-in-out' or use cubic-bezier like [.33, 1.81, 1, 1];
            });
        }
    }
}
</script>
<style lang="less">
// @import "../static/css/style.less";
</style>
