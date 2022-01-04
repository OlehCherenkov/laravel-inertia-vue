<template>
    <header class="bg-white shadow mb-10">
        <div class="max-w-7xl mx-auto py-6 px-4 sm:px-6 lg:px-8">
            <h1 class="text-3xl font-bold text-gray-900">
                {{ title }}
            </h1>
        </div>
    </header>
    <Link :href="route('users.index')" class="text-indigo-600 hover:text-indigo-900 my-5 block">
        Back
    </Link>
    <form @submit.prevent="store">
        <div class="shadow overflow-hidden sm:rounded-md">
            <div class="px-4 py-5 bg-white sm:p-6">
                <div class="grid grid-cols-6 gap-6">
                    <div class="col-span-6">
                        <label class="block text-sm font-medium text-gray-700">Name</label>
                        <input v-model="form.name" :class="{'border-red-500': form.errors.name}" type="text"
                               class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border border-gray-300 rounded-md">
                        <div class="text-red-500 mt-2" v-if="form.errors.name">{{ form.errors.name }}</div>
                    </div>
                    <div class="col-span-6">
                        <label class="block text-sm font-medium text-gray-700">Email</label>
                        <input v-model="form.email" :class="{'border-red-500': form.errors.email}" type="email"
                               class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border border-gray-300 rounded-md">
                        <div class="text-red-500 mt-2" v-if="form.errors.email">{{ form.errors.email }}</div>
                    </div>
                    <div class="col-span-6">
                        <label class="block text-sm font-medium text-gray-700">Password</label>
                        <input v-model="form.password" :class="{'border-red-500': form.errors.password}" type="password"
                               class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border border-gray-300 rounded-md">
                        <div class="text-red-500 mt-2" v-if="form.errors.password">{{ form.errors.password }}</div>
                    </div>
                </div>
            </div>
            <div class="px-4 py-3 bg-gray-50 text-right sm:px-6">
                <button
                    type="submit"
                    class="inlite-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 ">
                    Create
                </button>
            </div>
        </div>
    </form>
</template>

<script>
import {Link, useForm} from '@inertiajs/inertia-vue3'
export default {
    components: {Link},
    props: {
        title: String,
    },
    setup() {
        const form = useForm({
            name: null,
            email: null,
            password: null
        })
        function store() {
            form.post(route('users.store'))
        }
        return {form, store}
    },
}
</script>