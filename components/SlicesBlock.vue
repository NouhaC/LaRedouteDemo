<template>
    <div class="container">
        <!-- Slice section template -->
        <section v-for="(slice, index) in slices" :key="'slice-' + index">
            <!-- Text slice component -->
            <template v-if="slice.slice_type === 'text_section'">
                <text-slice :slice="slice"/>
            </template>
            <!-- Quote slice component -->
            <template v-else-if="slice.slice_type === 'quote'">
                <quote-slice :slice="slice"/>
            </template>
            <!-- Full Width Image slice component -->
            <template v-else-if="slice.slice_type === 'full_width_image'">
                <full-width-image :slice="slice"/>
            </template>
            <!-- Image Gallery slice component -->
            <template v-else-if="slice.slice_type === 'image_gallery'">
                <image-gallery :slice="slice"/>
            </template>
            <!-- Image Highlight slice component -->
            <template v-else-if="slice.slice_type === 'image_highlight'">
                <image-highlight :slice="slice"/>
            </template>
            <!-- Brands slice component -->
            <template v-else-if="slice.slice_type === 'featured_brands'">
                <featured-brands :slice="slice"/>
            </template>
             <!-- Campaign Banner slice component -->
            <template v-else-if="slice.slice_type === 'campaign_banner'">
                <campaign-banner :slice="slice"/>
            </template>
        </section>
    </div>
</template>

<script>
// Imports for all slices
const TextSlice = () => import("./slices/TextSlice.vue");
const QuoteSlice = () => import("./slices/QuoteSlice.vue");
const FullWidthImage = () => import("./slices/FullWidthImage.vue");
const ImageGallery = () => import("./slices/ImageGallery.vue");
const ImageHighlight = () => import("./slices/ImageHighlight.vue");
const FeaturedBrands = () => import("./slices/FeaturedBrands.vue");
const CampaignBanner = () => import("./slices/CampaignBanner.vue");

export default {
  props: ['slices'],
  name: 'slices-block',
  components: {
    TextSlice,
    QuoteSlice,
    FullWidthImage,
    ImageGallery,
    ImageHighlight,
    FeaturedBrands,
    CampaignBanner
  },
}
</script>