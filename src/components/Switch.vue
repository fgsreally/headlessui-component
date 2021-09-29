<template>
  <Switch
    v-model="enabled"
    :class="enabled ? 'bg-indigo-900' : 'bg-indigo-700'"
    class="relative inline-flex items-center h-6 rounded-full w-28"
    @click='isopen(enabled)'
  >
    <span class="sr-only">Enable notifications</span>
    <span
      :class="enabled ? 'translate-x-6' : 'translate-x-1'"
      class="inline-block w-4 h-4 transform bg-white rounded-full"
    />
  </Switch>
</template>

<script>
  import { ref } from 'vue'
  import { Switch } from '@headlessui/vue'

  export default {
    components: { Switch },
methods:{
    isopen:function(data){
        this.$emit('isOpen',data);
    }
},
    setup() {
      const enabled = ref(false)

      return { enabled }
    },
  }
</script>