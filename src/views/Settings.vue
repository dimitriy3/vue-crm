<template>
   <form class="settings-grid">
      <div><p>{{'Dark_Theme'|localize}}</p>
         <div class="btn waves-effect waves-light" onclick="changeTheme()">
            <i class="material-icons">refresh</i>
         </div>
      </div>

      <div><p>{{'Color_Navbar'|localize}}</p>
         <div class="btn waves-effect waves-light" onclick="changeColorNavbar()">
            <i class="material-icons">refresh</i>
         </div>
      </div>

      <div><p>{{'Shadow_Navbar'|localize}}</p>
         <div class="btn waves-effect waves-light" onclick="changeShadowNavbar()">
            <i class="material-icons">refresh</i>
         </div>
      </div>

      <div><p>{{'Color_Dockbar'|localize}}</p>
         <div class="btn waves-effect waves-light" onclick="changeColorDockbar()">
            <i class="material-icons">refresh</i>
         </div>
      </div>

      <div><p>{{'Color_Active_Dockbar'|localize}}</p>
         <div class="btn disabled waves-effect waves-light" onclick="changeColorActiveDockbar()">
            <i class="material-icons">refresh</i>
         </div>
      </div>
      <small>Ведётся разработка этой страницы</small>
   </form>
   <!-- {{'Dark_Light'|localize}} -->
</template>

<script>
export default {
  metaInfo() {
    return {
      title: this.$title('Menu_Settings')
    }
  },
  name: 'settings'
}
</script>
