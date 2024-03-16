
  <template>
    <nav>
      <v-navigation-drawer class="navig" v-model="drawer">
        <v-list-item
          prepend-avatar="https://randomuser.me/api/portraits/men/85.jpg"
          title=""
          subtitle="Admin"
          nav
        >
          <template v-slot:append>
            <v-btn
              variant="text"
              icon="mdi-chevron-left"
              @click.stop="drawer = !drawer"
            ></v-btn>
          </template>
        </v-list-item>
  
        <v-divider></v-divider>
  
        <v-list density="compact" nav>
          <v-list-group value="Profile">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-view-dashboard"
                title="Visit Profile"
                value="Profile"
                class="mt-5 navitems"
              ></v-list-item> <!-- ekkeda title a mana side bar lo main item name-->
            </template>
  
            <v-list-item to="/" value="" title=" "></v-list-item> <!--- to lo path paste chyi ah page ki elali aneydhi-->
            <!-- Add more subitems here -->
          </v-list-group>

          <v-list-group value="Member">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-view-dashboard"
                title="Member"
                value="Member"
                class="mt-5 navitems"
              ></v-list-item> <!-- ekkeda title a mana side bar lo main item name-->
            </template>
  
            <v-list-item to="/"  title="New Registration"></v-list-item> <!--- to lo path paste chyi ah page ki elali aneydhi-->
            <!-- Add more subitems here -->
          </v-list-group>
  
          <v-list-group value="Income">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-account-multiple"
                title="Income"
                value="Income"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/" title="Team Income"></v-list-item>
            <!-- Add more subitems here -->
          </v-list-group>
  
          <v-list-group value="Fund Request">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-calendar-month"
                title="Fund Request"
                value="Fund Request"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/"  title="New Request"></v-list-item>
            <v-list-item to="/" title="View Statements"></v-list-item>
            <!-- Add more subitems here -->
          </v-list-group>
  
          <v-list-group value="Top Up">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-credit-card"
                title="Top Up"
                value="Top Up"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/"  title="Top UP Member"></v-list-item>
            <v-list-item to="/" title="Top UP History"></v-list-item>
            <!-- Add more subitems here -->
          </v-list-group>
  
          <v-list-group value="P2P Transfer">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-view-dashboard"
                title="P2P Transfer"
                value="P2P Transfer"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/"  title="Transfer Fund"></v-list-item>
            <v-list-item to="/"  title="View Transfers"></v-list-item>
            <!-- Add more subitems here -->
          </v-list-group>
  
          <v-list-group value="Wallet to Fund">
            <template v-slot:activator="{ props }">
            
                <v-list-item
                  v-bind="props"
                  prepend-icon="mdi-account-plus"
                  title="Wallet to Fund"
                  value="Wallet to Fund"
                  class="mt-5 navitems"
                ></v-list-item>
             
            </template>
  
            <v-list-item to="/"  title="Transfer Money"></v-list-item>
            <v-list-item to="/"  title="Transaction History"></v-list-item>
            
          </v-list-group>
  
          <v-list-group value="My Team">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-credit-card"
                title="My Team"
                value="My Team"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/"  title="Grid View"></v-list-item>
           
          </v-list-group>
  
          <v-list-group value="Withdrawl">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-home-city"
                title="Withdrawl"
                value="Withdrawl"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/" title="New Withdraw"></v-list-item>
            <v-list-item to="/" title="Withdrawls History"></v-list-item>
          
          </v-list-group>
  
          <v-list-group value="Support">
            <template v-slot:activator="{ props }">
              <v-list-item
                v-bind="props"
                prepend-icon="mdi-minus-circle"
                title="Support"
                value="Support"
                class="mt-5 navitems"
              ></v-list-item>
            </template>
  
            <v-list-item to="/" value="" title="New Request"></v-list-item>
            <v-list-item to="/" value="" title="View History"></v-list-item>
         
          </v-list-group>
          <v-list-item
          prepend-icon="mdi-logout"
          title="Sign Out"
          value="signOut"
          class="mt-5 navitems"
          @click="signOut"
        ></v-list-item>
        </v-list>
      </v-navigation-drawer>
  
      <v-toolbar class="navig">
        <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title></v-toolbar-title>
        <v-spacer></v-spacer>
      </v-toolbar>
      <v-main></v-main>
    </nav>
  </template>
  
  <script>
  export default {
    name: "SideBar",
    data() {
      return {
        showNotifications: false,
        dnd: false,
        leadrequests: [],
        count: "0",
        drawer: true,
        items: [
          { title: "Home", icon: "mdi-home-city" },
          { title: "My Account", icon: "mdi-account" },
          { title: "Users", icon: "mdi-account-group-outline" },
        ],
      };
    },
  };
  </script>
  
  <style>
  .navig {
    /* background: #976d89; */
    background: rgb(27, 165, 70);
    color: white;
    /* background-color: #2e1764; */
  }
  .logo-img {
    width: 55px;
    height: 55px;
    border-radius: 50px;
  }
  .menuicon {
    color: black;
  }
  .navigation {
    background-color: #250361;
  }
  .navi {
    color: white;
  }

  
  .list-item-custom .v-icon {
    color: #3f51b5;
  }
  .not {
    z-index: 3;
  }
  .noti {
    height: 5rem;
    width: 20rem;
  }
  </style>