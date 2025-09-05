<script setup>
import gsap from "gsap";

const projects = [
  {
    name: "Chatbot Alkam AI",
    live: "https://wa.me/6285784706902?text=.allmenu",
    github: "https://github.com/hik4m",
    techstack: [
      "javascript"
    ],
    image: "/solvedthis.png",
    description:
      "Alkam is a versatile AI Chatbot designed to deliver high utility across various scenarios. Equipped with a range of exciting features, Alkam can engage in intelligent and relevant conversations, answer questions accurately, and assist users in accomplishing complex tasks.",
  },
  {
    name: "Claveto",
    live: "",
    github: "https://github.com/hik4m",
    techstack: ["next.js", "gsap", "lenis"],
    image: "/nike-landing-page.jpg",
    description:
      "Claveto is a dedicated website designed specifically for 12th-grade students, serving as a central hub for all their academic needs. It offers a streamlined platform to access essential learning resources, class announcements, assignment details, and collaborative tools. Claveto aims to simplify the final year of high school by providing students with a clear, organized, and easily accessible resource to help them excel in their studies and prepare for their next steps.",
  },
  {
    name: "MClass",
    live: "",
    github: "https://github.com/hik4m",
    techstack: [
      "next.js",
      "tailwindcss",
      "drizzle orm",
      "supabase",
      "react query",
    ],
    image: "/mclass.png",
    description:
      "MClass is a comprehensive LMS platform that connects students and teachers. It provides features for joining classes, accessing course materials, submitting assignments, and managing classes. MCLASS streamlines the learning process and promotes engagement within a secure digital environment. It is designed to transform online and blended learning.",
  },
  {
    name: "Excom",
    live: "",
    github: "https://github.com/hik4m",
    techstack: [
      "next.js",
      "tailwindcss",
      "drizzle orm",
      "supabase",
      "react query",
      "framer motion",
    ],
    image: "/balmed.png",
    description:
      "Extra Computer is a comprehensive online platform dedicated to all things technology. It serves as your reliable source for the latest computer news, in-depth hardware and software reviews, helpful tutorials, and practical troubleshooting guides. Whether you're looking to upgrade your PC, learn a new skill, or solve a tech dilemma, Extra Computer provides clear, actionable information to help you navigate the digital world with confidence.",
  },
  {
    name: "Movie List",
    live: "",
    github: "https://github.com/hik4m",
    techstack: [
      "astro.js",
      "tailwindcss",
      "react.js",
      "supabase",
      "framer motion",
    ],
    image: "/movie-list.png",
    description:
      "This project is a Movie List web application built with Astro, React, Tailwind CSS, and Supabase. The app allows users to browse and manage a personalized list of movies. Astro handles fast static site generation, while React is used for interactive components. Tailwind CSS ensures a clean and responsive UI design. User authentication and data storage are managed by Supabase, enabling users to sign up, log in, and save their favorite movies securely.",
  },
  {
    name: "What'sNext",
    live: "",
    github: "",
    techstack: [
      "nuxt.js",
      "tailwindcss",
      "drizzle orm",
      "postgresql",
      "better-auth",
    ],
    image: "/whatsnext.png",
    description:
      "What’sNext is a Web Project Management application built with Nuxt, Drizzle ORM, PostgreSQL, and Tailwind CSS. It helps users plan, manage, and track projects and tasks with ease. Powered by Nuxt for a fast and dynamic frontend, Drizzle ORM for type-safe interaction with a PostgreSQL database, and styled with Tailwind CSS for a modern UI, What’sNext offers a clean and efficient experience focused on productivity and team collaboration.",
  },
];

const preload = usePreload();

function startAnimation() {
  const listProjects = document.querySelectorAll(".project");
  const tl = gsap.timeline();

  tl.fromTo(
    ".title-projects",
    {
      y: 20,
      opacity: 0,
    },
    {
      ease: "power4.inOut",
      opacity: 1,
      y: 0,
      duration: 0.5,
    }
  ).to(listProjects, {
    stagger: 0.05,
    duration: 0.75,
    opacity: 1,
    ease: "power3.inOut",
  });
}

onMounted(() => {
  if (preload.value.hasPlayed) {
    startAnimation();
  }
});

watch(
  () => preload.value.hasPlayed,
  () => {
    if (preload.value.hasPlayed) {
      startAnimation();
    }
  }
);
</script>

<template>
  <section class="main-container">
    <h1 class="title-projects">Projets</h1>

    <div class="projects-container">
      <article v-for="project in projects" :key="project.name" class="project">
        <div class="description-project">
          <h2 class="title-project">{{ project.name }}</h2>
          <p class="text-project">
            {{ project.description }}
          </p>
          <div class="link-project">
            <p v-if="project.live" class="link">
              <GoToWebsite
                :href="project.live"
                :text="`site • ${project.name}`"
              >
                live
              </GoToWebsite>
            </p>
            <p v-if="project.github" class="link">
              <GoToWebsite
                :href="project.github"
                :text="`github • ${project.name}`"
              >
                github
              </GoToWebsite>
            </p>
          </div>
          <div class="tech-stack">
            <p
              v-for="stack in project.techstack"
              :key="stack"
              @pointerenter="scrambleHoverAnimation"
            >
              • <span class="link">{{ stack }}</span>
            </p>
          </div>
        </div>

        <div class="image-project">
          <NuxtImg :src="'/portofolio' + project.image" alt="Project Image" />
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.main-container {
  font-family: "PP Editorial", serif;
}

.title-projects {
  font-size: 3em;
  margin-bottom: 5rem;
  opacity: 0;
  text-align: left !important;
}

.projects-container {
  display: flex;
  flex-direction: column;
  gap: 7rem;
  position: relative;
}

.project {
  display: grid;
  grid-template-columns: 2fr 2fr;
  gap: 2rem;
  min-height: 50dvh;
  opacity: 0;
  padding-bottom: 2rem;
}

.project:not(:last-child) {
  border-bottom: 1px #171717 solid;
}

.description-project {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.title-project {
  font-size: 2.2em;
  font-weight: bold;
}

.description-project .text-project {
  font-size: 1.2em;
  line-height: 1.6;
  max-width: 90%;
}

.link-project {
  text-transform: uppercase;
  display: flex;
  gap: 0.75rem;
}

.tech-stack {
  margin-top: auto;
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
  text-transform: uppercase;
  font-family: "Work Sans";
}

.tech-stack p {
  cursor: pointer;
}

.image-project {
  display: flex;
  align-items: center;
  justify-content: end;
}

.image-project img {
  width: 100%;
  max-width: 480px;
  height: 100%;
  filter: blur(5px);
  object-fit: cover;
  border-radius: 0.25rem;
  transition: filter 0.3s cubic-bezier(0.075, 0.82, 0.165, 1);
}

.project:hover .image-project img {
  filter: blur(0px);
}

@media (max-width: 1024px) {
  .project {
    grid-template-columns: 1fr;
  }

  .image-project {
    order: -1;
    justify-content: center;
  }
}

.title-projects {
  text-align: center;
  font-size: 2.5em;

  .title-project {
    font-size: 1.8em;
  }

  .description-project .text-project {
    font-size: 1.1em;
  }

  .tech-stack {
    font-size: 0.95em;
  }
}

@media (max-width: 600px) {
  .main-container {
    padding: 1rem;
  }

  .project {
    gap: 1.5rem;
  }

  .title-projects {
    font-size: 2em;
  }

  .title-project {
    font-size: 1.6em;
  }

  .description-project .text-project {
    font-size: 1em;
  }

  .tech-stack {
    font-size: 0.85em;
  }

  .link-project {
    gap: 0.5rem;
  }

  .image-project img {
    max-width: 100%;
  }
  .image-project img {
    filter: blur(0px);
  }
}
</style>
