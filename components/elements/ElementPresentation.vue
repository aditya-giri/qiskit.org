<template>
  <header class="element-presentation">
    <CommunityHeader
      :main-title="title"
      aside-position="start"
      no-gradient
    >
      <template #aside>
        <img
          class="element-presentation__logo"
          :src="logo"
          :alt="`${title} logo`"
        >
      </template>
      <p class="element-presentation__description">
        {{ description }}
      </p>
      <AppCta
        v-if="to"
        class="element-presentation__get-started-cta"
        :url="to"
        :segment="{
          action: segmentAction
        }"
      >
        Get Started!
      </AppCta>
      <AppCta
        v-if="sources"
        class="element-presentation__github-cta"
        :url="sources"
        :segment="{
          action: segmentAction
        }"
      >
        <div class="element-presentation__github-cta-layout">
          <svg
            class="element-presentation__github-cta-icon"
            viewBox="0 0 24 24"
            width="24"
            height="24"
            role="img"
          ><path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12" /></svg>
          <span class="element-presentation__github-cta-label">GitHub</span>
        </div>
      </AppCta>
    </CommunityHeader>
  </header>
</template>

<script lang="ts">
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator'
import AppCta from '~/components/ui/AppCta.vue'
import CommunityHeader from '~/components/ui/CommunityHeader.vue'

@Component({
  components: { AppCta, CommunityHeader }
})
export default class extends Vue {
  @Prop(String) logo
  @Prop(String) title
  @Prop(String) description
  @Prop({ type: String, required: false }) to
  @Prop({ type: String, required: false }) sources
  @Prop(String) segmentAction
}
</script>

<style lang="scss" scoped>
.element-presentation {
  &__description {
    @include body-long-04();
    margin: $spacing-05 0;
  }

  &__logo {
    width: $logo-size;
    height: $logo-size;

    @include mq($until: medium) {
      width: $logo-size-small;
      height: $logo-size-small;
    }
  }

  &__github-cta-layout {
    display: flex;
    align-items: center;
  }

  &__github-cta-label {
    padding-left: $spacing-03;
  }

  &__github-cta-icon {
    width: $icon-size;
    height: $icon-size;
  }
}
</style>
