<template>
    <form class="space-y-6" @submit.prevent="saveCompany">
        <div class="space-y-4 rounded-md shadow-sm">
            <div>
                <label
                    for="name"
                    class="block text-sm font-medium text-gray-700"
                    >Name</label
                >
                <div class="mt-1">
                    <input
                        type="text"
                        name="name"
                        id="name"
                        class="
                            block
                            mt-1
                            w-full
                            rounded-md
                            shadow-sm
                            focus:ring
                            focus:ring-indigo-200
                            focus:ring-opacity-50
                        "
                        :class="{
                            'border-gray-300 focus:border-indigo-300':
                                !errors.name,
                            'border-red-300 focus:border-red-300': errors.name,
                        }"
                        v-model="form.name"
                    />
                    <div
                        class="mt-2 mb-6 text-sm text-red-600"
                        v-if="errors.name"
                    >
                        {{ errors.name }}
                    </div>
                </div>
            </div>

            <div>
                <label
                    for="email"
                    class="block text-sm font-medium text-gray-700"
                    >Email</label
                >
                <div class="mt-1">
                    <input
                        type="text"
                        name="email"
                        id="email"
                        class="
                            block
                            mt-1
                            w-full
                            rounded-md
                            shadow-sm
                            focus:ring
                            focus:ring-indigo-200
                            focus:ring-opacity-50
                        "
                        :class="{
                            'border-gray-300 focus:border-indigo-300':
                                !errors.email,
                            'border-red-300 focus:border-red-300': errors.email,
                        }"
                        v-model="form.email"
                    />
                    <div
                        class="mt-2 mb-6 text-sm text-red-600"
                        v-if="errors.email"
                    >
                        {{ errors.email }}
                    </div>
                </div>
            </div>

            <div>
                <label
                    for="address"
                    class="block text-sm font-medium text-gray-700"
                    >Address</label
                >
                <div class="mt-1">
                    <input
                        type="text"
                        name="address"
                        id="address"
                        class="
                            block
                            mt-1
                            w-full
                            rounded-md
                            border-gray-300
                            shadow-sm
                            focus:border-indigo-300
                            focus:ring
                            focus:ring-indigo-200
                            focus:ring-opacity-50
                        "
                        v-model="form.address"
                    />
                </div>
            </div>

            <div>
                <label
                    for="website"
                    class="block text-sm font-medium text-gray-700"
                    >Website</label
                >
                <div class="mt-1">
                    <input
                        type="text"
                        name="website"
                        id="website"
                        class="
                            block
                            mt-1
                            w-full
                            rounded-md
                            border-gray-300
                            shadow-sm
                            focus:border-indigo-300
                            focus:ring
                            focus:ring-indigo-200
                            focus:ring-opacity-50
                        "
                        v-model="form.website"
                    />
                </div>
            </div>
        </div>

        <button
            type="submit"
            class="
                inline-flex
                items-center
                px-4
                py-2
                text-xs
                font-semibold
                tracking-widest
                text-white
                uppercase
                bg-gray-800
                rounded-md
                border border-transparent
                ring-gray-300
                transition
                duration-150
                ease-in-out
                hover:bg-gray-700
                active:bg-gray-900
                focus:outline-none focus:border-gray-900 focus:ring
                disabled:opacity-25
            "
        >
            Create
        </button>
    </form>
</template>

<script>
import { reactive } from "vue";
import useCompanies from "../../composables/companies";

export default {
    setup() {
        const form = reactive({
            name: "",
            email: "",
            address: "",
            website: "",
        });

        const { errors, storeCompany } = useCompanies();

        const saveCompany = async () => {
            await storeCompany({ ...form });
        };

        return {
            form,
            errors,
            saveCompany,
        };
    },
};
</script>
