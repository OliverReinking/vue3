# Composition API

## Replacing data with ref 

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Replacing data with ref
      </h1>
      <div class="mt-8">
        <Data />
      </div>
      <div class="mt-8">
        <DataAPI />
      </div>
    </div>
  </div>
</template>
<script>
import Data from "./components/api/Data";
import DataAPI from "./components/api/DataAPI";
export default {
  name: "App",
  //
  components: {
    Data,
    DataAPI,
  },
};
</script>
```

#### Data.vue (Child)

```js
<template>
  <h2>Alte Schreibweise: {{ firstName }}</h2>
</template>
<script>
export default {
  name: "Data",
  //
  data() {
    return {
      firstName: "Klaus",
    };
  },
};
</script>
```

#### DataAPI.vue (Child)

```js
<template>
  <h2>Neue Schreibweise: {{ firstName }}</h2>
</template>
<script>
import { ref } from "vue";
export default {
  name: "DataAPI",
  //
  setup() {
      const firstName = ref('Klaus')
      return {
          firstName: firstName
      }
  },
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Replacing data with ref
      </h1>
      <div class="mt-8">
        <Data />
      </div>
      <div class="mt-8">
        <DataAPI />
      </div>
    </div>
  </div>
</template>
<script>
import Data from "./components/api/Data";
import DataAPI from "./components/api/DataAPIV2";
export default {
  name: "App",
  //
  components: {
    Data,
    DataAPI,
  },
};
</script>
```

#### Data.vue (Child)

```js
<template>
  <h2>Alte Schreibweise: {{ firstName }}</h2>
</template>
<script>
export default {
  name: "Data",
  //
  data() {
    return {
      firstName: "Klaus",
    };
  },
};
</script>
```

#### DataAPIV2.vue (Child)

```js
<template>
  <h2>Neue Schreibweise: {{ firstName }}</h2>
  <p>{{ greeting }} </p>
</template>
<script>
import { ref } from "vue";
export default {
  name: "DataAPI",
  //
  setup() {
    const firstName = ref("Klaus");
    firstName.value = 'Angela';
    const greeting = `Hallo ${firstName.value}`
    console.log("firstName: ", firstName);
    return {
      firstName,
      greeting
    };
  },
};
</script>
```

## Replacing data with reactive

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Replacing data with reactive
      </h1>
      <div class="mt-8">
        <DataReactive />
      </div>
      <div class="mt-8">
        <DataReactiveAPI />
      </div>
    </div>
  </div>
</template>
<script>
import DataReactive from "./components/api/DataReactive";
import DataReactiveAPI from "./components/api/DataReactiveAPI";
export default {
  name: "App",
  //
  components: {
    DataReactive,
    DataReactiveAPI,
  },
};
</script>
```

#### DataReactive.vue (Child)

```js
<template>
  <h2>Alte Schreibweise</h2>
  <h3>{{ firstName }}</h3>
  <h3>{{ lastName }}</h3>
  <h3>{{ club }}</h3>
</template>
<script>
export default {
  name: "Data",
  //
  data() {
    return {
      firstName: "Gerd",
      lastName: "Müller",
      club: "Bayern München",
    };
  },
};
</script>
```

#### DataReactiveAPI.vue (Child)

```js
<template>
  <h2>Neue Schreibweise</h2>
  <h3>{{ state.firstName }}</h3>
  <h3>{{ state.lastName }}</h3>
  <h3>{{ state.club }}</h3>
  <p>{{ greeting }}</p>
</template>
<script>
import { reactive } from "vue";
export default {
  name: "DataAPI",
  //
  setup() {
    const state = reactive({
      firstName: "Gerd",
      lastName: "Müller",
      club: "Bayern München",
    });
    //
    const greeting = `Hallo ${state.firstName} ${state.lastName} (${state.club})`;
    //
    return {
      state,
      greeting,
    };
  },
};
</script>
```

## Reactivity

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Reactivity
      </h1>
      <div class="mt-8">
        <ReactivityAPIA />
      </div>
    </div>
  </div>
</template>
<script>
import ReactivityAPIA from "./components/api/ReactivityAPIA";
export default {
  name: "App",
  //
  components: {
    ReactivityAPIA,
  },
};
</script>
```

#### ReactiveAPIA.vue (Child)

```js
<template>
  <div>
    <h2>{{ framework }}</h2>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  name: "ReactivityAPIA",
  //
  setup() {
    let framework = ref("Vue 2");
    //
    setTimeout(() => {
      framework.value = "Vue 3";
      console.log("new framework:", framework);
    }, 2000);
    //
    return {
      framework,
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Reactivity
      </h1>
      <div class="mt-8">
        <ReactivityAPIB />
      </div>
    </div>
  </div>
</template>
<script>
import ReactivityAPIB from "./components/api/ReactivityAPIB";
export default {
  name: "App",
  //
  components: {
    ReactivityAPIB,
  },
};
</script>
```

#### ReactivityAPIB.vue (Child)

```js
<template>
  <div>
    <h2>{{ firstName }} {{ lastName }}</h2>
  </div>
</template>
<script>
import { reactive, toRefs } from "vue";
export default {
  name: "ReactivityAPIB",
  //
  setup() {
    const state = reactive({
      firstName: "Angela",
      lastName: "Merkel",
    });
    //
    setTimeout(() => {
      state.firstName = "Annalena";
      state.lastName = "Baerbock";
      console.log("new state:", state);
    }, 2000);
    //
    return toRefs(state);
  },
};
</script>
```

## Methods

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Methods
      </h1>
      <div class="mt-8">
        <Methods />
      </div>
      <div class="mt-8">
        <MethodsAPIRef />
      </div>
      <div class="mt-8">
        <MethodsAPIReactive />
      </div>
    </div>
  </div>
</template>
<script>
import Methods from "./components/api/Methods";
import MethodsAPIRef from "./components/api/MethodsAPIRef";
import MethodsAPIReactive from "./components/api/MethodsAPIReactive";
export default {
  name: "App",
  //
  components: {
    Methods,
    MethodsAPIRef,
    MethodsAPIReactive
  },
};
</script>
```

#### Methods.vue (Child)

```js
<template>
  <h2>Alte Schreibweise</h2>
  <h3>{{ firstName }} {{ lastName }}</h3>
  <h4>{{ goals }}</h4>
  <div class="btn-group justify-center">
    <button v-on:click.prevent="changeName" class="btn btn-sm btn-primary">
      Namen ändern
    </button>
    <button v-on:click.prevent="newGoal" class="btn btn-sm btn-secondary">Tor erzielt</button>
  </div>
</template>
<script>
export default {
  name: "Methods",
  //
  data() {
    return {
      firstName: "Gerd",
      lastName: "Müller",
      goals: 0,
    };
  },
  //
  methods: {
    changeName() {
      this.firstName = "Klaus";
    },
    newGoal() {
      this.goals++;
    },
  },
};
</script>
```

#### MethodsAPIRef.vue (Child)

```js
<template>
  <h2>Neue Schreibweise mit Ref</h2>
  <h3>{{ firstName }} {{ lastName }}</h3>
  <h4>{{ goals }}</h4>
  <div class="btn-group justify-center">
    <button v-on:click.prevent="changeName" class="btn btn-sm btn-primary">
      Namen ändern
    </button>
    <button v-on:click.prevent="newGoal" class="btn btn-sm btn-secondary">
      Tor erzielt
    </button>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  name: "MethodsAPIRef",
  //
  setup() {
    const firstName = ref("Gerd");
    const lastName = ref("Müller");
    const goals = ref(0);
    //
    function changeName() {
      this.firstName = "Klaus";
      this.lastName = "Fischer";
    }
    //
    function newGoal() {
      goals.value++;
    }
    //
    return {
      firstName,
      lastName,
      goals,
      changeName,
      newGoal
    };
  },
};
</script>
```

#### MethodsAPIReactive.vue (Child)

```js
<template>
  <h2>Neue Schreibweise mit Reactive</h2>
  <h3>{{ firstName }} {{ lastName }}</h3>
  <h4>{{ goals }}</h4>
  <div class="btn-group justify-center">
    <button v-on:click.prevent="changeName" class="btn btn-sm btn-primary">
      Namen ändern
    </button>
    <button v-on:click.prevent="newGoal" class="btn btn-sm btn-secondary">
      Tor erzielt
    </button>
  </div>
</template>
<script>
import { reactive, toRefs } from "vue";
export default {
  name: "MethodsAPIReactive",
  //
  setup() {
    const state = reactive({
      firstName: "Gerd",
      lastName: "Müller",
      goals: 0
    });
    //
    function changeName() {
      state.firstName = "Klaus";
      state.lastName = "Fischer";
    }
    //
    function newGoal() {
      state.goals++;
    }
    //
    return {
      ...toRefs(state),
      changeName,
      newGoal,
    };
  },
};
</script>
```

## v-model

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        v-model & Composition API
      </h1>
      <div class="mt-8">
        <h4>Alte Schreibweise</h4>
        <VModel />
      </div>
      <div class="mt-8">
        <h4>Composition API mit Ref</h4>
        <VModelAPIRef />
      </div>
      <div class="mt-8">
        <h4>Composition API mit Reactive</h4>
        <VModelAPIReactive />
      </div>
    </div>
  </div>
</template>
<script>
import VModel from "./components/api/VModel";
import VModelAPIRef from "./components/api/VModelAPIRef";
import VModelAPIReactive from "./components/api/VModelAPIReactive";
export default {
  name: "App",
  //
  components: {
    VModel,
    VModelAPIRef,
    VModelAPIReactive,
  },
};
</script>
```

#### VModel.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstName">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstName"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2">
      <label class="label" for="lastName">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastName"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "VModel",
  //
  data() {
    return {
      firstName: "",
      lastName: "",
    };
  },
};
</script>
```

#### VModelAPIRef.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstName">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstName"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2">
      <label class="label" for="lastName">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastName"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  name: "VModelAPIRef",
  //
  setup() {
    const firstName = ref("");
    const lastName = ref("");
    //
    return {
      firstName,
      lastName
    }
  },
};
</script>
```

#### VModelAPIReactive.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstName">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstName"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2">
      <label class="label" for="lastName">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastName"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { reactive, toRefs } from "vue";
export default {
  name: "VModelAPIReactive",
  //
  setup() {
    const state = reactive({
      firstName: "",
      lastName: "",
    });
    //
    return {
      ...toRefs(state),
    };
  },
};
</script>
```

## Computed Properties

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Computed Properties & Composition API
      </h1>
      <div class="mt-8">
        <h4>Alte Schreibweise</h4>
        <Computed />
      </div>
      <div class="mt-8">
        <h4>Composition API mit Ref</h4>
        <ComputedAPIRef />
      </div>
      <div class="mt-8">
        <h4>Composition API mit Reactive</h4>
        <ComputedAPIReactive />
      </div>
    </div>
  </div>
</template>
<script>
import Computed from "./components/api/Computed";
import ComputedAPIRef from "./components/api/ComputedAPIRef";
import ComputedAPIReactive from "./components/api/ComputedAPIReactive";
export default {
  name: "App",
  //
  components: {
    Computed,
    ComputedAPIRef,
    ComputedAPIReactive,
  },
};
</script>
```

#### Computed.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstName">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstName"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2">
      <label class="label" for="lastName">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastName"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
    <h2>{{ fullName }}</h2>
  </div>
</template>
<script>
export default {
  name: "Computed",
  //
  data() {
    return {
      firstName: "",
      lastName: "",
    };
  },
  //
  computed: {
      fullName() {
          return `${this.firstName} ${this.lastName}`
      }
  }
};
</script>

```

#### ComputedAPIRef.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIRef">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIRef"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2">
      <label class="label" for="lastNameAPIRef">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIRef"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
    <h2>{{ fullName }}</h2>
  </div>
</template>
<script>
import { ref, computed } from "vue";
export default {
  name: "ComputedAPIRef",
  //
  setup() {
    const firstName = ref("");
    const lastName = ref("");
    //
    const fullName = computed(function() {
      return `${firstName.value} ${lastName.value}`;
    });
    //
    return {
      firstName,
      lastName,
      fullName
    };
  },
};
</script>
```

#### ComputedAPIReactive.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIReactive">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIReactive"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2">
      <label class="label" for="lastNameAPIReactive">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIReactive"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
    <h2>{{ fullName }}</h2>
  </div>
</template>
<script>
import { reactive, toRefs, computed } from "vue";
export default {
  name: "ComputedAPIReactive",
  //
  setup() {
    const state = reactive({
      firstName: "",
      lastName: "",
    });
    //
    const fullName = computed(function() {
      return `${state.firstName} ${state.lastName}`;
    });
    //
    return {
      ...toRefs(state),
      fullName
    };
  },
};
</script>
```

## Watcher

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Watch & Composition API
      </h1>
      <div class="mt-8">
        <h4>Alte Schreibweise</h4>
        <Watch />
      </div>
      <div class="mt-8">
        <h4>Composition API mit Ref</h4>
        <WatchAPIRef />
      </div>
      <div class="mt-8">
        <h4>Composition API mit Reactive</h4>
        <WatchAPIReactive />
      </div>
    </div>
  </div>
</template>
<script>
import Watch from "./components/api/Watch";
import WatchAPIRef from "./components/api/WatchAPIRef";
import WatchAPIReactive from "./components/api/WatchAPIReactive";
export default {
  name: "App",
  //
  components: {
    Watch,
    WatchAPIRef,
    WatchAPIReactive,
  },
};
</script>
```

#### Watch.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstName">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstName"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastName">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastName"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "Watch",
  //
  data() {
    return {
      firstName: "Gerd",
      lastName: "Müller",
    };
  },
  //
  watch: {
    firstName(newValue, oldValue) {
      console.log("Watch old value: ", oldValue);
      console.log("Watch new value: ", newValue);
    },
    lastName(newValue, oldValue) {
      console.log("Watch old value: ", oldValue);
      console.log("Watch new value: ", newValue);
    },
  },
};
</script>

```

#### WatchAPIRef.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIRef">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIRef"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIRef">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIRef"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { ref, watch } from "vue";
export default {
  name: "WatchAPIRef",
  //
  setup() {
    const firstName = ref("Klaus");
    const lastName = ref("Fischer");
    //
    watch(firstName, (newValue, oldValue) => {
      console.log("WatchAPIRef firstName old value: ", oldValue);
      console.log("WatchAPIRef firstName new value: ", newValue);
    });
    //
    watch(lastName, (newValue, oldValue) => {
      console.log("WatchAPIRef lastName old value: ", oldValue);
      console.log("WatchAPIRef lastName new value: ", newValue);
    });
    //
    return {
      firstName,
      lastName
    };
  }
};
</script>
```

#### WatchAPIReactive.vue (Child)
```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIReactive">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIReactive"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIReactive">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIReactive"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { reactive, toRefs, watch } from "vue";
export default {
  name: "WatchAPIReactive",
  //
  setup() {
    const state = reactive({
      firstName: "Uwe",
      lastName: "Seeler",
    });
    //
    watch(
      state,
      function (newValue, oldValue)  {
        console.log("WatchAPIReactive firstName old value: ", oldValue.firstName);
        console.log("WatchAPIReactive firstName new values: ", newValue.firstName);
        console.log("WatchAPIReactive lastName old value: ", oldValue.lastName);
        console.log("WatchAPIReactive lastName new values: ", newValue.lastName);
      },
    );
    //
    return {
      ...toRefs(state),
    };
  },
};
</script>
```

#### WatchAPIRefV2.vue (Child)
Um diese Variante von WatchAPIRef zu verwenden, ersetze in der App.vue  

    import WatchAPIRef from "./components/api/WatchAPIRef";

durch

    import WatchAPIRef from "./components/api/WatchAPIRefV2";

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIRef">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIRef"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIRef">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIRef"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { ref, watch } from "vue";
export default {
  name: "WatchAPIRef",
  //
  setup() {
    const firstName = ref("Klaus");
    const lastName = ref("Fischer");
    //
    watch(
      [firstName, lastName],
      (newValues, oldValues) => {
        console.log("WatchAPIRefV2 firstName old value: ", oldValues[0]);
        console.log("WatchAPIRefV2 firstName new value: ", newValues[0]);
        console.log("WatchAPIRefV2 lastName old value: ", oldValues[1]);
        console.log("WatchAPIRefV2 lastName new value: ", newValues[1]);
      },
      {
        immediate: false,
      }
    );
    //
    return {
      firstName,
      lastName,
    };
  },
};
</script>
```

#### WatchAPIReactiveV2.vue (Child)
Um diese Variante von WatchAPIReactive zu verwenden, ersetze in der App.vue  

    import WatchAPIRef from "./components/api/WatchAPIReactive";

durch

    import WatchAPIReactive from "./components/api/WatchAPIRReactiveV2";

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIReactive">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIReactive"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIReactive">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIReactive"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { reactive, toRefs, watch } from "vue";
export default {
  name: "WatchAPIReactiveV2",
  //
  setup() {
    const state = reactive({
      firstName: "Uwe",
      lastName: "Seeler",
    });
    //
    watch(
      () => {
        return { ...state }
      },
      function (newValue, oldValue)  {
        console.log("WatchAPIReactive firstName old value: ", oldValue.firstName);
        console.log("WatchAPIReactive firstName new values: ", newValue.firstName);
        console.log("WatchAPIReactive lastName old value: ", oldValue.lastName);
        console.log("WatchAPIReactive lastName new values: ", newValue.lastName);
      },
    );
    //
    return {
      ...toRefs(state),
    };
  },
};
</script>
```

#### WatchAPIReactiveV3.vue (Child)
Um diese Variante von WatchAPIReactive zu verwenden, ersetze in der App.vue  

    import WatchAPIRef from "./components/api/WatchAPIReactive";

durch

    import WatchAPIReactive from "./components/api/WatchAPIRReactiveV3";

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIReactive">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIReactive"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIReactive">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIReactive"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { reactive, toRefs, watch } from "vue";
export default {
  name: "WatchAPIReactiveV3",
  //
  setup() {
    const state = reactive({
      firstName: "Uwe",
      lastName: "Seeler",
    });
    //
    watch(
      () => state.firstName,
      function(newValue, oldValue) {
        console.log(
          "WatchAPIReactive firstName old value: ",
          oldValue
        );
        console.log(
          "WatchAPIReactive firstName new values: ",
          newValue
        );
      }
    );
    //
    return {
      ...toRefs(state),
    };
  },
};
</script>
```


#### WatchAPIReactiveV4.vue (Child)
Um diese Variante von WatchAPIReactive zu verwenden, ersetze in der App.vue  

    import WatchAPIRef from "./components/api/WatchAPIReactive";

durch

    import WatchAPIReactive from "./components/api/WatchAPIRReactiveV4";

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIReactive">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIReactive"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIReactive">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIReactive"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="offensiveAPIReactive">
        <span class="label-text">Offensivfähigkeit</span>
      </label>
      <input
        type="text"
        id="offensiveAPIReactive"
        v-model.number="skills.offensive"
        placeholder="Offensivfähigkeit"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import { reactive, toRefs, watch } from "vue";
export default {
  name: "WatchAPIReactiveV4",
  //
  setup() {
    const state = reactive({
      firstName: "Uwe",
      lastName: "Seeler",
      skills: {
        offensive: 9,
      },
    });
    //
    watch(
      () => state.skills,
      function(newValue, oldValue) {
        console.log(
          "WatchAPIReactive state.skills old value: ",
          oldValue
        );
        console.log(
          "WatchAPIReactive state.skills new values: ",
          newValue
        );
      },
      {
        deep: true
      }
    );
    //
    return {
      ...toRefs(state),
    };
  },
};
</script>
```

#### WatchAPIReactiveV5.vue (Child)
Um diese Variante von WatchAPIReactive zu verwenden, ersetze in der App.vue  

    import WatchAPIRef from "./components/api/WatchAPIReactive";

durch

    import WatchAPIReactive from "./components/api/WatchAPIRReactiveV5";

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstNameAPIReactive">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        id="firstNameAPIReactive"
        v-model="firstName"
        placeholder="Vorname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="lastNameAPIReactive">
        <span class="label-text">Nachname</span>
      </label>
      <input
        type="text"
        id="lastNameAPIReactive"
        v-model="lastName"
        placeholder="Nachname"
        class="input input-bordered"
      />
    </div>
    <div class="form-control w-1/2 px-2">
      <label class="label" for="offensiveAPIReactive">
        <span class="label-text">Offensivfähigkeit</span>
      </label>
      <input
        type="text"
        id="offensiveAPIReactive"
        v-model.number="skills.offensive"
        placeholder="Offensivfähigkeit"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
import _ from 'lodash'
import { reactive, toRefs, watch } from "vue";
export default {
  name: "WatchAPIReactiveV5",
  //
  setup() {
    const state = reactive({
      firstName: "Uwe",
      lastName: "Seeler",
      skills: {
        offensive: 9,
      },
    });
    //
    watch(
      () => _.cloneDeep(state.skills),
      function(newValue, oldValue) {
        console.log(
          "WatchAPIReactive state.skills old value: ",
          oldValue
        );
        console.log(
          "WatchAPIReactive state.skills new values: ",
          newValue
        );
      },
      {
        deep: true
      }
    );
    //
    return {
      ...toRefs(state),
    };
  },
};
</script>
```





## 

### x. Beispiel

#### App.vue (Parent)

```js

```

#### X.vue (Child)

```js

```

#### X.vue (Child)

```js

```

#### X.vue (Child)

```js

```
