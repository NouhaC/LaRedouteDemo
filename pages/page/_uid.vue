<template>
  <section class="page">
    <!-- Vue tag to add header component -->
    <header class="site-header">
      <img class="logo" src="https://www.europcar.com/files/live/sites/Europcar/files/Meganav/NEW-Logo-size%20fit%20for%20header.png" alt="Prismic">
      <nav>
        <ul>
          <li v-for="menuLink in menuLinks" :key="menuLink.id">
            <prismic-link :field="menuLink.link">{{ $prismic.richTextAsPlain(menuLink.label) }}</prismic-link>
          </li>
        </ul>
      </nav>
    </header>
    <!-- Button to edit document in dashboard -->
    <prismic-edit-button :documentId="documentId"/>
    <!-- Slices block component -->
    <slices-block :slices="slices"/>
  </section>
</template>

<script>
import Prismic from "prismic-javascript"
import PrismicConfig from "~/prismic.config.js"
// Imports for all components
import HeaderPrismic from '~/components/HeaderPrismic.vue'
import SlicesBlock from '~/components/SlicesBlock.vue'

export default {
  name: 'page',
  components: {
    HeaderPrismic,
    SlicesBlock,
  },
  head () {
    return {
      title: 'Prismic Nuxt.js Multi Page Website',
    }
  },
  async asyncData({ params, error, req }) {
    try{
      // Fetching the API object
      const api = await Prismic.getApi(PrismicConfig.apiEndpoint, {req})

      // Query to get post content
      let document = {}
      const result = await api.getByUID("page", params.uid)
      document = result.data

      // Query to get the menu content
      let menuContent = {}
      const menu = await api.getSingle('menu')
      menuContent = menu.data

      // Load the edit button
      if (process.client) window.prismic.setupEditButton()

      return {
        // Post content
        document,
        documentId: result.id,

        // Set slices as variable
        slices: document.page_content,

        // Menu
        menuContent,
        menuLinks: menuContent.menu_links
      }
    } catch (e) {
      // Returns error page
      error({ statusCode: 404, message: 'Page not found' })
    }
  },
}
</script>

<style lang="sass">
.site-header
  background-color: #090
  height: 30px
  color: #484d52
  font-weight: 700
  a
    color: #fff
    padding-right: 20px
    font-weight: 700
  nav a:hover
    color: #72767B

.homepage .site-header
  color: #ffffff
  a
    color: #ffffff
  nav a:hover
    color: #c8c9cb

.site-header
  .logo
    display: inline-block
    font-size: 22px
    font-weight: 900
    margin: -10px 30px;
  nav
    float: right
    ul
      margin: 0
      padding-left: 0
    li
      display: inline-block
      margin-left: 40px

@media (max-width: 1060px)
  .site-header
    padding-left: 20px
    padding-right: 20px

@media (max-width: 767px)
  .site-header
    height: auto

  .homepage .site-header
    position: absolute
    left: 0
    right: 0

  .site-header
    .logo
      display: block
      text-align: center
    nav
      float: none
      text-align: center
      li
        display: inline-block
        margin-left: 10px
        margin-right: 10px
</style>