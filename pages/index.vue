<template>
    <div id="home">
        <transition name="menu">
            <div class="menu" v-show="isView">
                <v-container>
                    <div v-for="(item, key) in items" :key="key">
                        <nuxt-link v-scroll-to="item.link" to>
                            <p class="menu-title">{{item.title}}</p>
                        </nuxt-link>
                    </div>
                </v-container>
            </div>
        </transition>
        <div class="big-space">
            <a class="down" href="#"><span></span><span></span><span></span></a>
            <div class="left-space">
                <div class="inner">
                    <transition name="name">
                        <h1 class="my-name">
                            <span
                            v-for="(t, index) in text"
                            :key="index"
                            class="item"
                            :style="{animationDelay: index*100+'ms'}"
                            v-text="t"
                            v-show="show"
                            />
                        </h1>
                    </transition>
                    <transition name="copy">
                        <p class="welcome" v-show="show2">Welcome to my portfolio-site.</p>
                    </transition>
                    <transition name="copy">
                        <h1 class="site-copy" v-show="show2">Design the Future</h1>
                    </transition>
                </div>
                <vue-particles
                class="particles-js"
                color="#ffffff"
                :particle-opacity="0.8"
                :particles-number="70"
                shape-type="circle"
                lines-color="translate"
                :particle-size="3"
                :lines-width="1"
                :line-linked="true"
                :line-opacity="0"
                :lines-distance="240"
                :move-speed="2"
                :hover-effect="false"
                hover-mode="grad"
                :click-effect="true"
                click-mode="push"
                >
                </vue-particles>
            </div>
            <transition name="menu">
                <div class="right-space" v-show="show2"></div>
            </transition>
        </div>  
        <section class="about">
            <div class="heading-wrapper">
                <h2 class="heading" id="about" >ABOUT</h2>
            </div>
            <div class="about-wrapper">
                <v-container>
                    <v-row justify="center">
                        <v-col cols="12" sm="12" md="6" lg="6" xl="6" class="text-wrap"> 
                            <div :class="visible === true ? 'active' : 'non-active'">
                                <h4 class="about-name">Seiya Kato</h4>
                                <p class="about-subtxt">I'm aiming to be a front end engineer</p>
                                <p class="about-text">
                                初めまして。ご覧いただきありがとうございます。<br>
                                名古屋在住の営業マンでwebサイトを作成することに興味を持ち<br>
                                フロントエンドエンジニアを目指し日々勉強しています。<br>
                                スタイリッシュで少しのユーモアがあるサイト制作をしていきたいです。
                                </p>
                                <img src="../static/slogo.png" class="s-logo">
                            </div>
                        </v-col>  
                        <v-col cols="12" sm="12" md="3" lg="3" xl="3" class="photo-wrapper"> 
                            <div :class="visible === true ? 'active2' : 'non-active2'">
                                <img src="../static/img-me.jpg" class="me-photo">
                            </div>
                        </v-col>
                    </v-row>
                </v-container>
            </div>
        </section>
        <section class="works">
            <div class="heading-wrapper">
                <h2 class="heading" id="works">WORKS</h2>
            </div> 
            <div class="point"></div>
            <carousel-3d 
            :controls-visible="true" 
            :clickable="true" 
            :autoplay="true"
            :autoplayTimeout="5000"
            :autoplayHoverPause="true"
            :width="480"
            :height="360"
            :controls-prev-html="'&#10218;'" 
            :controls-next-html="'&#10219;'"
            >
            <slide v-for="(worklist, i) in worklists" :index="i" :key="i">
                <transition name="card">
                    <img :src="worklist.img" @click="worklist.dialog=true" v-show="visible3" class="work-img">
                </transition>
            </slide>
            </carousel-3d>
            <div v-for="(worklist, i) in worklists" :key="i">
                <transition name="work">
                    <v-card dark v-show="worklist.dialog" class="bg" @click="worklist.dialog = false">
                        <v-card-title class="headline">
                        <h1 class="work-title">{{worklist.title}}</h1>
                        </v-card-title>
                        <v-container>
                            <v-row>
                                <v-col md="6" cols="12">
                                    <h4 class="work-item">Concept</h4>
                                    <p class="work-description">{{worklist.description}}</p>
                                    <h4 class="work-item">Skills</h4>
                                    <p>{{worklist.Skills}}</p>
                                    <h4 class="work-item">Site</h4>
                                    <a :href="worklist.url" class="site-url">
                                        <span>{{worklist.url}}</span>
                                    </a>
                                    <a :href="worklist.github">
                                        <v-icon>mdi-github</v-icon>
                                        <span class="github-link">GitHub</span>
                                    </a>
                                </v-col>
                                <v-col md="6" cols="12">
                                    <img :src='worklist.img' class="work-img">
                                </v-col>
                            </v-row>
                        </v-container>
                        <v-card-actions>
                            <v-spacer></v-spacer>
                            <v-btn
                                color="white"
                                text
                                @click="worklist.dialog = false"
                            >
                                close
                            </v-btn>
                        </v-card-actions>
                    </v-card>
                </transition>
            </div>
        </section>
        <section class="skills">
            <div class="heading-wrapper">
                <h2 class="heading" id="skills">SKILLS</h2>
            </div>
            <div class="skills-wrapper">
                <v-container>
                    <v-row>
                        <v-col cols="12" sm="12" md="6" lg="6" xl="6">
                            <div :class="visible2 === true ? 'active' : 'non-active'">
                                <p class="skill-text">
                                HTML/CSSと並行してJavascriptを学びつつ徐々にJQueryに移行していきましたが
                                Vueを使用することでの多くの利点を知り現在はNuxtをメインに使用しています。<br>
                                PHPやMySQLは現在基礎を学んだ段階ですが今後も継続的に学ぶつもりです。<br>
                                浮かんだアイディアを具現化するためにも幅広くスキルを習得していきたいと考えています。
                                </p>
                            </div>
                        </v-col>
                        <v-col cols="12" sm="12" md="6" lg="6" xl="6">
                            <div v-for="(bar, key) in bars" :key="key">
                                <v-row justify="center">
                                    <div class="skillbar">
                                        <div class="skillbar-title">{{bar.title}}<span >{{bar.figure}}</span></div>
                                        <div v-if="visible2" :class="bar.class1"></div>
                                        <div v-else :class="bar.class2"></div>
                                        <div class="skill-bar-percent"></div>
                                    </div>
                                </v-row>
                            </div>
                        </v-col>   
                    </v-row>
                </v-container>
            </div>
        </section>
        <section class="contact" >
            <div class="heading-wrapper">
                <h2 class="heading" id="contact">CONTACT</h2>
            </div>
            <div class="contact-form">
                <v-text-field label="NAME" v-model="name" outlined clearable color="grey darken-3" required :rules="[rules.required, rules.counter]"></v-text-field>
                <v-text-field label="E-mail" v-model="email" outlined clearable color="grey darken-3" required :rules="[rules.required, rules.email]"></v-text-field>
                <v-textarea label="MESSAGE" v-model="message" outlined clearable color="grey darken-3" required :rules="[rules.required, rules.counter]"></v-textarea>
                <v-text-field v-model="botfield" label="人間は入力しないでください" v-show="false"></v-text-field>
                <v-row justify="center">
                    <v-btn
                    x-large
                    class="send-btn"
                    @click="submit"
                    >
                    SEND MESSAGE
                    </v-btn>
                </v-row>
            </div>
        </section>
        <Footer />
    </div>
</template>

<script>
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'
import { Carousel3d, Slide } from 'vue-carousel-3d';

export default {
components: {
    Header,
    Footer,
    Carousel3d,
    Slide
},
data(){
    return{
        text: 'SEIYA KATO',
        isView: false,
        show:false,
        show2:false,
        visible:false,
        visible2:false,
        visible3:false,
        items:[
            {   
                title:'Top',
                link:'#home' 
            },
            {   
                title:'About',
                link:'#about' 
            },
            {   
                title:'Works',
                link:'#works' 
            },
            {   
                title:'Skills',
                link:'#skills' 
            },
            {   
                title:'Contact',
                link:'#contact' 
            },
        ],
        worklists:[
            {
                title: 'SEIYA KATO',
                dialog:false,
                img: require('../static/nightmin.jpg'),
                description:'制作物を掲載するための媒体が必要と感じ、制作しました。レイアウトやデザインに関しては見やすさを追求しシンプルにまとめています。現在は最低限の機能しか実装していないため自身の技術力の向上と共にリッチ化を図るべく徐々に手を加えていけたらと思っています。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Netlify',
                url:'https://seiyakato.netlify.app/',
                github:'https://github.com/Se-Ya66/SEIYA-KATO'
            },
            {
                title: 'NEO-SOUL SUGGESTER',
                dialog:false,
                img: require('../static/peoplemin.jpg'),
                description:'大好きな音楽ジャンルの１つであるネオソウルの魅力を紹介する目的で制作しました。アーティストのデータベースだけでなく個人的におすすめな曲紹介ページも用意しています。サイト内の音源は全てspotifyのリンクより試聴可能です。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Netlify',
                url:'https://neosoul-suggester.netlify.app/',
                github:'https://github.com/Se-Ya66/NEOSOUL-SUGGESTER'
            },
            {
                title:"MY Todo",
                dialog:false,
                img: require('../static/todomin.jpg'),
                description:'学習を通じて得たスキルを試す目的で制作しました。自身では初の制作物となるためVuetifyの各種UIコンポーネントの使用やFirebaseでのログイン、データの保管など苦労する点は多々ありましたが基礎は学べたと感じています。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Firebase /Netlify',
                url:'https://mytodocards.netlify.app/',
                github:'https://github.com/Se-Ya66/My-Todo'
            },
            {
                title:"NEO-SOUL Reviews",
                dialog:false,
                img: require('../static/reviewmin.jpg'),
                description:'5人のネオソウルを代表するアーティストの楽曲レビューサイト。外部APIを使用したアプリの学習目的で作成したためアーティスト画像はYouTubeAPIより取得。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Firebase /Netlify',
                url:'https://neosoul-reviews.netlify.app/',
                github:'https://github.com/Se-Ya66/NEOSOUL-Reviews'
            },
            {
                title:"ThanksCard Provider",
                dialog:false,
                img: require('../static/wedmin.jpg'),
                description:'友人の挙式での使用のために作成。トップページのQRコードを読み取ると新郎新婦からのサンクスカードをダウンロードするページに遷移。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Netlify',
                url:'https://mytodocards.netlify.app/',
                github:'https://github.com/Se-Ya66/My-Todo'
            },
        ],
        bars:[
            {
                title:'HTML/CSS',
                figure:'44%',
                class1:'skillbar-bar-html1',
                class2:'skillbar-bar-html2',
            },
            {
                title:'Vue.js',
                figure:'35%',
                class1:'skillbar-bar-vue1',
                class2:'skillbar-bar-vue2',
            },
            {
                title:'jQuery',
                figure:'20%',
                class1:'skillbar-bar-jquery1',
                class2:'skillbar-bar-jquery2',
            },
            {
                title:'PHP',
                figure:'10%',
                class1:'skillbar-bar-php1',
                class2:'skillbar-bar-php2',
            },
            {
                title:'MySQL',
                figure:'10%',
                class1:'skillbar-bar-mysql1',
                class2:'skillbar-bar-mysql2',
            },
            {
                title:'Photoshop',
                figure:'10%',
                class1:'skillbar-bar-mysql1',
                class2:'skillbar-bar-mysql2',
            },
            {
                title:'Illustarator',
                figure:'10%',
                class1:'skillbar-bar-mysql1',
                class2:'skillbar-bar-mysql2',
            },
        ],
        rules: {
            required: value => !!value || 'Required.',
            counter: value => value.length >= 1 || 'Min 1 characters',
            email: value => {
                const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
                return pattern.test(value) || 'Invalid e-mail.'
            },
        },
        name: "",
        email: "",
        message: "",
        botfield: "",
}
},
mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.show = !this.show;
    this.show2 = !this.show2;
},
methods: {
    handleScroll() {
        if (window.scrollY > 10) {
            this.isView = true;
        } else {
            this.isView = false;
        }
        if (!this.visible) {
            const top = document.querySelector('.point').getBoundingClientRect().top;
            this.visible = top < window.innerHeight + 300;
        }
        if (!this.visible2) {
            const top2 = document.querySelector('.skills-wrapper').getBoundingClientRect().top;
            this.visible2 = top2 < window.innerHeight - 300;
        }
        if (!this.visible3) {
            const top3 = document.querySelector('.skills').getBoundingClientRect().top;
            this.visible3 = top3 < window.innerHeight + 300;
        }
    },
    change_class() {
        this.isView = !this.isView
    },
    async submit() {
        const params = new FormData()
        params.append('form-name', 'contact')
        params.append('name', this.name)
        params.append('email', this.email)
        params.append('message', this.message)
        params.append('bot-field', this.botfield)
        const response = await this.$axios.$post(window.location.origin, params)
        console.log(response)
        this.resetForm();
    },
    resetForm() {
        this.name = '';
        this.email = '';
        this.message = '';
    }
    }
}
</script>

<style>

a{
    color:#fff;
}
.v-btn{
    /* font-family: 'Montserrat', sans-serif; */
    font-family: 'Roboto', sans-serif;
}
#home {
    color: #fff;
    font-size: 1.4rem;
    /* font-family: 'Montserrat', sans-serif;   */
    font-family: 'Roboto', sans-serif;
}
*, *::before, *::after {
    box-sizing: border-box;
    margin : 0;
    padding : 0;
}
a{
    color:#fff;
}
/* --------------------------------
* transition
* -------------------------------- */
@keyframes text-in {
    0% {
        transform: translate(0, -20px);
        opacity: 0;
    }
}
.item {
    display: inline-block;
    min-width: 0.3em;
    animation: text-in .8s cubic-bezier(0.22, 0.15, 0.25, 1.43) 0s backwards;
}

.non-active{
    opacity:0;
}
.active{
    opacity:1;
    transition: all 2s;
}
.non-active2{
    opacity:0;
    transform: translateY(30px);
}
.active2{
    opacity:1;
    transform: translateY(0);
    transition: all 2s;
}
.card-enter-active,
.menu-enter-active,
.menu-leave-active{
    transition: opacity 1s;
}
.menu-leave-active{
    transition: opacity 0.5s;
}
.card-enter,
.menu-enter {
    opacity: 0;
}
.card-enter-to,
.menu-enter-to {
    opacity: 1;
}

.menu-leave {
    opacity: 1;
}

.menu-leave-to {
    opacity: 0;
}

.copy-enter-active {
    transition: opacity 2s;
}
.copy-enter {
    opacity: 0;
}
.copy-enter-to {
    opacity: 1;
}
.work-leave-active,
.work-enter-active {
    transition: opacity 1s;
}
.work-enter {
    opacity: 0;
}
.work-enter-to {
    opacity: 1;
}
.work-leave {
    opacity: 1;
}
.work-leave-to {
    opacity: 0;
}
/* --------------------------------
* parts
* -------------------------------- */
.menu{
    position:fixed;
    background-color: transparent;
    bottom:0;
    right:0;
    z-index:999;
    color:black;
    line-height:1;
    font-size:18px;
}
.menu p{
    transition: .5s;
}
.menu p{
    position: relative;
    display: inline-block;
    transition: .3s;
}
.menu p::after {
    position: absolute;
    bottom: -3px;
    left: 50%;
    content: '';
    width: 0;
    height:1.5px;
    transition: .3s;
    -webkit-transform: translateX(-50%);
    transform: translateX(-50%);
    background-color: black;
}
.menu p:hover::after {
    width: 100%;
}
.menu-title{
    color:black;
}
.heading {
    font-family: 'Roboto', sans-serif;
    text-align: center;
    position: relative;
    display: inline-block;
    margin: 30px 0 15px;
    padding-bottom: 15px;
    letter-spacing: 3px;
    font-size: 1.3rem;
    font-weight:400;
}
.heading::before,
.heading::after {
    content: '';
    position: absolute;
    right: 0;
    bottom: 0;
    left: 0;
    border-bottom: 1px solid #999;
}
.heading::before {
    bottom: 5px;    
}
.heading-wrapper{
    text-align: center;
}
/* --------------------------------
* header
* -------------------------------- */
.down {
    position: absolute;
    bottom: -40px;
    right: 49%;
    z-index: 999;
    display: inline-block;
    -webkit-transform: translate(0, -50%);
    transform: translate(0, -50%);
    text-decoration: none;
}
.down {
    padding-top: 80px;
}
.down span {
    z-index: 999;
    position: absolute;
    top: 0;
    left: 50%;
    width: 24px;
    height: 24px;
    margin-left: -12px;
    border-left: 1px solid #fff;
    border-bottom: 1px solid #fff;
    -webkit-transform: rotate(-45deg);
    transform: rotate(-45deg);
    -webkit-animation: sdb 2s infinite;
    animation: sdb 2s infinite;
    opacity: 0;
    box-sizing: border-box;
}
.down span:nth-of-type(1) {
    -webkit-animation-delay: 0s;
    animation-delay: 0s;
}
.down span:nth-of-type(2) {
    top: 16px;
    -webkit-animation-delay: .15s;
    animation-delay: .15s;
}
.down span:nth-of-type(3) {
    top: 32px;
    -webkit-animation-delay: .3s;
    animation-delay: .3s;
}
@-webkit-keyframes sdb {
    0% {
        opacity: 0;
    }
    50% {
        opacity: 1;
    }
    100% {
        opacity: 0;
    }
}
@keyframes sdb {
    0% {
        opacity: 0;
    }
    50% {
        opacity: 1;
    }
    100% {
        opacity: 0;
    }
}
.big-space{
    width:100%;
    position:relative;
}
.left-space{
    color:white;
    background: linear-gradient(to right, #DECBA4, #3E5151);
}
.particles-js {
    background-size: cover;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    
}
.my-name{
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    text-align: center;
}
.welcome{
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    text-align: center;
}
.site-copy{
    font-family: 'Yellowtail', cursive;
    font-weight: 400;
    text-align: center;
}

/* --------------------------------
* about
* -------------------------------- */
.about {
    padding: 80px 0;
    background: white;
    color: #333;
    width:100%;
}
.about-wrapper{
    margin-top: 40px;
    width:100%;
}
.about-name{
    font-weight:400;
    letter-spacing: 1px;
}
.about-subtxt{
    letter-spacing:1px;
    font-family: 'Old Standard TT', serif;
    font-size:18px;
	line-height:30px;
	font-weight:300;
}
.about-text {
    font-weight:200;
    font-size:15px;
    margin-top: 30px;
    line-height:35px;
}
.s-logo{
    opacity:0.3;
}
.photo-wrapper{
    text-align: center;
}
/* --------------------------------
* works
* -------------------------------- */
.works {
    padding: 80px 0;
    background: linear-gradient(to top, #323232 0%, #3F3F3F 40%, #1C1C1C 150%), linear-gradient(to top, rgba(255,255,255,0.40) 0%, rgba(0,0,0,0.25) 200%);
    background-blend-mode: multiply;
    color: white;
}
.bg{
    width:100%;
    height:100vh;
    position: fixed;
    left: 0;
    top: 0;
    z-index:999;
    padding-top:10px;
    
}
.card-title{
    padding:16px 30px;
	font-size:14px;
	line-height:15px;
	font-weight:bold;
	text-transform:uppercase;
	letter-spacing:2px;
}
.work-description{
    font-weight:200;
    font-size:15px;
    line-height:25px;
}
.work-card-title{
    text-align: center;
    letter-spacing: 3px;
    font-size: 2rem;
    font-weight:400;
}
.work-item{
    color:#d3b572;
    margin-bottom: 5px;
}
.work-img{
    cursor: pointer;
}
.github-link{
    color: #fff;
    text-decoration:underline;
}
.site-url{
    display: block;
    margin-bottom: 15px;
}
.site-url span{
    color: #fff;
    text-decoration:underline;
}
.work-img{
    width:100%;
}
/* --------------------------------
* skills
* -------------------------------- */
.skills {
    padding: 80px 0;
    background: linear-gradient(to bottom, #D5DEE7 0%, #E8EBF2 50%, #E2E7ED 100%), linear-gradient(to bottom, rgba(0,0,0,0.02) 50%, rgba(255,255,255,0.02) 61%, rgba(0,0,0,0.02) 73%), linear-gradient(33deg, rgba(255,255,255,0.20) 0%, rgba(0,0,0,0.20) 100%);
    background-blend-mode: normal,color-burn;
    color: #333;
    height:100vh;
}
.skills-wrapper {
    margin: 50px auto 0;
    height:auto;
}
.skillbar {
	position:relative;
	display:block;
	margin-bottom:53px;
	width:80%;
	background:#e2e1e2;
	height:7px;
	border-radius:3px;
}
.skillbar-title {
	position:absolute;
	top:-27px;
	left:0;
	font-weight:bold;
	font-size:13px;
	line-height:27px;
	letter-spacing:2px;
    color:black;
    display:block;
}
.skillbar-title span {
    display:inline-block;
    margin-left: 20px;
}
.skillbar-bar-html1 {
	height:7px;
	width:44%;
	background:#3E5151;
    transition: all 2s;
}
.skillbar-bar-html2 {
	height:7px;
	width:0%;
	background:#3E5151;
}
.skillbar-bar-vue1 {
	height:7px;
	width:35%;
	background:#3E5151;
    transition: all 2s;
}
.skillbar-bar-vue2 {
	height:7px;
	width:0%;
	background:#3E5151;
}
.skillbar-bar-jquery1 {
	height:7px;
	width:20%;
	background:#3E5151;
    transition: all 2s;
}
.skillbar-bar-jquery2 {
	height:7px;
	width:0%;
	background:#3E5151;
}
.skillbar-bar-php1 {
    height:7px;
	width:10%;
	background:#3E5151;
    transition: all 2s;
}
.skillbar-bar-php2 {
    height:7px;
	width:0%;
	background:#3E5151;
}
.skillbar-bar-mysql1{
	height:7px;
	width:10%;
	background:#3E5151;
    transition: all 2s;
}
.skillbar-bar-mysql2{
	height:7px;
	width:0%;
	background:#3E5151;
}
.skill-bar-percent {
	position:absolute;
	top:-24px;
	font-size:14px;
	color:#796f7a;
	margin-left:-20px;
}
.skill-text{
    font-weight:200;
    font-size:15px;
    line-height:35px;
}
/* --------------------------------
* contact
* -------------------------------- */
.contact {
    padding: 80px 0 150px;
    background: white;
    color: #333;
}
.contact-form {
    width: 50%;
    margin: 50px auto 0;
}
.send-btn{
    margin-top: 20px;
}
/* --------------------------------
* responsive
* -------------------------------- */

@media (min-width:960px) {
    .about{
        position: relative;
    }
    .s-logo{
        height:70%;
        position:absolute;
        top:50%;
        left: 50%;
        transform:translate(-50%, -50%);
    }
}
@media(min-width:600px) and (max-width:960px) {
    .text-wrap{
        text-align: center;
    }
}
@media (min-width: 769px) {
.big-space{
    overflow: hidden;
    position: relative;
    height: 100vh;
}
.left-space{
    transform:skew(-6deg, 0deg);
    margin-left:-10%;
    width:60%;
    height:100vh;
    top:0;
    left:0;
    z-index:998;
    position:absolute;
    overflow: hidden;
    padding-top: 10%;
}
.inner{
    transform:skew(6deg, 0deg);
    position: absolute;
    top:50%;
	left: 50%;
	transform:translate(-50%, -50%);
    width:100%;
    margin: 0 auto;
    text-align: center;
    margin-left:10%;
}
.particles-js {
    transform:skew(6deg, 0deg);
}
.my-name{
    transform:skew(6deg, 0deg);
    font-size:6vw;
}
.welcome{
    transform:skew(6deg, 0deg);
    font-size:2vw;
}
.site-copy{
    transform:skew(6deg, 0deg);
    font-size:6vw;
}
.right-space{
    width: 60%;
    height: 100vh;
    padding-top: 50%;
    position:absolute;
    background: url('../static/topme.jpg') center center /cover no-repeat;
    z-index:997;
    top:0;
    right:0;
}
}
@media (max-width: 768px) {
    
    .left-space{
        transform:skew(0deg, -10deg);
        margin-top:-10%;
        padding:30% 0;
        position: relative;
        overflow: hidden;
    }
    .particles-js {
        transform:skew(0deg, 10deg);
    }
    .inner{
        transform:skew(0deg, 10deg);
    }
    .my-name{
        font-size:10vw;
    }
    .welcome{
        font-size:4vw;
    }
    .site-copy{
        font-size:10vw;
    }
    .right-space{
        width:100%;
        height:80vw;
        background: url('../static/topme.jpg') center center /cover no-repeat;
        margin-top: -70px;
    }
    .heading {
        margin-top: 20px;
        font-size: 1.5rem;
    }
    /* --- about --- */
    .about-text {
        line-height: 1.8;
    }
    .text-wrap{
        position: relative;
    }
    .s-logo{
        height:80%;
        position:absolute;
        top:50%;
        left: 50%;
        transform:translate(-50%, -50%);
    }
    /* --- works --- */
    .work-title{
        font-size:25px;
    }
    /* --- skills --- */
    .skills{
        height:1000px;
    }
    .skillbar {
        width:90%;
    }
    /* --- contact --- */
    .contact {
        padding-bottom: 80px;
    }
    .contact-form {
        width: 80%;
    }
    
}
</style>