<template>
    <div id="app">
        <router-view />
    </div>
</template>
<script>
    import { mapMutations, mapActions } from 'vuex'
    export default {
        name: 'App',
        created() {
            this.check()
                .then(res => {
                    this.setUser(res.data)
                    this.setLogin(res.isLogin)
                    this.$router.push('/user')
                })
                .catch(error => {})
        },
        methods: {
            ...mapMutations(['setUser', 'setLogin']),
            ...mapActions(['check'])
        }
    }
</script>
<style lang="scss">
    @import '@/assets/global.scss';
    @import '@/assets/color.scss';
    html, body {
        width: 100%;
        height: 100%;
    }
    #app {
        width: 100%;
        height: 100%;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        background: rgb(245, 245, 245);
    }
</style>