<template>
    <nav>
        <v-app-bar dense app flat class="">
            <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
            <v-app-bar-title class="text-uppercase grey--text">
                <span class="font-weight-light">Todo</span>
                <span>Ninja</span>
            </v-app-bar-title>
            <v-spacer></v-spacer>
            <v-btn plain color="grey">
                <span>Sign Out</span>
                <v-icon right>mdi-exit-to-app</v-icon>
            </v-btn>
            
        </v-app-bar>

        <v-navigation-drawer v-model="drawer" app class="primary">
            <v-layout column align-center>
                <v-flex class="mt-5">
                    <v-avatar size="100">
                        <img src="/generic_avatar.png">
                    </v-avatar>
                    <p class="white--text text-center text-h6 mt-1">Leo</p>
                </v-flex>
            </v-layout>
            <v-container>
                <v-list>
                    <v-list-item v-for="link in links" :key="link.route" router :to="link.route">
                        <v-list-item-action>
                            <v-icon class="white--text">{{ link.icon }}</v-icon>
                        </v-list-item-action>
                        <v-list-item-content>
                            <v-list-item-title class="white--text">{{ link.text }}</v-list-item-title>
                        </v-list-item-content>

                    </v-list-item>
                </v-list>
            </v-container>
        </v-navigation-drawer>
    </nav>
</template>

<script>
export default {
    data: () => ({
        drawer: false,
        links: [
            {icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
            {icon: 'mdi-folder', text: 'My Projects', route: '/projects'},
            {icon: 'mdi-account', text: 'Team', route: '/team'}
        ]
    }),
}
</script>