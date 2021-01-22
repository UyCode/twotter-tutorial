<template>
    <div class="user-profile">
        <div class="user-profile_user-panel">
            <h1 class="user-profile_username">@{{user.username}}</h1>
            <div class="user-profile-admin-badge" v-if="user.isAdmin">Admin</div>
            <div class="user-profile_follower-count">
                <strong> followers: </strong> {{ followers }}
            </div>
        </div>
    </div>
    
</template>

<script>
    export default {
        name: "UserProfile",
        data(){
            return {
                followers: 0,
                user:{
                    id: 1,
                    username: 'Binezir',
                    firstName: 'ahmatjan',
                    lastName: 'rawutjan',
                    email: 'Hyper-Hack@outlook.com',
                    isAdmin: true
                }
            }
        },
        computed:{
            fullName() {
                return `${this.user.firstName } ${this.user.lastName}`
            }
        },
        methods: {
            followUser() {
                this.followers++;
            }
        },
        mounted() {
            this.followUser();
        },
        watch:{
            followers(newFollowers, oldFollowers){
                if(oldFollowers < newFollowers){
                    console.log(`${this.user.username} gained a follower`)
                }
            }
        }

    }
</script>

<style scoped>
.user-profile{
    display: grid;
    grid-template-columns: 1fr 3fr;
    width: 100%;
    padding: 50px 5%;
}

    .user-profile_user-panel{
        display: flex;
        flex-direction: column;
        margin-right: 50px;
        padding-right: 20px;
        background-color: #ffffff;
        border-radius: 5px;
        border: 1px solid #DFE3E8;
    }

    h1{
        margin: 0;
        font-weight: lighter;
    }

    .user-profile-admin-badge{
        background: #82219c;
        color: white;
        border-radius: 5px;
        margin-right: auto;
        padding: 0 10px;
        font-weight: bold;
    }


</style>