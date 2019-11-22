<template>
  <div id="sidemenu">
    <b-menu>
      <b-menu-list label="">
        <b-menu-item label="My Stash"></b-menu-item>
        <b-menu-item label="Add New Tea"></b-menu-item>
      </b-menu-list>
      <b-menu-list label="Account">
        <b-menu-item label="My Account"></b-menu-item>
        <b-menu-item label="Log Out"></b-menu-item>
      </b-menu-list>
    </b-menu>
  </div>
</template>
<script>
export default {
    name: "SideMenu"
}
</script>
<style lang="scss" scoped>
    #sidemenu {
        margin-left: 1rem;
        margin-top: 2rem;
        width: 10rem;
    }
</style>