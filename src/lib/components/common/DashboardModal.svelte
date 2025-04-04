<script lang="ts">
    import * as Dialog from "$lib/components/ui/dialog/index.js";
    import { Input } from "$lib/components/ui/input/index.js";
    import { Label } from "$lib/components/ui/label/index.js";
    import Button from "../ui/button/button.svelte";

    let invoiceData = {
        date: "",
        invoice: "",
        title: "",
        description: "",
        provider: "",
        paymentStatus: "",
        totalAmount: "",
        paymentMethod: "",
    };

    function handleSubmit() {
        console.log("Form Submitted:", invoiceData);
    }
</script>

<Dialog.Root>
    <Dialog.Trigger
        class="w-fit text-white rounded-full text-sm font-bold bg-blue-500 px-3 py-1"
    >
        Add Invoice
    </Dialog.Trigger>

    <Dialog.Content class="w-full sm:max-w-[800px]">
        <Dialog.Header>
            <Dialog.Title>Add Invoice</Dialog.Title>
            <Dialog.Description>
                Fill in the details below to add a new invoice.
            </Dialog.Description>
        </Dialog.Header>

        <form on:submit|preventDefault={handleSubmit} class="grid gap-6 py-6">
            <!-- Date and Invoice Fields Side by Side -->
            <div class="grid grid-cols-2 gap-4">
                <div class="grid grid-cols-1 gap-2">
                    <Label for="date" class="text-left">Date</Label>
                    <Input
                        id="date"
                        type="date"
                        bind:value={invoiceData.date}
                        class="w-full"
                        required
                    />
                </div>

                <div class="grid grid-cols-1 gap-2">
                    <Label for="invoice" class="text-left">Invoice #</Label>
                    <Input
                        id="invoice"
                        bind:value={invoiceData.invoice}
                        class="w-full"
                        required
                    />
                </div>
            </div>

            <!-- Title and Description Fields Side by Side -->
            <div class="grid grid-cols-2 gap-4">
                <div class="grid grid-cols-1 gap-2">
                    <Label for="title" class="text-left">Title</Label>
                    <Input
                        id="title"
                        bind:value={invoiceData.title}
                        class="w-full"
                        required
                    />
                </div>

                <div class="grid grid-cols-1 gap-2">
                    <Label for="description" class="text-left"
                        >Description</Label
                    >
                    <Input
                        id="description"
                        bind:value={invoiceData.description}
                        class="w-full"
                        required
                    />
                </div>
            </div>

            <!-- Provider and Status Fields Side by Side -->
            <div class="grid grid-cols-2 gap-4">
                <div class="grid grid-cols-1 gap-2">
                    <Label for="provider" class="text-left">Provider</Label>
                    <Input
                        id="provider"
                        bind:value={invoiceData.provider}
                        class="w-full"
                        required
                    />
                </div>

                <div class="grid grid-cols-1 gap-2">
                    <Label for="paymentStatus" class="text-left">Status</Label>
                    <Input
                        id="paymentStatus"
                        bind:value={invoiceData.paymentStatus}
                        class="w-full"
                        required
                    />
                </div>
            </div>

            <!-- Amount and Payment Method Fields Side by Side -->
            <div class="grid grid-cols-2 gap-4">
                <div class="grid grid-cols-1 gap-2">
                    <Label for="totalAmount" class="text-left">Amount ($)</Label
                    >
                    <Input
                        id="totalAmount"
                        type="number"
                        step="0.01"
                        bind:value={invoiceData.totalAmount}
                        class="w-full"
                        required
                    />
                </div>

                <div class="grid grid-cols-1 gap-2">
                    <Label for="paymentMethod" class="text-left">Method</Label>
                    <Input
                        id="paymentMethod"
                        bind:value={invoiceData.paymentMethod}
                        class="w-full"
                        required
                    />
                </div>
            </div>

            <Dialog.Footer>
                <Button type="submit">Save Invoice</Button>
            </Dialog.Footer>
        </form>
    </Dialog.Content>
</Dialog.Root>
