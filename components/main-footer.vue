<script setup>
const socials = [
  {
    name: "instagram",
    href: "https://instagram.com/aqlizaa",
  },
  {
    name: "github",
    href: "https://github.com/hik4m",
  },
  {
    name: "linkedin",
    href: "https://linkedin.com/in/aqliza-hikam",
  },
];
</script>

<template>
  <footer>
    <NuxtLink to="/" class="title">Hikam.</NuxtLink>
    <ul class="socials">
      <li
        v-for="social in socials"
        :key="social.name"
        class="link"
        @pointerenter="scrambleHoverAnimation"
      >
        <GoToWebsite :href="social.href" :text="social.name">
          {{ social.name }}
        </GoToWebsite>
      </li>
    </ul>
  </footer>
</template>

<style lang="css" scoped>
footer {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-inline: 1.25rem;
  padding-block: 0.5rem;
  z-index: 3;
}

.title {
  text-transform: uppercase;
}

.socials {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  list-style: none;
}

.socials {
  text-transform: uppercase;
}

.socials .link {
  transition: filter 0.3s ease, opacity 0.3s ease;
}

.socials:hover .link {
  filter: blur(3px);
  opacity: 0.5;
}

.socials .link:hover {
  filter: none;
  opacity: 1;
}

</style>
