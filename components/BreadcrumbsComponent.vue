<script setup lang="ts">
import {
  Breadcrumb,
  BreadcrumbItem,
  BreadcrumbLink,
  BreadcrumbList,
  BreadcrumbPage,
  BreadcrumbSeparator,
} from "~/components/ui/breadcrumb";

interface BreadcrumbItem {
  title: string;
  href?: string;
}

defineProps<{
  breadcrumbs: BreadcrumbItem[];
}>();
</script>

<template>
  <Breadcrumb>
    <BreadcrumbList>
      <template v-for="(item, index) in breadcrumbs" :key="index">
        <BreadcrumbItem>
          <template v-if="index === breadcrumbs.length - 1">
            <BreadcrumbPage class="font-bold">{{ item.title }}</BreadcrumbPage>
          </template>
          <template v-else>
            <BreadcrumbLink as-child>
              <NuxtLink :to="{ name: item.href ?? 'index' }">{{
                item.title
              }}</NuxtLink>
            </BreadcrumbLink>
          </template>
        </BreadcrumbItem>
        <BreadcrumbSeparator v-if="index !== breadcrumbs.length - 1" />
      </template>
    </BreadcrumbList>
  </Breadcrumb>
</template>
