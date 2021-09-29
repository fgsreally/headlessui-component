<template>
  <div>
    <div class="flex items-center justify-center">
      <button
        type="button"
        @click="openModal();btnopen()"
        class="
          px-4
          py-2
          text-sm
          font-medium
          text-white
          bg-black
          rounded-md
          bg-opacity-20
          hover:bg-opacity-30
          focus:outline-none
          focus-visible:ring-2
          focus-visible:ring-white
          focus-visible:ring-opacity-75
        "
      >
        {{ dialog.note }}
      </button>
    </div>
    <TransitionRoot appear :show="isOpen" as="template">
      <Dialog as="div" @close="closeModal">
        <div class="fixed inset-0 z-10 overflow-y-auto">
          <div class="min-h-screen px-4 text-center">
            <TransitionChild
              as="template"
              enter="duration-300 ease-out"
              enter-from="opacity-0"
              enter-to="opacity-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100"
              leave-to="opacity-0"
            >
              <DialogOverlay class="fixed inset-0" />
            </TransitionChild>

            <span class="inline-block h-screen align-middle" aria-hidden="true">
              &#8203;
            </span>

            <TransitionChild
              as="template"
              enter="duration-300 ease-out"
              enter-from="opacity-0 scale-95"
              enter-to="opacity-100 scale-100"
              leave="duration-200 ease-in"
              leave-from="opacity-100 scale-100"
              leave-to="opacity-0 scale-95"
            >
              <div
                class="
                  inline-block
                  w-full
                  max-w-md
                  p-6
                  my-8
                  overflow-hidden
                  text-left
                  align-middle
                  transition-all
                  transform
                  bg-white
                  shadow-xl
                  rounded-2xl
                "
              >
                <DialogTitle
                  as="h3"
                  class="text-lg font-medium leading-6 text-gray-900"
                >
                  {{ dialog.title }}
                </DialogTitle>
                <div class="mt-2">
                  <p class="text-sm text-gray-500">
                    {{ dialog.body }}
                  </p>
                </div>

                <div class="mt-4 flex">
                  <button
                    type="button"
                    class="
                      m-1
                      inline-flex
                      justify-center
                      px-4
                      py-2
                      text-sm
                      font-medium
                      text-blue-900
                      bg-blue-100
                      border border-transparent
                      rounded-md
                      hover:bg-blue-200
                      focus:outline-none
                      focus-visible:ring-2
                      focus-visible:ring-offset-2
                      focus-visible:ring-blue-500
                    "
                    v-for="(item, index) in dialog.answer"
                    :key="index"
                     @click="
                     closeModal();
                      buttonclick(item);
                    "
                  >
                    {{ item }}
                  </button>
                </div>
              </div>
            </TransitionChild>
          </div>
        </div>
      </Dialog>
    </TransitionRoot>
  </div>
</template>

<script>
import { ref } from "vue";
import {
  TransitionRoot,
  TransitionChild,
  Dialog,
  DialogOverlay,
  DialogTitle,
} from "@headlessui/vue";

export default {
  props: { dialog: Object },
  components: {
    TransitionRoot,
    TransitionChild,
    Dialog,
    DialogOverlay,
    DialogTitle,
  },
  methods: {
    buttonclick: function(data){
      this.$emit("buttonClick", data);
    },
     btnopen: function(){
      this.$emit("btnOpen");
    }
  },
  setup() {
    const isOpen = ref(false);

    return {
      isOpen,
      closeModal() {
        isOpen.value = false;
      },
      openModal() {
        isOpen.value = true;
      },
    };
  },
};
</script>
