<template>
    <div class="banner-wrapper" >

        <div class="imgbox">
            <div class="leftbox"> 
                <a :href="leftbox.url" target="_brank">
                    <img :src="leftbox.image" alt="">
                </a>
            </div>
            <div class="rightbox" >
                <a :href="item.url" target="_brank" v-for='item in this.rightbox' :key="item.url">
                    <img :src="item.image" alt="">
                </a>   
            </div>
        </div>

        <div class="canvas">
            <canvas ref="mcanvas" ></canvas>
        </div>
    </div>

</template>

<script>
import water from '@/util/util'
export default {
    data(){
        return { 
            leftbox:{
                image:'https://media.dappreview.cn/images/DR---0x001/dsDeXF6HMyDkmpYZrJWsy4hB444WhhQM.png',
                url:"https://twitter.com/dapp_review/status/1092776407615193088"
            },
            rightbox:[{"title":null,"subtitle":null,"image":"https://media.dappreview.cn/images/DR-Jason/C3dtAS55jzcxN8Y8maj8Jwtw24wwnerd.jpg","url":"https://trongem.com/?r=TRLo7V8K6r5fCxfNFXwcP1kgCSKxUiVafi"},{"title":null,"subtitle":null,"image":"https://media.dappreview.cn/images/DR-Jason/4FnmWiXWybJRkJCSeBndBPMwtCR87NQG.png","url":"https://eosbet.io/?ref=dappreview23&utm_source=dappreview"},{"title":null,"subtitle":null,"image":"https://media.dappreview.cn/images/DR-Jason/chNJA4ARts87KWwAGywhmt5MP3PKFSRH.jpg","url":"https://troninvest.pro/?masternode=TNL5vbAg218o9EioEqPfWdpAMTHKpYUsWy"},{"title":null,"subtitle":null,"image":"https://media.dappreview.cn/images/DR-Jason/C4ishRxct6yGfRJKFtewxZntJZQadwRn.png","url":"http://contest.decentraland.org/?utm_source=dapp_review"}],
        }
    },
    methods:{
        getbanner(){
            this.axios.get('/api/banner/banner/?type=2&lang=zh').then(res=>{  
                this.swapbox(res.data.results)
            }).catch(err=>{
                console.log("err")
            })
        },
        swapbox(arrList){
            this.leftbox = arrList[0] 
            arrList.shift()
            this.rightbox = arrList  
        },
        initCanvas(){  
            water(this.$refs.mcanvas, "#fff", 50 ) 
        }
    },
    created(){
        // this.getbanner()

    },
    mounted(){

        this.initCanvas()
    }

}
</script>

<style lang='stylus' scoped>

@import '~@/assets/css/util.styl'

.banner-wrapper
    position relative
    width 100%
    height 24rem
    background $mainColor
    font-size 0 
    .imgbox
        box-sizing border-box
        width 95%
        position absolute 
        z-index 5
        margin auto 
        left 0
        right 0  
        .leftbox, .rightbox  
            vertical-align top
            box-sizing border-box
            width 50%
            height 0 
            display inline-block  
            a
                overflow hidden
                margin .5%
                box-sizing border-box 
                display inline-block
                img 
                    width 100%
                    transition all .25s
                    &:hover
                        transform scale(1.1)
        .rightbox  
            box-sizing border-box
            a
                width 47%
                img 
                    width 100%
 
    .canvas
        width 100%
        height 100px
        position absolute
        bottom 0 
        transform rotateZ(180deg)
</style>