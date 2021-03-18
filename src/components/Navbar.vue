<template>
  <nav>
      <div>
          <p>Display name</p>
          <p class="email">Display email</p>
      </div>
      <button @click="handleClick">Logout</button>
  </nav>
</template>

<script>
import useLogout from '../composables/useLogout'

export default {
    setup(){
        const { logout, error } = useLogout();

        const handleClick = async () => {
            await logout();
            if(!error.value){
                console.log("User Logged Out")
            }
        }

        return { handleClick}
    }
}
</script>

<style>
 nav{
     padding: 20px;
     display: flex;
     justify-content: space-between;
     align-items: center;
     border-bottom: 1px solid #eee;
 }
 nav p{
     margin: 2px auto;
     font-size: 16px;
     color: #444;
 }
 nav p.email{
     font-size: 14px;
     color: #999;
 }
</style>