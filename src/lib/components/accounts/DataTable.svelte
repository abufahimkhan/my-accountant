<script lang="ts">
    import * as Table from "$lib/components/ui/table/index.js";
    import { Printer } from "@lucide/svelte";
    import { Pencil, RefreshCw, Trash2 } from "lucide-svelte";
    import Button from "../ui/button/button.svelte";
    import TableCardWrapper from "./TableCardWrapper.svelte";
    // Lucide Icons
    import { buttonVariants } from "$lib/components/ui/button/index.js";
    import * as Dialog from "$lib/components/ui/dialog/index.js";
    import { Input } from "$lib/components/ui/input/index.js";
    import { Label } from "$lib/components/ui/label/index.js";
    import DtTooltop from "../common/DTTooltop.svelte";
    import DtModal from "../common/DTModal.svelte";
    const invoices = [
        {
            date: "2024-03-25",
            invoice: "INV001",
            title: "printer",
            description: "Building a company website",
            provider: "For office",
            paymentStatus: "Paid",
            totalAmount: 250.0,
            paymentMethod: "Credit Card",
        },
        {
            date: "2024-03-24",
            invoice: "INV002",
            title: "Employee Table",
            description: "For employees",
            provider: "Jane Smith",
            paymentStatus: "Pending",
            totalAmount: 150.0,
            paymentMethod: "PayPal",
        },
        {
            date: "2024-03-24",
            invoice: "INV002",
            title: "Chair",
            description: "For employees",
            provider: "Jane Smith",
            paymentStatus: "Pending",
            totalAmount: 150.0,
            paymentMethod: "PayPal",
        },
        {
            date: "2024-03-24",
            invoice: "INV002",
            title: "Round Table",
            description: "For Consultancy",
            provider: "Jane Smith",
            paymentStatus: "Pending",
            totalAmount: 150.0,
            paymentMethod: "PayPal",
        },
        {
            date: "2024-03-24",
            invoice: "INV002",
            title: "Boss Chair 1",
            description: "Bought initially",
            provider: "Jane Smith",
            paymentStatus: "Pending",
            totalAmount: 150.0,
            paymentMethod: "PayPal",
        },
        {
            date: "2024-03-24",
            invoice: "INV002",
            title: "Boss Chair 2",
            description: "Bought recently",
            provider: "Jane Smith",
            paymentStatus: "Pending",
            totalAmount: 150.0,
            paymentMethod: "PayPal",
        },
        {
            date: "2024-03-24",
            invoice: "INV002",
            title: "Boss Table",
            description: "Bought at front",
            provider: "Jane Smith",
            paymentStatus: "Pending",
            totalAmount: 150.0,
            paymentMethod: "PayPal",
        },
        {
            date: "2024-03-23",
            invoice: "INV003",
            title: "Electronics",
            description: "Expense on electricians",
            provider: "Michael Brown",
            paymentStatus: "Unpaid",
            totalAmount: 350.0,
            paymentMethod: "Bank Transfer",
        },
    ];

    // Calculate total amount
    const totalAmount = invoices
        .reduce((sum, item) => sum + item.totalAmount, 0)
        .toFixed(2);
</script>

<TableCardWrapper>
    <div class="flex flex-col gap-5">
       <DtModal/>
        <!-- Scrollable Table Wrapper -->
        <div class="overflow-x-auto max-h-[400px]">
            <Table.Root class="min-w-full">
                <Table.Caption>A list of your recent invoices.</Table.Caption>

                <Table.Header
                    class="bg-gray-100 dark:bg-muted sticky top-0 z-10"
                >
                    <Table.Row>
                        <Table.Head>Date</Table.Head>
                        <Table.Head>Invoice</Table.Head>
                        <Table.Head>Title</Table.Head>
                        <Table.Head>Description</Table.Head>
                        <Table.Head>Provider</Table.Head>
                        <Table.Head>Status</Table.Head>
                        <Table.Head>Method</Table.Head>
                        <Table.Head class="text-right">Amount</Table.Head>
                        <Table.Head class="text-center">Actions</Table.Head>
                    </Table.Row>
                </Table.Header>

                <Table.Body>
                    {#each invoices as invoice, i (i)}
                        <Table.Row class="*:text-nowrap">
                            <Table.Cell>{invoice.date}</Table.Cell>
                            <Table.Cell class="font-medium"
                                >{invoice.invoice}</Table.Cell
                            >
                            <Table.Cell>{invoice.title}</Table.Cell>
                            <Table.Cell>{invoice.description}</Table.Cell>
                            <Table.Cell>{invoice.provider}</Table.Cell>
                            <Table.Cell>{invoice.paymentStatus}</Table.Cell>
                            <Table.Cell>{invoice.paymentMethod}</Table.Cell>
                            <Table.Cell class="text-right"
                                >${invoice.totalAmount.toFixed(2)}</Table.Cell
                            >
                            <Table.Cell class="flex justify-center gap-2">
                                <DtTooltop message="Edit Data">
                                    <button
                                        class="p-1 text-blue-500 hover:text-blue-700"
                                    >
                                        <Pencil size={18} />
                                    </button>
                                </DtTooltop>

                                <DtTooltop message="Delete Data">
                                    <button
                                        class="p-1 text-red-500 hover:text-red-700"
                                    >
                                        <Trash2 size={18} />
                                    </button>
                                </DtTooltop>

                                <DtTooltop message="Update Data">
                                    <button
                                        class="p-1 text-green-500 hover:text-green-700"
                                    >
                                        <RefreshCw size={18} />
                                    </button>
                                </DtTooltop>

                                <DtTooltop message="Print Data Sheet">
                                    <button
                                        class="p-1 text-sky-500 hover:text-green-700"
                                    >
                                        <Printer size={18} />
                                    </button>
                                </DtTooltop>
                            </Table.Cell>
                        </Table.Row>
                    {/each}
                </Table.Body>
            </Table.Root>
        </div>

        <!-- Total Amount at the Bottom -->
        <div class="mt-4 mr-52 flex justify-end text-lg font-semibold">
            <span
                >Total Amount: <span class="text-green-600">${totalAmount}</span
                ></span
            >
        </div>
    </div>
</TableCardWrapper>
