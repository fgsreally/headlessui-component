<template>
  <Menu class='h-40 w-40 bg-gradient-to-r from-yellow-400 via-red-500 to-pink-500'>
    <MenuButton>More</MenuButton>
    <MenuItems>
      <MenuItem v-slot="{ active }">
        <a :class='{ "bg-blue-500": active }' href="/account-settings">
          Account settings
        </a>
      </MenuItem>
      <MenuItem v-slot="{ active }">
        <a :class='{ "bg-blue-500": active }' href="/account-settings">
          Documentation
        </a>
      </MenuItem>
      <MenuItem disabled>
        <span class="opacity-75">Invite a friend (coming soon!)</span>
      </MenuItem>
    </MenuItems>
  </Menu>
</template>


<script>
  import { Menu, MenuButton, MenuItems, MenuItem } from "@headlessui/vue";

  export default {
      name:'Menu1',
    components: {
      Menu,
      MenuButton,
      MenuItems,
      MenuItem,
    },
  };
</script>


<style scoped >

</style>