<template>
    <section class="full-width-image campaign-setion" :style="{ backgroundImage: 'linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.6)), url(' + slice.primary.image_banniere_de_campagne + ')' }">
        <prismic-image :field="slice.primary.image_banniere_de_campagne "/>
        <h2> {{slice.primary.campagne.title }} </h2>
        <p class="campaign-description">{{ slice.primary.campagne.description }}</p>
        <prismic-link :field="slice.primary.button_link"> {{ slice.primary.button_label }} </prismic-link>
    </section>
</template>

<script>
export default {
  props: ['slice'],
  name: 'campaign-banner'
}
</script>

<style lang="sass" scoped>
@media (max-width: 767px)
  .campaign-section
    margin-bottom: 2rem
</style>