<script lang="ts">
    import * as Card from "$lib/components/ui/card/index.js";
    export let title:string="";
    export let description:string="";
</script>

<Card.Root class="w-full h-fit overflow-hidden">
    <Card.Header>
        <Card.Title>{title}</Card.Title>
        <Card.Description>{description}</Card.Description>
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
