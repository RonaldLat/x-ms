<script>
    import { supabase } from "$lib/supabaseClient.js";
    import { currentUser } from "$lib/store/authState.js";

    const noteDetails = {
        title: "",
        note: "",
    };

    const createNote = async () => {
        const { data, error } = await supabase
            .from("notes")
            .insert([
                {
                    authorID: $currentUser.id,
                    authorEmail: $currentUser.email,
                    noteTitle: noteDetails.title,
                    note: noteDetails.note,
                },
            ])
            .select();
            noteDetails.title =''
            noteDetails.note =''
            console.log('error', error)
            console.log('data', data)
    };
    console.log($currentUser);
</script>

<form class="flex-col gap-5 w-4/5 mx-auto mt-64 pt-6 -z-10" on:submit={createNote}>
    <div class="relative mb-3">
        <input
            bind:value={noteDetails.title}
            id="title"
            type="text"
            name="title"
            class="text-gray-dark border-2 peer block w-full appearance-none rounded-md border-gray-400 px-0 py-[14px] pl-6 text-sm focus:border-gray-800 focus:outline-none focus:ring-0"
            placeholder=" "
            required
        />
        <label
            for="user_email"
            class="absolute top-4 left-6 text-gray-middle bg-white duration-300 transform -translate-y-6 transparent peer-placeholder-shown:translate-y-0 peer-focus:-translate-y-6 peer-focus:px-[4px] peer-focus:text-gray-dark peer-focus:transparent"
        >
            Note Title
        </label>
    </div>

    <div class="relative mb-3">
        <textarea
            bind:value={noteDetails.note}
            name="email"
            class="text-gray-dark border-2 peer block w-full appearance-none rounded-sm border-gray-400 px-0 py-[14px] pl-6 text-sm focus:border-gray-800 focus:outline-none focus:ring-0"
            placeholder=" "
            required
        />
        <label
            for="note"
            class="absolute top-4 left-6 text-gray-middle bg-white duration-300 transform -translate-y-6 transparent peer-placeholder-shown:translate-y-0 peer-focus:-translate-y-6 peer-focus:px-[4px] peer-focus:text-gray-dark peer-focus:transparent"
        >
            Note
        </label>
        <button type="submit" class="py-3 px-6 bg-blue-400 mt-4 rounded-sm"
            >Create</button
        >
    </div>
</form>
