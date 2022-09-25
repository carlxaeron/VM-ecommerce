<script setup>
  // import { computed, ref, onMounted } from "vue";
  import { useMainStore } from "@/stores/main";
  import SectionMain from "@/components/SectionMain.vue";
  import LayoutAuthenticated from "@/layouts/LayoutAdminAuthenticated.vue";

  const mainStore = useMainStore();
  </script>

  <template>
    <LayoutAuthenticated>
      <SectionMain>
        <h1>Hello World</h1>
      </SectionMain>
    </LayoutAuthenticated>
  </template>
