<script lang="ts">
    import { Button } from "$lib/components/ui/button/index.js";
    import * as Card from "$lib/components/ui/card/index.js";

    const frameworks = [
        {
            value: "sveltekit",
            label: "SvelteKit",
        },
        {
            value: "next",
            label: "Next.js",
        },
        {
            value: "astro",
            label: "Astro",
        },
        {
            value: "nuxt",
            label: "Nuxt.js",
        },
    ];
</script>

<Card.Root class="w-full h-fit overflow-hidden">
    <Card.Header>
        <Card.Title>VISA TEA</Card.Title>
        <Card.Description>Total Expense List</Card.Description>
    </Card.Header>
    <Card.Content class="overflow-auto max-h-[600px]">
        <!-- Make Table Scrollable -->
        <slot></slot>
    </Card.Content>
    <!-- <Card.Footer class="flex justify-between">
        <Button variant="outline">Cancel</Button>
        <Button>Deploy</Button>
    </Card.Footer> -->
</Card.Root>
