<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
            <router-link class="navbar-brand" :to="{ name : 'Home'}">Logo</router-link>

            <ul class="navbar-nav ml-auto">
                <li class="nav-item active">
                    <router-link class="nav-link" :to="{ name : 'Home' }"> Home </router-link>
                </li>
                <li class="nav-item">
                    <router-link class="nav-link" :to="{ name : 'Login'}"> Login </router-link>
                </li>
                <li class="nav-item">
                    <router-link class="nav-link" :to="{ name : 'Register'}"> Register </router-link>
                </li>
                <li class="nav-item">
                    <router-link class="nav-link" :to="{ name : 'Dashboard'}"> Dashboard </router-link>
                </li>
            </ul>
        </nav>


        <router-view></router-view>
    </div>
</template>
