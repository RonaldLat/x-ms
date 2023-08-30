<script>
    import "../app.css";
    import Icon from "@iconify/svelte";
    import { goto } from "$app/navigation";
    import Nav from "../lib/components/Nav.svelte";
</script>

<div class="relative">
    <div class="fixed right-1 top-1 -z-10">
        <Nav />
    </div>
    <div class="mt-32
    ">
    <slot />
    </div>
    <div class="fixed right-6 bottom-2 z-50 bg-blue-600 p-3 rounded-md" on:click={()=>goto('/new')}>
        <Icon icon="mdi:note-plus" class=" text-gray-100  text-3xl"  />
    </div>
</div>
