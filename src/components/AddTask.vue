<script lang="ts">
import { defineComponent, ref } from "vue";
import Task from "@/models/Task";
import { useStore } from "@/store";
import { MutationType } from "@/store/mutations";
import { useRouter } from "vue-router";

export default defineComponent({
  name: "AddTask",
  setup() {
    const taskName = ref("");
    const router = useRouter(); // Substitute of Vue prototype this.$router
    const store = useStore();
    const addTask = (): void => {
      const newTask = new Task(taskName.value);
      store.commit(MutationType.SetTask, newTask);
      taskName.value = "";
      router.push({ path: "/" });
    };

    return { taskName, addTask };
  },
});
</script>
