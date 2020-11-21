<template>
    <div id="home">
        <Header />
        <div class="index">
            <div class="header">
                <transition name="header">
                    <div v-show="show" class="site-wrapper">
                        <h1 class="site-title">SEIYA KATO</h1>
                        <h3 class="site-description">Welcome to my portfolio-site.</h3>
                    </div>
                </transition>
            </div>
            <section class="about">
                <div class="heading-wrapper">
                    <h2 class="heading" id="about" >ABOUT</h2>
                </div>
                <div class="about-wrapper">
                <v-container>
                    <v-row justify="space-around">
                    <v-col md="6">
                        <transition name="name">
                            <div v-show="visible">
                                <h4 class="my-name">Seiya Kato</h4>
                                <p class="about-subtxt">I'm aiming to be a front end engineer</p>
                            </div>
                        </transition>
                        <transition name="text">
                            <p class="about-text" v-show="visible">
                            初めまして。ご覧いただきありがとうございます。<br>
                            名古屋在住の営業マンでwebサイトを作成することに興味を持ち<br>
                            フロントエンドエンジニアを目指し日々勉強しています。<br>
                            スタイリッシュで少しのユーモアがあるサイト制作をしていきたいです。
                            </p>
                        </transition>
                    </v-col>  
                    <v-col md="4">
                        <transition name="img">
                            <img src="../images/img-me.jpg" v-show="visible">
                        </transition>
                    </v-col>
                    </v-row>
                </v-container>
                </div>
            </section>
            <section class="works">
                <div class="heading-wrapper">
                    <h2 class="heading" id="works">WORKS</h2>
                </div> 
                <div class="works-wrapper">
                    <v-container class="pa-4 text-center">
                        <v-row
                            class="fill-height"
                            align="center"
                            justify="center"
                        >
                            <template v-for="(worklist, i) in worklists">
                                <v-col
                                    cols="12"
                                    md="4"
                                    :key="i"
                                >
                                    <v-dialog v-model="worklist.dialog">
                                        <template v-slot:activator="{ on }">
                                                <v-card
                                                v-on="on"
                                                class="card-btn"
                                                hover
                                                >
                                                    <v-img
                                                        :src='worklist.img'
                                                        height="225px"
                                                    >
                                                    </v-img>
                                                </v-card>
                                                <p class="mt-4 subheading text-center card-title">
                                                        {{worklist.title}}
                                                </p>
                                        </template>
                                            <v-card dark>
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
                                    </v-dialog>
                                </v-col>
                            </template> 
                        </v-row>
                    </v-container>
                </div>
            
            </section>
            <section class="skills">
                <div class="heading-wrapper">
                    <h2 class="heading" id="skills">SKILLS</h2>
                </div>
                <div class="skills-wrapper">
                    <v-container>
                        <v-row>
                            <v-col md="6" cols="12">
                                <transition name="text">
                                <p class="skill-text" v-show="visible2">
                                HTML/CSSと並行してJavascriptを学びつつ徐々にJQueryに移行していきましたが
                                Vueを使用することでの多くの利点を知り現在はNuxtをメインに使用しています。<br>
                                PHPやMySQLは現在基礎を学んだ段階ですが今後も継続的に学ぶつもりです。<br>
                                浮かんだアイディアを具現化するためにも幅広くスキルを習得していきたいと考えています。
                                </p>
                                </transition>
                            </v-col>
                            <v-col md="6" cols="12">
                                <transition name="img">
                                <div v-show="visible2">
                                <v-row justify="center">
                                <div class="skillbar clearfix " data-percent="94%">
                                    <div class="skillbar-title">HTML/CSS<span >44%</span></div>
                                    <div class="skillbar-bar-html"></div>
                                    <div class="skill-bar-percent"></div>
                                </div> <!-- End Skill Bar -->
                                </v-row>
                                <v-row justify="center">
                                <div class="skillbar clearfix " data-percent="86%">
                                    <div class="skillbar-title">Vue.js<span >35%</span></div>
                                    <div class="skillbar-bar-vue"></div>
                                    <div class="skill-bar-percent"></div>
                                </div> <!-- End Skill Bar -->
                                </v-row>
                                <v-row justify="center">
                                <div class="skillbar clearfix " data-percent="41%">
                                    <div class="skillbar-title">jQuery<span >20%</span></div>
                                    <div class="skillbar-bar-jquery"></div>
                                    <div class="skill-bar-percent"></div>
                                </div> <!-- End Skill Bar -->
                                </v-row>
                                <v-row justify="center">
                                <div class="skillbar clearfix " data-percent="52%">
                                    <div class="skillbar-title">PHP<span >10%</span></div>
                                    <div class="skillbar-bar-php"></div>
                                    <div class="skill-bar-percent"></div>
                                </div> <!-- End Skill Bar -->  
                                </v-row>
                                <v-row justify="center">
                                <div class="skillbar clearfix " data-percent="52%">
                                    <div class="skillbar-title">MySQL<span >10%</span></div>
                                    <div class="skillbar-bar-mysql"></div>
                                    <div class="skill-bar-percent"></div>
                                </div> <!-- End Skill Bar -->  
                                </v-row>
                                </div>
                                </transition>
                            </v-col>   
                        </v-row>
                    </v-container>
                </div>
            </section>
            <section class="contact" >
                <div class="heading-wrapper">
                    <h2 class="heading" id="contact">CONTACT</h2>
                </div>
                <v-form name="contact" method="POST" class="contact-form">
                    <v-text-field label="NAME" name="name" filled clearable color="grey darken-3" required></v-text-field>
                    <v-text-field label="E-mail" name="email" filled clearable color="grey darken-3" required></v-text-field>
                    <v-textarea label="MESSAGE" name="message" filled clearable color="grey darken-3" required></v-textarea>
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
                </v-form>
            </section>
            <Footer />
        </div>
    </div>
</template>

<script>
import Header from '~/components/Header.vue'
import Footer from '~/components/Footer.vue'
export default {
components: {
    Header,
    Footer,
},
data(){
    return{
        isView: false,
        show:false,
        visible:false,
        visible2:false,
        worklists:[
            {
                title: 'SEIYA KATO',
                dialog:false,
                img: require('../images/nightmin.jpg'),
                description:'制作物を掲載するための媒体が必要と感じ、制作しました。レイアウトやデザインに関しては見やすさを追求しシンプルにまとめています。現在は最低限の機能しか実装していないため自身の技術力の向上と共にリッチ化を図るべく徐々に手を加えていけたらと思っています。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Netlify',
                url:'https://seiyakato.netlify.app/',
                github:'https://github.com/Se-Ya66/SEIYA-KATO'
            },
            {
                title: 'NEO-SOUL SUGGESTER',
                dialog:false,
                img: require('../images/peoplemin.jpg'),
                description:'大好きな音楽ジャンルの１つであるネオソウルの魅力を紹介する目的で制作しました。アーティストのデータベースだけでなく個人的におすすめな曲紹介ページも用意しています。サイト内の音源は全てspotifyのリンクより試聴可能です。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Netlify',
                url:'https://neosoul-suggester.netlify.app/',
                github:'https://github.com/Se-Ya66/NEOSOUL-SUGGESTER'
            },
            {
                title:"MY Todo",
                dialog:false,
                img: require('../images/todomin.jpg'),
                description:'学習を通じて得たスキルを試す目的で制作しました。自身では初の制作物となるためVuetifyの各種UIコンポーネントの使用やFirebaseでのログイン、データの保管など苦労する点は多々ありましたが基礎は学べたと感じています。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Firebase /Netlify',
                url:'https://mytodocards.netlify.app/',
                github:'https://github.com/Se-Ya66/My-Todo'
            }
        ],
        name: "",
        email: "",
        message: "",
        botfield: "",
    }
},
mounted() {
    window.addEventListener('scroll', this.handleScroll);
    this.show = !this.show;
},
methods: {
    handleScroll() {
        if (window.scrollY > 10) {
        this.isView = true;
        } else {
        this.isView = false;
        }
        if (!this.visible) {
        const top = this.$el.getBoundingClientRect().top;
        this.visible = top < window.innerHeight + 100;
        }
        if (!this.visible2) {
        const top = document.querySelector('.skills-wrapper').getBoundingClientRect().top;
        this.visible2 = top < window.innerHeight + 100;
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
    }   
    }
}
</script>

<style>
a{
    color:#fff;
}
#home{
    max-width: 100%;
}
.v-btn{
    font-family: 'Montserrat', sans-serif;
}
*{
    margin : 0;
    padding : 0;
}
.index {
    box-sizing : border-box;
    color: #fff;
    font-size: 1.4rem;
    font-family: 'Montserrat', sans-serif;  
}
*, *::before, *::after {
    box-sizing: border-box;
}
a{
    color:#fff;
}
/* --------------------------------
* transition
* -------------------------------- */
.header-enter-active {
    transition: opacity 4s;
}
.header-enter {
    opacity: 0;
}
.header-enter-to {
    opacity: 1;
}
.text-enter-active {
    transition: opacity 3s;
}
.text-enter {
    opacity: 0;
}
.text-enter-to {
    opacity: 1;
}
.name-enter-active {
    transition: opacity 2s;
}
.name-enter {
    opacity: 0;
}
.name-enter-to {
    opacity: 1;
}
.img-enter-active, .img-leave-active {
    transform: translate(0px, 0px);
    transition: transform 1s cubic-bezier(0, 0, 0.2, 1) 0s;
}
.img-enter, .img-leave-to {
    transform: translateX(100vw) translateX(0px);
}
/* --------------------------------
* parts
* -------------------------------- */
.heading {
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
.header{
    width: 100%;
    height: 100vh;
    padding-top: 50%;
    position:relative;
    background: url('../images/night.jpg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
.site-wrapper{
    position:absolute;
	left:37%;
	top:40%;
}
.site-title {
    text-transform:uppercase;
    line-height:normal;
    font-weight:300;
    color:#fff;
    letter-spacing:6px;
    margin-bottom:10px;
}
.site-description{
    color:#fff;
    font-size:19px;
    line-height:normal;
    font-weight:400;
    text-transform:none;
    margin-bottom:20px;
    letter-spacing:2px;
    font-family: 'Old Standard TT', serif;
}
/* --------------------------------
* about
* -------------------------------- */
.about {
    padding: 80px 30px;
    background-color: #fff;
    color: #333;
}
.about-wrapper{
    margin-top: 40px;
}
.my-name{
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
/* --------------------------------
* works
* -------------------------------- */
.works {
    padding: 80px 0;
    background-color: #383634;
    color: #fff;
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
    background:#f8f8f8;
    color: #333;
}
.skills-wrapper {
    margin: 50px auto 0;
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
    color:#5b4c5c;
    display:block;
}
.skillbar-title span {
    display:inline-block;
    margin-left: 20px;
}
.skillbar-bar-html {
	height:7px;
	width:44%;
	background:#e88988;
}
.skillbar-bar-vue {
	height:7px;
	width:35%;
	background:#e88988;
}
.skillbar-bar-jquery {
	height:7px;
	width:20%;
	background:#e88988;
}
.skillbar-bar-php {
	height:7px;
	width:10%;
	background:#e88988;
}
.skillbar-bar-mysql{
    height:7px;
	width:10%;
	background:#e88988;
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
    background-color: white;
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
@media (max-width: 1024px) {
    .header{
        width: 100%;
        height: 100vh;
        padding-top: 50%;
        position:relative;
        background: url('../images/night-m.jpg');
        background-repeat: no-repeat;
        background-position: center center;
        background-size: cover;
    }
    .site-wrapper{
        text-align: center;
        position:absolute;
        left:37%;
        top:40%;
    }
}
@media (max-width: 768px) {
    
    .header{
        position: relative;
    }
    .site-wrapper{
        text-align: center;
        position:absolute;
        left:30%;
        top:40%;
    }
}
@media (max-width: 767px) {
    
    .heading {
        margin-top: 20px;
        font-size: 1.5rem;
    }
    /* --- header --- */
    .header{
        width: 100%;
        height: 100vh;
        padding-top: 50%;
        position:relative;
        background: url('../images/night-s.jpg');
        background-repeat: no-repeat;
        background-position: center center;
        background-size: cover;
    }
    .site-wrapper{
        text-align: center;
        position:absolute;
        left:25%;
        top:40%;
    }
    .site-description{
        font-size: 13px;
    }
    .site-title {
        font-size: 26px;
    }
    /* --- about --- */
    .about-text {
        line-height: 1.8;
    }
    /* --- works --- */
    .work-title{
        font-size:25px;
    }
    /* --- skills --- */
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