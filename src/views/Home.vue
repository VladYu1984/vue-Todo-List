<template>
    <div class="mainInfo">
        <h2>Home page</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Facilis commodi dolorem nostrum modi magnam iste officiis magni asperiores quo laborum vero omnis, alias libero molestiae porro. Placeat a sint eius!</p>
        <router-link to="/todos" class="routerLink">Todos</router-link>
    </div>
    <hr>
</template>

<style>
.mainInfo {
    width: 85%;
    background-color: rgb(239, 250, 28);
    margin: auto;
    margin-top: 25px;
    border: 2.5px solid rgb(49, 163, 102);
    text-decoration: none;
}

.routerLink {
    font-size: 20px;
    text-decoration: none;
}
</style>