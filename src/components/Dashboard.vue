<template>
  <div class="home pt-4">
    <h1 class="subtitle-1 grey--text">Dashboard</h1>

    <v-container class="mt-8">

      <v-layout row class="mb-8">
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small plain color="grey" @click="sortBy('title')" v-bind="attrs" v-on="on">
              <v-icon left small>mdi-folder</v-icon>
              <span class="caption text-lowercase">By project name</span>
            </v-btn>
          </template>
          <span>Sort projects by name</span>
        </v-tooltip>
        <v-tooltip top>
          <template v-slot:activator="{ on, attrs }">
            <v-btn small plain color="grey" @click="sortBy('person')" v-bind="attrs" v-on="on">
              <v-icon left small>mdi-account</v-icon>
              <span class="caption text-lowercase">By person</span>
            </v-btn>
          </template>
          <span>Sort projects by owner</span>
        </v-tooltip>
      </v-layout>

      <v-card flat class="mb-8" v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 pb-0 project ${project.status}`">
          <v-flex xs12 md6>
            <p class="caption grey--text mb-1">Project title</p>
            <p>{{ project.title }}</p>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <p class="caption grey--text mb-1">Person</p>
            <p>{{ project.person }}</p>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <p class="caption grey--text mb-1">Due by</p>
            <p>{{ project.due }}</p>
          </v-flex>
          <v-flex xs2 sm4 md2>
            <div>
              <v-chip small :color="colors[project.status]" :class="`white--text caption my-2`">{{ project.status }}</v-chip>
            </div>
          </v-flex>
          <v-flex xs12>
            <v-divider></v-divider>
          </v-flex>
        </v-layout>
      </v-card>
    </v-container>
  </div>
  
</template>

<script>

  export default {
    name: 'Dashboard',
    components: {

    },
    data: function() {
      return {
      projects: [
        {title: 'Design a new website', person: 'Leo', due: '1st Jan 2022', status: 'ongoing'},
        {title: 'Code up the homepage', person: 'Peter Parker', due: '1st Jun 2021', status: 'complete'},
        {title: 'Design video thumbnails', person: 'Bruce Wayne', due: '1st Jul 2021', status: 'overdue'},
        {title: 'Create forum', person: 'Goku', due: '1st Oct 2021', status: 'ongoing'}
      ],
      colors: {
        complete: 'cyan',
        ongoing: 'orange',
        overdue: 'deep-orange'
      }}
    },
    methods: {
      sortBy(prop){
        this.projects.sort((a, b) => a[prop] < b[prop] ? -1 : 1)
      }
    },
  }
</script>

<style>

/* Fix chip size on small screens */
.v-chip:not(.v-chip--active) {
  max-width: min-content;
}

.project.complete {
  border-left: 4px solid #00BCD4;
}

.project.ongoing {
  border-left: 4px solid #FF9800;
}

.project.overdue {
  border-left: 4px solid #FF5722;
}


</style>
