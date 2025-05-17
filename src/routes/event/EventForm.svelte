<script lang="ts">
  import { goto } from "$app/navigation";
  import { v4 as uuidv4 } from "uuid";
  import { loggedInUser } from "$lib/runes.svelte";

  let uuid = self.crypto.randomUUID();
  let event = $state(0);

  async function addEvent() {
    
  }

</script>

<div class="field">
  <label class="label">Playlist Title</label> <input class="input" type="text" placeholder="Enter playlist title" name="title">
</div>
<button class="button is-link">Add Playlist</button>


  addPlaylist: {
    handler: async function (request, h) {
      const newPlayList = {
        title: request.payload.title,
      };
      await db.playlistStore.addPlaylist(newPlayList);
      return h.redirect("/dashboard");
    },

    