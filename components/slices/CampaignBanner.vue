<template>
    <section class='full-width-image campaign-banner'>
        <prismic-image :field="slice.primary.image_banniere_de_campagne "/>
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
  .content-section
    margin-bottom: 2rem
</style>