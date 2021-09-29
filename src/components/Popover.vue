<template>
  <div class="w-full max-w-sm px-4">
    <Popover v-slot="{ open }" class="relative">
      <PopoverButton
        :class="open ? '' : 'text-opacity-90'"
        class="
          inline-flex
          items-center
          px-3
          py-2
          text-base
          font-medium
          text-white
          bg-blue-700
          rounded-md
          group
          hover:text-opacity-100
          focus:outline-none
          focus-visible:ring-2
          focus-visible:ring-white
          focus-visible:ring-opacity-75
        "
      >
        <span>{{ note }}</span>
        <ChevronDownIcon
          :class="open ? '' : 'text-opacity-70'"
          class="
            w-5
            h-5
            ml-2
            text-orange-300
            transition
            duration-150
            ease-in-out
            group-hover:text-opacity-80
          "
          aria-hidden="true"
        />
      </PopoverButton>

      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="translate-y-1 opacity-0"
        enter-to-class="translate-y-0 opacity-100"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="translate-y-0 opacity-100"
        leave-to-class="translate-y-1 opacity-0"
      >
        <PopoverPanel
          class="
            absolute
            z-10
            w-screen
            max-w-sm
            px-4
            mt-3
            transform
            -translate-x-1/2
            left-1/2
            sm:px-0
            lg:max-w-3xl
          "
        >
          <div
            class="
              overflow-hidden
              rounded-lg
              shadow-lg
              ring-1 ring-black ring-opacity-5
            "
          >
            <div class="relative grid gap-8 bg-white p-7 lg:grid-cols-2">
              <a
                v-for="item in solutions"
                :key="item.name"
                :href="item.href"
                class="
                  flex
                  items-center
                  p-2
                  -m-3
                  transition
                  duration-150
                  ease-in-out
                  rounded-lg
                  hover:bg-gray-50
                  focus:outline-none
                  focus-visible:ring
                  focus-visible:ring-orange-500
                  focus-visible:ring-opacity-50
                "
              >
                <div
                  class="
                    flex
                    items-center
                    justify-center
                    flex-shrink-0
                    w-10
                    h-10
                    text-white
                    sm:h-12
                    sm:w-12
                  "
                >
                  <div v-html="item.icon"></div>
                </div>
                <div class="ml-4">
                  <p class="text-sm font-medium text-gray-900">
                    {{ item.name }}
                  </p>
                  <p class="text-sm text-gray-500">
                    {{ item.description }}
                  </p>
                </div>
              </a>
            </div>
            <!-- <div class="p-4 bg-gray-50">
              <a
                href="##"
                class="flow-root px-2 py-2 transition duration-150 ease-in-out rounded-md hover:bg-gray-100 focus:outline-none focus-visible:ring focus-visible:ring-orange-500 focus-visible:ring-opacity-50"
              >
                <span class="flex items-center">
                  <span class="text-sm font-medium text-gray-900">
                    Documentation
                  </span>
                </span>
                <span class="block text-sm text-gray-500">
                  Start integrating products and tools
                </span>
              </a>
            </div> -->
          </div>
        </PopoverPanel>
      </transition>
    </Popover>
  </div>
</template>

<script>
import { Popover, PopoverButton, PopoverPanel } from "@headlessui/vue";
import { ChevronDownIcon } from "@heroicons/vue/solid";

export default {
  components: { Popover, PopoverButton, PopoverPanel, ChevronDownIcon },
  props: { solutions: Array, note: String },
  methods: {
    isopen: function (data) {
      this.$emit("isOpen", data);
    },
  },
};
</script>