<template>
  <div id="app">
    <header id="header">
      <h1>Wazak's Pointless Button</h1>
      <nav>
        <router-link to="/leaderboard"><i class="fas fa-trophy"></i></router-link>        
        <router-link to= "/"><i class = "fas fa-stop"></i></router-link>
        <router-link to="/dashboard"><i class="fas fa-user"></i></router-link>
      </nav>
    </header>
    <router-view />
  </div>
</template>


<style>
/* Color scheme: https://paletton.com/#uid=7040u0knHs+edG7jrvYscpiuCk2 */
/* red: #e74c3c
 * blue: #277E8E
 */
body {
  font-family: 'Work Sans', sans-serif;
  font-weight: 300;
  font-size: 13pt;
  margin: 0px 200px;
}

#header {
  /* Semi-circle */
  margin: 0 1em 1em 0;
  height: 100px;
  width: 400px;

  /* Fixed position */
  position: fixed;
  z-index: 10000;
  left: 50%;
  transform: translate(-50%, 0);
  /* Color and alignment */
  background: black;
  text-align: center;
  box-shadow: 0 0 0 1em #FFF;
}

nav {
  display: flex;
  justify-content: center;
}

h1 {
  color: #fff;
  font-size: 18px;
}

h2 {
  font-size: 12px;
}

#header .fas {
  font-size: 25px;
  color: #fff;
  width: 50px;
}

.pure-button-primary {
  background-color: #277E8E;
}

.button {
  align-content: right;
  text-align: center;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

.center {
  width: 500px;
  height: 250px;
  margin-top: 150px;
}

.smallCenter {
  width: 200px;
  height: 50px;
  margin-top: 30px;
}

.help {
  align-content: right;
  text-align: center;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

#black {
  padding-top: 300px;
  color: black;
  justify-content: center;

}
</style>

