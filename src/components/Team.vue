<template>
  <div class="team pt-4">
    <h1 class="subtitle-1 grey--text">Team</h1>

    <v-container fluid class="my-4">
      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
          <v-card flat class="text-center ma-3">
            <v-responsive class="pt-4">
              <v-avatar>
                <img :src="person.avatar">
              </v-avatar>
            </v-responsive>
            <v-card-text>
              <div>
                <p class="text-subtitle-1 mb-0">{{ person.name }}</p>
                <p class="grey--text">{{ person.role }}</p>
              </div>
            </v-card-text>
            <v-card-actions>
              <v-btn plain color="grey">
                <v-icon small left>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
  
</template>

<script>

  export default {
    name: 'Team',
    components: {

    },
    data() {
      return {
        team: [
          {name: 'Peter Parker', role: 'Web Developer', avatar: '/generic_avatar.png'},
          {name: 'Bruce Wayne', role: 'Graphic Designer', avatar: '/generic_avatar.png'},
          {name: 'Leo', role: 'Web Developer', avatar: '/generic_avatar.png'},
          {name: 'Goku', role: 'Social media maverick', avatar: '/generic_avatar.png'},
          {name: 'Naruto', role: 'Sales guru', avatar: '/generic_avatar.png'}       
        ]
      }
    }
  }
</script>