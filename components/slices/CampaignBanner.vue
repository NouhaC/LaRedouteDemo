<template>
    <section class="campaign-section" :style="{ backgroundImage: 'linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.6)), url(' + slice.primary.image_banniere_de_campagne.url + ')' }">
        <h2 class="campaign-title"> {{slice.primary.campagne.title }} </h2>
        <p class="campaign-description">{{ slice.primary.campagne.description }}</p>
        <prismic-link class="campaign-button" :field="slice.primary.button_link"> {{ slice.primary.button_label }} </prismic-link>
    </section>
</template>

<script>
export default {
  props: ['slice'],
  name: 'campaign-banner'
}
</script>

<style lang="sass" scoped>
.campaign-section
  margin: -70px 0 80px
  padding: 10em 0 8em
  background-position: center center
  background-size: cover
  color: #ffffff
  line-height: 1.75
  text-align: center

.campaign-section
  text-align: center

.campaign-title, .campaign-description
  width: 90%
  max-width: 490px
  margin-left: auto
  margin-right: auto

.campaign-title
  color: #ffffff
  font-size: 70px
  font-weight: 900
  line-height: 70px

.campaign-button
  background: #ffffff
  border-radius: 7px
  color: #484D52
  font-size: 14px
  font-weight: 700
  padding: 15px 40px
  &:hover
    background: #c8c9cb

@media (max-width: 767px)
  .campaign-section
    margin: 0 0 40px
    padding: 10em 0 6em
  .banner-title
    font-size: 50px
    line-height: 50px
</style>
