
<script setup lang="ts">
import { dashboard, login, register } from '@/routes';
import { Head, Link } from '@inertiajs/vue3';

withDefaults(
    defineProps<{
        canRegister: boolean;
    }>(),
    {
        canRegister: true,
    },
);
</script>

<template>
    <Head title="Inventory Management System">
        <link rel="preconnect" href="https://rsms.me/" />
        <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
    </Head>
    <div
        class="flex min-h-screen flex-col items-center bg-gradient-to-br from-slate-50 to-blue-50 p-6 text-slate-900 lg:justify-center lg:p-8 dark:from-slate-950 dark:to-slate-900 dark:text-slate-100"
    >
        <header
            class="mb-6 w-full max-w-[335px] text-sm not-has-[nav]:hidden lg:max-w-5xl"
        >
            <nav class="flex items-center justify-end gap-4">
                <Link
                    v-if="$page.props.auth.user"
                    :href="dashboard()"
                    class="inline-block rounded-lg border border-slate-300 bg-white px-5 py-2 text-sm font-medium text-slate-700 transition-all hover:border-slate-400 hover:shadow-sm dark:border-slate-700 dark:bg-slate-800 dark:text-slate-200 dark:hover:border-slate-600"
                >
                    Dashboard
                </Link>
                <template v-else>
                    <Link
                        :href="login()"
                        class="inline-block rounded-lg px-5 py-2 text-sm font-medium text-slate-700 transition-colors hover:text-slate-900 dark:text-slate-300 dark:hover:text-slate-100"
                    >
                        Log in
                    </Link>
                    <Link
                        v-if="canRegister"
                        :href="register()"
                        class="inline-block rounded-lg bg-blue-600 px-5 py-2 text-sm font-medium text-white transition-all hover:bg-blue-700 hover:shadow-lg dark:bg-blue-500 dark:hover:bg-blue-600"
                    >
                        Get Started
                    </Link>
                </template>
            </nav>
        </header>

        <div class="flex w-full items-center justify-center opacity-100 transition-opacity duration-750 lg:grow starting:opacity-0">
            <main class="flex w-full max-w-[335px] flex-col overflow-hidden lg:max-w-5xl lg:flex-row lg:gap-12">
                <!-- Left Content Section -->
                <div class="flex-1 lg:py-12">
                    <div class="mb-8">
                        <div class="mb-4 inline-flex items-center gap-2 rounded-full bg-blue-100 px-4 py-1.5 text-sm font-medium text-blue-700 dark:bg-blue-900/30 dark:text-blue-300">
                            <svg class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M20 7l-8-4-8 4m16 0l-8 4m8-4v10l-8 4m0-10L4 7m8 4v10M4 7v10l8 4" />
                            </svg>
                            Inventory Management
                        </div>
                        <h1 class="mb-4 text-4xl font-bold tracking-tight text-slate-900 lg:text-5xl dark:text-white">
                            Take Control of Your Inventory
                        </h1>
                        <p class="mb-8 text-lg text-slate-600 dark:text-slate-400">
                            Streamline your stock management with real-time tracking, automated alerts, and comprehensive analytics. Built for businesses that demand efficiency.
                        </p>
                    </div>

                    <!-- Features List -->
                    <ul class="mb-8 space-y-4">
                        <li class="flex items-start gap-3">
                            <div class="mt-1 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-green-100 dark:bg-green-900/30">
                                <svg class="h-4 w-4 text-green-600 dark:text-green-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                </svg>
                            </div>
                            <div>
                                <h3 class="font-semibold text-slate-900 dark:text-white">Real-Time Stock Tracking</h3>
                                <p class="text-sm text-slate-600 dark:text-slate-400">Monitor inventory levels across multiple locations instantly</p>
                            </div>
                        </li>
                        <li class="flex items-start gap-3">
                            <div class="mt-1 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-green-100 dark:bg-green-900/30">
                                <svg class="h-4 w-4 text-green-600 dark:text-green-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                </svg>
                            </div>
                            <div>
                                <h3 class="font-semibold text-slate-900 dark:text-white">Automated Alerts</h3>
                                <p class="text-sm text-slate-600 dark:text-slate-400">Get notified when stock levels reach critical thresholds</p>
                            </div>
                        </li>
                        <li class="flex items-start gap-3">
                            <div class="mt-1 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-green-100 dark:bg-green-900/30">
                                <svg class="h-4 w-4 text-green-600 dark:text-green-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                </svg>
                            </div>
                            <div>
                                <h3 class="font-semibold text-slate-900 dark:text-white">Advanced Analytics</h3>
                                <p class="text-sm text-slate-600 dark:text-slate-400">Gain insights with detailed reports and forecasting tools</p>
                            </div>
                        </li>
                        <li class="flex items-start gap-3">
                            <div class="mt-1 flex h-6 w-6 shrink-0 items-center justify-center rounded-full bg-green-100 dark:bg-green-900/30">
                                <svg class="h-4 w-4 text-green-600 dark:text-green-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                                </svg>
                            </div>
                            <div>
                                <h3 class="font-semibold text-slate-900 dark:text-white">Multi-User Access</h3>
                                <p class="text-sm text-slate-600 dark:text-slate-400">Collaborate with your team with role-based permissions</p>
                            </div>
                        </li>
                    </ul>

                    <!-- CTA Buttons -->
                    <div class="flex flex-wrap gap-4">
                        <Link
                            v-if="canRegister"
                            :href="register()"
                            class="inline-flex items-center gap-2 rounded-lg bg-blue-600 px-6 py-3 font-semibold text-white transition-all hover:bg-blue-700 hover:shadow-lg dark:bg-blue-500 dark:hover:bg-blue-600"
                        >
                            Start Free Trial
                            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
                            </svg>
                        </Link>
                        <a
                            href="#features"
                            class="inline-flex items-center gap-2 rounded-lg border border-slate-300 bg-white px-6 py-3 font-semibold text-slate-700 transition-all hover:border-slate-400 hover:shadow-sm dark:border-slate-700 dark:bg-slate-800 dark:text-slate-200 dark:hover:border-slate-600"
                        >
                            Learn More
                        </a>
                    </div>
                </div>

                <!-- Right Visual Section -->
                <div class="relative mt-8 flex items-center justify-center lg:mt-0 lg:w-[480px]">
                    <div class="relative w-full rounded-2xl bg-gradient-to-br from-blue-500 to-purple-600 p-8 shadow-2xl">
                        <!-- Dashboard Preview Card -->
                        <div class="space-y-4 rounded-xl bg-white p-6 shadow-lg dark:bg-slate-800">
                            <div class="flex items-center justify-between">
                                <h3 class="text-lg font-semibold text-slate-900 dark:text-white">Inventory Overview</h3>
                                <span class="rounded-full bg-green-100 px-3 py-1 text-xs font-medium text-green-700 dark:bg-green-900/30 dark:text-green-400">Live</span>
                            </div>

                            <!-- Stats Grid -->
                            <div class="grid grid-cols-2 gap-4">
                                <div class="rounded-lg bg-slate-50 p-4 dark:bg-slate-700/50">
                                    <p class="text-xs text-slate-600 dark:text-slate-400">Total Items</p>
                                    <p class="text-2xl font-bold text-slate-900 dark:text-white">2,847</p>
                                    <p class="text-xs text-green-600 dark:text-green-400">↑ 12.5%</p>
                                </div>
                                <div class="rounded-lg bg-slate-50 p-4 dark:bg-slate-700/50">
                                    <p class="text-xs text-slate-600 dark:text-slate-400">Low Stock</p>
                                    <p class="text-2xl font-bold text-slate-900 dark:text-white">23</p>
                                    <p class="text-xs text-amber-600 dark:text-amber-400">⚠ Alert</p>
                                </div>
                                <div class="rounded-lg bg-slate-50 p-4 dark:bg-slate-700/50">
                                    <p class="text-xs text-slate-600 dark:text-slate-400">Value</p>
                                    <p class="text-2xl font-bold text-slate-900 dark:text-white">$142K</p>
                                    <p class="text-xs text-green-600 dark:text-green-400">↑ 8.2%</p>
                                </div>
                                <div class="rounded-lg bg-slate-50 p-4 dark:bg-slate-700/50">
                                    <p class="text-xs text-slate-600 dark:text-slate-400">Categories</p>
                                    <p class="text-2xl font-bold text-slate-900 dark:text-white">18</p>
                                    <p class="text-xs text-slate-600 dark:text-slate-400">Active</p>
                                </div>
                            </div>

                            <!-- Recent Activity -->
                            <div class="space-y-2 pt-2">
                                <p class="text-xs font-medium text-slate-600 dark:text-slate-400">Recent Activity</p>
                                <div class="space-y-2">
                                    <div class="flex items-center gap-2 text-xs">
                                        <div class="h-2 w-2 rounded-full bg-blue-500"></div>
                                        <span class="text-slate-700 dark:text-slate-300">Stock updated: Office Supplies</span>
                                    </div>
                                    <div class="flex items-center gap-2 text-xs">
                                        <div class="h-2 w-2 rounded-full bg-green-500"></div>
                                        <span class="text-slate-700 dark:text-slate-300">New item added: Laptop Dell XPS</span>
                                    </div>
                                    <div class="flex items-center gap-2 text-xs">
                                        <div class="h-2 w-2 rounded-full bg-amber-500"></div>
                                        <span class="text-slate-700 dark:text-slate-300">Low stock alert: Printer Ink</span>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!-- Floating Elements -->
                        <div class="absolute -right-4 -top-4 rounded-lg bg-white p-3 shadow-lg dark:bg-slate-800">
                            <svg class="h-8 w-8 text-blue-600 dark:text-blue-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z" />
                            </svg>
                        </div>
                        <div class="absolute -bottom-4 -left-4 rounded-lg bg-white p-3 shadow-lg dark:bg-slate-800">
                            <svg class="h-8 w-8 text-purple-600 dark:text-purple-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
                            </svg>
                        </div>
                    </div>
                </div>
            </main>
        </div>
    </div>
</template>
