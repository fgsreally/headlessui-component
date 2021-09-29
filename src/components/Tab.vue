<template>
  <div class="w-full max-w-md px-2 py-16 sm:px-0">
    <TabGroup>
      <TabList class="flex p-1 space-x-1 bg-blue-900/20 rounded-xl">
        <Tab
          v-for="category in Object.keys(categories)"
          as="template"
          :key="category"
          v-slot="{ selected }"
        >
          <button
            @click="change(category)"
            :class="[
              'w-full py-2.5 text-sm leading-5 font-medium text-blue-700 rounded-lg',
              'focus:outline-none focus:ring-2 ring-offset-2 ring-offset-blue-400 ring-white ring-opacity-60',
              selected
                ? 'bg-white shadow'
                : 'text-blue-100 hover:bg-white/[0.12] hover:text-blue-200',
            ]"
          >
            {{ category }}
          </button>
        </Tab>
      </TabList>

      <TabPanels class="mt-2">
        <TabPanel
          v-for="(posts, idx) in Object.values(categories)"
          :key="idx"
          :class="[
            'bg-white rounded-xl p-3',
            'focus:outline-none focus:ring-2 ring-offset-2 ring-offset-blue-400 ring-white ring-opacity-60',
          ]"
        >
          <ul>
            <li
              v-for="post in posts"
              :key="post.id"
              class="relative p-3 rounded-md hover:bg-coolGray-100"
              @click="liclick"
            >
              <h3 class="text-sm font-medium leading-5">
                {{ post.title }}
              </h3>

              <ul
                class="
                  flex
                  mt-1
                  space-x-1
                  text-xs
                  font-normal
                  leading-4
                  text-coolGray-500
                "
              >
                <li>{{ post.date }}</li>
                <li>&middot;</li>
                <li>{{ post.commentCount }} comments</li>
                <li>&middot;</li>
                <li>{{ post.shareCount }} shares</li>
              </ul>

              <a
                href="#"
                :class="[
                  'absolute inset-0 rounded-md',
                  'focus:z-10 focus:outline-none focus:ring-2 ring-blue-400',
                ]"
              />
            </li>
          </ul>
        </TabPanel>
      </TabPanels>
    </TabGroup>
  </div>
</template>

<script>
import { TabGroup, TabList, Tab, TabPanels, TabPanel } from "@headlessui/vue";

export default {
  name: "Tabitem",
  components: {
    TabGroup,
    TabList,
    Tab,
    TabPanels,
    TabPanel,
  },
  props: {
    categories: Object,
  },
  date: {
    key: "",
  },
  methods: {
    change: function (key) {
      if (key != this.key) {
        this.key = key;
        this.$emit("tabChange");
      }else{
          this.$emit('tabClick')
      }
    },
    liclick: function () {
      this.$emit("liClick");
    },
  },

};
</script>