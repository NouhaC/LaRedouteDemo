<template>
    <section class='full-width-image content-setion'>
        <prismic-image :field="slice.primary.image_banniere_de_campagne "/>
        <div class="campaign-content container">
            <h2 class="campaign-title">
                {{ $prismic.richTextAsPlain(slice.primary.campagne.title) }}
                </h2>
            <!-- Template for page tagline. -->
            <p class="campaign-description">{{ $prismic.richTextAsPlain(slice.primary.campagne.description) }}</p>
            <prismic-link class="campaign-button" :field="slice.primary.button_link">
                {{ $prismic.richTextAsPlain(slice.primary.button_label) }}
            </prismic-link>
        </div>
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