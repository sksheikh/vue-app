<template>
    <div class="container">
        <div class="row justify-content-center align-items-center g-2">
            <div class="col-md-6 mt-4">
                <h2>Register</h2>
                <form @submit.prevent="register">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input
                            type="name"
                            class="form-control"
                            id="name"
                            v-model="form.name"
                        />
                        <p class="text-danger" v-for="error in errors.name" :key="error">
                            {{ error}}
                        </p>
                    </div>
                    <div class="form-group">
                        <label for="email">Email address</label>
                        <input
                            type="email"
                            class="form-control"
                            id="email"
                            v-model="form.email"
                        />
                        <p class="text-danger" v-for="error in errors.email" :key="error">
                            {{ error}}
                        </p>
                    </div>
                    <div class="form-group">
                        <label for="password">Password</label>
                        <input
                            type="password"
                            class="form-control"
                            id="password"
                            v-model="form.password"
                        />
                        <p class="text-danger" v-for="error in errors.password" :key="error">
                            {{ error}}
                        </p>
                    </div>
                    <div class="form-group">
                        <label for="confirm_password">Confirm Password</label>
                        <input
                            type="confirm_password"
                            class="form-control"
                            id="confirm_password"
                            v-model="form.confirm_password"
                        />
                        <p class="text-danger" v-for="error in errors.confirm_password" :key="error">
                            {{ error}}
                        </p>
                    </div>

                    <button type="submit" class="btn btn-primary">
                        Register
                    </button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import {reactive,ref} from 'vue'
import {useRouter} from 'vue-router'
export default {
    setup() {
        const router = useRouter();
        let form = reactive({
            name : '',
            email : '',
            password: '',
            confirm_password: ''
        });

        let errors = ref([])

        const register = async() =>{
            await axios.post('/api/register',form).then(res=>{
                if(res.data.success){
                    localStorage.setItem('token',res.data.data.token)
                    router.push({name: 'Dashboard'})
                }
            }).catch(e =>{
                errors.value = e.response.data.message
            });
        }
        return{
            form,
            register,
            errors
        }
    }
}
</script>
