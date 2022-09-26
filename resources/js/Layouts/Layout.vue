<template>
    <header class="p-6 flex bg-gray-200 justify-between">
        <h1 class="font-bold text-lg"><Link href="/">My App</Link></h1>
        <p class="text-sm">Welcome back {{ $page.props.auth.user }}</p>

        <Nav />
    </header>

    <section class="p-6 max-w-7xl mx-auto">
        <slot />
    </section>
</template>

<script setup>
import Nav from "@/Components/Nav.vue";
import { Link } from "@inertiajs/inertia-vue3";
</script>
