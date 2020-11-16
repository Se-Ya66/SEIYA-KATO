<template>
    <div>
        <v-app-bar
        :color="isView === true ? 'white' : 'transparent'"
        app
        flat
        >
            <v-menu offset-y>
                <template v-slot:activator="{ on, attrs }">
                    <v-app-bar-nav-icon 
                    v-bind="attrs"
                    v-on="on"
                    :color="isView === true ? 'black' : 'white'"
                    class="d-sm-none hamb"
                    >
                    </v-app-bar-nav-icon>
                </template>
                <v-list>
                    <v-list-item
                    v-for="(item, i) in items"
                    :key="i"
                    >
                        <nuxt-link  v-scroll-to="item.link" to>
                            <v-list-item-title
                            class="link">{{ item.title }}</v-list-item-title>
                        </nuxt-link>
                    </v-list-item>
                </v-list>
            </v-menu>
            <v-container>
                <v-toolbar-items
                class="hidden-xs-only nav">
                    <v-row
                    align="center"
                    justify="center"
                    class="d-xs-none"
                    >
                        <v-col cols="1" md="1" sm="2" class="d-xs-none">
                            <nuxt-link class="link" v-scroll-to="'#home'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">HOME</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1" md="1" sm="2" class="d-xs-none">
                            <nuxt-link class="link" v-scroll-to="'#about'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">ABOUT</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1" md="1" sm="2" class="d-xs-none">
                            <nuxt-link class="link" v-scroll-to="'#works'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">WORKS</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1" md="1" sm="2" class="d-xs-none">
                            <nuxt-link class="link" v-scroll-to="'#skills'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">SKILLS</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1" md="1" sm="2" class="d-xs-none">
                            <nuxt-link class="link" v-scroll-to="'#contact'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">CONTACT</p>
                            </nuxt-link>
                        </v-col>
                    </v-row>
                </v-toolbar-items>
            </v-container>
    </v-app-bar>
    </div>
</template>

<script>
export default {
    data(){
        return{
        isView: false,
        show: false,
        items:[
            {   
                title:'HOME',
                link:'#home' 
            },
            {   
                title:'ABOUT',
                link:'#about' 
            },
            {   
                title:'WORKS',
                link:'#works' 
            },
            {   
                title:'SKILLS',
                link:'#skills' 
            },
            {   
                title:'CONTACT',
                link:'#contact' 
            },
        
        ],
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
.link{
    color:black;
    font-family: 'Montserrat', sans-serif;
}
.white-color{
    color:white;
}
.white-text,
.black-text{
    color:#fff;
    display: inline-block;
    text-align: center;
    font-family: 'Montserrat', sans-serif;
    position: relative;
    padding-bottom: 3px;
    font-size:16px;
    margin-top:13px;
}
.black-text{
    color:#000;
}
.white-text:before,
.black-text:before{
	content: '';
	width: 0;
	left: 50%;
	bottom: 0;
	transition: all 0.3s ease;
	border-bottom: 2px solid #fff;
	position: absolute;
	display: block;
}
.white-text:hover:before,
.black-text:hover:before{
	width: 50%;
	border-bottom: 2px solid #fff;
}
.white-text:after,
.black-text:after{
	content: '';
	width: 0;
	right: 50%;
	bottom: 0;
	transition: all 0.3s ease;
	border-bottom: 2px solid #fff;
	position: absolute;
	display: block;
}
.white-text:hover:after,
.black-text:hover:after{
	width: 50%;
	border-bottom: 2px solid #fff;
}
.black-text:before,.black-text:hover:before,
.black-text:after,.black-text:hover:after{
    border-bottom: 2px solid #000;
}
@media (min-width:768px) {
    .hamb{
        display: none;
    }
}
@media (max-width: 767px) {
    .nav{
        display: none;
    }
}
</style>