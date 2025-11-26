<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { dashboard } from '@/routes';
import { type BreadcrumbItem } from '@/types';
import { Head, usePage } from '@inertiajs/vue3';
import PlaceholderPattern from '@/components/PlaceholderPattern.vue';

import {
    AlertTriangle,
    ArrowDownCircle,
    ArrowUpCircle,
    Boxes,
    CalendarDays,
    Clock,
    DollarSign,
    LineChart,
    Package,
    Truck,
    User,
} from 'lucide-vue-next';

const page = usePage();
const user = page.props.auth.user;

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Dashboard',
        href: dashboard().url,
    },
];
</script>

<template>
    <Head title="Dashboard" />

    <AppLayout :breadcrumbs="breadcrumbs">
        <div
            class="flex h-full flex-1 flex-col gap-6 overflow-x-auto rounded-xl p-4"
        >
            <div class="mb-2 flex items-center justify-between">
                <div>
                    <h1 class="flex items-center gap-2 text-2xl font-bold">
                        Welcome back, {{ user.name }}!
                    </h1>
                    <p class="text-sm text-gray-500 dark:text-gray-400">
                        Here's your inventory overview for today.
                    </p>
                </div>
            </div>

            <div class="grid gap-4 md:grid-cols-4">
                <!-- Total Products -->
                <div
                    class="flex items-start justify-between rounded-xl border bg-white p-4 shadow-sm dark:bg-neutral-900"
                >
                    <div>
                        <h3 class="text-sm text-gray-500">Total Products</h3>
                        <p class="mt-1 text-2xl font-bold">1,240</p>
                        <span class="mt-1 block text-xs text-green-500"
                            >+12 this week</span
                        >
                    </div>
                    <Boxes class="h-8 w-8 text-blue-600" />
                </div>

                <!-- Low Stock -->
                <div
                    class="flex items-start justify-between rounded-xl border bg-white p-4 shadow-sm dark:bg-neutral-900"
                >
                    <div>
                        <h3 class="text-sm text-gray-500">Low Stock Items</h3>
                        <p class="mt-1 text-2xl font-bold">18</p>
                        <span class="mt-1 block text-xs text-red-500"
                            >Needs restocking</span
                        >
                    </div>
                    <AlertTriangle class="h-8 w-8 text-red-600" />
                </div>

                <!-- Suppliers -->
                <div
                    class="flex items-start justify-between rounded-xl border bg-white p-4 shadow-sm dark:bg-neutral-900"
                >
                    <div>
                        <h3 class="text-sm text-gray-500">Total Suppliers</h3>
                        <p class="mt-1 text-2xl font-bold">32</p>
                    </div>
                    <Truck class="h-8 w-8 text-purple-600" />
                </div>

                <!-- Sales -->
                <div
                    class="flex items-start justify-between rounded-xl border bg-white p-4 shadow-sm dark:bg-neutral-900"
                >
                    <div>
                        <h3 class="text-sm text-gray-500">Today’s Sales</h3>
                        <p class="mt-1 text-2xl font-bold">₱8,950</p>
                        <span class="mt-1 block text-xs text-green-500"
                            >+5.3% from yesterday</span
                        >
                    </div>
                    <DollarSign class="h-8 w-8 text-green-600" />
                </div>
            </div>

            <div class="grid gap-4 md:grid-cols-2">
                <!-- CHART -->
                <div
                    class="min-h-[250px] rounded-xl border bg-white p-4 shadow-sm dark:bg-neutral-900"
                >
                    <div class="mb-2 flex items-center gap-2">
                        <LineChart class="h-5 w-5 text-blue-600" />
                        <h3 class="font-semibold">Stock Levels Overview</h3>
                    </div>
                    <div
                        class="relative h-[200px] w-full overflow-hidden rounded-lg border"
                    >
                        <PlaceholderPattern />
                    </div>
                </div>

                <!-- RECENT ACTIVITY -->
                <div
                    class="rounded-xl border bg-white p-4 shadow-sm dark:bg-neutral-900"
                >
                    <div class="mb-4 flex items-center gap-2">
                        <Clock class="h-5 w-5 text-gray-600" />
                        <h3 class="font-semibold">Recent Activity</h3>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="w-full text-sm">
                            <thead class="text-left text-gray-500">
                                <tr>
                                    <th class="pb-2">Item</th>
                                    <th class="pb-2">Qty</th>
                                    <th class="pb-2">Date</th>
                                    <th class="pb-2">Actions</th>
                                </tr>
                            </thead>

                            <tbody class="divide-y">
                                <tr>
                                    <td class="flex items-center gap-2 py-3">
                                        <Package
                                            class="h-4 w-4 text-blue-600"
                                        />
                                        Milk Tea Powder
                                    </td>
                                    <td
                                        class="flex items-center gap-1 text-green-600"
                                    >
                                        <ArrowDownCircle class="h-4 w-4" />
                                        Stock In
                                    </td>
                                    <td>+20</td>
                                    <td class="flex items-center gap-1">
                                        <CalendarDays class="h-4 w-4" /> Feb 3
                                    </td>
                                </tr>

                                <tr>
                                    <td class="flex items-center gap-2 py-3">
                                        <Package
                                            class="h-4 w-4 text-blue-600"
                                        />
                                        Tapioca Pearls
                                    </td>
                                    <td
                                        class="flex items-center gap-1 text-red-600"
                                    >
                                        <ArrowUpCircle class="h-4 w-4" /> Stock
                                        Out
                                    </td>
                                    <td>-10</td>
                                    <td class="flex items-center gap-1">
                                        <CalendarDays class="h-4 w-4" /> Feb 2
                                    </td>
                                </tr>

                                <tr>
                                    <td class="flex items-center gap-2 py-3">
                                        <Package
                                            class="h-4 w-4 text-blue-600"
                                        />
                                        Straw Cup
                                    </td>
                                    <td
                                        class="flex items-center gap-1 text-green-600"
                                    >
                                        <ArrowDownCircle class="h-4 w-4" />
                                        Stock In
                                    </td>
                                    <td>+50</td>
                                    <td class="flex items-center gap-1">
                                        <CalendarDays class="h-4 w-4" /> Feb 2
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

            <div
                class="min-h-[200px] rounded-xl border bg-white p-4 dark:bg-neutral-900"
            >
                <div class="mb-2 flex items-center gap-2">
                    <AlertTriangle class="h-5 w-5 text-yellow-600" />
                    <h3 class="font-semibold">Upcoming Expirations</h3>
                </div>
                <div
                    class="relative h-[150px] w-full overflow-hidden rounded-lg border"
                >
                    <PlaceholderPattern />
                </div>
            </div>
        </div>
    </AppLayout>
</template>
