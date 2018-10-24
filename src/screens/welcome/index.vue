<template>
    <nb-container>
        <nb-grid>
            <nb-row>
                <swiper class="wrapper" :showsButtons="true">
                    <view class="slide1">
                        <text class="text-wrapper">Hello Swiper</text>
                    </view>
                    <view class="slide2">
                        <text class="text-wrapper">Beautiful</text>
                    </view>
                    <view class="slide3">
                        <text class="text-wrapper">And simple</text>
                    </view>
                </swiper>
            </nb-row>
        </nb-grid>
    </nb-container>
</template>

<script>
    import Swiper from 'react-native-swiper';
    export default {
        components: {
            Swiper
        }
    }
</script>

<style>
    .slide1 {
        flex: 1;
        justify-content: center;
        align-items: center;
        background-color: #9dd6eb;
    }
    .slide2 {
        flex: 1;
        justify-content: center;
        align-items: center;
        background-color: #97cae5;
    }
    .slide3 {
        flex: 1;
        justify-content: center;
        align-items: center;
        background-color: #92bbd9;
    }
    .text-wrapper {
        color: #fff;
        font-size: 30px;
        font-weight: bold;
    }
</style>