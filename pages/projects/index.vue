<script setup lang="ts">
const title = "Projects";
useAppTitle(title);
const breadcrumbs = useBreadcrumbs();
breadcrumbs.value = [{ title: title, href: "/projects" }];
definePageMeta({
  title: title,
  meta: [
    {
      name: "description",
      content: "Dashboard page description",
    },
  ],
});

const { projects } = await useContent();
</script>
<template>
  <div class="flex h-full flex-1 flex-col gap-4 rounded-xl p-4">
    <div class="grid auto-rows-min gap-4 md:grid-cols-3">
      <ProjectCard
        v-for="project in projects"
        :key="project.name"
        :project="project"
        class="relative aspect-video overflow-hidden rounded-xl border border-sidebar-border/70 dark:border-sidebar-border p-2"
      />
    </div>
  </div>
</template>
