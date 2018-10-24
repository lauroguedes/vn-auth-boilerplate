<template>
    <view class="container">
        <app-loading v-if="!isAppReady"> </app-loading>
        <welcome-screen v-if="isAppReady && showWelcome"></welcome-screen>
        <auth-login-screen v-if="!isAuth && isAppReady && !showWelcome"></auth-login-screen>
        <app v-if="isAppReady && isAuth && !showWelcome"></app>
    </view>
</template>

<script>
    import Vue from "vue-native-core";
    import { VueNativeBase } from "native-base";
    import { AppLoading } from "expo";
    import App from "../App";
    import AuthLoginScreen from '../screens/auth/login';
    import WelcomeScreen from '../screens/welcome';
    // registering all native-base components to the global scope of the Vue
    Vue.use(VueNativeBase);

    export default {
        components: {
            App,
            AppLoading,
            AuthLoginScreen,
            WelcomeScreen
        },
        data() {
            return {
                isAppReady: false,
                isAuth: true,
                showWelcome: true
            };
        },
        mounted() {
            this.loadFonts();
        },
        methods: {
            loadFonts: async function() {
                try {
                    this.isAppReady = false;
                    await Expo.Font.loadAsync({
                        Roboto: require("native-base/Fonts/Roboto.ttf"),
                        Roboto_medium: require("native-base/Fonts/Roboto_medium.ttf"),
                        Ionicons: require("@expo/vector-icons/fonts/Ionicons.ttf")
                    });
                    this.isAppReady = true;
                } catch (error) {
                    console.log("some error occured", error);
                    this.isAppReady = true;
                }
            }
        }
    };
</script>

<style>
    .container {
        flex: 1;
    }
</style>