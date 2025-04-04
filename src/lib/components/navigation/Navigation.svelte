<script lang="ts">
    import {
        CircleUser,
        Menu,
        Moon,
        Package2,
        Search,
        Sun,
    } from "@lucide/svelte";
    import { Button } from "$lib/components/ui/button/index.js";
    import * as DropdownMenu from "$lib/components/ui/dropdown-menu/index.js";
    import { Input } from "$lib/components/ui/input/index.js";
    import * as Sheet from "$lib/components/ui/sheet/index.js";
    import { ModeWatcher, toggleMode } from "mode-watcher";

    const menuItems = [
        { label: "Dashboard", href: "/dashboard" },
        { label: "Daily Expences", href: "/daily-expenses" },
        { label: "Customer List", href: "/customer-list" },
        { label: "Services", href: "/services" },
        { label: "Analytics", href: "/analytics" },
    ];
</script>

<header
    class="bg-background sticky top-0 flex h-16 items-center gap-4 border-b px-4 md:px-6"
>
    <nav class="hidden md:flex md:items-center md:gap-5 md:text-sm lg:gap-6">
        <a
            href="/"
            class="flex items-center gap-2 text-lg font-semibold md:text-base"
        >
            <Package2 class="h-6 w-6" />
            <span class="sr-only">Deploys Tech</span>
        </a>
        {#each menuItems as item}
            <a
                href={item.href}
                class="text-muted-foreground hover:text-foreground transition-colors text-nowrap"
            >
                {item.label}
            </a>
        {/each}
    </nav>

    <Sheet.Root>
        <Sheet.Trigger asChild let:builder>
            <Button
                variant="outline"
                size="icon"
                class="shrink-0 md:hidden"
                builders={[builder]}
            >
                <Menu class="h-5 w-5" />
                <span class="sr-only">Toggle navigation menu</span>
            </Button>
        </Sheet.Trigger>
        <Sheet.Content side="left">
            <nav class="grid gap-6 text-lg font-medium">
                <a
                    href="/"
                    class="flex items-center gap-2 text-lg font-semibold"
                >
                    <Package2 class="h-6 w-6" />
                    <span class="sr-only">Acme Inc</span>
                </a>
                {#each menuItems as item}
                    <a href={item.href} class="hover:text-foreground">
                        {item.label}
                    </a>
                {/each}
            </nav>
        </Sheet.Content>
    </Sheet.Root>

    <div class="flex w-full items-center gap-4 md:ml-auto md:gap-2 lg:gap-4">
        <form class="ml-auto flex-1 sm:flex-initial">
            <div class="relative">
                <Search
                    class="text-muted-foreground absolute left-2.5 top-2.5 h-4 w-4"
                />
                <Input
                    type="search"
                    placeholder="Search products..."
                    class="pl-8 sm:w-[300px] md:w-[200px] lg:w-[300px]"
                />
            </div>
        </form>
        <ModeWatcher />
        <Button on:click={toggleMode} variant="outline" size="icon">
            <Sun
                class="h-[1.2rem] w-[1.2rem] rotate-0 scale-100 transition-all dark:-rotate-90 dark:scale-0"
            />
            <Moon
                class="absolute h-[1.2rem] w-[1.2rem] rotate-90 scale-0 transition-all dark:rotate-0 dark:scale-100"
            />
            <span class="sr-only">Toggle theme</span>
        </Button>
        <DropdownMenu.Root>
            <DropdownMenu.Trigger asChild let:builder>
                <Button
                    builders={[builder]}
                    variant="secondary"
                    size="icon"
                    class="rounded-full"
                >
                    <CircleUser class="h-5 w-5" />
                    <span class="sr-only">Toggle user menu</span>
                </Button>
            </DropdownMenu.Trigger>
            <DropdownMenu.Content align="end">
                <DropdownMenu.Label>My Account</DropdownMenu.Label>
                <DropdownMenu.Separator />
                <DropdownMenu.Item>Settings</DropdownMenu.Item>
                <DropdownMenu.Item>Support</DropdownMenu.Item>
                <DropdownMenu.Separator />
                <DropdownMenu.Item>Logout</DropdownMenu.Item>
            </DropdownMenu.Content>
        </DropdownMenu.Root>
    </div>
</header>
