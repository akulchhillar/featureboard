<template>
  <table class="table table-auto border-spacing-y-2 border-separate">
    <tbody>
      <FeaturePill
        title="Rollout Enterprise Plan For kl"
        upvotes="55"
        tag="Details"
        :created-date="
          new Date('12/31/2015').toLocaleDateString('en-us', {
            weekday: 'long',
            year: 'numeric',
            month: 'short',
            day: 'numeric',
          })
        "
      />
      <FeaturePill title="REST API REST API REST " upvotes="20" tag="Details" />
      <FeaturePill
        title="UPI Integration"
        upvotes="43"
        tag="Details"
        :created-date="
          new Date('12/25/2015').toLocaleDateString('en-us', {
            weekday: 'long',
            year: 'numeric',
            month: 'short',
            day: 'numeric',
          })
        "
      />
      <!-- <FeaturePill title="Rollout Entreprise Plan" upvotes="55" />
      <FeaturePill title="REST API" upvotes="20" tag="Details" />
      <FeaturePill title="UPI Integration" upvotes="43" tag="Details" />
      <FeaturePill title="Rollout Entreprise Plan" upvotes="55" tag="Details" />
      <FeaturePill title="REST API" upvotes="20" tag="Details" />
      <FeaturePill title="UPI Integration" upvotes="43" tag="Details" /> -->
    </tbody>
  </table>
</template>

<script setup>
import FeaturePill from "./FeaturePill.vue";
</script>

<script>
export default {
  name: "Content",
};
</script>
