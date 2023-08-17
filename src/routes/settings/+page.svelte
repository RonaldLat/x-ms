<script>
    import { supabase } from "$lib/supabaseClient.js";
    import { currentUser } from "$lib/store/authState.js";
    let avatar, fileinput;

    const imageUpload = async (e) => {
        let image = e.target.files[0];
        let reader = new FileReader();
        reader.readAsDataURL(image);
        reader.onload = (e) => {
            avatar = e.target.result;
        };

        const { data, error } = await supabase.storage
            .from("dms_users")
            .upload(`/${$currentUser.id}.png`, image, {
                cacheControl: "3600",
                upsert: false,
            });
        console.log(data);
        console.log(error);
    };
</script>

<div id="app">
    <h1>Upload Image</h1>

    {#if avatar}
        <img class="avatar" src={avatar} alt="d" />
    {:else}
        <img
            class="avatar"
            src="https://cdn4.iconfinder.com/data/icons/small-n-flat/24/user-alt-512.png"
            alt=""
        />
    {/if}
    <img
        class="upload"
        src="https://static.thenounproject.com/png/625182-200.png"
        alt=""
        on:click={() => {
            fileinput.click();
        }}
    />
    <div
        class="chan"
        on:click={() => {
            fileinput.click();
        }}
    >
        Choose Image
    </div>
    <input
        style="display:none"
        type="file"
        accept=".jpg, .jpeg, .png"
        on:change={(e) => imageUpload(e)}
        bind:this={fileinput}
    />
</div>
