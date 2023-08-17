<script>
    import { onMount } from "svelte";
    import { Avatar } from "flowbite-svelte";
    import { goto } from "$app/navigation";
    import { supabase } from "$lib/supabaseClient.js";
    import Auth from "./Auth.svelte";
    import { currentUser } from "$lib/store/authState.js";

    const navigationLinks = [
        { label: "New Note", route: "/note" },
        { label: "Home", route: "/" },
        { label: "Notes", route: "/notes" },
        { label: "Settings", route: "/settings" },
        // Add more links as needed
    ];

    function navigateTo(route) {
        goto(route);
    }

    let avatarUrl = "";
    const getImg = async () => {
        const { data } = supabase.storage
            .from("dms_users")
            .getPublicUrl($currentUser.id +'.png');
        avatarUrl = data.publicUrl;
    };
    getImg();
</script>

<nav class="bg-grey-800 p-4">
    <ul class="flex flex-col space-x-4">
        {#each navigationLinks as link (link.label)}
            <li>
                <a
                    href={link.route}
                    class="text-green-600 hover:underline cursor-pointer px-3 py-2 rounded-lg"
                >
                    {link.label}
                </a>
            </li>
        {/each}
    </ul>
    <button
        on:click={() => goto("/register")}
        type="button"
        class="text-white bg-gradient-to-r from-blue-500 via-blue-600 to-blue-700 hover:bg-gradient-to-br focus:ring-4 focus:outline-none focus:ring-blue-300 dark:focus:ring-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center mr-2 mb-2"
        >Register</button
    >

    <Auth />
    {#if $currentUser}
        <p class="bold">{$currentUser.user_metadata.username}</p>
    {/if}
    <Avatar src={avatarUrl} rounded />
</nav>

<style>
    /* Custom styling for active link */
    .font-bold {
        font-weight: bold;
    }
</style>
