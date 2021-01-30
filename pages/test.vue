<template>
    <div>
        <div class="testbg">
            <div class="test-inner">
                <div>
                    ダミーダミーダミーダミーダミーダミーダミーダミーダミーダミーダミーダミー
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return{

        }
    }
}
</script>

<style>
.testbg{
    position: fixed;
    width:100%;
    height: 100vh;
    background-color: black;
}
.test-inner{
    position: fixed;
    width:80%;
    /* height: 100vh; */
    background-color: white;
    top: 50%;
    left: 50%;
    transform: translateY(-50%) translateX(-50%);
}
</style>