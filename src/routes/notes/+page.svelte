<script>
    import Note from "../../lib/components/Note.svelte";
    import { supabase } from "$lib/supabaseClient.js";
    import { currentUser } from "$lib/store/authState.js";
    import { notes } from "$lib/store/notes.js";

    const getNotes = async () => {
        let { data, error } = await supabase
            .from("notes")
            .select()
            .eq('authorID', $currentUser.id).order('created_at', { ascending: false })
        $notes = data;
        console.log("error", error);
        console.log("data", data);
    };
    getNotes()
        console.log("notes", notes);

</script>

<div class="mx-auto container py-20 px-6 grid grid-cols-1 md:grid-cols-2 gap-3 md:gap-5 place-items-center items-center w-full justify-items-center mt-2 ">
    {#each $notes as note}
        <Note {note} />
    {/each}
</div>
