# Components

## Our first child

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Our first child
      </h1>
      <Hallo />
    </div>
  </div>
</template>
<script>
import Willkommen from './components/Willkommen.vue';
export default {
  name: "App",
  //
  components: {
    Hallo: Willkommen
  }
};
</script>
```

#### Willkommen.vue (Child)

```js
<template>
  <h2>
    Herzlich Willkommen!
  </h2>
</template>
<script>
export default {
  name: "Willkommen",
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Our first child
      </h1>
      <Hallo first-name="Klaus" />
    </div>
  </div>
</template>
<script>
import Willkommen from './components/WillkommenProp.vue';
export default {
  name: "App",
  //
  components: {
    Hallo: Willkommen
  }
};
</script>
```

#### WillkommenProp.vue (Child)

```js
<template>
  <h2>
    Herzlich Willkommen {{ firstName }}!
  </h2>
</template>
<script>
export default {
  name: "WillkommenProp",
  //
  props: {
    firstName: {
      type: String,
    },
  },
};
</script>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Our first child
      </h1>
      <Willkommen v-bind:firstName="userName" />
    </div>
  </div>
</template>
<script>
import Willkommen from './components/WillkommenProp.vue';
export default {
  name: "App",
  //
  components: {
    Willkommen
  },
  //
  data() {
    return {
      userName: 'Annalena'
    }
  }
};
</script>
```

#### WillkommenProp.vue (Child)

```js
<template>
  <h2>
    Herzlich Willkommen {{ firstName }}!
  </h2>
</template>
<script>
export default {
  name: "WillkommenProp",
  //
  props: {
    firstName: {
      type: String,
    },
  },
};
</script>
```

## Prop Types and Validations

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Prop Types and Validations
      </h1>
      <Spielbericht
        home-team="FC Schalke 04"
        guest-team="Borussia Dortmung"
        spectators="70000"
        is-published="true"
      />
    </div>
  </div>
</template>
<script>
import Spielbericht from "./components/Spielbericht.vue";
export default {
  name: "App",
  //
  components: {
    Spielbericht,
  },
};
</script>
```

#### Spielberricht.vue (Child)

```js
<template>
  <div>
    <h2>Spielbericht</h2>
    <h3>{{ homeTeam }} gegen {{ guestTeam }}</h3>
    <h4>Zuschauer: {{ spectators }}</h4>
    <div>
      Wurde dieser Spielbericht veröffentlicht:
      {{ isPublished ? "Ja" : "Nein" }}
    </div>
  </div>
</template>
<script>
export default {
  name: "Spielbericht",
  //
  props: {
    homeTeam: {
      type: String,
      required: true,
    },
    guestTeam: {
      type: String,
      required: true,
    },
    spectators: {
      type: Number,
      default: 0,
    },
    isPublished: {
      type: Boolean,
      default: false,
    },
  },
};
</script>
```

## Non-Prop Attributes

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Prop Types and Validations
      </h1>
      <Spielbericht
        id="1904"
      />
    </div>
  </div>
</template>
<script>
import Spielbericht from "./components/SpielberichtNonProp.vue";
export default {
  name: "App",
  //
  components: {
    Spielbericht,
  },
};
</script>
```

#### SpielberichtNonProp.vue (Child)

```js
<template>
  <div>
    <h2>Spielbericht</h2>
  </div>
</template>
<script>
export default {
  name: "SpielberichtNonProp",
  //
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Prop Types and Validations
      </h1>
      <Spielbericht
        id="1904"
      />
    </div>
  </div>
</template>
<script>
import Spielbericht from "./components/SpielberichtNonPropWithoutRoot.vue";
export default {
  name: "App",
  //
  components: {
    Spielbericht,
  },
};
</script>
```

#### SpielberichtNonPropWithoutRoot.vue (Child)

```js
<template>
  <h2>Spielbericht</h2>
  <div>Dies ist eine Child-Komponente ohne Root-Element!</div>
</template>
<script>
export default {
  name: "SpielberichtNonPropWithoutRoot",
  //
};
</script>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Prop Types and Validations
      </h1>
      <Spielbericht
        id="1904"
      />
    </div>
  </div>
</template>
<script>
import Spielbericht from "./components/SpielberichtNonPropAttrs.vue";
export default {
  name: "App",
  //
  components: {
    Spielbericht,
  },
};
</script>
```

#### SpielberichtNonPropsAttrs.vue (Child)

```js
<template>
  <h2>Spielbericht</h2>
  <div v-bind="$attrs">Dies ist eine Child-Komponente ohne Root-Element!</div>
</template>
<script>
export default {
  name: "SpielberichtNonPropAttrs",
  //
};
</script>
```

### 4. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Prop Types and Validations
      </h1>
      <Spielbericht
        id="1904"
      />
    </div>
  </div>
</template>
<script>
import Spielbericht from "./components/SpielberichtNonPropAttrsWithRoot.vue";
export default {
  name: "App",
  //
  components: {
    Spielbericht,
  },
};
</script>
```

#### SpielberichtNonPropAttrsWithRoot.vue (Child)

```js
<template>
  <div>
    <h2>Spielbericht</h2>
    <div v-bind="$attrs">Dies ist eine Child-Komponente mit Root-Element!</div>
  </div>
</template>
<script>
export default {
  name: "SpielberichtNonPropAttrsWithRoot",
  //
};
</script>
```

### 5. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Prop Types and Validations
      </h1>
      <Spielbericht
        id="1904"
      />
    </div>
  </div>
</template>
<script>
import Spielbericht from "./components/SpielberichtNonPropAttrsWithRootInherit.vue";
export default {
  name: "App",
  //
  components: {
    Spielbericht,
  },
};
</script>
```

#### SpielberichtNonPropAttrsWithRootInherit.vue (Child)

```js
<template>
  <div>
    <h2>Spielbericht</h2>
    <div v-bind="$attrs">Dies ist eine Child-Komponente mit Root-Element!</div>
  </div>
</template>
<script>
export default {
  name: "SpielberichtNonPropAttrsWithRootInherit",
  //
  inheritAttrs: false,
};
</script>
```

## Provide and Inject

### 1. Beispiel

#### App.vue (Parent)

```js

```

#### Inject.vue (Child)

```js
<template>
    <div>
        {{ userName }}
    </div>
</template>
<script>
    export default {
        name: "Inject",
        //
        inject: [
            'userName'
        ]
    }
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Provide & Inject
      </h1>
      <Inject />
      <div>App.vue: {{ userName }}</div>
    </div>
  </div>
</template>
<script>
import Inject from "./components/Inject.vue";
export default {
  name: "App",
  //
  components: {
    Inject,
  },
  //
  provide: {
    userName: "Klaus Fichtel",
  },
};
</script>
```

#### Inject.vue (Child)

```js
<template>
    <div>
        {{ userName }}
    </div>
</template>
<script>
    export default {
        name: "Inject",
        //
        inject: [
            'userName'
        ]
    }
</script>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Provide & Inject
      </h1>
      <Inject />
      <div>App.vue: {{ name }}</div>
    </div>
  </div>
</template>
<script>
import Inject from './components/Inject.vue';
export default {
  name: "App",
  //
  components: {
    Inject
  },
  //
  data() {
    return {
      name: 'Klaus Fichtel'
    }
  },
  //
  provide: {
    userName: this.name
  }
};
</script>
```

#### Inject.vue (Child)

```js
<template>
    <div>
        {{ userName }}
    </div>
</template>
<script>
    export default {
        name: "Inject",
        //
        inject: [
            'userName'
        ]
    }
</script>
```

### 4. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Provide & Inject
      </h1>
      <Inject />
      <div>App.vue: {{ name }}</div>
    </div>
  </div>
</template>
<script>
import Inject from "./components/Inject.vue";
export default {
  name: "App",
  //
  components: {
    Inject,
  },
  //
  data() {
    return {
      name: "Klaus Fichtel",
    };
  },
  //
  provide() {
    return {
      userName: this.name,
    };
  },
};
</script>
```

#### Inject.vue (Child)

```js
<template>
    <div>
        {{ userName }}
    </div>
</template>
<script>
    export default {
        name: "Inject",
        //
        inject: [
            'userName'
        ]
    }
</script>
```

## Custom Component Events

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Custom Component Events
      </h1>
      <button class="btn btn-sm btn-primary" v-on:click="isVisible = true">Popup öffnen</button>
      <Popup v-show="isVisible" />
    </div>
  </div>
</template>
<script>
import Popup from "./components/Popup.vue";
export default {
  name: "App",
  //
  components: {
    Popup,
  },
  //
  data() {
    return {
      isVisible: false,
    };
  },
};
</script>
```

#### Popup.vue (Child)

```js
<template>
  <div>
    <h2>Popup.vue</h2>
    <button class="btn btn-sm btn-secondary">Popup schließen</button>
  </div>
</template>
<script>
export default {
  name: "Popup,",
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Custom Component Events
      </h1>
      <button class="btn btn-sm btn-primary" v-on:click="isVisible = true">
        Popup öffnen
      </button>
      <Popup v-show="isVisible" v-on:close="isVisible = false" />
    </div>
  </div>
</template>
<script>
import Popup from "./components/PopupWithEmit.vue";
export default {
  name: "App",
  //
  components: {
    Popup,
  },
  //
  data() {
    return {
      isVisible: false,
    };
  },
};
</script>
```

#### PopupWithEmit.vue (Child)

```js
<template>
  <div>
    <h2>Popup.vue</h2>
    <div class="mt-8">
      <button class="btn btn-sm btn-secondary" v-on:click="$emit('close')">
        Popup schließen
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "PopupWithEmit,",
  //
  emits: ["close"],
};
</script>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Custom Component Events
      </h1>
      <button class="btn btn-sm btn-primary" v-on:click="isVisible = true">
        Popup öffnen
      </button>
      <Popup v-show="isVisible" v-on:close="closePopup" />
    </div>
  </div>
</template>
<script>
import Popup from "./components/PopupWithEmitAndData.vue";
export default {
  name: "App",
  //
  components: {
    Popup,
  },
  //
  data() {
    return {
      isVisible: false,
    };
  },
  //
  methods: {
    closePopup(name) {
      this.isVisible = false;
      console.log("name is: ", name);
    },
  },
};
</script>
```

#### PopupWithEmitAndData.vue (Child)

```js
<template>
  <div>
    <h2>Popup.vue</h2>
    <button
      class="btn btn-sm btn-secondary"
      v-on:click="$emit('close', 'Klaus Fichtel')"
    >
      Popup schließen
    </button>
  </div>
</template>
<script>
export default {
  name: "PopupWithEmitAndData,",
  //
  emits: ["close"],
};
</script>
```

## Validating Component Events

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Custom Component Events
      </h1>
      <button class="btn btn-sm btn-primary" v-on:click="isVisible = true">
        Popup öffnen
      </button>
      <Popup v-show="isVisible" v-on:close="closePopup" />
    </div>
  </div>
</template>
<script>
import Popup from "./components/PopupValidatingEvent.vue";
export default {
  name: "App",
  //
  components: {
    Popup,
  },
  //
  data() {
    return {
      isVisible: false,
    };
  },
  //
  methods: {
    closePopup(name) {
      this.isVisible = false;
      console.log("name is: ", name);
    },
  },
};
</script>
```

#### PopupValidatingEvent.vue (Child)

```js
<template>
  <div>
    <h2>Popup.vue</h2>
    <div class="form-control px-2">
      <label class="label" for="firstName">
        <span class="label-text">Name</span>
      </label>
      <input
        type="text"
        id="name"
        v-model="name"
        placeholder="Name"
        class="input input-bordered"
      />
    </div>
    <button
      class="mt-8 btn btn-sm btn-secondary"
      v-on:click="$emit('close', name)"
    >
      Popup schließen
    </button>
  </div>
</template>
<script>
export default {
  name: "PopupValidatingEvent,",
  //
  data() {
    return {
      name: "",
    };
  },
  //
  emits: {
    close: (name) => {
      if (!name) {
        return false;
      } else {
        return true;
      }
    },
  },
};
</script>
```

## Components and v-model

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Components and v-model
      </h1>
      <Input v-model="name" />
      <div class="mt-8">
        eingegeben wurde: {{ name }}
      </div>
    </div>
  </div>
</template>
<script>
import Input from "./components/Input.vue";
export default {
  name: "App",
  //
  components: {
    Input,
  },
  //
  data() {
    return {
      name: "",
    };
  }
};
</script>
```

#### Input.vue (Child)

```js
<template>
  <input type="text" class="input input-bordered" />
</template>
<script>
export default {
  name: "Input",
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Components and v-model
      </h1>
      <Input v-model="name" />
      <div class="mt-8">
        eingegeben wurde: {{ name }}
      </div>
    </div>
  </div>
</template>
<script>
import Input from "./components/InputVModel.vue";
export default {
  name: "App",
  //
  components: {
    Input,
  },
  //
  data() {
    return {
      name: "",
    };
  }
};
</script>
```

#### InputVModel.vue (Child)

```js
<template>
  <input
    type="text"
    v-bind:value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
    class="input input-bordered"
  />
</template>
<script>
export default {
  name: "InputVModel",
  //
  props: {
    modelValue: String,
  },
};
</script>
```

## Slots

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Slots
      </h1>
    </div>
    <div class="mt-4">
      <Card
        title="Schalke 04"
        body="Fussballverein"
        :action-on="true"
        member-link="https://schalke04.de/"
        web-link="https://schalke04.de/"
      />
    </div>
    <div class="mt-4">
      <Card
        title="BVB 09"
        body="Fussballverein"
        :action-on="true"
        member-link="https://www.bvb.de/"
        web-link="https://www.bvb.de/"
      />
    </div>
  </div>
</template>
<script>
import Card from "./components/Card.vue";
export default {
  name: "App",
  //
  components: {
    Card,
  },
};
</script>
```

#### Card.vue (Child)

```js
<template>
  <div class="card border-2 border-gray-100">
    <div class="card-body">
      <div class="card-title">
        {{ title }}
      </div>
      <div>
        {{ body }}
      </div>
      <div class="card-actions" v-if="actionOn">
        <a class="link link-primary" v-bind:href="memberLink" target="_blank"
          >Mitglied werden</a
        >
        <a class="link link-secondary" v-bind:href="webLink" target="_blank"
          >zur Webseite</a
        >
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  //
  props: {
    title: {
      type: String,
    },
    body: {
      type: String,
    },
    actionOn: {
      type: Boolean,
      default: false,
    },
    memberLink: {
      type: String,
    },
    webLink: {
      type: String,
    },
  },
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Slots
      </h1>
    </div>
    <div class="mt-4">
      <Card title="Schalke 04" body="Fussballverein">
        <a
          class="link link-primary"
          href="https://schalke04.de/"
          target="_blank"
          >Mitglied werden</a
        >
        <a
          class="link link-secondary"
          href="https://schalke04.de/"
          target="_blank"
          >zur Webseite</a
        >
      </Card>
    </div>
    <div class="mt-4">
      <Card title="BVB 09" body="Fussballverein">
        <a class="link link-primary" href="https://www.bvb.de/" target="_blank"
          >Mitglied werden</a
        >
        <a
          class="link link-secondary"
          href="https://www.bvb.de/"
          target="_blank"
          >zur Webseite</a
        >
      </Card>
    </div>
    <div class="mt-4">
      <Card title="Vue" body="JavaScript-Framework">
        <img src="./assets/logo.png" />
      </Card>
    </div>
  </div>
</template>
<script>
import Card from "./components/CardSlot.vue";
export default {
  name: "App",
  //
  components: {
    Card,
  },
};
</script>
```

#### CardSlot.vue (Child)

```js
<template>
  <div class="card border-2 border-gray-100">
    <div class="card-body">
      <div class="card-title">
        {{ title }}
      </div>
      <div>
        {{ body }}
      </div>
      <div class="card-actions">
          <slot></slot>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Card",
  //
  props: {
    title: {
      type: String,
    },
    body: {
      type: String,
    },
  },
};
</script>
```

## Named Slots

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Slots
      </h1>
    </div>
    <div class="mt-4">
      <Card title="Schalke 04">
        <template v-slot:body>
          Fussballverein
        </template>
        <template v-slot:default>
          <a
            class="link link-primary"
            href="https://schalke04.de/"
            target="_blank"
            >Mitglied werden</a
          >
          <a
            class="link link-secondary"
            href="https://schalke04.de/"
            target="_blank"
            >zur Webseite</a
          >
        </template>
      </Card>
    </div>
    <div class="mt-4">
      <Card title="BVB 09">
        <template v-slot:body>
          Fussballverein
        </template>
        <template v-slot:default>
          <a
            class="link link-primary"
            href="https://www.bvb.de/"
            target="_blank"
            >Mitglied werden</a
          >
          <a
            class="link link-secondary"
            href="https://www.bvb.de/"
            target="_blank"
            >zur Webseite</a
          >
        </template>
      </Card>
    </div>
    <div class="mt-4">
      <Card title="Vue">
        <template v-slot:body>
          JavaScript-Framework
        </template>
        <template v-slot:default>
          <img src="./assets/logo.png" class="h-12 mx-auto" />
        </template>
      </Card>
    </div>
  </div>
</template>
<script>
import Card from "./components/CardNamedSlots.vue";
export default {
  name: "App",
  //
  components: {
    Card,
  },
};
</script>
```

#### CardNamedSlots.vue (Child)

```js
<template>
  <div class="card border-2 border-gray-100">
    <div class="card-body">
      <div class="card-title">
        {{ title }}
      </div>
      <div>
        <slot name="body"></slot>
      </div>
      <div class="card-actions">
        <slot></slot>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "CardNamedSlots",
  //
  props: {
    title: {
      type: String,
    },
  },
};
</script>
```

### 2. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Slots
      </h1>
    </div>
    <div class="mt-4">
      <div class="card border-2 border-gray-100">
        <div class="card-body">
          <div class="card-title">
            Schalke 04
          </div>
          <div>
            Fussballverein
          </div>
          <div class="card-actions">
            <a
              class="link link-primary"
              href="https://schalke04.de/"
              target="_blank"
              >Mitglied werden</a
            >
            <a
              class="link link-secondary"
              href="https://schalke04.de/"
              target="_blank"
              >zur Webseite</a
            >
          </div>
        </div>
      </div>
      <div class="card border-2 border-gray-100">
        <div class="card-body">
          <div class="card-title">
            BVB 09
          </div>
          <div>
            Fussballverein
          </div>
          <div class="card-actions">
            <a
              class="link link-primary"
              href="https://schalke04.de/"
              target="_blank"
              >Mitglied werden</a
            >
            <a
              class="link link-secondary"
              href="https://schalke04.de/"
              target="_blank"
              >zur Webseite</a
            >
          </div>
        </div>
      </div>
    </div>
    <div class="mt-4">
      <div class="card border-2 border-gray-100">
        <div class="card-body">
          <div class="card-title">
            Vue
          </div>
          <div>
            JavaScript-Framework
          </div>
          <div class="card-actions">
            <img src="./assets/logo.png" class="h-12 mx-auto" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
};
</script>
```

## Slot Props

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Slots Props
      </h1>
    </div>
    <div class="mt-8">
      <PlayersList />
    </div>
  </div>
</template>
<script>
import PlayersList from "./components/PlayersList";
export default {
  name: "App",
  //
  components: {
    PlayersList,
  },
};
</script>
```

#### PlayersList.vue (Child)

```js
<template>
  <h3 v-for="player in players" :key="player.lastName">
      {{ player.firstName }} {{ player.lastName }} ({{ player.age }})
  </h3>
</template>

<script>
export default {
  name: "PlayersList",
  //
  data() {
    return {
      players: [
        {
          firstName: "Klaus",
          lastName: "Fischer",
          age: 21
        },
        {
          firstName: "Klaus",
          lastName: "Fichtel",
          age: 22
        },
        {
          firstName: "Norbert",
          lastName: "Nigbur",
          age: 23
        },
      ],
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
    <div class="prose text-center">
      <h1>
        Slots Props
      </h1>
    </div>
    <div class="mt-8">
      <PlayersList>
        <template v-slot:default="slotProps">
          {{ slotProps.firstName }} {{ slotProps.lastName }} ({{ slotProps.age }})
        </template>
      </PlayersList>
    </div>
  </div>
</template>
<script>
import PlayersList from "./components/PlayersListSlots";
export default {
  name: "App",
  //
  components: {
    PlayersList,
  },
};
</script>
```

#### PlayersListSlot.vue (Child)

```js
<template>
  <h3 v-for="player in players" :key="player.lastName">
      <slot v-bind:firstName="player.firstName" v-bind:lastName="player.lastName" v-bind:age="player.age"></slot>
  </h3>
</template>

<script>
export default {
  name: "PlayersList",
  //
  data() {
    return {
      players: [
        {
          firstName: "Klaus",
          lastName: "Fischer",
          age: 21
        },
        {
          firstName: "Klaus",
          lastName: "Fichtel",
          age: 22
        },
        {
          firstName: "Norbert",
          lastName: "Nigbur",
          age: 23
        },
      ],
    };
  },
};
</script>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center">
      <h1>
        Slots Props
      </h1>
    </div>
    <div class="mt-8">
      <PlayersList>
        <template v-slot:default="listOfPlayers">
          {{ listOfPlayers.player.firstName }}
          {{ listOfPlayers.player.lastName }} ({{ listOfPlayers.player.age }})
        </template>
      </PlayersList>
    </div>
  </div>
</template>
<script>
import PlayersList from "./components/PlayersListObject";
export default {
  name: "App",
  //
  components: {
    PlayersList,
  },
};
</script>
```

#### PlayersListObject.vue (Child)

```js
<template>
  <h3 v-for="player in players" :key="player.lastName">
      <slot v-bind:player="player"></slot>
  </h3>
</template>

<script>
export default {
  name: "PlayersList",
  //
  data() {
    return {
      players: [
        {
          firstName: "Klaus",
          lastName: "Fischer",
          age: 21
        },
        {
          firstName: "Klaus",
          lastName: "Fichtel",
          age: 22
        },
        {
          firstName: "Norbert",
          lastName: "Nigbur",
          age: 23
        },
      ],
    };
  },
};
</script>
```

## Component Styles

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Component Styles
      </h1>
    </div>
    <h4>Title of App.vue</h4>
    <Styles />
  </div>
</template>
<script>
import Styles from "./components/Styles";
export default {
  name: "App",
  //
  components: {
    Styles,
  },
};
</script>
<style>
h4 {
  color: orange;
  font-size: 1.4rem;
}
</style>
```

#### Styles.vue (Child)

```js
<template>
  <div>
    <h4>
      Title of Styles.vue
    </h4>
  </div>
</template>
<script>
export default {
  name: "Styles",
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
        Component Styles
      </h1>
    </div>
    <h4>Title of App.vue</h4>
    <Styles />
  </div>
</template>
<script>
import Styles from "./components/StylesV2";
export default {
  name: "App",
  //
  components: {
    Styles,
  },
};
</script>
<style>
h4 {
  color: orange;
  font-size: 1.4rem;
}
</style>
```

#### StylesV2.vue (Child)

```js
<template>
  <div>
    <h4>
      Title of Styles.vue
    </h4>
  </div>
</template>
<script>
export default {
  name: "StylesV2",
};
</script>
<style>
h4 {
  color: red;
}
</style>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Component Styles
      </h1>
    </div>
    <h4>Title of App.vue</h4>
    <Styles />
  </div>
</template>
<script>
import Styles from "./components/StylesV3";
export default {
  name: "App",
  //
  components: {
    Styles,
  },
};
</script>
<style>
h4 {
  color: orange;
  font-size: 1.4rem;
}
</style>
```

#### StylesV3.vue (Child)

```js
<template>
  <div>
    <h4>
      Title of Styles.vue
    </h4>
  </div>
</template>
<script>
export default {
  name: "StylesV3",
};
</script>
<style scoped>
h4 {
  color: red;
}
</style>
```

### 4. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Component Styles
      </h1>
    </div>
    <h4>Title of App.vue</h4>
    <Styles />
  </div>
</template>
<script>
import Styles from "./components/StylesV4";
export default {
  name: "App",
  //
  components: {
    Styles,
  },
};
</script>
<style scoped>
h4 {
  color: orange;
  font-size: 1.4rem;
}
</style>
```

#### StylesV5.vue (Child)

```js
<template>
  <h4>
    Title of Styles.vue
  </h4>
</template>
<script>
export default {
  name: "StylesV4",
};
</script>
<style scoped>
h4 {
  color: red;
}
</style>
```

### 5. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Component Styles
      </h1>
    </div>
    <h4>Title of App.vue</h4>
    <Styles>
      <h4>
        Child Styles Title
      </h4>
    </Styles>
  </div>
</template>
<script>
import Styles from "./components/StylesV5";
export default {
  name: "App",
  //
  components: {
    Styles,
  },
};
</script>
<style scoped>
h4 {
  color: orange;
  font-size: 1.4rem;
}
</style>
```

#### StylesV5.vue (Child)

```js
<template>
  <h4>
    Title of Styles.vue
  </h4>
</template>
<script>
export default {
  name: "StylesV5",
};
</script>
<style scoped>
h4 {
  color: red;
}
</style>
```

## Dynamic Components

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Dynamic Components
      </h1>
    </div>
    <div class="tabs tabs-boxed">
      <button
        v-on:click="tabActive = 'TabA'"
        class="tab"
        v-bind:class="{ 'tab-active': tabActive === 'TabA' }"
      >
        A
      </button>
      <button
        v-on:click="tabActive = 'TabB'"
        class="tab"
        v-bind:class="{ 'tab-active': tabActive === 'TabB' }"
      >
        B
      </button>
      <button
        v-on:click="tabActive = 'TabC'"
        class="tab"
        v-bind:class="{ 'tab-active': tabActive === 'TabC' }"
      >
        C
      </button>
    </div>
    <div class="mt-8 p-4 shadow-lg">
      <TabA v-if="tabActive === 'TabA'" />
      <TabB v-if="tabActive === 'TabB'" />
      <TabC v-if="tabActive === 'TabC'" />
    </div>
  </div>
</template>
<script>
import TabA from "./components/TabA";
import TabB from "./components/TabB";
import TabC from "./components/TabC";
export default {
  name: "App",
  //
  data() {
    return {
      tabActive: "TabA",
    };
  },
  //
  components: {
    TabA,
    TabB,
    TabC,
  },
};
</script>
```

#### TabA.vue (Child)

```js
<template>
  <div>
    Child TabA: Here is the content.
  </div>
</template>
<script>
export default {
  name: "TabA",
};
</script>
```

#### TabB.vue (Child)

```js
<template>
  <div>
    Child TabB: Here is the content.
  </div>
</template>
<script>
export default {
  name: "TabB",
};
</script>
```

#### TabC.vue (Child)

```js
<template>
  <div>
    Child TabC: Here is the content.
  </div>
</template>
<script>
export default {
  name: "TabC",
};
</script>
```

## Keep Alive

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Dynamic Components
      </h1>
    </div>
    <div class="tabs tabs-boxed">
      <button
        v-on:click="tabActive = 'TabA'"
        class="tab"
        v-bind:class="{ 'tab-active': tabActive === 'TabA' }"
      >
        A
      </button>
      <button
        v-on:click="tabActive = 'TabB'"
        class="tab"
        v-bind:class="{ 'tab-active': tabActive === 'TabB' }"
      >
        B
      </button>
      <button
        v-on:click="tabActive = 'TabC'"
        class="tab"
        v-bind:class="{ 'tab-active': tabActive === 'TabC' }"
      >
        C
      </button>
    </div>
    <div class="mt-8 p-4 shadow-lg">
      <keep-alive>
        <component v-bind:is="tabActive" />
      </keep-alive>
    </div>
  </div>
</template>
<script>
import TabA from "./components/TabA";
import TabB from "./components/TabB";
import TabC from "./components/TabCKeepAlive";
export default {
  name: "App",
  //
  data() {
    return {
      tabActive: "TabA",
    };
  },
  //
  components: {
    TabA,
    TabB,
    TabC,
  },
};
</script>
```

#### TabA.vue (Child)

```js
<template>
  <div>
    Child TabA: Here is the content.
  </div>
</template>
<script>
export default {
  name: "TabA",
};
</script>
```

#### TabB.vue (Child)

```js
<template>
  <div>
    Child TabB: Here is the content.
  </div>
</template>
<script>
export default {
  name: "TabB",
};
</script>
```

#### TabC.vue (Child)

```js
<template>
  <div>
    Child TabC: Here is the content.
    <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
      <div class="form-control px-2">
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
    </div>
  </div>
</template>
<script>
export default {
  name: "TabCKeepAlive",
  //
  data() {
    return {
      firstName: "",
    };
  },
};
</script>
```

## Teleport

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Teleport
      </h1>
    </div>
    <div class="mt-8 p-4 shadow-lg">
      <Portal />
    </div>
  </div>
</template>
<script>
import Portal from "./components/Portal";
export default {
  name: "App",
  //
  components: {
    Portal,
  },
};
</script>
```

#### Portal.vue (Child)

```js
<template>
  <div>
    Hallo, ich wurde gebeamt, oder?
  </div>
</template>
<script>
export default {
  name: "Portal",
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
        Teleport
      </h1>
    </div>
    <div class="mt-8 p-4 shadow-lg">
      <teleport to="#portal">
        <Portal />
      </teleport>
    </div>
  </div>
</template>
<script>
import Portal from "./components/Portal";
export default {
  name: "App",
  //
  components: {
    Portal,
  },
};
</script>
```

#### Portal.vue (Child)

```js
<template>
  <div>
    Hallo, ich wurde gebeamt, oder?
  </div>
</template>
<script>
export default {
  name: "Portal",
};
</script>
```

## HTTP Get

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        HTTP
      </h1>
    </div>
    <div class="mt-8">
      <BlogList />
    </div>
  </div>
</template>
<script>
import BlogList from "./components/BlogList";
export default {
  name: "App",
  //
  components: {
    BlogList,
  },
};
</script>
```

#### BlogList.vue (Child)

```js
<template>
  <div>
    <div class="text-center">
      <button class="btn btn-sm" v-on:click="getBlogs">
        Lade die Blog-Artikel
      </button>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "BlogList",
  //
  data() {
    return {
      blogs: [],
    };
  },
  //
  methods: {
    getBlogs() {
      axios
        .get("https://jsonplaceholder.typicode.com/blogs")
        .then((response) => {
          console.log("response: ", response.data);
        })
        .catch((error) => {
          console.log("error: ", error);
        });
    },
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
        HTTP
      </h1>
    </div>
    <div class="mt-8">
      <BlogList />
    </div>
  </div>
</template>
<script>
import BlogList from "./components/BlogListShowData";
export default {
  name: "App",
  //
  components: {
    BlogList,
  },
};
</script>
```

#### BlogListShowData.vue (Child)

```js
<template>
  <div>
    <div
      v-for="blog in blogs"
      :key="blog.id"
      class="my-2 card bg-gray-200 text-gray-900"
    >
      <div class="card-body">
        <h2 class="card-title">{{ blog.title }}</h2>
        {{ blog.body }}
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "BlogListShowData",
  //
  created() {
    this.getBlogs();
  },
  //
  data() {
    return {
      blogs: [],
    };
  },
  //
  methods: {
    getBlogs() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((response) => {
          console.log("response: ", response.data);
          this.blogs = response.data;
        })
        .catch((error) => {
          console.log("error: ", error);
        });
    },
  },
};
</script>
```

## HTTP Post

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        HTTP
      </h1>
    </div>
    <div class="mt-8">
      <BlogList />
    </div>
    <div class="mt-8">
      <BlogCreate />
    </div>
  </div>
</template>
<script>
import BlogList from "./components/BlogList";
import BlogCreate from "./components/BlogCreate";
export default {
  name: "App",
  //
  components: {
    BlogList,
    BlogCreate
  },
};
</script>
```

#### BlogList.vue (Child)

```js
<template>
  <div>
    <div class="text-center">
      <button class="btn btn-sm" v-on:click="getBlogs">
        Lade die Blog-Artikel
      </button>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "BlogList",
  //
  data() {
    return {
      blogs: [],
    };
  },
  //
  methods: {
    getBlogs() {
      axios
        .get("https://jsonplaceholder.typicode.com/blogs")
        .then((response) => {
          console.log("response: ", response.data);
        })
        .catch((error) => {
          console.log("error: ", error);
        });
    },
  },
};
</script>
```

#### BlogCreate.vue (Child)

```js
<template>
  <div>
    <form v-on:submit.prevent="sendPostData">
      <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
        <div class="form-control w-full px-2">
          <label class="label" for="title">
            <span class="label-text">Titel</span>
          </label>
          <input
            type="text"
            id="title"
            v-model="form.title"
            placeholder="Titel"
            class="input input-bordered"
          />
        </div>
        <div class="form-control w-full px-2">
          <label class="label" for="body">
            <span class="label-text">Artikel</span>
          </label>
          <input
            type="text"
            id="body"
            v-model="form.body"
            placeholder="Artikel"
            class="input input-bordered"
          />
        </div>
        <div class="form-control w-full px-2">
          <label class="label" for="userId">
            <span class="label-text">Nr</span>
          </label>
          <input
            type="text"
            id="userId"
            v-model.number="form.userId"
            placeholder="Nr"
            class="input input-bordered"
          />
        </div>
      </div>
      <div class="mt-8 text-center">
        <button class="btn btn-sm btn-primary">Blog speichern</button>
      </div>
    </form>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "BlogCreate",
  //
  data() {
    return {
      form: {
        title: "",
        body: "",
        userId: 0,
      },
    };
  },
  //
  methods: {
    sendPostData() {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", this.form)
        .then((response) => console.log("response: ", response))
        .catch((error) => console.log("error: ", error));
    },
  },
};
</script>
```

## Component Lifecycle Hooks

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Lifecycle Hooks
      </h1>
      <div class="mt-8">
        <Parent />
      </div>
    </div>
  </div>
</template>
<script>
import Parent from "./components/Parent";
export default {
  name: "App",
  //
  components: {
    Parent,
  },
};
</script>
```

#### Parent.vue (Child)

```js
<template>
  <div>
    <h2>Child Parent.vue</h2>
    <div class="mt-8">
      <button class="btn btn-sm" v-on:click="showChild = !showChild">
        Toggle Child
      </button>
    </div>
    <div class="mt-8">
      <Child v-if="showChild" />
    </div>
  </div>
</template>
<script>
import Child from "./Child";
export default {
  name: "Parent",
  //
  data() {
    return {
      showChild: true,
    };
  },
  //
  components: {
    Child,
  },
  //
  beforeCreate() {
    console.log("Parent beforeCreate");
  },
  //
  created() {
    console.log("Parent created");
  },
  //
  beforeMount() {
    console.log("Parent beforeMount");
  },
  //
  mounted() {
    console.log("Parent mounted");
  },
  //
  beforeUpdate() {
    console.log("Parent beforeUpdate");
  },
  //
  updated() {
    console.log("Parent updated");
  },
  //
  beforeUnmount() {
    console.log("Parent beforeUnmount");
  },
  //
  unmounted() {
    console.log("Parent unmounted");
  },
};
</script>
```

#### Child.vue (Child)

```js
<template>
  <div>
    <h2>
      Child Child.vue
    </h2>
  </div>
</template>

<script>
export default {
  name: "Child",
  //
  beforeCreate() {
    console.log("Child beforeCreate");
  },
  //
  created() {
    console.log("Child created");
  },
  //
  beforeMount() {
    console.log("Child beforeMount");
  },
  //
  mounted() {
    console.log("Child mounted");
  },
  //
  beforeUpdate() {
    console.log("Child beforeUpdate");
  },
  //
  updated() {
    console.log("Child updated");
  },
  //
  beforeUnmount() {
    console.log("Child beforeUnmount");
  },
  //
  unmounted() {
    console.log("Child unmounted");
  },
};
</script>
```

## HTTP GET - second version

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        HTTP GET with Lifecylce Hooks
      </h1>
    </div>
    <div class="mt-8">
      <BlogList />
    </div>
  </div>
</template>
<script>
import BlogList from "./components/BlogListLifecycle";
export default {
  name: "App",
  //
  components: {
    BlogList,
  },
};
</script>
```

#### BlogListLifecycle.vue (Child)

```js
<template>
  <div>
    <div v-for="blog in blogs" :key="blog.id" class="my-2 card bg-gray-200 text-gray-900">
        <div class="card-body">
            <h2 class="card-title">{{ blog.title }}</h2>
            {{ blog.body }}
        </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "BlogListLifecycle",
  //
  created() {
    this.getBlogs();
  },
  //
  data() {
    return {
      blogs: [],
    };
  },
  //
  methods: {
    getBlogs() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then((response) => {
          console.log("response: ", response.data);
          this.blogs = response.data
        })
        .catch((error) => {
          console.log("error: ", error);
        });
    },
  },
};
</script>
```

## Template Refs

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Template Refs
      </h1>
    </div>
    <div class="mt-8">
      <TemplateRef />
    </div>
  </div>
</template>
<script>
import TemplateRef from "./components/TemplateRef";
export default {
  name: "App",
  //
  components: {
    TemplateRef,
  },
};
</script>
```

#### TemplateRef.vue (Child)

```js
<template>
  <div class="p-2 flex flex-wrap items-center justify-between -mx-2">
    <div class="form-control w-1/2 px-2">
      <label class="label" for="firstName">
        <span class="label-text">Vorname</span>
      </label>
      <input
        type="text"
        ref="firstName"
        id="firstName"
        class="input input-bordered"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "TemplateRef",
  //
  mounted() {
    this.$refs.firstName.focus();
  },
};
</script>
```

## Mixins

### 1. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Mixins
      </h1>
    </div>
    <div class="mt-8">
      <CounterByClick />
    </div>
  </div>
</template>
<script>
import CounterByClick from "./components/CounterByClick";
export default {
  name: "App",
  //
  components: {
    CounterByClick,
  },
};
</script>
```

#### CounterByClick.vue (Child)

```js
<template>
  <div class="text-center">
    <button v-on:click="addCount" class="btn btn-sm btn-primary">
      {{ count }}-mal angeklickt
    </button>
  </div>
</template>
<script>
export default {
  name: "CounterByClick",
  //
  data() {
    return {
      count: 0,
    };
  },
  //
  methods: {
    addCount() {
      this.count += 1;
    },
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
        Mixins
      </h1>
      <div class="mt-8">
        <CounterByClick />
      </div>
      <div class="mt-8">
        <CounterByHover />
      </div>
    </div>
  </div>
</template>
<script>
import CounterByClick from "./components/CounterByClick";
import CounterByHover from "./components/CounterByHover";
export default {
  name: "App",
  //
  components: {
    CounterByClick,
    CounterByHover,
  },
};
</script>
```

#### CounterByHover.vue (Child)

```js
<template>
  <div class="text-center">
    <h2 v-on:mouseover="addCount">
      {{ count }}-mal mit der Maus überfahren
     </h2>
  </div>
</template>
<script>
export default {
  name: "CounterByHover",
  //
  data() {
    return {
      count: 0,
    };
  },
  //
  methods: {
    addCount() {
      this.count += 1;
    },
  },
};
</script>
```

### 3. Beispiel

#### App.vue (Parent)

```js
<template>
  <div class="container px-6 py-16 max-w-md mx-auto">
    <div class="prose text-center mb-4">
      <h1>
        Mixins
      </h1>
      <div class="mt-8">
        <CounterByClick />
      </div>
      <div class="mt-8">
        <CounterByHover />
      </div>
    </div>
  </div>
</template>
<script>
import CounterByClick from "./components/CounterByClickMixin";
import CounterByHover from "./components/CounterByHoverMixin";
export default {
  name: "App",
  //
  components: {
    CounterByClick,
    CounterByHover,
  },
};
</script>
```

#### counter.js

```js
export default {
  data() {
    return {
      count: 0,
    };
  },
  //
  methods: {
    addCount() {
      this.count += 1;
    },
  },
};
```

#### CounterByClickMixin.vue (Child)

```js
<template>
  <div class="text-center">
    <button v-on:click="addCount" class="btn btn-sm btn-primary">
      {{ count }}-mal angeklickt
    </button>
  </div>
</template>
<script>
import CounterMixin from "../mixins/counter";
export default {
  name: "CounterByClickMixin",
  //
  data() {
    return {
      count: 100,
    };
  },
  //
  mixins: [CounterMixin],
};
</script>
```

#### CounterByHoverMixin.vue (Child)

```js
<template>
  <div class="text-center">
    <h2 v-on:mouseover="addCount">{{ count }}-mal mit der Maus überfahren</h2>
  </div>
</template>
<script>
import CounterMixin from "../mixins/counter";
export default {
  name: "CounterByHover",
  //
  mixins: [CounterMixin],
};
</script>
```
