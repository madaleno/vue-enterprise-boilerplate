<script>
import appConfig from '@src/app.config'

export default {
  page: {
    // All subcomponent titles will be injected into this template
    titleTemplate(title) {
      title = typeof title === 'function' ? title(this.$store) : title
      return title ? `${title} | ${appConfig.title}` : appConfig.title
    },
  },
}
</script>

<template>
  <div id="app">
    <!--
    Even when routes use the same component, treat them
    as distinct and create the component again.
    -->
    <div :key="$route.fullPath">
      <router-view/>
    </div>
  </div>
</template>

<!-- This should generally be the only global CSS in the app -->
<style lang="scss">
// Allow element/type selectors, because this is global CSS
// stylelint-disable selector-max-type, selector-class-pattern

@import '~normalize.css/normalize.css';
@import '~@design';

*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  background: $color-body-bg;
}

#app {
  @extend %typography-small;
}

// ===
// Base element styles
// ===

a,
a:visited {
  color: $color-link-text;
}

h1 {
  @extend %typography-xxlarge;
}

h2 {
  @extend %typography-xlarge;
}

h3 {
  @extend %typography-large;
}

h4 {
  @extend %typography-medium;
}

h5,
h6 {
  @extend %typography-small;
}

// ===
// Animations
// ===

@keyframes spin {
  100% {
    transform: rotate(360deg);
  }
}
</style>
