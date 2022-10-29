<script>
	import Router from 'svelte-spa-router';
	import { onMount } from "svelte";
	import SignUp from "./pages/SignUp.svelte";
	import Login from "./pages/Login.svelte";
	import Home from "./pages/Home.svelte";
	import PrivateRoute from "./component/PrivateRoute.svelte";
	import { user } from "./store/index";
	import api from "./api/index";
	import "./style/index.css"
  

	let isLoading = true;
  
   async function fetchAccount(){
	  const account = await api.getAccount();
	  user.update(() => account);
	  navigate("/");
	}
  
  
	onMount(async () => {
	  if(!$user){
		fetchAccount()
	  }
	  else{
		navigate("/login");
	  }
	});
  
	isLoading = false;


	const routes = {
		'/': Home,
		'/login': Login,
		'/signup':SignUp
	};
  
  </script>
  
  <Router {routes} />
  
  