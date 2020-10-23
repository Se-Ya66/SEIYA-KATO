<template>
    <div>
        <v-footer color="black" >
            <v-container class="pa-6 text-center">
                <v-row  class="icons" justify="center" align="center">
                    <v-col md="1">
                        <v-icon large color="white" class="icon">mdi-twitter</v-icon>
                    </v-col >
                    <v-col md="1">
                        <v-icon large color="white" class="icon">mdi-facebook</v-icon>
                    </v-col>
                    <v-col md="1">
                        <v-icon large color="white" class="icon">mdi-github</v-icon>
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
/** 画像ホバー時のアニメを設定 */
.icon:hover{
    -webkit-animation: bound 1s ease-in infinite;
    -moz-animation:    bound 1s ease-in infinite;
    animation: bound 1s ease-in infinite;

cursor: pointer;
}

/** アニメーションの定義 */
@keyframes bound {
/** 開始時は１倍の大きさ */
from { transform: scale(1); }
/** 0%～25%にかけて1.15倍する */
25% { transform: scale(1.15); }
/** 25%～50%にかけて0.95倍する */
50% { transform: scale(0.95); }
/** 50%～75%にかけて1.05倍する */
75% { transform: scale(1.05); }
/** 終了時は元の大きさに戻す */
to { transform: scale(1); }
}
</style>