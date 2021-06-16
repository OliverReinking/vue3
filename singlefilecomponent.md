# Single File Components

## Text Binding

### 1. Beispiel

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

```js
```

```js
```

### 2. Beispiel

```js
```

```js
```

### 3. Beispiel

```js
```

```js
```


