<template>
  <div>
    <v-container>
      <v-row>
        <!-- User Card -->
        <v-col cols="12">
          <v-card class="user-card">
            <v-row class="items-center">
              <v-col cols="2">
                <!-- User Icon -->
                <v-icon color="primary">mdi-account-circle</v-icon>
              </v-col>
              <v-col cols="10">
                <!-- User ID and Name -->
                <div class="user-info">
                  <div class="user-id">User ID: {{ userId }}</div>
                  <div class="user-name">User Name: {{ userName }}</div>
                </div>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
        
        <!-- Cards -->
        <v-col v-for="(card, index) in cards" :key="index" cols="12" sm="6" md="4" lg="4">
          <v-card class="cards">
            <v-row class="items-center">
              <v-col cols="4">
                <!-- Image on the left -->
                <img :src="card.imageSrc" alt="Card Image">
              </v-col>
              <v-col cols="8" class="text-right">
                <!-- Heading and count on the right -->
                <div class="content">
                  <!-- Use dot notation to access userDetails properties -->
                  <div class="headline">{{ card.heading }}</div>
                  <div class="count">Count: {{ userDetails[Object.keys(userDetails)[index]] }}</div>
                </div>
              </v-col>
            </v-row>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'MyComponent',
  data() {
    return {
      userDetails:[],
      userId: 'EE32474625',
      // EE32474625
      // EE58988463
   
      userName: 'John Doe', 
      cards: [
        { heading: 'My Total Team',  imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
        { heading: 'Carrry Forward',   imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
        { heading: 'My Total Income',   imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
       
        { heading: 'Available Wallet',  imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
        { heading: 'Bank Withdrawls',  imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
        { heading: 'Available Funds',  imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
       
        { heading: 'Silver Bonus',  imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
        { heading: 'Gold Bonus',  imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
        { heading: 'Diamond Bonus',   imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },
      
        { heading: 'Royality',   imageSrc: 'https://tse1.mm.bing.net/th?id=OIP.Yo_q-DsKk-TOGwhZ1UD8mgHaHa&pid=Api&P=0&h=220' },

      ]
    }
  },
  created() {
    // Fetch user details when the component is created
    this.fetchUserDetails();
  },
  methods: {
    async fetchUserDetails() {
      try {
        // Make GET request to the API endpoint
        const response = await axios.get(`http://localhost:3000/fund/user_details/${this.userId}`);
        // Set the userDetails data to the response data
       
        const extractedData = {
          totalTeam: response.data.teamCount,
          carryForward: response.data.parent,
          totalIncome: response.data.totalIncome,
          availableWallet: response.data.WalletIncome,
          bankWithdrawl: response.data.bankWithdrawl,
          availableFunds: response.data.fund,
          silverBonus: response.data.silverBonus,
          goldBonus: response.data.goldBonus,
          diamondBonus: response.data.diamondBonus,
          royalty: response.data.royality
        };
        // Assigning the extracted data to userDetails
        this.userDetails = extractedData;
        console.log(this.userDetails)
      } catch (error) {
        console.error('Error fetching user details:', error);
      }
    }
  }
}
</script>

<style scoped>
.user-card {
  margin-bottom: 20px;
  /* Add any additional card styling here */
}

.cards {
  margin-bottom: 20px;
  /* Add any additional card styling here */
}

.headline {
  font-size: 18px;
  font-weight: bold;
  /* Add any additional heading styling here */
}

.count {
  font-size: 14px;
  /* Add any additional count styling here */
}

img {
  height: 100px;
  width: 100px;
}

.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.user-info {
  padding: 10px;
}

.user-id, .user-name {
  font-weight: bold;
  margin-bottom: 5px;
}
</style>
