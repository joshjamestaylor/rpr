<script setup lang="ts">
const state = reactive({
  name: "",
  email: "",
  phone: "",
  vehicle: "",
  repairType: "",
  message: "",
});

const repairTypes = [
  "Dent Repair",
  "Scratch Repair",
  "Collision Repair",
  "Paint Respray",
  "Bumper Repair",
  "Other",
];

const testimonials = [
  {
    title: "Sarah M. ★★★★★",
    description:
      '"After a nasty car park scrape, these guys had my bumper looking brand new in two days. Couldn\'t be happier — the colour match was spot on."',
    icon: "i-heroicons-chat-bubble-left-ellipsis",
  },
  {
    title: "James R. ★★★★★",
    description:
      '"Brought in my VW after a rear-end collision. The repair was immaculate and they handled all the insurance paperwork. Highly recommended."',
    icon: "i-heroicons-chat-bubble-left-ellipsis",
  },
  {
    title: "Claire T. ★★★★★",
    description:
      "\"Honest pricing, fast turnaround and a finish you'd swear was factory fresh. I've already sent three friends their way.\"",
    icon: "i-heroicons-chat-bubble-left-ellipsis",
  },
];

const services = [
  {
    icon: "i-heroicons-wrench-screwdriver",
    title: "Dent & Scratch Repair",
    description:
      "From stone chips to deep scratches, we fix all surface damage with precision paintless or traditional repair techniques.",
  },
  {
    icon: "i-heroicons-shield-exclamation",
    title: "Collision Repair",
    description:
      "Structural and cosmetic restoration after accidents, bringing your vehicle back to pre-accident condition.",
  },
  {
    icon: "i-heroicons-swatch",
    title: "Paint Matching & Respray",
    description:
      "Computer-matched paint technology ensures a seamless, factory-quality finish on every panel we touch.",
  },
  {
    icon: "i-heroicons-arrow-path",
    title: "Bumper Repair",
    description:
      "Cracked, scraped or misaligned bumpers repaired and refinished to look as good as new — often same day.",
  },
  {
    icon: "i-heroicons-adjustments-horizontal",
    title: "Frame Straightening",
    description:
      "State-of-the-art laser measuring and pulling equipment to restore your vehicle's structural integrity.",
  },
  {
    icon: "i-heroicons-document-check",
    title: "Insurance Work",
    description:
      "Fully approved repairer for all major insurers. We handle the claims process so you don't have to.",
  },
];

async function onSubmit(event: any) {
  console.log("Enquiry submitted:", event.data);
  alert("Thank you! We'll be in touch within 24 hours.");
  Object.assign(state, {
    name: "",
    email: "",
    phone: "",
    vehicle: "",
    repairType: "",
    message: "",
  });
}
</script>

<template>
  <!-- Hero -->
  <UPageHero
    headline="Trusted Local Experts"
    title="Premium Car Body Repair & Restoration"
    description="From minor dents to major collision damage, we restore your vehicle to showroom condition. Quality guaranteed, competitively priced."
    :links="[
      {
        label: 'Get a Free Quote',
        to: '#contact',
        size: 'xl',
        color: 'primary',
        class: 'rounded-none',
      },
      {
        label: 'Our Services',
        to: '#services',
        size: 'xl',
        variant: 'outline',
        class: 'rounded-none',
      },
    ]"
  />

  <!-- Services -->
  <UPageSection
    id="services"
    headline="What We Do"
    title="Comprehensive Body Repair Services"
    description="Whether it's a small scuff or a serious smash, our skilled technicians have you covered."
    :features="services"
  />

  <!-- Testimonials -->
  <UPageSection
    id="reviews"
    headline="Customer Reviews"
    title="What Our Customers Say"
    description="Hundreds of satisfied customers across the region trust us with their vehicles."
  >
    <UPageGrid>
      <UPageCard
        v-for="testimonial in testimonials"
        :key="testimonial.title"
        :title="testimonial.title"
        :description="testimonial.description"
        :icon="testimonial.icon"
        spotlight
      />
    </UPageGrid>
  </UPageSection>

  <!-- CTA -->
  <UPageCTA
    title="Ready to Restore Your Vehicle?"
    description="Book a free, no-obligation estimate today. We'll have it looking brand new — fast."
    variant="subtle"
    :links="[
      {
        label: 'Book a Free Estimate',
        to: '#contact',
        size: 'xl',
        color: 'primary',
        class: 'rounded-none',
      },
    ]"
  />

  <!-- Contact Form -->
  <UPageSection
    id="contact"
    headline="Get in Touch"
    title="Request a Free Quote"
    description="Fill in the form below and we'll get back to you within 24 hours with a competitive estimate."
  >
    <UForm
      :state="state"
      class="space-y-6 max-w-2xl mx-auto"
      @submit="onSubmit"
    >
      <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
        <UFormField label="Full Name" name="name" required>
          <UInput
            v-model="state.name"
            placeholder="John Smith"
            size="lg"
            class="w-full"
          />
        </UFormField>

        <UFormField label="Email Address" name="email" required>
          <UInput
            v-model="state.email"
            type="email"
            placeholder="john@example.com"
            size="lg"
            class="w-full"
          />
        </UFormField>

        <UFormField label="Phone Number" name="phone">
          <UInput
            v-model="state.phone"
            type="tel"
            placeholder="07700 900000"
            size="lg"
            class="w-full"
          />
        </UFormField>

        <UFormField label="Vehicle (Make, Model & Year)" name="vehicle">
          <UInput
            v-model="state.vehicle"
            placeholder="e.g. Ford Focus 2021"
            size="lg"
            class="w-full"
          />
        </UFormField>
      </div>

      <UFormField label="Type of Repair" name="repairType">
        <USelect
          v-model="state.repairType"
          :items="repairTypes"
          placeholder="Select repair type..."
          size="lg"
          class="w-full"
        />
      </UFormField>

      <UFormField label="Description of Damage" name="message">
        <UTextarea
          v-model="state.message"
          placeholder="Please describe the damage or work required..."
          :rows="5"
          size="lg"
          class="w-full"
        />
      </UFormField>

      <UButton type="submit" label="Send Enquiry" size="xl" block class="rounded-none" />
    </UForm>
  </UPageSection>
</template>
