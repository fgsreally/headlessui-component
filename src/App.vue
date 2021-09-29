<template>
  <div class="flex justify-center items-center w-screen h-screen">
    <Dialog
      :dialog="dialog"
      @buttonClick="test"
      @btnOpen="test('open')"
    ></Dialog>
    <Popoveritem
      :solutions="solutions"
      :note="'solutions'"
      :isOpen="test"
    ></Popoveritem>
    <Switchitem :isOpen="test"></Switchitem>
    <Tabitem
      @tabChange="test('go')"
      @liClick="test('click')"
      @tabClick="test('same')"
      :categories="categories"
    ></Tabitem>
    <Disclosureitem :logs="logs" @isOpen="test"></Disclosureitem>
  </div>
</template>

<script>
import Tabitem from "./components/Tab";
import Disclosureitem from "./components/Disclosure";
import Dialog from "./components/Dialog";
import Popoveritem from "./components/Popover.vue";
import Switchitem from "./components/Switch.vue";
export default {
  name: "App",
  components: {
    Tabitem,
    Disclosureitem,
    Dialog,
    Popoveritem,
    Switchitem,
  },
  setup() {
    var categories = {
      Recent: [
        {
          id: 1,
          title: "Does drinking coffee make you smarter?",
          date: "5h ago",
          commentCount: 5,
          shareCount: 2,
        },
        {
          id: 2,
          title: "So you've bought coffee... now what?",
          date: "2h ago",
          commentCount: 3,
          shareCount: 2,
        },
      ],
      Popular: [
        {
          id: 1,
          title: "Is tech making coffee better or worse?",
          date: "Jan 7",
          commentCount: 29,
          shareCount: 16,
        },
        {
          id: 2,
          title: "The most innovative things happening in coffee",
          date: "Mar 19",
          commentCount: 24,
          shareCount: 12,
        },
      ],
      Trending: [
        {
          id: 1,
          title: "Ask Me Anything: 10 answers to your questions about coffee",
          date: "2d ago",
          commentCount: 9,
          shareCount: 5,
        },
        {
          id: 2,
          title: "The worst advice we've ever heard about coffee",
          date: "4d ago",
          commentCount: 1,
          shareCount: 2,
        },
      ],
    };
    var logs = [
      {
        question: "问题1",
        answer: "回答1",
      },
      {
        question: "问题2",
        answer: "回答2",
      },
      {
        question: "问题2",
        answer: "回答2",
      },
    ];
    var dialog = {
      note: "提示",
      title: "注意样式的影响",
      body: "最关键的是组件中是否有关键属性破坏布局（因为展示时往往单一组件占用页面，对整体影响看不出来）",
      answer: ["关闭", "打开"],
    };
    var solutions = [
      {
        name: "Insights",
        description: "Measure actions your users take",
        href: "##",
        icon: `
            <svg
              width="48"
              height="48"
              viewBox="0 0 48 48"
              fill="none"
              aria-hidden='true'
              xmlns="http://www.w3.org/2000/svg"
            >
              <rect width="48" height="48" rx="8" fill="#FFEDD5" />
              <path
                d="M24 11L35.2583 17.5V30.5L24 37L12.7417 30.5V17.5L24 11Z"
                stroke="#FB923C"
                stroke-width="2"
              />
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M16.7417 19.8094V28.1906L24 32.3812L31.2584 28.1906V19.8094L24 15.6188L16.7417 19.8094Z"
                stroke="#FDBA74"
                stroke-width="2"
              />
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M20.7417 22.1196V25.882L24 27.7632L27.2584 25.882V22.1196L24 20.2384L20.7417 22.1196Z"
                stroke="#FDBA74"
                stroke-width="2"
              />
            </svg>
          `,
      },
      {
        name: "Automations",
        description: "Create your own targeted content",
        href: "##",
        icon: `
            <svg
              width="48"
              height="48"
              viewBox="0 0 48 48"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <rect width="48" height="48" rx="8" fill="#FFEDD5" />
              <path
                d="M28.0413 20L23.9998 13L19.9585 20M32.0828 27.0001L36.1242 34H28.0415M19.9585 34H11.8755L15.9171 27"
                stroke="#FB923C"
                stroke-width="2"
              />
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M18.804 30H29.1963L24.0001 21L18.804 30Z"
                stroke="#FDBA74"
                stroke-width="2"
              />
            </svg>
          `,
      },
      {
        name: "Reports",
        description: "Keep track of your growth",
        href: "##",
        icon: `
            <svg
              width="48"
              height="48"
              viewBox="0 0 48 48"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <rect width="48" height="48" rx="8" fill="#FFEDD5" />
              <rect x="13" y="32" width="2" height="4" fill="#FDBA74" />
              <rect x="17" y="28" width="2" height="8" fill="#FDBA74" />
              <rect x="21" y="24" width="2" height="12" fill="#FDBA74" />
              <rect x="25" y="20" width="2" height="16" fill="#FDBA74" />
              <rect x="29" y="16" width="2" height="20" fill="#FB923C" />
              <rect x="33" y="12" width="2" height="24" fill="#FB923C" />
            </svg>
          `,
      },
    ];
    function test(str) {
      console.log(str);
    }

    return { categories, test, logs, dialog, solutions };
  },
};
</script>

<style>
</style>