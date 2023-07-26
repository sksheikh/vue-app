<template>
    <div class="container">
        <h2 class="text-center mt-4">Dashboard Page</h2>
        <button type="submit" class="btn btn-dark" @click="logout">Logout</button>
    </div>
</template>

<script>
import {useRouter} from 'vue-router'
export default {

    setup(){
        const router = useRouter();
        function logout() {
            localStorage.removeItem('token');
            router.push({ name : 'Home'});
        }

        return{
            logout
        }
    }
}
</script>
