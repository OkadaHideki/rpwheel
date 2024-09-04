<template>
    <v-app>
        <v-app-bar color="primary">
            <template v-slot:prepend>
                <v-icon>mdi-dev-to</v-icon>
            </template>
            <v-app-bar-title class="d-flex flex-row justify-center align-center">RPWheel_OECU</v-app-bar-title>
            <Time></Time>
            <v-btn icon="mdi-account-circle-outline"></v-btn>
            <template v-slot:append>
                <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
            </template>
        </v-app-bar>
        <v-footer color="grey-darken-3" class="d-flex flex-row justify-center align-center" app>
            <h6>rpwheel</h6>
        </v-footer>
        <v-main>
            <slot />
        </v-main>
        <v-navigation-drawer location="right" v-model="drawer" disable-resize-watcher temporary>
            <v-list nav>
                <v-list-item to="/" prepend-icon="mdi-file-document-outline" title="搬入票" value="home"></v-list-item>
                <v-list-item to="/map" prepend-icon="mdi-cellphone-marker" title="ドライバー位置情報" value="about"></v-list-item>
                <v-list-item to="/users" prepend-icon="mdi-account-multiple" title="ユーザー管理" value="user"></v-list-item>
                <v-list-item></v-list-item>
                <v-list-item></v-list-item>
                <v-list-item></v-list-item>
                <v-list-item></v-list-item>
                <v-list-item></v-list-item>
                <v-list-item prepend-icon="mdi-logout" class="bg-red" title="ログアウト" value="user"></v-list-item>
            </v-list>
        </v-navigation-drawer>
    </v-app>
</template>
<script setup>
import { ref } from 'vue'

const drawer = ref(false)

const indexRef = ref()
const mapRef = ref()
</script>