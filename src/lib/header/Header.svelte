<script>
  import {focus} from './focus.js'
  import Toggle from './Toggle.svelte'

  let open = false

  const navToggle = async () => {
    open = !open
  }

  const handleNavWithKey = (e) => {
    if (e.code === 'Escape' && open === true) {
      open = false
    }
  }
</script>

<svelte:window on:keydown={handleNavWithKey}/>

<div use:focus class="sidenav" class:open>
  <div class="right-side">
    <Toggle on:click={navToggle}>&times;</Toggle>
  </div>
  <a href="/about">About</a>
  <a href="/services">Services</a>
  <a href="/clients">Clients</a>
  <a href="/contact">Contact</a>
</div>


<div id="main" class:pushMainToRight={open}>
  <div class="NavBrand">
    <h2>NavBrand</h2>
  </div>

  <div class="NavBurger">
    <Toggle on:click={navToggle}>open</Toggle>
  </div>

</div>

<style>

  /* The side navigation menu */
  .sidenav {
    height: 100%; /* 100% Full-height */
    width: 0; /* 0 width - change this with JavaScript */
    position: fixed; /* Stay in place */
    z-index: 1; /* Stay on top */
    top: 0;
    left: 0;
    background-color: aquamarine; /* Black*/
    overflow-x: hidden; /* Disable horizontal scroll */
    padding-top: 60px; /* Place content 60px from the top */; /* 0.5 second transition effect to slide in the sidenav */
    transition: 0.8s;
    visibility: hidden;
    display: none;
  }

  /* The navigation menu links */
  .sidenav a {
    padding: 8px 8px 8px 32px;
    text-decoration: none;
    font-size: 25px;
    color: #818181;
    display: block;;
  }

  .right-side {
    display: flex;
    justify-content: end;
  }

  /* When you mouse over the navigation links, change their color */
  .sidenav a:hover {
    color: #f1f1f1;
  }

  /* Style page content - use this if you want to push the page content to the right when you open the side navigation */
  #main {;
    transition: 0.5s;
    background-color: yellowgreen;
    display: grid;
    grid-template-columns:1fr 1fr;
    grid-template-rows: 1fr;
    align-items: center;
    height: 60px;
  }

  .NavBrand {
    margin-left: 12%;
  }

  .NavBurger {
    display: flex;
    justify-content: end;
    margin-right: 12%;
  }

  .open {
    width: 40%;
    visibility: visible;
    display: initial;
  }

  .pushMainToRight {

  }

  /* On smaller screens, where height is less than 450px, change the style of the sidenav (less padding and a smaller font size) */
  @media screen and (max-height: 450px) {
    .sidenav {
      padding-top: 15px;
    }

    .sidenav a {
      font-size: 18px;
    }
  }
</style>
