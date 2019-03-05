<template>
<div class="charts-wrapper">
    <div class="charts-bar">
        <h2>数据一览</h2>
        <div class="bar">
            <span @click="getVolume" :class="voActive">交易额</span>
            <span @click="getUser" :class="usActive">日活</span>
            <span @click="getTx" :class="txActive">交易笔数</span>
        </div>
    </div>
    <div class="charts"> 
        <ve-line :data="chartData" :colors="colors"  :extend="extend" :settings="chartSettings"></ve-line>
    </div>
</div>
</template>

<script>
    export default {
    data () { 
        this.colors = ["#00a1ff", "#40c96c", "#ffd444"]
        this.extend = { 
            legend: {
                textStyle: {
                color: 'rgba(255,255,255,1)'
                }
            },
            xAxis: {
                axisLabel : {
                    color : 'rgba(255,255,255,.6)'
                },
                
            },
            yAxis: {
                axisLabel : {
                    color : 'rgba(255,255,255,.6)'
                },
                splitLine: {
                    lineStyle: {
                        color: 'rgba(255,255,255,.2)',
                        type: 'dashed'
                    }
                }, 
            }
        }, 
        this.chartSettings = {
            metrics: ['eos', 'tron','eth'],
            dimension: ['日期']
        }
            

        return {
            chartData: {
                columns: ['日期', 'eos', 'tron', 'eth'],
                rows: []
            },
            results:[{"chain":"tron","timestamp":1551657600,"total_dapp":225,"total_user":59219,"total_tx":1106706,"total_contract":546,"total_volume":970392850.5927364,"total_volume_USD":22001341.491043236,"total_volume_CNY":161988146.5498669},{"chain":"eth","timestamp":1551657600,"total_dapp":1622,"total_user":13720,"total_tx":65994,"total_contract":4241,"total_volume":27279.588734938956,"total_volume_USD":3475062.616358355,"total_volume_CNY":26631617.461366672},{"chain":"eos","timestamp":1551657600,"total_dapp":421,"total_user":92474,"total_tx":2494174,"total_contract":805,"total_volume":4230203.465910544,"total_volume_USD":13818726.188369116,"total_volume_CNY":106947085.08319817},{"chain":"eos","timestamp":1551571200,"total_dapp":419,"total_user":80809,"total_tx":2366875,"total_contract":797,"total_volume":2721637.561707882,"total_volume_USD":9671728.703447662,"total_volume_CNY":68807849.6042148},{"chain":"eth","timestamp":1551571200,"total_dapp":1616,"total_user":10109,"total_tx":60670,"total_contract":4220,"total_volume":18514.473558825168,"total_volume_USD":2451306.741683941,"total_volume_CNY":18074699.80974122},{"chain":"tron","timestamp":1551571200,"total_dapp":224,"total_user":51258,"total_tx":965151,"total_contract":537,"total_volume":429454056.8177954,"total_volume_USD":9760773.230907174,"total_volume_CNY":71688972.82141274},{"chain":"eos","timestamp":1551484800,"total_dapp":417,"total_user":76414,"total_tx":2370007,"total_contract":793,"total_volume":4141135.263707261,"total_volume_USD":14641951.832606098,"total_volume_CNY":104695282.14369309},{"chain":"eth","timestamp":1551484800,"total_dapp":1615,"total_user":10029,"total_tx":60276,"total_contract":4218,"total_volume":19320.241127381214,"total_volume_USD":2618385.838781501,"total_volume_CNY":18861328.004801806},{"chain":"tron","timestamp":1551484800,"total_dapp":224,"total_user":58563,"total_tx":964056,"total_contract":535,"total_volume":378829987.8276103,"total_volume_USD":8680308.259528477,"total_volume_CNY":63238272.569938675},{"chain":"tron","timestamp":1551398400,"total_dapp":224,"total_user":63305,"total_tx":869866,"total_contract":533,"total_volume":424900302.9029126,"total_volume_USD":10036598.919324545,"total_volume_CNY":70928812.48421994},{"chain":"eth","timestamp":1551398400,"total_dapp":1612,"total_user":11623,"total_tx":73299,"total_contract":4209,"total_volume":21897.331495210077,"total_volume_USD":3001160.1887026057,"total_volume_CNY":21377204.820477143},{"chain":"eos","timestamp":1551398400,"total_dapp":414,"total_user":93117,"total_tx":2485320,"total_contract":790,"total_volume":4236435.232806076,"total_volume_USD":15054064.755598353,"total_volume_CNY":107104635.26010242},{"chain":"eth","timestamp":1551312000,"total_dapp":1611,"total_user":8531,"total_tx":37259,"total_contract":4200,"total_volume":18812.52704411646,"total_volume_USD":2581500.4778275937,"total_volume_CNY":18365673.639311403},{"chain":"tron","timestamp":1551312000,"total_dapp":223,"total_user":60995,"total_tx":817392,"total_contract":532,"total_volume":370273115.12691957,"total_volume_USD":8838331.250899075,"total_volume_CNY":61809869.68320947},{"chain":"eos","timestamp":1551312000,"total_dapp":414,"total_user":94663,"total_tx":2532634,"total_contract":789,"total_volume":5871212.0912921885,"total_volume_USD":20808471.79430957,"total_volume_CNY":148434708.66803125},{"chain":"tron","timestamp":1551225600,"total_dapp":223,"total_user":63218,"total_tx":872188,"total_contract":528,"total_volume":385467085.2974535,"total_volume_USD":9323254.560692249,"total_volume_CNY":64346206.45151458},{"chain":"eth","timestamp":1551225600,"total_dapp":1611,"total_user":10470,"total_tx":52283,"total_contract":4184,"total_volume":19709.276800273903,"total_volume_USD":2723476.9913282874,"total_volume_CNY":19241122.924731586},{"chain":"eos","timestamp":1551225600,"total_dapp":411,"total_user":92892,"total_tx":2533818,"total_contract":785,"total_volume":5901459.315889063,"total_volume_USD":21299880.05454888,"total_volume_CNY":149199412.42957863},{"chain":"eos","timestamp":1551139200,"total_dapp":410,"total_user":98020,"total_tx":2645021,"total_contract":784,"total_volume":5677626.42148951,"total_volume_USD":19496766.538979206,"total_volume_CNY":143540517.8173747},{"chain":"tron","timestamp":1551139200,"total_dapp":221,"total_user":64686,"total_tx":948368,"total_contract":527,"total_volume":402276994.02382725,"total_volume_USD":9744750.760805164,"total_volume_CNY":67152292.6222798},{"chain":"eth","timestamp":1551139200,"total_dapp":1608,"total_user":10434,"total_tx":54412,"total_contract":4163,"total_volume":24367.249900235387,"total_volume_USD":3330883.91016431,"total_volume_CNY":23788455.32584772},{"chain":"eos","timestamp":1551052800,"total_dapp":410,"total_user":97008,"total_tx":2696651,"total_contract":783,"total_volume":5709770.496990531,"total_volume_USD":20439278.5468615,"total_volume_CNY":144353177.35142112},{"chain":"tron","timestamp":1551052800,"total_dapp":221,"total_user":65149,"total_tx":861453,"total_contract":527,"total_volume":275820043.62652636,"total_volume_USD":6718870.550352505,"total_volume_CNY":46042772.90488405},{"chain":"eth","timestamp":1551052800,"total_dapp":1608,"total_user":9497,"total_tx":42844,"total_contract":4154,"total_volume":22608.54070784524,"total_volume_USD":3158695.8126008776,"total_volume_CNY":22071520.701480173},{"chain":"tron","timestamp":1550966400,"total_dapp":218,"total_user":65965,"total_tx":786928,"total_contract":518,"total_volume":317603245.85806596,"total_volume_USD":7645121.581347682,"total_volume_CNY":53017663.00457006},{"chain":"eos","timestamp":1550966400,"total_dapp":408,"total_user":87457,"total_tx":2406594,"total_contract":780,"total_volume":5561005.707594569,"total_volume_USD":20445928.52274815,"total_volume_CNY":140592138.26260996},{"chain":"eth","timestamp":1550966400,"total_dapp":1608,"total_user":9318,"total_tx":46713,"total_contract":4141,"total_volume":27611.059418103447,"total_volume_USD":3818491.750308466,"total_volume_CNY":26955214.73108608},{"chain":"eth","timestamp":1550880000,"total_dapp":1608,"total_user":9120,"total_tx":47447,"total_contract":4132,"total_volume":22520.440678565927,"total_volume_USD":3611485.9720411804,"total_volume_CNY":21985513.309620306},{"chain":"tron","timestamp":1550880000,"total_dapp":218,"total_user":64084,"total_tx":760748,"total_contract":516,"total_volume":286351172.1659819,"total_volume_USD":7361739.702364768,"total_volume_CNY":47800739.27092106},{"chain":"eos","timestamp":1550880000,"total_dapp":408,"total_user":94120,"total_tx":2849013,"total_contract":780,"total_volume":6451954.265787983,"total_volume_USD":27694063.834994666,"total_volume_CNY":163116906.16697222},{"chain":"tron","timestamp":1550793600,"total_dapp":218,"total_user":65806,"total_tx":710062,"total_contract":515,"total_volume":280338491.3462032,"total_volume_USD":7040522.847514058,"total_volume_CNY":46797039.56188368},{"chain":"eos","timestamp":1550793600,"total_dapp":408,"total_user":94148,"total_tx":2832602,"total_contract":780,"total_volume":6046973.043482354,"total_volume_USD":23453576.23595237,"total_volume_CNY":152878258.88013422},{"chain":"eth","timestamp":1550793600,"total_dapp":1608,"total_user":9162,"total_tx":44482,"total_contract":4107,"total_volume":19247.792776430295,"total_volume_USD":2858749.368904211,"total_volume_CNY":18790600.51741265},{"chain":"tron","timestamp":1550707200,"total_dapp":213,"total_user":68906,"total_tx":860158,"total_contract":509,"total_volume":282662441.74547803,"total_volume_USD":7014087.746835878,"total_volume_CNY":47184977.72282789},{"chain":"eth","timestamp":1550707200,"total_dapp":1604,"total_user":9180,"total_tx":43770,"total_contract":4094,"total_volume":19166.643666722804,"total_volume_USD":2808876.261744335,"total_volume_CNY":18711378.940135263},{"chain":"eos","timestamp":1550707200,"total_dapp":407,"total_user":85482,"total_tx":2682648,"total_contract":779,"total_volume":5650698.26668894,"total_volume_USD":21786559.49162825,"total_volume_CNY":142859726.0574043},{"chain":"eth","timestamp":1550620800,"total_dapp":1599,"total_user":9478,"total_tx":43811,"total_contract":4066,"total_volume":24049.406316787587,"total_volume_USD":3538437.396037191,"total_volume_CNY":23793514.58217284},{"chain":"tron","timestamp":1550620800,"total_dapp":212,"total_user":64602,"total_tx":889591,"total_contract":506,"total_volume":325867200.4290971,"total_volume_USD":8212291.273894071,"total_volume_CNY":55221910.21304579},{"chain":"eos","timestamp":1550620800,"total_dapp":403,"total_user":95400,"total_tx":2768262,"total_contract":776,"total_volume":5213704.131194631,"total_volume_USD":19929236.310924232,"total_volume_CNY":134010163.72554758},{"chain":"tron","timestamp":1550534400,"total_dapp":211,"total_user":59955,"total_tx":946807,"total_contract":504,"total_volume":268554693.83595866,"total_volume_USD":6642906.050882506,"total_volume_CNY":44695610.92608579},{"chain":"eth","timestamp":1550534400,"total_dapp":1599,"total_user":10196,"total_tx":48180,"total_contract":4047,"total_volume":24678.765461968735,"total_volume_USD":3568102.9091519243,"total_volume_CNY":24007345.301910847},{"chain":"eos","timestamp":1550534400,"total_dapp":399,"total_user":97020,"total_tx":2964332,"total_contract":765,"total_volume":5591697.519992116,"total_volume_USD":19999300.515798084,"total_volume_CNY":134561733.64505532},{"chain":"eth","timestamp":1550448000,"total_dapp":1594,"total_user":10067,"total_tx":47818,"total_contract":4022,"total_volume":19470.235777663882,"total_volume_USD":2863523.261258565,"total_volume_CNY":16825770.725600112},{"chain":"tron","timestamp":1550448000,"total_dapp":209,"total_user":57760,"total_tx":827795,"total_contract":500,"total_volume":235259625.67509514,"total_volume_USD":5894065.960744746,"total_volume_CNY":37685520.495434724},{"chain":"eos","timestamp":1550448000,"total_dapp":399,"total_user":97263,"total_tx":2643606,"total_contract":764,"total_volume":5178712.020593378,"total_volume_USD":18757537.58517303,"total_volume_CNY":98684094.5768988},{"chain":"eos","timestamp":1550361600,"total_dapp":396,"total_user":84240,"total_tx":2668856,"total_contract":759,"total_volume":5356146.070390633,"total_volume_USD":15528835.310324533,"total_volume_CNY":102065228.43445364},{"chain":"tron","timestamp":1550361600,"total_dapp":206,"total_user":48334,"total_tx":760175,"total_contract":490,"total_volume":234623773.3409228,"total_volume_USD":5619931.151100105,"total_volume_CNY":37583665.25315607},{"chain":"eth","timestamp":1550361600,"total_dapp":1590,"total_user":9128,"total_tx":45250,"total_contract":4007,"total_volume":19929.997705985512,"total_volume_USD":2688202.661232996,"total_volume_CNY":17223087.37253944},{"chain":"eth","timestamp":1550275200,"total_dapp":1583,"total_user":10474,"total_tx":49096,"total_contract":3997,"total_volume":16728.02661053221,"total_volume_USD":2059552.1087173612,"total_volume_CNY":13949758.342764424},{"chain":"tron","timestamp":1550275200,"total_dapp":204,"total_user":58571,"total_tx":946492,"total_contract":481,"total_volume":258341604.07302395,"total_volume_USD":6174043.65011022,"total_volume_CNY":41818032.45092653},{"chain":"eos","timestamp":1550275200,"total_dapp":395,"total_user":82782,"total_tx":2848808,"total_contract":758,"total_volume":5297297.865389916,"total_volume_USD":14891531.658978703,"total_volume_CNY":100863322.2325945},{"chain":"eos","timestamp":1550188800,"total_dapp":395,"total_user":98937,"total_tx":2684206,"total_contract":758,"total_volume":5560846.922996819,"total_volume_USD":15583067.162930287,"total_volume_CNY":105545672.2012434},{"chain":"tron","timestamp":1550188800,"total_dapp":204,"total_user":60481,"total_tx":945216,"total_contract":480,"total_volume":287560443.9765452,"total_volume_USD":6888351.863299451,"total_volume_CNY":46655496.00531362},{"chain":"eth","timestamp":1550188800,"total_dapp":1583,"total_user":9929,"total_tx":45368,"total_contract":3990,"total_volume":18401.346408102567,"total_volume_USD":2257180.596663111,"total_volume_CNY":15288109.899258956},{"chain":"eth","timestamp":1550102400,"total_dapp":1581,"total_user":9077,"total_tx":34726,"total_contract":3988,"total_volume":15857.903286212324,"total_volume_USD":1931851.4950148126,"total_volume_CNY":13087521.138127364},{"chain":"tron","timestamp":1550102400,"total_dapp":203,"total_user":59395,"total_tx":893469,"total_contract":476,"total_volume":319352884.2842399,"total_volume_USD":7663025.344026942,"total_volume_CNY":51913931.49564499},{"chain":"eos","timestamp":1550102400,"total_dapp":391,"total_user":100459,"total_tx":2604732,"total_contract":755,"total_volume":5536074.9494957635,"total_volume_USD":15348301.590876041,"total_volume_CNY":103978603.95754895},{"chain":"eth","timestamp":1550016000,"total_dapp":1573,"total_user":11373,"total_tx":48779,"total_contract":3972,"total_volume":20882.00591288954,"total_volume_USD":2585927.7510126703,"total_volume_CNY":17501223.398979392},{"chain":"eos","timestamp":1550016000,"total_dapp":390,"total_user":96704,"total_tx":2659622,"total_contract":753,"total_volume":5965944.787490952,"total_volume_USD":17120327.262255605,"total_volume_CNY":116667062.06467956},{"chain":"tron","timestamp":1550016000,"total_dapp":202,"total_user":61199,"total_tx":930662,"total_contract":475,"total_volume":269382878.1025318,"total_volume_USD":6539350.003844777,"total_volume_CNY":44507437.171171725},{"chain":"tron","timestamp":1549929600,"total_dapp":200,"total_user":59932,"total_tx":901941,"total_contract":470,"total_volume":234751673.56157926,"total_volume_USD":5874505.398470407,"total_volume_CNY":39955046.3911256},{"chain":"eth","timestamp":1549929600,"total_dapp":1573,"total_user":10114,"total_tx":48232,"total_contract":3962,"total_volume":19548.523056694416,"total_volume_USD":2396771.867119011,"total_volume_CNY":16179353.194034876},{"chain":"eos","timestamp":1549929600,"total_dapp":389,"total_user":93150,"total_tx":2456181,"total_contract":741,"total_volume":6381857.9452853305,"total_volume_USD":18836527.132944588,"total_volume_CNY":121231385.72910608},{"chain":"tron","timestamp":1549843200,"total_dapp":198,"total_user":60840,"total_tx":905531,"total_contract":465,"total_volume":199098744.01730078,"total_volume_USD":4860112.737621049,"total_volume_CNY":33886870.46586428},{"chain":"eth","timestamp":1549843200,"total_dapp":1569,"total_user":9976,"total_tx":52881,"total_contract":3958,"total_volume":21154.604567943203,"total_volume_USD":2538868.612584416,"total_volume_CNY":17508628.04275572},{"chain":"eos","timestamp":1549843200,"total_dapp":388,"total_user":80242,"total_tx":2459414,"total_contract":741,"total_volume":5689830.808700245,"total_volume_USD":15690133.597100612,"total_volume_CNY":108085463.4209585},{"chain":"eos","timestamp":1549756800,"total_dapp":387,"total_user":86070,"total_tx":2440810,"total_contract":739,"total_volume":4881009.440403078,"total_volume_USD":13446157.790538255,"total_volume_CNY":78197396.36031109},{"chain":"tron","timestamp":1549756800,"total_dapp":195,"total_user":53424,"total_tx":1000198,"total_contract":463,"total_volume":263547689.9172065,"total_volume_USD":6781141.612067803,"total_volume_CNY":45517317.62310284},{"chain":"eth","timestamp":1549756800,"total_dapp":1569,"total_user":9708,"total_tx":57158,"total_contract":3957,"total_volume":14552.755930904841,"total_volume_USD":1768601.0202885773,"total_volume_CNY":10570521.98139568},{"chain":"tron","timestamp":1549670400,"total_dapp":195,"total_user":58687,"total_tx":1003938,"total_contract":453,"total_volume":236408150.1326952,"total_volume_USD":6120243.980282273,"total_volume_CNY":40830048.10879022},{"chain":"eth","timestamp":1549670400,"total_dapp":1569,"total_user":9140,"total_tx":55394,"total_contract":3957,"total_volume":19962.541503059892,"total_volume_USD":2382771.9837820902,"total_volume_CNY":14499967.206520587},{"chain":"eos","timestamp":1549670400,"total_dapp":387,"total_user":87794,"total_tx":2742238,"total_contract":739,"total_volume":3755831.9897150397,"total_volume_USD":10359503.701205323,"total_volume_CNY":60171217.93114769},{"chain":"tron","timestamp":1549584000,"total_dapp":195,"total_user":53983,"total_tx":945423,"total_contract":452,"total_volume":196976948.44677615,"total_volume_USD":5305972.590012413,"total_volume_CNY":34019885.84949498},{"chain":"eth","timestamp":1549584000,"total_dapp":1569,"total_user":10426,"total_tx":54104,"total_contract":3957,"total_volume":21269.537207358335,"total_volume_USD":2514997.247300179,"total_volume_CNY":15449315.00617254},{"chain":"eos","timestamp":1549584000,"total_dapp":387,"total_user":82636,"total_tx":2685180,"total_contract":739,"total_volume":4034070.5419101873,"total_volume_USD":10854127.156702125,"total_volume_CNY":64628806.18504918},{"chain":"eos","timestamp":1549497600,"total_dapp":387,"total_user":80622,"total_tx":2961177,"total_contract":739,"total_volume":5233052.329303426,"total_volume_USD":12275676.208530616,"total_volume_CNY":83837384.90270083},{"chain":"eth","timestamp":1549497600,"total_dapp":1569,"total_user":10708,"total_tx":49814,"total_contract":3956,"total_volume":25796.3410691243,"total_volume_USD":2702819.4150748528,"total_volume_CNY":18737398.717151728},{"chain":"tron","timestamp":1549497600,"total_dapp":195,"total_user":61216,"total_tx":1005407,"total_contract":452,"total_volume":234795694.6443739,"total_volume_USD":6027105.7222072445,"total_volume_CNY":40551560.94527878},{"chain":"tron","timestamp":1549411200,"total_dapp":194,"total_user":62724,"total_tx":983537,"total_contract":451,"total_volume":279181503.62986815,"total_volume_USD":7228909.460152025,"total_volume_CNY":48217433.35791802},{"chain":"eth","timestamp":1549411200,"total_dapp":1566,"total_user":9356,"total_tx":48809,"total_contract":3942,"total_volume":35124.4856779382,"total_volume_USD":3705025.7961320416,"total_volume_CNY":25512978.414994854},{"chain":"eos","timestamp":1549411200,"total_dapp":387,"total_user":72457,"total_tx":2767819,"total_contract":738,"total_volume":6384188.198596901,"total_volume_USD":15085584.627867687,"total_volume_CNY":102279436.47723734},{"chain":"eth","timestamp":1549324800,"total_dapp":1565,"total_user":9197,"total_tx":53898,"total_contract":3942,"total_volume":17558.58601442202,"total_volume_USD":1820797.0772825396,"total_volume_CNY":12753833.04089637},{"chain":"tron","timestamp":1549324800,"total_dapp":193,"total_user":60938,"total_tx":955909,"total_contract":451,"total_volume":255819597.6485701,"total_volume_USD":6517971.550990092,"total_volume_CNY":44182598.92182083},{"chain":"eos","timestamp":1549324800,"total_dapp":387,"total_user":77895,"total_tx":2751102,"total_contract":738,"total_volume":4982167.37070076,"total_volume_USD":11635234.531642433,"total_volume_CNY":79818021.53366116},{"chain":"eos","timestamp":1549238400,"total_dapp":386,"total_user":85336,"total_tx":3080578,"total_contract":735,"total_volume":6643098.251186734,"total_volume_USD":15838957.920308648,"total_volume_CNY":106427367.81218764},{"chain":"tron","timestamp":1549238400,"total_dapp":193,"total_user":59466,"total_tx":1074819,"total_contract":450,"total_volume":296427674.100441,"total_volume_USD":7906735.622007701,"total_volume_CNY":51196019.20451697},{"chain":"eth","timestamp":1549238400,"total_dapp":1561,"total_user":9825,"total_tx":47420,"total_contract":3935,"total_volume":15380.89626468662,"total_volume_USD":1650983.5640504642,"total_volume_CNY":11172048.980369845},{"chain":"tron","timestamp":1549152000,"total_dapp":192,"total_user":58944,"total_tx":1232002,"total_contract":448,"total_volume":336880258.3347117,"total_volume_USD":8569497.182474328,"total_volume_CNY":58182584.42861384},{"chain":"eos","timestamp":1549152000,"total_dapp":384,"total_user":83888,"total_tx":3283126,"total_contract":733,"total_volume":7955215.715794347,"total_volume_USD":19029069.81973816,"total_volume_CNY":127448464.10466579},{"chain":"eth","timestamp":1549152000,"total_dapp":1556,"total_user":13652,"total_tx":54324,"total_contract":3929,"total_volume":18460.11332949196,"total_volume_USD":1984355.202760858,"total_volume_CNY":13408665.317753147}],
            classActive:['usActive', 'voActive', 'txActive'],
            usActive: "",
            voActive: "",
            txActive: "",

        }
    },
    methods:{
        renderCharData(arrList, type){
            arrList = arrList.reverse()
            let that = this
            let lastDate = null
            let newDate = null 
            let obj = {}
            let arr = []
            arrList.forEach((element, index, myarr) => {
                // 根据时间戳获取当天日期
                if(!newDate){ 
                    newDate = that.transformDate(element.timestamp)
                    lastDate = newDate 
                }
                if(index % 3 === 0 && index !== 0){
                    let day = newDate.split('-')[1] - 0 + 1
                    
                    let month = newDate.split('-')[0] 
                    if(day === 32){
                        day = 1
                        month ++
                        if(month === 13){
                            month = 1
                        }
                    }
                    newDate = month + '-' + day
                }
                // 猜测是接口时间戳出了问题，遍历时间戳转换成日期全部都是第一天。
                // 所以下面采用另外一种方式解决
                 
                
                if(lastDate !== newDate){
                    
                    lastDate = newDate // 表示到了第二天 
                    // if(JSON.stringify(obj) !== '{}'){
                        // console.log(arr)
                        arr.push(obj)
                        obj = {}
                        obj["日期"] = newDate
                        obj[element.chain] = element[type]
                    // }
                    // 创建新的对象
                }else{
                    // 表示是同一天
                    // console.log("同一天")
                    obj["日期"] = newDate
                    obj[element.chain] = element[type]
                    if(index === myarr.length-1){
                        arr.push(obj)
                        obj = {}
                    } 
                }
                // 根据相同的日期创建对象

                // 将创建好的对象放到数组里面

            }); 
            this.chartData.rows=arr  
        },
        transformDate(timeStamp){
            let date = new Date(timeStamp)
            let month = date.getMonth()+1
            let day = date.getDate()
            return month + '-' + day
        },

        getUser(){
            // 日活
            this.renderCharData(this.results, "total_user")
            this.filterClass("usActive")
        },
        getTx(){
            // 交易笔数
            this.renderCharData(this.results, "total_tx")
            this.filterClass("txActive")
        },
        getVolume(){
            // 交易额
            this.renderCharData(this.results, "total_volume_CNY")
            this.filterClass("voActive")
        },
        filterClass(str){ 
            let arr = this.classActive
            arr.forEach(el=>{ 
                if(el == str){ 
                    this[el] = 'active' 
                }else{ 
                    this[el] = ''
                } 
            }) 
        }
    },
    created() { 

        // this.axios.get('/api/dapp/total/stats/')
        //     .then(res => { 
        //         this.results = res.data.results 
        //         console.log(JSON.stringify(this.results))
                this.renderCharData(this.results, "total_user")
        //     }).catch(err => {
        //         console.log("error")
        //     })
    },
  }
</script>

<style lang='stylus' scoped>

@import '~@/assets/css/util.styl'
.charts-wrapper
    position relative
    width 100%
    padding 5rem 0
    background $deep2 
    .charts
        width 85% 
        margin auto   
    &:before
        content ''
        display block
        position absolute
        width 6rem
        height 12rem
        background-image url(https://dapp.review/assets/327a0296.svg)
        top -8rem
        z-index 55
    &:after
        content '' 
        width 0
        height 0
        border 5rem solid transparent
        border-right-color #ffdd5c
        position absolute
        bottom -2rem
        right 0
        z-index 999 
    .charts-bar
        width 14rem
        height 5rem
        margin 0 auto 3rem auto
        color #fff 
        text-align center 
        font-size 0
        h2 
            cursor pointer
            font-size 2rem
            margin 2rem 0
        .bar 
            height 40px
            line-height 40px 
            border-bottom 1px solid rgba(255,255,255,.5)
            span 
                cursor pointer
                color rgba(255,255,255,.5)
                display inline-block
                height 40px
                padding 0 .8rem
                font-size 1rem 
            .active
                color #fff
                border-bottom 1px solid rgba(255,255,255,1)
    



        

</style>