<script>
    import "../app.css";
    import Icon from "@iconify/svelte";

    import Nav from "../lib/components/Nav.svelte";
    import { goto } from "$app/navigation";

    const handleClick = (url) => {
        goto(url);
    };
</script>

<Nav />
<slot />

<div
    class="fixed z-50 w-full h-16 max-w-lg -translate-x-1/2 bg-white border border-gray-200 rounded-full bottom-4 left-1/2 dark:bg-gray-700 dark:border-gray-600"
>
    <div class="grid h-full max-w-lg grid-cols-5 mx-auto">
    <a href="/" class="inline-flex" >
        <button
            data-tooltip-target="tooltip-home"
            type="button"
            class="inline-flex flex-col items-center justify-center px-5 rounded-l-full hover:bg-gray-50 dark:hover:bg-gray-800 group"
        >
            <Icon icon="mdi:home" class="text-gray-300 w-7 h-7" />
        </button>
    </a>
        <div
            id="tooltip-home"
            role="tooltip"
            class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700"
        >
            Home
            <div class="tooltip-arrow" data-popper-arrow />
        </div>

    <a href="/tags" class="inline-flex" >
        <button
            data-tooltip-target="tooltip-wallet"
            type="button"
            class="inline-flex flex-col items-center justify-center px-5 hover:bg-gray-50 dark:hover:bg-gray-800 group"
        >
            <Icon icon="mdi:tag" class="text-gray-300 w-7 h-7" />
        </button>
    </a>
        <div
            id="tooltip-wallet"
            role="tooltip"
            class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700"
        >
            Tags
            <div class="tooltip-arrow" data-popper-arrow />
        </div>
        <div class="flex items-center justify-center">
    <a href="/new" class="inline-flex" >
            <button
                data-tooltip-target="tooltip-new"
                type="button"
                class="inline-flex items-center justify-center w-10 h-10 font-medium bg-blue-600 rounded-full hover:bg-blue-700 group focus:ring-4 focus:ring-blue-300 focus:outline-none dark:focus:ring-blue-800"
            >
                <Icon icon="mdi:plus" class="text-gray-100 w-7 h-7" />
            </button>
    </a>
        </div>
        <div
            id="tooltip-new"
            role="tooltip"
            class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700"
        >
            Create new item
            <div class="tooltip-arrow" data-popper-arrow />
        </div>
    <a href="/bookmarks" class="inline-flex" >
        <button
            data-tooltip-target="tooltip-settings"
            type="button"
            class="inline-flex flex-col items-center justify-center px-5 hover:bg-gray-50 dark:hover:bg-gray-800 group"
        >
            <Icon icon="mdi:bookmark-multiple" class="text-gray-300 w-7 h-7" />
        </button>
    </a>
        <div
            id="tooltip-settings"
            role="tooltip"
            class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700"
        >
            Bookmarks
            <div class="tooltip-arrow" data-popper-arrow />
        </div>
    <a href="/account" class="inline-flex" >
        <button
            data-tooltip-target="tooltip-profile"
            type="button"
            class="inline-flex flex-col items-center justify-center px-5 rounded-r-full hover:bg-gray-50 dark:hover:bg-gray-800 group"
        >
            <Icon icon="mdi:account" class="text-gray-300 w-7 h-7" />
        </button>
    </a>
        <div
            id="tooltip-profile"
            role="tooltip"
            class="absolute z-10 invisible inline-block px-3 py-2 text-sm font-medium text-white transition-opacity duration-300 bg-gray-900 rounded-lg shadow-sm opacity-0 tooltip dark:bg-gray-700"
        >
            Profile
            <div class="tooltip-arrow" data-popper-arrow />
        </div>
    </div>
</div>
