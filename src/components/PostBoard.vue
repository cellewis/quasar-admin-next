<template>
  <div class="q-pa-md" >
    <div class="q-gutter-md row items-start">
      <q-select
        color="pink"
        filled
        v-model="model"
        :options="options"
        label="Select a topic: "
        style="width: 250px"
      />

      <q-btn flat round color="primary" icon="fas fa-filter" @click="getPost" />
      <q-btn flat round color="primary" icon="fas fa-sync-alt" />
    </div>
    </div>

    <q-page-sticky position="bottom-right" :offset="[2, 80]">
      <q-toggle
        v-model="subbed"
        checked-icon="check"
        color="red"
        unchecked-icon="clear"
         @click="showNotif"
      />
      
    </q-page-sticky>

    <q-page-sticky position="bottom-right" :offset="[5, 18]">
      <q-btn fab icon="far fa-edit" color="accent" @click="fixed = true"/>
    </q-page-sticky>

    <q-dialog v-model="fixed">
      <q-card style="width: 600px; height: 400px; background-color: powderblue;">
        <q-card-section>
          <div class="text-h6">NEW DISCUSSION</div>
        </q-card-section>
        
        <q-card-section>
        <q-input filled  v-model="ph" placeholder="Enter Title of Post"  />
        </q-card-section>
      
        <q-separator />

        
        <q-card-section style="height: 200px" class="scroll" counter maxlength="260">
          <q-input type="textarea" v-model="text" counter maxlength="260"  autogrow>
          </q-input>
        </q-card-section>

        <q-separator />

        <q-card-actions align="right">
          <q-btn flat label="Discard" color="primary" v-close-popup />
          <q-btn flat label="Post" color="primary" v-close-popup @click="triggerPositive"/>
        </q-card-actions>
      </q-card>
    </q-dialog>

    

</template>

<script>
import {defineComponent, defineAsyncComponent, ref} from 'vue';
import {axios} from 'axios';
import { useQuasar } from 'quasar'

export default defineComponent({
  name: 'PostBoard',

  methods:{

    async getPost(){
        const url = "https://swarmnet-staging.herokuapp.com/topics"

        try{
            let response = fetch(url);
            let result = await response.json();
            console.log(result);

        }
        catch(e){
              console.log(e);//catch and log any errors
        }
        
        
    }

  },

  setup () {
    const $q = useQuasar()

    return {
        model: ref(null),

        subbed: ref(true),

        fixed: ref(false),

        text: ref(''),

        ph: ref(''),

        dense: ref(false),
    
        options: [
        {
          label: 'Flooding',
        },
        {
          label: 'Hurricanes',
        },
        {
          label: 'Landslides',
        },
        {
          label: 'Fires',
        },
        {
          label: 'Earthquake',
        },
        {
          label: 'Tropical Storms',
        },
        {
          label: 'Precipitation',
        },
        {
          label: 'Tropical Storms',
        },
        {
          label: 'Volcanic Eruptions',
        },
        {
          label: 'Land Erosion',
        },
        {
          label: 'Drought',
        },
        {
          label: 'Cyclones',
        }
      ],

       showNotif () {
        $q.notify({
          message: 'SUBSCRIBBED',
          color: 'primary',
          avatar: 'https://cdn.quasar.dev/img/boy-avatar.png',
          actions: [
            { label: 'Dismiss', color: 'white', handler: () => { /* ... */ } }
          ]
        })
       },

      triggerPositive () {
        $q.notify({
          type: 'positive',
          message: 'DISCUSSION POSTED'
        })

        // simulate delay
        setTimeout(() => {
          notif({
            type: 'positive',
            message: 'Found the results that you were looking for',
            timeout: 1000
          })
        }, 4000)
      }
      

    }
  }

})
</script>