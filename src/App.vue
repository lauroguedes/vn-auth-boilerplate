
<template>
    <root>
        <!--<welcome-screen v-if="showWelcomeScreen"></welcome-screen>
        <auth-login-screen v-if="!isAuth"></auth-login-screen>-->
        <app-navigation></app-navigation>
    </root>
</template>

<script>
    import React from 'react';
    import { StackNavigator, DrawerNavigator } from 'vue-native-router';
    import { Root } from 'native-base';
    import HomeScreen from './screens/home';
    import SideBarScreen from "./screens/sidebar";

    const Drawer = DrawerNavigator(
        {
            Home: {screen: HomeScreen},
        },
        {
            initialRouteName: 'Home',
            contentOptions: {
                activeTintColor: '#e91e63'
            },
            contentComponent: props => {
                return <SideBarScreen {...props} />
            }
        }
    );

    const AppNavigation = StackNavigator({
            Drawer: {screen: Drawer}
        },
        {
            initialRouteName: 'Drawer',
            headerMode: 'none'
        }
    );

    export default {
        components: {
            Root,
            AppNavigation
        }
    }
</script>