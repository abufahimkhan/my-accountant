<script lang="ts">
 import * as Tooltip from "$lib/components/ui/tooltip";
 export let label:string="";
 export let message:string="";
</script>
 
<Tooltip.Root>
 <Tooltip.Trigger><slot></slot></Tooltip.Trigger>
 <Tooltip.Content>
  <p>{message}</p>
 </Tooltip.Content>
</Tooltip.Root>