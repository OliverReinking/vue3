# Input Components

## Input Form

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputForm";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputForm.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <div class="form-control w-full px-2">
          <label class="label" for="category">
            <span class="label-text">Kategorie</span>
          </label>
          <select
            id="category"
            class="select select-bordered"
            v-model="event.category"
          >
            <option
              v-for="category in categories"
              :value="category"
              :key="category"
              :selected="category === event.category"
              >{{ category }}
            </option>
          </select>
        </div>
        <div class="form-control w-full px-2">
          <label class="label" for="title">
            <span class="label-text">Titel</span>
          </label>
          <input
            type="text"
            id="title"
            v-model="event.title"
            placeholder="Titel"
            class="input input-bordered"
          />
        </div>
        <div class="form-control w-full px-2">
          <label class="label" for="description">
            <span class="label-text">Beschreibung</span>
          </label>
          <input
            type="text"
            id="description"
            v-model="event.description"
            placeholder="Beschreibung"
            class="input input-bordered"
          />
        </div>
        <div class="form-control w-full px-2">
          <label class="label" for="location">
            <span class="label-text">Veranstaltungsort</span>
          </label>
          <input
            type="text"
            id="location"
            v-model="event.location"
            placeholder="Veranstaltungsort"
            class="input input-bordered"
          />
        </div>
        <div class="form-control w-full px-2">
          <label class="label" for="pets">
            <span class="label-text">Sind Haustiere erlaubt?</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-yes"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="1"
                class="radio"
              />
              <span class="radio-mark" for="pets-yes"></span>
            </div>
            <span class="label-text">Ja</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-no"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="0"
                class="radio"
              />
              <span class="radio-mark" for="pets-no"></span>
            </div>
            <span class="label-text">Nein</span>
          </label>
        </div>
        <div class="mt-4 form-control w-full">
          <label class="label">
            <span class="label-text">Extras</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                type="checkbox"
                id="extras-catering"

                class="checkbox"
                checked
              />
              <span class="checkbox-mark" for="extras-catering"></span>
            </div>
            <span class="label-text">Catering</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                type="checkbox"
                id="extras-live"
                v-model="event.extras.live"
                class="checkbox"
              />
              <span class="checkbox-mark" for="extras-live"></span>
            </div>
            <span class="label-text">Live</span>
          </label>
        </div>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import { ref, reactive } from "vue";
export default {
  name: "InputForm",
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: true,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

## BaseInput

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputFormV1";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputV1.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <div class="form-control w-full px-2">
          <label class="label" for="category">
            <span class="label-text">Kategorie</span>
          </label>
          <select
            id="category"
            class="select select-bordered"
            v-model="event.category"
          >
            <option
              v-for="category in categories"
              :value="category"
              :key="category"
              :selected="category === event.category"
              >{{ category }}
            </option>
          </select>
        </div>
        <BaseInput type="text" label="Titel" v-model="event.title" />
        <BaseInput
          type="text"
          label="Beschreibung"
          v-model="event.description"
        />
        <BaseInput
          type="text"
          label="Veranstaltungsort"
          v-model="event.location"
        />
        <div class="form-control w-full px-2">
          <label class="label" for="pets">
            <span class="label-text">Sind Haustiere erlaubt?</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-yes"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="1"
                class="radio"
              />
              <span class="radio-mark" for="pets-yes"></span>
            </div>
            <span class="label-text">Ja</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-no"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="0"
                class="radio"
              />
              <span class="radio-mark" for="pets-no"></span>
            </div>
            <span class="label-text">Nein</span>
          </label>
        </div>
        <div class="mt-4 form-control w-full">
          <label class="label">
            <span class="label-text">Extras</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                type="checkbox"
                id="extras-catering"
                v-model="event.extras.catering"
                class="checkbox"
              />
              <span class="checkbox-mark" for="extras-catering"></span>
            </div>
            <span class="label-text">Catering</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                type="checkbox"
                id="extras-live"
                v-model="event.extras.live"
                class="checkbox"
              />
              <span class="checkbox-mark" for="extras-live"></span>
            </div>
            <span class="label-text">Live</span>
          </label>
        </div>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import BaseInput from "./form/BaseInput";
import { ref, reactive } from "vue";
export default {
  name: "InputFormV1",
  //
  components: {
    BaseInput,
  },
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: false,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

#### BaseInput.vue (Child)

```js
<template>
  <div class="form-control w-full px-2">
    <label class="label" v-if="label">
      <span class="label-text">{{ label }}</span>
    </label>
    <input
      v-bind="$attrs"
      :placeholder="label"
      class="input input-bordered"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>
<script>
export default {
  name: "BaseInput",
  //
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
  },
};
</script>

```


## BaseSelect

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputFormV2";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputV2.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <BaseSelect
          label="Kategorie"
          :options="categories"
          v-model="event.category"
        />
        <BaseInput type="text" label="Titel" v-model="event.title" />
        <BaseInput
          type="text"
          label="Beschreibung"
          v-model="event.description"
        />
        <BaseInput
          type="text"
          label="Veranstaltungsort"
          v-model="event.location"
        />
        <div class="form-control w-full px-2">
          <label class="label" for="pets">
            <span class="label-text">Sind Haustiere erlaubt?</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-yes"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="1"
                class="radio"
              />
              <span class="radio-mark" for="pets-yes"></span>
            </div>
            <span class="label-text">Ja</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-no"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="0"
                class="radio"
              />
              <span class="radio-mark" for="pets-no"></span>
            </div>
            <span class="label-text">Nein</span>
          </label>
        </div>
        <div class="mt-4 form-control w-full">
          <label class="label">
            <span class="label-text">Extras</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                type="checkbox"
                id="extras-catering"
                v-model="event.extras.catering"
                class="checkbox"
              />
              <span class="checkbox-mark" for="extras-catering"></span>
            </div>
            <span class="label-text">Catering</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                type="checkbox"
                id="extras-live"
                v-model="event.extras.live"
                class="checkbox"
              />
              <span class="checkbox-mark" for="extras-live"></span>
            </div>
            <span class="label-text">Live</span>
          </label>
        </div>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import BaseInput from "./form/BaseInput";
import BaseSelect from "./form/BaseSelect";
import { ref, reactive } from "vue";
export default {
  name: "InputFormV2",
  //
  components: {
    BaseInput,
    BaseSelect,
  },
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: false,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

#### BaseSelect.vue (Child)

```js
<template>
  <div class="form-control w-full px-2">
    <label class="label" v-if="label">
      <span class="label-text">Kategorie</span>
    </label>
    <select
      v-bind="$attrs"
      class="select select-bordered"
      :value="modelValue"
      @change="$emit('update:modelValue', $event.target.value)"
    >
      <option
        v-for="option in options"
        :value="option"
        :key="option"
        :selected="option === modelValue"
        >{{ option }}
      </option>
    </select>
  </div>
</template>
<script>
export default {
  name: "BaseSelect",
  //
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    options: {
      type: Array,
      required: true,
    },
  },
};
</script>
```

## Base Checkbox

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputFormV3";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputV3.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <BaseSelect
          label="Kategorie"
          :options="categories"
          v-model="event.category"
        />
        <BaseInput type="text" label="Titel" v-model="event.title" />
        <BaseInput
          type="text"
          label="Beschreibung"
          v-model="event.description"
        />
        <BaseInput
          type="text"
          label="Veranstaltungsort"
          v-model="event.location"
        />
        <div class="form-control w-full px-2">
          <label class="label" for="pets">
            <span class="label-text">Sind Haustiere erlaubt?</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-yes"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="1"
                class="radio"
              />
              <span class="radio-mark" for="pets-yes"></span>
            </div>
            <span class="label-text">Ja</span>
          </label>
          <label class="cursor-pointer label justify-start">
            <div class="mr-2">
              <input
                id="pets-no"
                name="pets"
                type="radio"
                v-model="event.pets"
                :value="0"
                class="radio"
              />
              <span class="radio-mark" for="pets-no"></span>
            </div>
            <span class="label-text">Nein</span>
          </label>
        </div>
        <div class="mt-4 form-control w-full">
          <label class="label">
            <span class="label-text">Extras</span>
          </label>
          <BaseCheckbox label="Catering" v-model="event.extras.catering" />
          <BaseCheckbox label="Live" v-model="event.extras.live" />
        </div>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import BaseInput from "./form/BaseInput";
import BaseSelect from "./form/BaseSelect";
import BaseCheckbox from "./form/BaseCheckbox";
import { ref, reactive } from "vue";
export default {
  name: "InputFormV3",
  //
  components: {
    BaseInput,
    BaseSelect,
    BaseCheckbox,
  },
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: true,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

#### BaseCheckbox.vue (Child)

```js
<template>
  <label class="cursor-pointer label justify-start">
    <div class="mr-2">
      <input
        type="checkbox"
        class="checkbox"
        :checked="modelValue"
        @change="$emit('update:modelValue', $event.target.checked)"
      />
      <span class="checkbox-mark" for="extras-catering"></span>
    </div>
    <span class="label-text" v-if="label">{{ label }}</span>
  </label>
</template>

<script>
export default {
  name: "BaseCheckbox",
  //
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
```

## BaseRadio

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputFormV4";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputFormV4.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <BaseSelect
          label="Kategorie"
          :options="categories"
          v-model="event.category"
        />
        <BaseInput type="text" label="Titel" v-model="event.title" />
        <BaseInput
          type="text"
          label="Beschreibung"
          v-model="event.description"
        />
        <BaseInput
          type="text"
          label="Veranstaltungsort"
          v-model="event.location"
        />
        <div class="form-control w-full px-2">
          <label class="label" for="pets">
            <span class="label-text">Sind Haustiere erlaubt?</span>
          </label>
          <BaseRadio name="pets" label="Ja" v-model="event.pets" value="1" />
          <BaseRadio name="pets" label="Nein" v-model="event.pets" value="0" />
        </div>
        <div class="mt-4 form-control w-full">
          <label class="label">
            <span class="label-text">Extras</span>
          </label>
          <BaseCheckbox label="Catering" v-model="event.extras.catering" />
          <BaseCheckbox label="Live" v-model="event.extras.live" />
        </div>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import BaseInput from "./form/BaseInput";
import BaseSelect from "./form/BaseSelect";
import BaseCheckbox from "./form/BaseCheckbox";
import BaseRadio from "./form/BaseRadio";
import { ref, reactive } from "vue";
export default {
  name: "InputFormV4",
  //
  components: {
    BaseInput,
    BaseSelect,
    BaseCheckbox,
    BaseRadio,
  },
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: true,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

#### BaseRadio.vue (Child)

```js
<template>
  <label class="cursor-pointer label justify-start mr-4">
    <div class="mr-2">
      <input
        v-bind="$attrs"
        type="radio"
        class="radio"
        :checked="modelValue === value"
        :value="value"
        @change="$emit('update:modelValue', value)"
      />
      <span class="radio-mark"></span>
    </div>
    <span class="label-text" v-if="label">{{ label }}</span>
  </label>
</template>
<script>
export default {
  name: "BaseRadio",
  //
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    value: {
      type: [String, Number],
      required: true,
    },
  },
  //
  inheritAttrs: false,
};
</script>
```

## BaseRadioGroup

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputFormV5";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputFormV5.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <BaseSelect
          label="Kategorie"
          :options="categories"
          v-model="event.category"
        />
        <BaseInput type="text" label="Titel" v-model="event.title" />
        <BaseInput
          type="text"
          label="Beschreibung"
          v-model="event.description"
        />
        <BaseInput
          type="text"
          label="Veranstaltungsort"
          v-model="event.location"
        />
        <BaseRadioGroup
          v-model="event.pets"
          title="Sind Haustiere erlaubt?"
          name="pets"
          vertical
          :options="petOptions"
        />
        <div class="mt-4 form-control w-full">
          <label class="label">
            <span class="label-text">Extras</span>
          </label>
          <BaseCheckbox label="Catering" v-model="event.extras.catering" />
          <BaseCheckbox label="Live" v-model="event.extras.live" />
        </div>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import BaseInput from "./form/BaseInput";
import BaseSelect from "./form/BaseSelect";
import BaseCheckbox from "./form/BaseCheckbox";
import BaseRadioGroup from "./form/BaseRadioGroup";
import { ref, reactive } from "vue";
export default {
  name: "InputFormV5",
  //
  components: {
    BaseInput,
    BaseSelect,
    BaseCheckbox,
    BaseRadioGroup,
  },
  //
  data() {
    return {};
  },
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const petOptions = ref([
      { label: "Ja", value: 1 },
      { label: "Nein", value: 0 },
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: true,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      petOptions,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

#### BaseRadioGroup.vue (Child)

```js
<template>
  <div class="form-control w-full px-2">
    <label class="label" :for="name">
      <span class="label-text" v-if="title">{{ title }}</span>
    </label>
    <div class="flex" :class="styleRadio">
      <BaseRadio
        v-for="option in options"
        :key="option.value"
        :label="option.label"
        :value="option.value"
        :name="name"
        :modelValue="modelValue"
        @update:modelValue="$emit('update:modelValue', $event)"
      />
    </div>
  </div>
</template>
<script>
import BaseRadio from "./BaseRadio";
import { computed } from "vue";
export default {
  name: "BaseRadioGroup",
  //
  components: {
    BaseRadio,
  },
  //
  props: {
    vertical: {
      type: Boolean,
      default: false,
    },
    options: {
      Array,
      required: true,
    },
    title: {
      type: String,
      default: "",
    },
    name: {
      type: String,
      required: true,
    },
    modelValue: {
      type: [String, Number],
      required: true,
    },
  },
  //
  setup(props) {
    const styleRadio = computed(function() {
      if (props.vertical) {
        return "flex-col items-start";
      }
      //
      return "flex-wrap flex-row items-start";
    });
    //
    return {
        styleRadio
    }
  },
};
</script>
```


## BaseCheckboxGroup

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Input Forms
      </h1>
      <div class="mt-8">
        <h2>InputForm.vue</h2>
        <InputForm />
      </div>
    </div>
  </div>
</template>
<script>
import InputForm from "./components/input/InputFormV6";
export default {
  name: "App",
  //
  components: {
    InputForm,
  },
};
</script>
```

#### InputFormV6.vue (Child)

```js
<template>
  <div>
    <h3>Neue Veranstaltung</h3>
    <form v-if="!showEventData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <BaseSelect
          label="Kategorie"
          :options="categories"
          v-model="event.category"
        />
        <BaseInput type="text" label="Titel" v-model="event.title" />
        <BaseInput
          type="text"
          label="Beschreibung"
          v-model="event.description"
        />
        <BaseInput
          type="text"
          label="Veranstaltungsort"
          v-model="event.location"
        />
        <BaseRadioGroup
          v-model="event.pets"
          title="Sind Haustiere erlaubt?"
          name="pets"
          vertical
          :options="petOptions"
        />
        <BaseCheckboxGroup title="Extras" vertical>
          <BaseCheckbox label="Catering" v-model="event.extras.catering" />
          <BaseCheckbox label="Live" v-model="event.extras.live" />
        </BaseCheckboxGroup>
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="sendInputData"
          class="btn btn-sm btn-primary"
        >
          Veranstaltung speichern
        </button>
      </div>
    </form>
    <div v-if="showEventData">
      <h3>Folgende Daten wurden eingegeben:</h3>
      <div v-for="(data, propertyName, index) in event" :key="index">
        {{ propertyName }}: {{ data }}
      </div>
      <div class="mt-4 text-center">
        <button
          v-on:click.prevent="showInputForm"
          class="btn btn-sm btn-secondary"
        >
          zum Eingabeformular
        </button>
      </div>
    </div>
  </div>
</template>
<script>
import BaseInput from "./form/BaseInputV3";
import BaseSelect from "./form/BaseSelect";
import BaseRadioGroup from "./form/BaseRadioGroup";
import BaseCheckbox from "./form/BaseCheckbox";
import BaseCheckboxGroup from "./form/BaseCheckboxGroup";
import { ref, reactive } from "vue";
export default {
  name: "InputFormV7",
  //
  components: {
    BaseInput,
    BaseSelect,
    BaseRadioGroup,
    BaseCheckbox,
    BaseCheckboxGroup,
  },
  //
  setup() {
    const showEventData = ref(false);
    //
    const categories = ref([
      "Erziehung",
      "Weiterbildung",
      "Gemeinschaft",
      "Natur",
    ]);
    //
    const petOptions = ref([
      { label: "Ja", value: 1 },
      { label: "Nein", value: 0 },
    ]);
    //
    const event = reactive({
      title: "",
      description: "",
      location: "",
      pets: 0,
      extras: {
        catering: true,
        live: false,
      },
    });
    //
    function sendInputData() {
      showEventData.value = true;
    }
    //
    function showInputForm() {
      showEventData.value = false;
    }
    //
    return {
      showEventData,
      categories,
      petOptions,
      event,
      sendInputData,
      showInputForm,
    };
  },
};
</script>
```

#### BaseCheckboxGroup.vue (Child)

```js
<template>
  <div class="form-control w-full px-2">
    <label class="label">
      <span class="label-text" v-if="title">{{ title }}</span>
    </label>
    <div class="flex" :class="styleCheckbox">
      <slot></slot>
    </div>
  </div>
</template>
<script>
import { computed } from "vue";
export default {
  name: "BaseCheckboxGroup",
  //
  props: {
    vertical: {
      type: Boolean,
      default: false,
    },
    title: {
      type: String,
      default: "",
    },
  },
  //
  setup(props) {
    const styleCheckbox = computed(function() {
      if (props.vertical) {
        return "flex-col items-start";
      }
      //
      return "flex-wrap flex-row items-start";
    });
    //
    return {
      styleCheckbox,
    };
  },
};
</script>
```

## Label & Input

### 1. Lösungsversuch

#### BaseInputV2.vue (Child)

```js
<template>
  <div class="form-control w-full px-2">
    <label class="label" v-if="label" :for="id">
      <span class="label-text">{{ label }}</span>
    </label>
    <input
      :id="id"
      v-bind="$attrs"
      :placeholder="label"
      class="input input-bordered"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>
<script>
export default {
  name: "BaseInputV2",
  //
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
    id: {
      type: String,
      default: ""
    }
  },
};
</script>
```

### 2. Lösungsversuch

#### UniqueID (src/composables)

```js
let UUID = 0;
//
export default function UniqueID() {
  const getID = () => {
    UUID++;
    return UUID;
  };
  //
  return {
    getID,
  };
}
```

#### BaseInputV3.vue (Child)

```js
<template>
  <div class="form-control w-full px-2">
    <label class="label" v-if="label" :for="uuid">
      <span class="label-text">{{ label }}</span>
    </label>
    <input
      :id="uuid"
      v-bind="$attrs"
      :placeholder="label"
      class="input input-bordered"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>
<script>
import UniqueID from '../../../composables/UniqueID'
export default {
  name: "BaseInputV3",
  //
  props: {
    label: {
      type: String,
      default: "",
    },
    modelValue: {
      type: [String, Number],
      default: "",
    },
  },
  //
  setup () {
    const uuid = UniqueID().getID()
    //
    return {
      uuid
    }
  }
};
</script>
```
