<script>
	// module
	import { Collapse,Navbar,NavbarToggler,NavbarBrand,Nav,NavItem,NavLink, Container } from 'sveltestrap';
	import { Router, Route, Link } from "svelte-routing";

	// component
	import Home from "./home/home.svelte";
	import About from "./about/about.svelte";
	import Find from "./find_chara/find_chara.svelte";
	
  	let isOpen = false;
  	function handleUpdate(event) {
    	isOpen = event.detail.isOpen;
  	}
</script>

<svelte:head>
	<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/css/bootstrap.min.css">
	<link rel="stylesheet" href="/style.css">
	<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Nunito&display=swap"> 
	<title>Find Anime Character</title>
</svelte:head>

<main>
	<Router>
		<Navbar dark expand="md" class="sticky-top custom-nav">
			<Container>
				<NavbarBrand href="/">FACharacter</NavbarBrand>
				<NavbarToggler on:click={() => (isOpen = !isOpen)} />
				<Collapse {isOpen} navbar expand="md" on:update={handleUpdate}>
				  <Nav class="ml-auto" navbar>
					<NavItem>
					  <NavLink>
						  <Link to="/">Home</Link>
						</NavLink>
					</NavItem>
					<NavItem>
					  <NavLink>
						  <Link to="find">Find Character</Link>
						</NavLink>
					</NavItem>
					<NavItem>
					  <NavLink>
						  <Link to="about">About Me</Link>
						</NavLink>
					</NavItem>
				  </Nav>
				</Collapse>
			</Container>
		</Navbar>
		<Route path="/" component={Home}></Route>
		<Route path="/*" component={Home}></Route>
		<Route path="find" component={Find}></Route>
		<Route path="about" component={About}></Route>
	</Router>
</main>