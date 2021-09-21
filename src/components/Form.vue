<template>
  <form class="form">
    <div class="form__filter-group">
      <FormFilters
        class="form__filters"
        :form="form"
        :switchFilters="switchFilters"
        @sendForm="sendForm()"
      />

      <FormSubFilters
        v-if="switchFilters === 'all' && switchSubFilters"
        class="form__sub-filters"
        :form="form"
        :switchSubFilters="switchSubFilters"
        @change="switchSubFilters = $event"
      />
    </div>

    <div class="form__switches">
      <v-switch
        class="form__switches-btn-group"
        :value="switchFilters"
        @change="switchFilters = $event"
      >
        <template #left>
          Основной поиск
        </template>

        <template #right>
          Искать по названию
        </template>
      </v-switch>

      <div v-if="switchFilters === 'all'" class="form__switches-btn-group">
        <v-switch-button
          :active="switchSubFilters === 'price'"
          @click="changeSubFilters('price')"
        >
          Цена
        </v-switch-button>

        <v-switch-button
          :active="switchSubFilters === 'metric'"
          @click="changeSubFilters('metric')"
        >
          Метраж
        </v-switch-button>
      </div>
    </div>
  </form>
</template>

<script>
import FormFilters from "@/components/form/FormFilters.vue";
import FormSubFilters from "@/components/form/FormSubFilters.vue";
import VSwitch from "@/components/common/VSwitch.vue";
import VSwitchButton from "@/components/common/VSwitchButton.vue";

export default {
  name: "Form",
  components: {
    FormFilters,
    FormSubFilters,
    VSwitch,
    VSwitchButton,
  },
  data() {
    return {
      switchFilters: "all", // 'all' or 'name'
      switchSubFilters: "", // '' or 'price' or 'metric'

      form: {
        city: "",
        purpose: "",
        type: "",

        name: "",

        startPrice: "",
        endPrice: "",
        period: "₽/месяц",

        startSquare: "",
        endSquare: "",
      },
    };
  },
  methods: {
    changeSubFilters(value) {
      this.switchSubFilters = this.switchSubFilters === value ? "" : value;
    },

    sendForm() {
      alert("Форма отправлена!");
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  display: flex;
  flex-direction: column;
  justify-content: space-between;

  width: 100%;
  background: #85b5e6;
}

.form__filter-group {
  display: flex;
  flex-direction: column;
  padding: 35px 20px;
}

.form__sub-filters {
  margin-top: 28px;
}

.form__switches {
  display: flex;
  justify-content: space-between;
  padding: 20px;
  background: #e6f2fe;
}

.form__switches-btn-group {
  display: flex;

  @media (max-width: 500px) {
    flex-direction: column;
  }
}
</style>
