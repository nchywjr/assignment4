<template>
  <div>
    <v-row>
      <v-col>
        <v-btn @click="fetchUsers">Fetch</v-btn>
      </v-col>
    </v-row>
        <v-row>
            <v-col>
                <v-data-table 
                :headers="headers"
                :items="users"
                :items-per-page="10"
                :loading="loading"
                >
                </v-data-table>
            </v-col>
        </v-row>
        <v-row></v-row>
  </div>
</template>
<script>
import axios from 'axios'

const uri = "https://api.coingecko.com/api/v3/coins/list"

export default {
    data(){
        return {
            headers:[
                {
                    text: 'ID',
                    value: 'id'
                },
                {
                    text: 'Symbol',
                    value: 'symbol'
                },
                {
                    text: 'Name',
                    value: 'name'
                },
            ],

            users: []
        }
    }, methods: {
        async fetchUsers(){
                const res = await axios.get(uri)
                this.users = res.data
                this.loading = true;     
        }
    }, 
}
</script>
