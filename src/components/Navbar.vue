<template>
    <header>
    <nav>
        <router-link to="/home"><div class="menu-item">Home</div></router-link>
        <router-link to="/employee"><div class="menu-item">Employee</div></router-link>
        <router-link to="/favorite"><div class="menu-item">Favorite Employee</div></router-link>
        <router-link to="/data"><div class="menu-item">Data</div></router-link>
        
    </nav>
    </header>
</template>

<script>
export default {
    name: 'navbar'
}
</script>

<style>
    nav{
        display: flex;
        align-items: center;
        justify-content: center;
    }
    nav .menu-item{
        color: #fff;
        padding: 10px 20px;
        position: relative;
        text-align: center;
        border-bottom: 3px solid transparent;
        display: flex;
        transition: 0.4s;
    }

    nav .menu-item:active,
    nav .menu-item:hover{
        background-color: #444;
        border-bottom-color: #ff5858;
    }
    nav .menu-item a{
        color: inherit;
        text-decoration: none;  
    }

    *{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: 'montserrat', sans-serif;
}

header{
  width: 100vw;
  background-color: #222;
  padding: 15px;
}
</style>