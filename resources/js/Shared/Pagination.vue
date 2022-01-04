<template>
    <div v-if="links.length > 3" class="bg-white px-4 py-3 flex items-center justify-between border-t border-gray-200 sm:px-6">
        <div class="hidden sm:flex-1 sm:flex sm:items-center sm:justify-between">
            <div>
                <nav class="relative z-0 inline-flex rounded-md shadow-sm -space-x-px" aria-label="Pagination">
                    <Link v-for="(link, k) in links" :key="k"
                       v-html="link.label"
                       :href="link.url"
                       :disabled="link.url === null"
                       :class="{'z-10 bg-indigo-50 border-indigo-500 text-indigo-600': link.active, 'bg-gray-100' : link.url === null}"
                       aria-current="page" class="bg-white border-gray-300 text-gray-500 hover:bg-gray-50 relative inline-flex items-center px-4 py-2 border text-sm font-medium"
                    />
                </nav>
            </div>
        </div>
    </div>
</template>

<script>
import {Link} from '@inertiajs/inertia-vue3'
export default {
    components: {Link},
    props: {
        links: Array,
    }
}
</script>
