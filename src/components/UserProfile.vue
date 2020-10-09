<template>
  <div class="user-profile">
    <div class="user-profile__sidebar">
      <div class="user-profile__user-panel">
        <h1 class="user-profile__username">@{{ state.user.username }}</h1>
        <div class="user-profile__admin-badge" v-if="state.user.isAdmin">Admin</div>
        <div class="user-profile__follower-count">
          <strong>Followers: </strong> {{ state.followers }}
        </div>
      </div>
      <CreateTwootPanel @add-twoot="addTwoot"/>
    </div>

    <div class="user-profile__twoots-wrapper">
      <TwootItem
        v-for="twoot in state.user.twoots"
        :key="twoot.id"
        :twoot="twoot"
        :username="state.user.username"
      />
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue'
import TwootItem from "./TwootItem";
import CreateTwootPanel from "./CreateTwootPanel";

export default {
  name: "UserProfile",
  components: {
    TwootItem,
    CreateTwootPanel,
  },
  setup(){
      const state = reactive({
          followers: 0,
            user: {
                id: 1,
                username: "_KerryMyles",
                firstName: "Shun",
                lastName: "Myles",
                email: "kmyles82@gmail.com",
                isAdmin: true,
                twoots: [
                { id: 1, content: "Twooter is Amazing" },
                {
                    id: 2,
                    content: "Don't forget to subscripe to the Earth is square",
                },
                ],
            },
      })

    function addTwoot(twoot){
        state.user.twoots.unshift({id: state.user.twoots.length + 1, content: twoot})
    }

      return{   
        state,
        addTwoot
      }
  },
//   data() {
//     return {
//       followers: 0,
//       user: {
//         id: 1,
//         username: "_KerryMyles",
//         firstName: "Shun",
//         lastName: "Myles",
//         email: "kmyles82@gmail.com",
//         isAdmin: true,
//         twoots: [
//           { id: 1, content: "Twooter is Amazing" },
//           {
//             id: 2,
//             content: "Don't forget to subscripe to the Earth is square",
//           },
//         ],
//       },
//     };
//   },
//   watch: {
//     followers(newFollowerCount, oldFollowerCount) {
//       if (oldFollowerCount < newFollowerCount) {
//         console.log(`${this.user.username} has gained a follower`);
//       }
//     },
//   },
//   computed: {
    
//   },
//   methods: {
//     followUser() {
//       this.followers++;
//     },
//     addTwoot(twoot){
//         this.user.twoots.unshift({id: this.user.twoots.length + 1, content: twoot})
//     }
//   },
//   mounted() {
//     this.followUser();
//   },
//   created() {},
};
</script>

<style scoped lang="scss">
.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-gap: 50px;
  padding: 50px 5%;
  .user-profile__user-panel {
    display: flex;
    flex-direction: column;
    padding: 20px;
    background-color: white;
    border-radius: 5px;
    border: 1px solid #dfe3e8;
    margin-bottom: auto;
    h1 {
      margin: 0;
    }
    .user-profile__admin-badge {
      background: rebeccapurple;
      color: white;
      border-radius: 5px;
      margin-right: auto;
      padding: 0 10px;
      font-weight: bold;
    }
  }
  .user-profile__twoots-wrapper {
    display: grid;
    grid-gap: 10px;
    margin-bottom: auto;
  }
}
</style>
