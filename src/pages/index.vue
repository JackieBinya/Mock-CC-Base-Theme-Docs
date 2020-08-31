<template>
  <Layout :sidebar="true">
    <div class="content">
      <g-image src="~/assets/img/mock-cc-screenshot.png"/>
    
     <p>Volutpat maecenas volutpat blandit aliquam etiam erat velit scelerisque in. Dapibus ultrices in iaculis nunc sed. Duis at tellus at urna. Facilisis gravida neque convallis a cras. Scelerisque in dictum non consectetur a. Nisi vitae suscipit tellus mauris a diam. Nunc lobortis mattis aliquam faucibus. Integer quis auctor elit sed vulputate. Cras pulvinar mattis nunc sed.</p>

     <ul>
       <li>Scelerisque in dictum non consectetur a. Nisi vitae suscipit tellus mauris a diam. Nunc lobortis mattis aliquam faucibus. Integer quis auctor elit sed vulputate.</li>
       <li>Scelerisque in dictum non consectetur a. Nisi vitae suscipit tellus mauris a diam. Nunc lobortis mattis aliquam faucibus. Integer quis auctor elit sed vulputate.</li>
       <li>Scelerisque in dictum non consectetur a. Nisi vitae suscipit tellus mauris a diam. Nunc lobortis mattis aliquam faucibus. Integer quis auctor elit sed vulputate.</li>
     </ul>
    </div>
  </Layout>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import GitLink from '~/components/GitLink.vue'
import Shortcut from '~/components/Shortcut.vue'

export default {
  components: {
    GitLink,
    Shortcut
  },
  data() {
    return {
      description: 'The ultimate static generated documentation theme for the JAM-stack'
    }
  },
  metaInfo() {
    return {
      title: this.description,
      meta: [
        { key: 'description', name: 'description', content: 'A theme for static site documentation based on Gridsome, ready to deploy to Netlify in one click.' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.content {
  display: flex;
  flex-direction: column;
}

h1 {
  text-align: center;
  max-width: 600px;
  margin: 1.5em auto 1.5em;

  @include respond-above(md) {
    max-width: 1000px;
  }
}

h2 {
  font-size: 1.4rem;
  margin: 0;
}

nav {
  display: flex;
  justify-content: space-between;
  flex-direction: column;

  @include respond-above(sm) {
    flex-direction: row;
  }
}

.git {
  margin: 3em 0 0;
  align-self: center;

  @include respond-above(md) {
    margin: 5em 0 0;
  }
}

img{
  width: 100%;
  height: 300px;
  margin-bottom: 1em;
}
</style>
