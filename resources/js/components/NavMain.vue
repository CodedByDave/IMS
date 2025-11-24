<script setup lang="ts">
import {
    SidebarGroup,
    SidebarGroupLabel,
    SidebarMenu,
    SidebarMenuButton,
    SidebarMenuItem,
} from '@/components/ui/sidebar';
import { urlIsActive } from '@/lib/utils';
import { type NavItem } from '@/types';
import { Link, usePage } from '@inertiajs/vue3';
import { ChevronDown } from 'lucide-vue-next';
import { ref } from 'vue';

defineProps<{ items: NavItem[] }>();

const page = usePage();
const openItems = ref<NavItem[]>([]);

function toggle(item: NavItem) {
    if (openItems.value.includes(item)) {
        openItems.value = openItems.value.filter((i) => i !== item);
    } else {
        openItems.value.push(item);
    }
}

function isOpen(item: NavItem) {
    return openItems.value.includes(item);
}
</script>

<template>
    <SidebarGroup class="px-2 py-0">
        <SidebarGroupLabel>Platform</SidebarGroupLabel>
        <SidebarMenu>
            <SidebarMenuItem v-for="item in items" :key="item.title">
                <!-- Parent with children -->
                <div
                    v-if="item.children"
                    class="flex cursor-pointer items-center justify-between rounded p-2 text-sm font-medium hover:bg-accent hover:text-accent-foreground"
                    :class="{
                        'bg-accent text-accent-foreground': isOpen(item),
                    }"
                    @click="toggle(item)"
                >
                    <div class="flex items-center space-x-2">
                        <component
                            :is="item.icon"
                            v-if="item.icon"
                            class="h-5 w-5 text-muted-foreground"
                        />
                        <span>{{ item.title }}</span>
                    </div>
                    <ChevronDown
                        class="h-4 w-4 text-muted-foreground transition-transform"
                        :class="{ 'rotate-180': isOpen(item) }"
                    />
                </div>

                <!-- Single link items -->
                <SidebarMenuButton
                    v-else
                    as-child
                    :is-active="urlIsActive(item.href, page.url)"
                >
                    <Link
                        :href="item.href"
                        class="flex items-center rounded p-2 text-sm font-medium hover:bg-accent hover:text-accent-foreground"
                    >
                        <component
                            :is="item.icon"
                            v-if="item.icon"
                            class="h-5 w-5 text-muted-foreground"
                        />
                        <span class="ml-2">{{ item.title }}</span>
                    </Link>
                </SidebarMenuButton>

                <!-- Render children if open -->
                <div
                    v-if="item.children && isOpen(item)"
                    class="mt-1 ml-4 space-y-1 border-l border-border pl-2"
                >
                    <SidebarMenuItem
                        v-for="child in item.children"
                        :key="child.title"
                    >
                        <SidebarMenuButton
                            as-child
                            :is-active="urlIsActive(child.href, page.url)"
                        >
                            <Link
                                :href="child.href"
                                class="flex items-center rounded p-2 text-sm font-medium hover:bg-accent hover:text-accent-foreground"
                            >
                                <component
                                    :is="child.icon"
                                    v-if="child.icon"
                                    class="h-4 w-4 text-muted-foreground"
                                />
                                <span class="ml-2">{{ child.title }}</span>
                            </Link>
                        </SidebarMenuButton>
                    </SidebarMenuItem>
                </div>
            </SidebarMenuItem>
        </SidebarMenu>
    </SidebarGroup>
</template>
