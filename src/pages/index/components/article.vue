<template>
<div class="article-wrapper">
    <div class="article-box">

        <h2>深|度|好|文</h2>

        <div class="article-list">
            <transition-group  tag="div"  name="list" class="list-show"  >
                <a 
                :href="item.url" 
                v-for="(item, index) in articleArr" 
                :key="item.id"  
                v-show="index===currentIndex" 
                @mouseenter="stop" 
                @mouseleave="go">

                    <div class="article">
                        <i class="logo" ></i>
                        <div class="text-box">  
                            <p>{{item.description}}</p>
                        </div>
                        <span class="index">{{index+1}}</span>
                        <img  :src="item.head_image" class="images" alt="">
                        <p class="img-title">{{item.title}}</p>
                    </div>
                </a>
                 
                 
            </transition-group> 
            


            <div class="code">
                <img src="https://dapp.review/assets/8ec37623.svg" alt="扫码获取更多">
                <p>扫码获取更多</p>
            </div>

        </div>

        
    </div>
    <div class="carousel-items">
        <span v-for="(item,index) in articleArr.length" 
        :key="index" :class="{'active':index===currentIndex}" 
        @mouseenter="change(index)"
        @mouseleave="go"
        ></span>
    </div>


</div>

</template>

<script>
export default {
    data(){
        return {
            articleArr:[{"id":60,"title":"336亿的生意——你所不了解的Dapp这一年（上）","subtitle":null,"head_image":"https://media.dappreview.cn/images/DR-Jason/ykrsBxfjhXsya6jKke5P3GwPyi3xhr2b.jpg","content":null,"description":"导读：2018年是Dapp元年。注意，这是特殊的一年，距离上次金融海啸整整十年，全球经济陷入又一次大滑坡。当这些结构性矛盾传导到游戏、金融等虚拟行业，就构成了Dapp登上历史舞台的契机。说人话的话很简单——来自生存压力的时代焦虑。游戏业的传统生态到了强弩之末，变成寡头政治；区块链需要游戏来落地，否则这个难得的财富通道将沦为空气；中产阶级对财富保值的焦虑，三者一拍即合。很多人对区块链游戏、Dapp的态度从观望转向看似主动地加入，甚至只是焦虑使然的被动行为。回过头来看，Dapp的故事就是在这种痛苦和挣扎中开启","url":"https://dapp.review/article/60"},{"id":61,"title":"336亿的生意——你所不了解的Dapp这一年（下）","subtitle":null,"head_image":"https://media.dappreview.cn/images/DR-Jason/dYXcm462spjPsWKT6bZXhscR46Mrie3P.jpg","content":null,"description":"如果说2018年上半年是群魔乱舞的黑暗中世纪，那么从7月份开始，Dapp则开始迎来了文艺复兴的先兆。下半年，越来越多游戏业老兵、头部企业开始布局游戏；捧着保温杯在500强的极客们，在加密艺术品这种新玩意儿中“重振雄风”；虽然整体还是BC游戏的天下，但技术性确实越来越强。作品性质的内容越来越多，这是个好彩头。同时我们针对钱包和去中心化交易所谈了一些自己的观点，有理由相信，在接下来的2019年，区块链将出现更多有意义、有意思的产品，而竞争，将会更加白热化。（万字长文预警）","url":"https://dapp.review/article/61"},{"id":62,"title":"区块链没有C端","subtitle":null,"head_image":"https://media.dappreview.cn/images/DR-Jason/4RjDfxjt3rHQmsjGCTwkje4pCwbkx6pK.jpg","content":null,"description":"导读：被互联网教育过的人，即使是傻子也明白一个道理：谁把握住用户谁就牛逼。尤其在中国，这块大陆上诞生了如微信、美团和拼多多这样垄断C端的「奇葩」巨头。其实，这才是人们呼吁区块链出现杀手级应用背后的逻辑。虽然每个人都嚷嚷着「不要用互联网的经验平行地理解区块链」，但我们似乎总是这样做的。用区块链做C端，会不会是现代版刻舟求剑？","url":"https://dapp.review/article/62"},{"id":64,"title":"「游戏资产上链」毫无价值？","subtitle":null,"head_image":"https://media.dappreview.cn/images/DR-Jason/HjGkxhtAwbzT5RrKxSr5Cinack4GffkB.jpg","content":null,"description":"导读：关于资产上链是否有意义的争议由来已久，一部分人误解了资产上链的概念。它首先是一个动作，上链让虚拟道具的性质无限逼近于实物资产，就像小浣熊水浒卡片、小时候传给初恋的纸条。但如果要它成为一个商业模式，在免费游戏的市场中分一杯羹，则是更大的问题。正巧，DappReview最近刚好有一些思考。","url":"https://dapp.review/article/64"},{"id":66,"title":"微信，世界上最成功的私链","subtitle":null,"head_image":"https://media.dappreview.cn/images/DR-Jason/ZKTc2JDjCDcfZMFXbmefdKZ4JiP2hpmd.jpg","content":null,"description":"导读：看标题你可能觉得我疯了：微信既没有通证经济设计、更未采用区块链技术，从这个层面看，它与区块","url":"https://dapp.review/article/66"},{"id":67,"title":"DR数据简报 | 交易额下降60%，Dapp真的凉了吗？","subtitle":null,"head_image":"https://media.dappreview.cn/images/DR-Jason/NtfkYxjXXdb3HxdwrwGdx6sfxKPRcTXh.jpg","content":null,"description":"Vincent：春节过后刚刚开工，就收到朋友们大量的私信，问我“为什么Dapp数据下滑的这么厉害”","url":"https://dapp.review/article/67"}],  
            currentIndex: 0,
            timer: ''
        }
    },
    methods: { 
        getArticle(){
            this.axios.get('/api/blog/article/groups/?show_in_index=1&language=1').then(res=>{
                console.log(res)
                let articles = res.data.results[0].articles
                articles.forEach(element => {
                    element.url = 'https://dapp.review/article/' + element.id
                }); 
                this.articleArr = articles 
                console.log(JSON.stringify(articles))
            }).catch(err=>{})
        },
        go() {
            this.timer = setInterval(() => {
                this.autoPlay()
            }, 3000)
        },
        stop() {
            clearInterval(this.timer)
            this.timer = null
        },
        change(index) {
            this.currentIndex = index
            this.stop()
        },
        autoPlay() {
            this.currentIndex++
            if (this.currentIndex > this.articleArr.length - 1) {
                this.currentIndex = 0
            }
        }
    },
    created() { 
        // this.getArticle()
    }
}
</script>

<style lang='stylus' scoped>
@import '~@/assets/css/util.styl'
.article-wrapper
    position relative
    width 100%
    padding 5rem 0
    background #fff
    .article-box 
        text-align center
        h2 
            font-size 2rem 
            line-height 5rem
            margin-bottom 5rem
            background #fff
            letter-spacing 1rem
        .article-list
            position relative
            padding 5rem 12rem
            background #f3f7ff 
            .list-show 
                overflow hidden
                position relative
                font-size 0
                width 100%
                height 40rem
                background #fefefe  
                box-sizing border-box
                border-radius 1rem
                box-shadow 0 90px 100px -25px rgba(50,50,80,.2), 0 50px 100px -37.5px rgba(0,0,0,.2) 
                &:before
                    position absolute
                    content ''
                    width 20rem
                    height 20rem 
                    top 0
                    bottom 0
                    left 0
                    right 0
                    margin auto 
                    background url(https://dapp.review/logo.svg) no-repeat
                    background-size 100% 
                    opacity .5
                a  
                    position absolute
                    left 0
                    $all100()
                    .article
                        position relative
                        $all100()
                        position relative
                        overflow hidden
                        span.index
                            color rgba(255,255,255,.3) 
                            font-size 5rem
                            z-index 999
                            position absolute
                            bottom 2rem
                            left 2rem
                            font-style italic
                        i.logo 
                            position absolute 
                            left 2rem
                            top 2rem
                            width 5rem 
                            height 5rem
                            background url(https://dapp.review/white-logo.svg) no-repeat
                            z-index 99
                        .img-title
                            position absolute
                            bottom 0
                            right 0
                            width 50% 
                            background #fff 
                            height 5rem
                            line-height 5rem
                            color $deep2
                            font-size 1.5rem
                            z-index 6
                        img.images
                            position absolute
                            margin auto
                            top 0
                            bottom 0
                            right -20%
                            height 100%
                            vertical-align middle
                            border-radius $radius 
                        &:before
                            content ''
                            display block
                            position absolute
                            top 0 
                            $all100() 
                            background rgba(218,150,206,.28)
                            user-select none
                            z-index 5
                        .text-box
                            position relative
                            color #000
                            font-size 1rem
                            font-weight 200
                            $all100()  
                            width 50% 
                            background #1f232f 
                            z-index 11 
                            p 
                                display inline-block
                                color #fff
                                opacity .85
                                line-height 2rem
                                letter-spacing .2rem
                                text-align left 
                                margin 5rem 6rem
                                width 30rem
                                height 22rem
                                padding 4rem
                                border 1px dashed rgba(255,255,255,.3)
                                border-right none 
                                border-top none
                                &:first-letter 
                                    font-size: 3em
                                    padding: 0.1em
                                    color: $logoGreen
                                    vertical-align: baseline

                        &:after
                            content ''
                            display inline-block
                            position absolute
                            width 0
                            height 0
                            top 0
                            right 18.6rem
                            border 20rem solid #1f232f
                            border-right-color transparent
                            border-bottom-color transparent
                            border-right-width 10rem
                            border-left-width 10rem

                            z-index 10
                    
            .carousel-items {
                position: absolute;
                z-index: 999;
                bottom: 0
                width: 100%;
                margin: 0 auto;
                text-align: center;
                font-size: 0;
                span {
                    display: inline-block;
                    height: 6px;
                    width: 30px;
                    margin: 0 3px;
                    background-color: #b2b2b2;
                    cursor: pointer;
                }
                .active {
                    background-color: red;
                }
            }
    .carousel-items
        position absolute
        width 1rem 
        height 20rem
        right 5rem
        top 0
        bottom 0
        margin auto  
        span 
            display inline-block
            width 1.5rem 
            height 1.5rem 
            border-radius 50%  
            margin .5rem 0
            background #eee
        .active
            background #1f232f


    .code
        padding 10rem  5rem
        color $deep2
        width 14rem 
        height 14rem 
        margin auto
        img 
            width 100%
            height 100% 
        p 
            font-size 2rem
            line-height 8rem  

</style>