<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated >
      <q-toolbar class="glossy">

      <div class="q-gutter-y-md column" > 
      <q-input filled bottom-slots v-model="text" label="Search board"  color="pink" style="max-width: 600px">         
        <template v-slot:prepend>           
          <q-icon name="search" />         
        </template>         
        <template v-slot:append>           
          <q-icon name="close" @click="text = ''" class="cursor-pointer" />         
          </template>
      </q-input>
     </div>
     
     <q-space/>

      <div class="q-gutter-sm row items-center no-wrap ">
         
          <q-btn round dense flat color="white" icon="notifications">
            <q-badge color="red" text-color="white" floating>
              5
            </q-badge>
            <q-menu
            >
              <q-list style="min-width: 100px">
                <messages></messages>
                <q-card class="text-center no-shadow no-border">
                  <q-btn label="View All" style="max-width: 120px !important;" flat dense
                         class="text-indigo-8"></q-btn>
                </q-card>
              </q-list>
            </q-menu>

          </q-btn>
          <q-btn round flat>
            <q-avatar size="26px">
              <img src="https://cdn.quasar.dev/img/boy-avatar.png">
            </q-avatar>
          </q-btn>
        </div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-primary text-white"
    >
      <q-list>
         <q-item to="/" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="menu"/>
          </q-item-section>
          <q-item-section>
            <q-item-label><strong>SWARNET</strong></q-item-label>
          </q-item-section>
        </q-item>

        <q-separator color="orange" inset />

        <q-item to="/" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="fas fa-home"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Post Board</q-item-label>
          </q-item-section>
        </q-item>

        <q-expansion-item 
          icon="fas fa-hand-holding-medical"
          label="Request Emergency Assistance">

        <q-list class="q-pl-lg">  
        <q-item to="/Dashboard2" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="local_police"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Police</q-item-label>
          </q-item-section>
        </q-item>

        <q-item to="/Dashboard2" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="local_fire_department"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Fire</q-item-label>
          </q-item-section>
        </q-item>

        <q-item to="/Dashboard2" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="fas fa-ambulance"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Ambulance</q-item-label>
          </q-item-section>
        </q-item>

        <q-item to="/Dashboard2" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="emergency"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>ODPM</q-item-label>
          </q-item-section>
        </q-item>
        </q-list>
        </q-expansion-item>

        <q-expansion-item
          icon="fas fa-donate"
          label="Request Donations"
        >
          <q-list class="q-pl-lg">
            <q-item to="/Login-1" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="fastfood"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Food Items</q-item-label>
              </q-item-section>
            </q-item>
            <q-item to="/Lock" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="attach_money"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Money</q-item-label>
              </q-item-section>
            </q-item>
            <q-item to="/Lock-2" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="kitchen"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Household Appliances</q-item-label>
              </q-item-section>
            </q-item>
            <q-item to="/Pricing" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="construction"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Construction Materials</q-item-label>
              </q-item-section>
            </q-item>
            
          </q-list>
        </q-expansion-item>

        <q-expansion-item
          icon="fas fa-hand-holding-usd"
          label="Make A Contribution"
        >
         <q-list class="q-pl-lg">
            <q-item to="/Login-1" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="fastfood"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Food Items</q-item-label>
              </q-item-section>
            </q-item>
            <q-item to="/Lock" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="attach_money"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Money</q-item-label>
              </q-item-section>
            </q-item>
            <q-item to="/Lock-2" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="kitchen"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Household Appliances</q-item-label>
              </q-item-section>
            </q-item>
            <q-item to="/Pricing" active-class="q-item-no-link-highlighting">
              <q-item-section avatar>
                <q-icon name="construction"/>
              </q-item-section>
              <q-item-section>
                <q-item-label>Construction Materials</q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-expansion-item>

        <q-item to="/Mail" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="fas fa-check-square"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Subscriptions</q-item-label>
          </q-item-section>
        </q-item>

        <q-item to="/directory" active-class="q-item-no-link-highlighting">
          <q-item-section avatar>
            <q-icon name="fas fa-binoculars"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Find Users</q-item-label>
          </q-item-section>
        </q-item>

       
      </q-list>
    </q-drawer>

    <q-page-container class="bg-grey-2">
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'
import Messages from "./Messages";

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink,
    Messages
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
