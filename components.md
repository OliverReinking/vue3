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

## X

### x. Beispiel

#### App.vue (Parent)

```js

```
#### X.vue (Child)

```js

```

### x. Beispiel

#### App.vue (Parent)

```js

```
#### X.vue (Child)

```js

```




