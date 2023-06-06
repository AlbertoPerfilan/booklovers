<script>
	import { loginGoogle } from "$lib/firebase/auth.client";
	import messagesStore from "$lib/stores/messages.store";

  async function handleClickLoginGoogle() {
    try {
      const user = await loginGoogle()
      console.log(user);
    } catch (error) {
      if(error.code === 'auth/popup-closed-by-user'){
        return
      }
      console.log(error);
      messagesStore.showError()
    }
  }
</script>

<div class="row">
	<div class="col">
		<button class="btn btn-primary w-100" on:click={handleClickLoginGoogle}> Login with google </button>
	</div>
</div>
