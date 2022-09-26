<template>
    <div class="flex justify-between">
        <h1 class="text-3xl font-bold">Users</h1>

        <input
            v-model="search"
            type="text"
            name="search"
            placeholder="Search"
            class="border px-2 rounded-lg"
        />
    </div>

    <!-- The preserve-scroll attribute preserves the scroll. -->
    <!-- <NavLink href="/users" preserve-scroll>Refresh</NavLink> -->

    <div class="bg-white shadow-md rounded my-6">
        <table class="min-w-max w-full table-auto">
            <tbody class="text-gray-600 text-sm font-light">
                <tr
                    v-for="user in users.data"
                    :key="user.id"
                    class="border-b border-gray-200 hover:bg-gray-100"
                >
                    <td class="py-3 px-6 text-left whitespace-nowrap">
                        <div class="flex items-center">
                            <span>{{ user.name }}</span>
                        </div>
                    </td>
                    <td class="py-3 px-6 text-right">
                        <a
                            href="#"
                            class="text-indigo-600 hover:text-indigo-900"
                            >Edit</a
                        >
                    </td>
                </tr>
            </tbody>
        </table>
    </div>

    <!-- Paginator -->
    <Paginator :links="users.links" />
</template>

<script setup>
import Nav from "@/Components/Nav.vue";
import NavLink from "@/Components/NavLink.vue";
import Paginator from "@/Components/Paginator.vue";
import { ref, watch } from "vue";
import { Inertia } from "@inertiajs/inertia";

let props = defineProps({
    users: Object,
    filters: Object,
});

let search = ref(props.filters.search || "");

watch(search, (value) => {
    Inertia.get(
        "/users",
        { search: value },
        { preserveState: true, replace: true }
    );
});
</script>
