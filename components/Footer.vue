<template>
    <div>
        <v-footer color="black" >
            <v-container class="pa-6 text-center">
                <v-row  class="icons" justify="center" align="center">
                    <v-col md="1" sm="1">
                        <a href="https://twitter.com/s_kato66">
                            <v-icon large color="white" class="icon">mdi-twitter</v-icon>
                        </a>
                    </v-col >
                    <v-col md="1" sm="1">
                        <a href="https://www.facebook.com/profile.php?id=100057343186398">
                            <v-icon large color="white" class="icon">mdi-facebook</v-icon>
                        </a>
                    </v-col>
                    <v-col md="1" sm="1">
                        <a href="https://github.com/Se-Ya66">
                            <v-icon large color="white" class="icon">mdi-github</v-icon>
                        </a>
                    </v-col>
                </v-row>
                <v-row justify="center" align="center" class="copyright">
                    © 2020 SEIYA KATO
                </v-row>
                <v-row justify="center">
                    <nuxt-link class="link" v-scroll-to="'#home'" to><v-icon x-large color="white">mdi-arrow-up-drop-circle-outline</v-icon></nuxt-link>
                </v-row>
            </v-container>
        </v-footer>
    </div>
</template>


<script>
export default {
    
}
</script>

<style>
a{
    text-decoration: none;
}
.link{
    text-decoration: none;
}
.copyright{
    margin-bottom: 20px;
    letter-spacing: 2px;
    font-size: 15px;
    color: white;
}
.icons{
    margin-bottom: 20px;
}
.icon{
    transform: scale(1);
}
.icon:hover{
    -webkit-animation: bound 1s ease-in infinite;
    -moz-animation:    bound 1s ease-in infinite;
    animation: bound 1s ease-in infinite;
    cursor: pointer;
}
@keyframes bound {
    from { transform: scale(1); }
    25% { transform: scale(1.15); }
    50% { transform: scale(0.95); }
    75% { transform: scale(1.05); }
    to { transform: scale(1); }
}
</style>