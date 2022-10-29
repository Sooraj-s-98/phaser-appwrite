<script>
  import { onMount } from "svelte";
  import { navigate } from "svelte-routing";
import GameLetGo from "../component/GameLetGo.svelte";
  import api from "../api/index";
  import { user } from "../store/index";


  async function logOut() {
    try {
      await api.deleteCurrentSession();
      user.update(() => null);
      navigate("/");
    } catch (e) {}
  }
</script>

<div class="container">

  <GameLetGo />
  <div class="d-flex justify-content-end">
    <button type="button" class="btn btn-primary ms-2" on:click={logOut}
      >Logout <i class="fa fa-sign-out" /></button
    >
  </div>
</div>
