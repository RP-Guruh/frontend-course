<script>
  import logo from "$lib/assets/logo.png";
  import { ChevronDownOutline } from "flowbite-svelte-icons";
  import {
    Navbar,
    NavBrand,
    NavHamburger,
    NavUl,
    NavLi,
    MegaMenu,
    Button,
  } from "flowbite-svelte";

  let menu2 = [
    {
      name: "Online Stores",
      help: "Connect with third-party tools that you're already using.",
    },
    {
      name: "Segmentation",
      help: "Connect with third-party tools that you're already using.",
    },
    {
      name: "Marketing CRM",
      help: "Connect with third-party tools that you're already using.",
    },

    {
      name: "Online Stores",
      help: "Connect with third-party tools that you're already using.",
    },
    {
      name: "Segmentation",
      help: "Connect with third-party tools that you're already using.",
    },
    {
      name: "Marketing CRM",
      help: "Connect with third-party tools that you're already using.",
    },

    {
      name: "Audience Management",
      help: "Connect with third-party tools that you're already using.",
    },
    {
      name: "Creative Tools",
      help: "Connect with third-party tools that you're already using.",
    },
    {
      name: "Marketing Automation",
      help: "Connect with third-party tools that you're already using.",
    },
  ];
</script>

<!-- Navbar Section -->
<Navbar
  let:hidden
  let:toggle
  class="absolute top-0 left-0 w-full p-6 bg-customeBlue bg-opacity-10"
>
  <!-- Brand Logo -->
  <NavBrand href="/">
    <img src={logo} class="me-3 h-6 sm:h-9" alt="Flowbite Logo" />
    <span class="self-center whitespace-nowrap text-xl font-bold text-white"
      >Build with Guruh</span
    >
  </NavBrand>

  <!-- Hamburger Menu for Mobile -->
  <NavHamburger on:click={toggle} />

  <!-- Navigation Links -->
  <NavUl {hidden}>
    <NavLi href="/" class="navli">
      <span class="limenu">Home</span>
    </NavLi>
    <NavLi class="cursor-pointer">
      <span class="limenu">Browse</span>
      <ChevronDownOutline
        class="w-6 h-6 ms-2 text-white dark:text-white inline"
      />
    </NavLi>
    <!-- Mega Menu Dropdown -->
    <MegaMenu class="bg-customeBlue absolute z-10 " full items={menu2} let:item>
      <a
        href="/"
        class="block p-3 rounded-lg hover:bg-gray-50 dark:hover:bg-gray-700 h-full group"
      >
        <div
          class="font-semibold text-customWhite dark:text-white group-hover:text-black"
        >
          {item.name}
        </div>
        <span
          class="text-sm font-light text-customWhite dark:text-gray-400 group-hover:text-black"
        >
          {item.help}
        </span>
      </a>
    </MegaMenu>
    <NavLi href="#">
      <span class="limenu">Become Instructor</span>
    </NavLi>
    <NavLi>
      <!-- Right-side Buttons (Login & Sign Up) -->
      <div class="flex md:order-2 space-x-2 -mt-2">
        <Button size="sm" style="background-color: #2447F9;">
          <span class="login">Login</span>
        </Button>
        <Button size="sm" color="primary">
          <span>Sign Up</span>
        </Button>
      </div>
    </NavLi>
  </NavUl>
</Navbar>

<style>
  .limenu {
    font-family: "Poppins", serif;
    font-weight: bold;
    font-style: normal;
    color: white;
    font-size: 16px;
  }
</style>
