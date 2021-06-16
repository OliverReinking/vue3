# Single File Components

## Text Binding

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Text Binding
    </h1>
    <div>Autor: {{ author }}</div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      author: "Oliver Reinking",
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Text Binding
    </h1>
    <div>
      Der Autor <span v-text="author"></span> hat das Buch
      <span v-text="book"></span> geschrieben.
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      author: "Oliver Reinking",
      book: "Vue 3",
    };
  },
};
</script>
```

## Binding HTML

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      HTML Binding
    </h1>
    <div>
      Der Autor {{ author }} hat das Buch {{ book }} geschrieben.
    </div>
    <div>
      <span v-html="description"></span>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      author: "Reinking",
      book: "Vue 3",
      description: "Eine Einführung in das JavaScript-Framework <b>VUE 3</b>",
    };
  },
};
</script>
```

## Binding to Attributes

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1 v-bind:id="headingId">
      Binding to Attributes
    </h1>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      headingId: "VUE3",
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1 v-bind:id="headingId">
      Binding to Attributes
    </h1>
    <button v-bind:disabled="isDisabled" class="btn">
      Button und das Attribut disabled
    </button>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      headingId: "VUE3",
      isDisabled: true,
    };
  },
};
</script>
```

## Binding Classes

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1 class="underline">
      Binding Classes
    </h1>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
    };
  },
};
</script>
<style>
.underline {
  text-decoration: underline;
}
</style>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16">
    <h1 class="underline">
      Binding Classes
    </h1>
    <h2 class="underline" v-bind:class="status">Status</h2>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      status: 'success'
    };
  },
};
</script>
<style scoped>
.underline {
  text-decoration: underline;
}
.danger {
  background-color: orangered;
  color: black;
}
.success {
  background-color: greenyellow;
  color: green;
}
</style>
```

### 3. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16">
    <h1 class="underline">
      Binding Classes
    </h1>
    <h2 class="underline" v-bind:class="status">Status</h2>
    <h3 v-bind:class="IsEspecially && 'especially'">Ist dies ein besonderer Text?</h3>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      status: 'success',
      IsEspecially: true
    };
  },
};
</script>
<style scoped>
.underline {
  text-decoration: underline;
}
.danger {
  background-color: orangered;
  color: black;
}
.success {
  background-color: greenyellow;
  color: green;
}
.especially {
  font-weight: 800;
  font-style: italic;
}
</style>
```

### 4. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16">
    <h1 class="underline">
      Binding Classes
    </h1>
    <h2 class="underline" v-bind:class="status">Status</h2>
    <h3 v-bind:class="IsEspecially ? 'especially' : 'normal' ">Ist dies ein besonderer Text?</h3>
  </div>
</template>
<script>

export default {
  name: "App",
  //
  data() {
    return {
      status: 'success',
      IsEspecially: false,
    };
  },
};
</script>
<style scoped>
.underline {
  text-decoration: underline;
}
.danger {
  background-color: orangered;
  color: black;
}
.success {
  background-color: greenyellow;
  color: green;
}
.especially {
  font-weight: 800;
  font-style: italic;
}
.normal {
  color: blue;
}
</style>
```

### 5. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16">
    <h1 class="underline">
      Binding Classes
    </h1>
    <h2 class="underline" v-bind:class="status">Status</h2>
    <h3 v-bind:class="IsEspecially ? 'especially' : 'normal'">
      Ist dies ein besonderer Text?
    </h3>
    <h4
      v-bind:class="[
        'underline',
        IsEspecially && IsBold
          ? 'especially_bold'
          : IsEspecially && !IsBold
          ? 'especially'
          : IsBold
          ? 'only_bold'
          : '',
      ]"
    >
      Ein Array mit mehreren Klassen?
    </h4>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      status: "success",
      IsEspecially: false,
      IsBold: true,
    };
  },
};
</script>
<style scoped>
.underline {
  text-decoration: underline;
}
.danger {
  background-color: orangered;
  color: black;
}
.success {
  background-color: greenyellow;
  color: green;
}
.especially {
  font-weight: 100;
  font-style: italic;
}
.especially_bold {
  font-weight: 800;
  color: orange;
  font-style: italic;
}
.only_bold {
  font-weight: 800;
}
.normal {
  color: blue;
}
</style>
```

## Binding Styles

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Binding Styles
    </h1>
    <div
      v-bind:style="{
        color: highlightColor,
      }"
    >
      Inline Style
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      highlightColor: "#4FC08D",
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Binding Styles
    </h1>
    <div
      v-bind:style="{
        color: highlightColor,
        'font-size': divSize + 'px',
      }"
    >
      Inline Style
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      highlightColor: "#4FC08D",
      divSize: "50",
    };
  },
};
</script>
```

### 3. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Binding Styles
    </h1>
    <div
      v-bind:style="{
        color: highlightColor,
        'font-size': divSize + 'px',
        padding: '20px'
      }"
    >
      Inline Style
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      highlightColor: "#4FC08D",
      divSize: '50'
    };
  },
};
</script>
```

### 4. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Binding Styles
    </h1>
    <div
      v-bind:style="{
        color: highlightColor,
        'font-size': divSize + 'px',
        padding: '2px',
      }"
    >
      Inline Style
    </div>
    <div v-bind:style="divStyleObject">
      Inline Style Version 2
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      highlightColor: "#4FC08D",
      divSize: "50",
      divStyleObject: {
        color: "orange",
        fontSize: "50px",
        padding: "2px",
      },
    };
  },
};
</script>
```

### 5. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Binding Styles
    </h1>
    <div v-bind:style="baseStyleObject">nur baseStyleObject</div>
    <div v-bind:style="[baseStyleObject, successStyleObject]">
      baseStyleObject und successStyleObject
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      baseStyleObject: {
        fontSize: "20px",
        padding: "2px",
      },
      successStyleObject: {
        color: "green",
        backgroundColor: "lightblue",
        border: "1 px solid",
      },
    };
  },
};
</script>
```

## Conditional Rendering

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Conditional Rendering
    </h1>
    <div v-if="inzidenzWert > 165" style="backgroundColor: red; color: white">
      Die Inzidenz liegt über 165!
    </div>
    <div
      v-else-if="inzidenzWert > 100 && inzidenzWert < 165"
      style="backgroundColor: orange; color: white"
    >
      Die Inzidenz liegt über 100, aber unter 165!
    </div>
    <div
      v-else-if="inzidenzWert > 50 && inzidenzWert < 100"
      style="backgroundColor: yellow; color: black"
    >
      Die Inzidenz liegt über 50, aber unter 100!
    </div>
    <div v-else style="backgroundColor: green; color: white">
      Die Inzidenz liegt unter 50!
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      inzidenzWert: 75,
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Conditional Rendering
    </h1>
    <div v-if="display === true">
      <h2>VUE 3</h2>
      <h2>Tailwindcss</h2>
      <h2>daisyUI</h2>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      display: true,
    };
  },
};
</script>
```

### 3. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Conditional Rendering
    </h1>
    <div v-show="display">
      Offensichtlich ist display true.
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      display: true,
    };
  },
};
</script>
```

## List Rendering

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      List Rendering
    </h1>
    <h2 v-for="name in names" :key="name">
      {{ name}}
    </h2>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      names: [
        'Vue 3',
        'Tailwindcss',
        'daisyUI'
      ]
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      List Rendering
    </h1>
    <h2 v-for="(name, index) in names" :key="index">
      {{ name}}, {{ index }}
    </h2>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      names: [
        'Vue 3',
        'Tailwindcss',
        'daisyUI'
      ]
    };
  },
};
</script>
```

### 3. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      List Rendering
    </h1>
    <h2 v-for="(fullName, index) in fullNames" :key="index">
      {{ fullName.name }} - {{ fullName.description }}
    </h2>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      fullNames: [
        { name: "VUE 3", description: "JavaScript-Framework" },
        { name: "tailwindcss", description: "CSS-Framework" },
        { name: "daisyUI", description: "tailwindcss-Erweiterung" },
      ],
    };
  },
};
</script>

```

### 4. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      List Rendering
    </h1>
    <template v-for="(framework, index) in frameworks" :key="index">
      <h3>{{ framework.name }}</h3>
      <h4>Liste der Plugins</h4>
      <h5 v-for="(plugin, index) in framework.plugins" :key="index">
        {{ plugin }}
      </h5>
    </template>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      frameworks: [
        {
          name: "VUE 3",
          plugins: ["vuex", "vue-router", "vuetify"],
        },
        {
          name: "tailwindcss",
          plugins: ["daisyUI", "@tailwindcss/typography"],
        },
      ],
    };
  },
};
</script>
```

### 5. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      List Rendering
    </h1>
    <template v-for="(item, key, index) in listFrameworks" :key="index">
      <h3>{{ key }}: {{ item }}</h3>
    </template>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      listFrameworks: {
        name: "VUE 3",
        description: "JavaScript-Framework",
        language: "JavaScript",
      },
    };
  },
};
</script>
```

## Lists and Keys

### 1. Beispiel

#### App.vue

```js

```

## Conditional List Rendering

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Conditional List Rendering
    </h1>
    <template v-for="name in names" :key="name">
      <h5 v-if="name === 'Annalena'">{{ name }}</h5>
    </template>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      names: ["Olaf", "Armin", "Annalena"],
    };
  },
};
</script>
```

## Methods

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Methods
    </h1>
    <h4>Summe von 1 + 2 + 3 + 4 + 5 + 6 = {{ add() }}</h4>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      names: ["Olaf", "Armin", "Annalena"],
    };
  },
  //
  methods: {
    add() {
      return 1 + 2 + 3 + 4 + 5 + 6;
    },
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Methods
    </h1>
    <h4>Summe von 1 + 2 + 3 + 4 + 5 + 6 = {{ add(1, 2, 3, 4, 5, 6) }}</h4>
    <h4>Summe von 1 + 2 + 3 + 5 + 8 + 13 = {{ add(1, 2, 3, 5, 8, 13) }}</h4>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  methods: {
    add(a, b, c, d, e, f) {
      return a + b + c + d + e + f;
    },
  },
};
</script>
```
### 3. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Methods
    </h1>
    <h4>Multipliziere die Variable price mit dem normalen Mehrwertsteuersatz {{ taxRate }} = {{ multiply(price) }} </h4>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      price: 100,
      taxRate: 19,
    };
  },
  //
  methods: {
    multiply(num) {
      return num * (100 + this.taxRate) / 100;
    }
  },
};
</script>
```

## Event Handling

### 1. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Event Handling
    </h1>
    <h5>{{ name }}</h5>
    <div class="mt-8">
      <button v-on:click="name = 'Annalena'" class="btn btn-sm btn-primary">Ändere den Namen</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      name: "Angela",
    };
  },
};
</script>
```

### 2. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Event Handling
    </h1>
    <h5>{{ count }}</h5>
    <div class="mt-8 btn-group">
      <button v-on:click="count += 1" class="btn btn-sm btn-primary">
        Plus
      </button>
      <button v-on:click="count += -1" class="btn btn-sm btn-secondary">
        Minus
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      count: 0,
    };
  },
};
</script>
```

### 3. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Event Handling
    </h1>
    <h5>{{ count }}</h5>
    <div class="mt-8 btn-group">
      <button v-on:click="changeCount(1)" class="btn btn-sm btn-primary">
        Plus
      </button>
      <button v-on:click="changeCount(-1)" class="btn btn-sm btn-secondary">
        Minus
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      count: 0,
    };
  },
  //
  methods: {
    changeCount(value) {
      this.count = this.count + value;
    },
  },
};
</script>
```

### 4. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Event Handling
    </h1>
    <h5>{{ count }}</h5>
    <div class="mt-8 btn-group">
      <button v-on:click="changeCount(1)" class="btn btn-sm btn-primary">
        Plus 1
      </button>
      <button v-on:click="changeCount(5)" class="btn btn-sm btn-primary">
        Plus 5
      </button>
      <button v-on:click="changeCount(-1)" class="btn btn-sm btn-secondary">
        Minus 1
      </button>
      <button v-on:click="changeCount(-5)" class="btn btn-sm btn-secondary">
        Minus 5
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      count: 0,
    };
  },
  //
  methods: {
    changeCount(value) {
      this.count = this.count + value;
    },
  },
};
</script>
```

### 5. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Event Handling
    </h1>
    <h5>{{ count }}</h5>
    <div class="mt-8 btn-group">
      <button v-on:click="changeCount(1, $event)" class="btn btn-sm btn-primary">
        Plus 1
      </button>
      <button v-on:click="changeCount(5, $event)" class="btn btn-sm btn-primary">
        Plus 5
      </button>
      <button v-on:click="changeCount(-1, $event)" class="btn btn-sm btn-secondary">
        Minus 1
      </button>
      <button v-on:click="changeCount(-5, $event)" class="btn btn-sm btn-secondary">
        Minus 5
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      count: 0,
    };
  },
  //
  methods: {
    changeCount(value, event) {
      console.log("event: ", event);
      this.count = this.count + value;
    },
  },
};
</script>
```

### 6. Beispiel

#### App.vue

```js
<template>
  <div class="container px-6 py-16 prose">
    <h1>
      Event Handling
    </h1>
    <h5>{{ name }} {{ lastName }} </h5>
    <h5>{{ count }}</h5>
    <div class="mt-8 btn-group">
      <button
        v-on:click="changeName($event), changeCount(1, $event)"
        class="btn btn-sm btn-primary"
      >
        Plus 1
      </button>
      <button
        v-on:click="changeCount(5, $event)"
        class="btn btn-sm btn-primary"
      >
        Plus 5
      </button>
      <button
        v-on:click="changeCount(-1, $event)"
        class="btn btn-sm btn-secondary"
      >
        Minus 1
      </button>
      <button
        v-on:click="changeCount(-5, $event)"
        class="btn btn-sm btn-secondary"
      >
        Minus 5
      </button>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  //
  data() {
    return {
      name: "Angela",
      lastName: "Merkel",
      count: 0,
    };
  },
  //
  methods: {
    changeName(event) {
      console.log("changeName: ", event);
      this.name = "Annalena";
    },
    changeCount(value, event) {
      console.log("changeCount: ", event);
      this.count = this.count + value;
    },
  },
};
</script>
```

## Form Handling

### 1. Beispiel

#### App.vue

```js

```

### 2. Beispiel

#### App.vue

```js

```

### 3. Beispiel

#### App.vue

```js

```

### 4. Beispiel

#### App.vue

```js

```

### 5. Beispiel

#### App.vue

```js

```

### 6. Beispiel

#### App.vue

```js

```

### 7. Beispiel

#### App.vue

```js

```

### 8. Beispiel

#### App.vue

```js

```

## X

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```

### x. Beispiel

#### App.vue

```js

```
