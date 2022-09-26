<template>
    <div>
        <Component
            :is="link.url ? 'Link' : 'span'"
            v-for="link in links"
            :href="link.url"
            v-html="link.label"
            class="p-2"
            :class="
                (link.url ? '' : 'text-gray-400',
                link.active ? 'border rounded-full' : '')
            "
        />
    </div>
</template>

<script>
import { Link } from "@inertiajs/inertia-vue3";

export default {
    props: {
        links: Array,
    },
    components: {
        Link,
    },
};
</script>
