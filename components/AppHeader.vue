<template>
    <header>
        
        <ul>
            <h1>Student Details</h1>
            <li>
                <nuxt-link to='/'>Home</nuxt-link>
            </li>
            <li>
                  <nuxt-link to='/about'>About</nuxt-link>
            </li>
             <li>
                  <nuxt-link to='/student'>Student</nuxt-link>
            </li>
            <li>
                  <nuxt-link to='/studentList/studentView'>Student List</nuxt-link>
            </li>
        </ul>
    </header>
</template>
<script>
export default {
    name:"AppHeader"
}
</script>
<style>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #333;
  color: aliceblue;
}

li {
  float: left;
}

li a {
  display: block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #111;
}
</style>