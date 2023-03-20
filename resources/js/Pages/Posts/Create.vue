<script setup>
import BreezeAuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import BreezeLabel from '@/Components/InputLabel.vue';
import BreezeInput from '@/Components/TextInput.vue';
import BreezeTextArea from '@/Components/Textarea.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';
const form = useForm({
    Product_Name: '',
    Description: '',
    Quantity: '',
    Price: ''
});
const submit = () => {
    form.post(route('posts.store'));
};
</script>
<template>
    <Head title="Dashboard" />
    <BreezeAuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Create Post
            </h2>
        </template>
        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 bg-white border-b border-gray-200">
                        <div className="flex items-center justify-between mb-6">
                            <Link
                                className="px-6 py-2 text-white bg-blue-500 rounded-md focus:outline-none"
                                :href="route('posts.index')"
                            >
                                Back
                            </Link>
                        </div>
                        <form name="createForm" @submit.prevent="submit">
                                <div className="flex flex-col">
                                    <div className="mb-4">
                                        <BreezeLabel for="Product_Name" value="Product Name" />
                                        
                                        <BreezeInput 
                                            id="Product_Name" 
                                            type="text" 
                                            class="mt-1 block w-full" 
                                            v-model="form.Product_Name" 
                                            autofocus />
                                        <span className="text-red-600" v-if="form.errors.Product_Name">
                                            {{ form.errors.Product_Name }}
                                        </span>
                                    </div>
                                    <div className="mb-4">
                                        <BreezeLabel for="Description" value="Description" />
                                        
                                        <BreezeTextArea 
                                            id="Description" 
                                            class="mt-1 block w-full" 
                                            v-model="form.Description" 
                                            autofocus />
                                        <span className="text-red-600" v-if="form.errors.Description">
                                            {{ form.errors.Description }}
                                        </span>
                                    </div>
                                    <div className="mb-4">
                                        <BreezeLabel for="Quantity" value="Quantity" />
                                        
                                        <BreezeInput 
                                            id="Quantity" 
                                            type="number" 
                                            class="mt-1" 
                                            v-model="form.Quantity" 
                                            autofocus />
                                        <span className="text-red-600" v-if="form.errors.Quantity">
                                            {{ form.errors.Quantity }}
                                        </span>
                                    </div>
                                    <div className="mb-4">
                                        <BreezeLabel for="Price" value="Price" />
                                        
                                        <BreezeInput 
                                            id="Price" 
                                            type="number" 
                                            class="mt-1" 
                                            v-model="form.Price" 
                                            autofocus />
                                        <span className="text-red-600" v-if="form.errors.Price">
                                            {{ form.errors.Price }}
                                        </span>
                                    </div>
                                </div>
  
                                <div className="mt-4">
                                    <button
                                        type="submit"
                                        className="px-6 py-2 font-bold text-white bg-green-500 rounded"
                                    >
                                        Save
                                    </button>
                                </div>
                            </form>
                    </div>
                </div>
            </div>
        </div>
    </BreezeAuthenticatedLayout>
</template>