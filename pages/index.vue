<template>
    <div id="home">
        <Header />
        <div class="index">
            <div class="header">
                <transition>
                    <div v-if="show" class="site-wrapper">
                        <h1 class="site-title">SEIYA KATO</h1>
                        <h3 class="site-description">Welcome to my portfolio-site.</h3>
                    </div>
                </transition>
            </div>
            <section class="about">
                <div class="heading-wrapper">
                    <h2 class="heading" id="about">ABOUT</h2>
                </div>
                <div class="about-wrapper">
                <v-container>
                    <v-row justify="space-around">
                    <v-col md="8">
                        <h4 class="my-name">Seiya Kato</h4>
                        <p class="about-subtxt">I'm aiming to be a front end engineer</p>
                        <p class="about-text">
                        初めまして。ご覧いただきありがとうございます。<br>
                        名古屋在住の営業マンでwebサイトを作成することに興味を持ち<br>
                        フロントエンドエンジニアを目指し日々勉強しています。<br>
                        スタイリッシュで少しのユーモアがあるサイト制作をしていきたいです。
                        </p>
                    </v-col>  
                    <v-col>
                        <img src="../images/img-me.jpg">
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
                                                <h1>{{worklist.title}}</h1>
                                                </v-card-title>
                                                <v-container>
                                                    <v-row>
                                                        <v-col>
                                                            <h4 class="work-item">Concept</h4>
                                                            <p class="work-description">{{worklist.description}}</p>
                                                            <h4 class="work-item">Skills</h4>
                                                            <p>{{worklist.Skills}}</p>
                                                            <h4 class="work-item">Site</h4>
                                                            <p>{{worklist.url}}</p>
                                                            <a :href="worklist.github">
                                                                <v-icon>mdi-github</v-icon>
                                                                <span class="github-link">GitHub</span>
                                                            </a>
                                                        </v-col>
                                                        <v-col>
                                                            <img :src='worklist.img'>
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
                            <v-col>
                                <p class="skill-text">
                                HTML/CSSと並行してJavascriptを学びつつ徐々にJQueryに移行していきましたが
                                Vueを使用することでの多くの利点を知り現在はNuxtをメインに使用しています。<br>
                                PHPやMySQLは現在基礎を学んだ段階ですが今後も継続的に学ぶつもりです。<br>
                                浮かんだアイディアを具現化するためにも幅広くスキルを習得していきたいと考えています。
                                </p>
                            </v-col>
                            <v-col>
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
                            </v-col>   
                        </v-row>
                    </v-container>
                </div>
            </section>
            <section class="contact" >
                <div class="heading-wrapper">
                    <h2 class="heading" id="contact">CONTACT</h2>
                </div>
                <v-form class="contact-form">
                    <v-text-field label="NAME" filled clearable color="grey darken-3"></v-text-field>
                    <v-text-field label="E-mail" filled clearable color="grey darken-3"></v-text-field>
                    <v-textarea label="MESSAGE" filled clearable color="grey darken-3"></v-textarea>
                    <v-row justify="center">
                        <v-btn
                        x-large
                        class="send-btn"
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
        worklists:[
            {
                title: 'SEIYA KATO',
                dialog:false,
                img: require('../images/nightmin.jpg'),
                description:'制作物を掲載するための媒体が必要と感じ、制作しました。レイアウトやデザインに関しては見やすさを追求しシンプルにまとめています。現在は最低限の機能しか実装していないため自身の技術力の向上と共にリッチ化を図るべく徐々に手を加えていけたらと思っています。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify',
                url:'https://www.google.com',
                github:'https://github.com/Se-Ya66/SEIYA-KATO'
            },
            {
                title: 'NEO-SOUL SUGGESTER',
                dialog:false,
                img: require('../images/peoplemin.jpg'),
                description:'大好きな音楽ジャンルの１つであるネオソウルの魅力を紹介する目的で制作しました。アーティストのデータベースだけでなく個人的におすすめな曲紹介ページも用意しています。サイト内の音源は全てspotifyのリンクより試聴可能です。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify',
                url:'https://www.google.com',
                github:'https://github.com/Se-Ya66/NEOSOUL-SUGGESTER'
            },
            {
                title:"MY Todo",
                dialog:false,
                img: require('../images/todomin.jpg'),
                description:'学習を通じて得たスキルを試す目的で制作しました。自身では初の制作物となるためVuetifyの各種UIコンポーネントの使用やFirebaseでのログイン、データの保管など苦労する点は多々ありましたが基礎は学べたと感じています。',
                Skills:'HTML /CSS /Nuxt.js /Vuetify /Firebase',
                url:'https://www.google.com',
                github:'https://github.com/Se-Ya66/My-Todo'
            }
        ]
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
    },
    change_class: function() {
    this.isView = !this.isView
}
}
}
</script>

<style>
.v-enter-active {
    transition: opacity 3s;
}
.v-enter {
    opacity: 0;
}
.v-enter-to {
    opacity: 1;
}
.v-btn{
    font-family: 'Montserrat', sans-serif;
}
*{
    margin : 0;
    padding : 0;
}
.index {

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
.header {
    position:relative;
    text-align: center;
    background: #151515 url('../images/night.jpg') center center / cover no-repeat fixed;
    background-size: cover;
    height: 100vh;
    position:relative;
}
.site-wrapper{
    position:absolute ;
	left:40%;
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
    color: inherit;
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
    display: table;
    width: 80%;
    margin: 50px auto 0;
    table-layout: fixed;
}
.skillset {
	background:#f8f8f8;
	display:table;
	width:100%;
}
.skillset .container{
	padding-top:66px ;
	padding-bottom:64px ;
}
.skillbar {
	position:relative;
	display:block;
	margin-bottom:53px;
	width:50%;
	background:#e2e1e2;
	height:7px;
	border-radius:3px;
	-moz-border-radius:3px;
	-webkit-border-radius:3px;
	-webkit-transition:0.4s linear;
	-moz-transition:0.4s linear;
	-ms-transition:0.4s linear;
	-o-transition:0.4s linear;
	transition:0.4s linear;
	-webkit-transition-property:width, background-color;
	-moz-transition-property:width, background-color;
	-ms-transition-property:width, background-color;
	-o-transition-property:width, background-color;
	transition-property:width, background-color;
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
* footer
* -------------------------------- */
.footer {
    padding: 12px 0;
    font-size: 1.3rem;
}
/* --------------------------------
* smart phone
* -------------------------------- */
@media (max-width: 1024px) {
    body {
    background-image: none;
    }
}
@media (max-width: 768px) {
    body {
    font-size: 1.3rem;
    }
    .heading {
    margin-top: 20px;
    font-size: 2.5rem;
    }
    .button:hover {
    opacity: 1;
    }
    /* --- header --- */
    .header {
    padding-top: 60px;
    }
    .site-title-sub {
    font-size: 1.7rem;
    }
    .site-title-sub::before,
    .site-title-sub::after {
    display: block;
    width: 80%;
    margin: 10px auto;
    }
    .site-title {
    margin-top: 35px;
    font-size: 5rem;
    }
    /* --- about --- */
    .about-text {
    line-height: 1.8;
    }
    /* --- works --- */
    .works-wrapper,
    .work-box {
    display: block;
    }
    .work-image {
    display: none;
    }
    .work-description {
    position: relative;
    }
    .work-box::after {
    top: 0;
    height: 100%;
    background-size: cover;
    transform: none;
    }
    /* --- skills --- */
    .skills-wrapper,
    .skill-box {
    display: block;
    }
    .skill-box {
    margin: 40px auto;
    }
    .skill-icon {
    width: 100px;
    height: 100px;
    font-size: 5rem;
    line-height: 92px;
    }
    .skill-text {
    margin: 0;
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
