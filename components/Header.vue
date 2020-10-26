<template>
    <div>
        <v-app-bar
        :color="isView === true ? 'white' : 'transparent'"
        app
        flat
        >
            <v-container>
                <v-toolbar-items>
                    <v-row
                    align="center"
                    justify="center"
                    >
                        <v-col cols="1">
                            <nuxt-link class="link" v-scroll-to="'#home'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">HOME</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1">
                            <nuxt-link class="link" v-scroll-to="'#about'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">ABOUT</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1">
                            <nuxt-link class="link" v-scroll-to="'#works'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">WORKS</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1">
                            <nuxt-link class="link" v-scroll-to="'#skills'" to>
                                <p text :class="isView === true ? 'black-text' : 'white-text'">SKILLS</p>
                            </nuxt-link>
                        </v-col>
                        <v-col cols="1">
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

</style>