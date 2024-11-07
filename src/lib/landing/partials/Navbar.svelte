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
  open={true}
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
  <NavHamburger on:click={toggle} class="text-white" />

  <!-- Navigation Links -->

  <NavUl
    {hidden}
    activeClass="active"
    ulClass="lg:bg-transparent bg-customeBlue flex flex-col p-4 mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0"
  >
    <a
      href="/"
      class="
        block py-2 pe-4 ps-3 md:p-0 rounded limenu hover-mobile
      "
    >
      Home
    </a>

    <a
      href="/"
      class="
          block py-2 pe-4 ps-3 md:p-0 rounded limenu hover-mobile
        "
    >
      Browse
      <ChevronDownOutline class="w-6 h-6 ms-2 limenu hover-mobile inline" />
    </a>

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
    <a
      href="/"
      class="
      block py-2 pe-4 ps-3 md:p-0 rounded limenu hover-mobile
    "
    >
      Become Instructor
    </a>
    <NavLi>
      <!-- Right-side Buttons (Login & Sign Up) -->
      <div class="flex md:order-2 space-x-2 mt-2 lg:-mt-2 btn-lgn-signup">
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

  .btn-lgn-signup {
    font-family: "Poppins", serif;
    font-weight: bold;
  }

  @media (max-width: 768px) {
    .limenu {
      font-family: "Poppins", serif;
      font-weight: bold;
      font-style: normal;
      color: white;
      font-size: 16px;
    }

    @media (max-width: 768px) {
      .hover-mobile:hover {
        background-color: #f3f4f6; /* warna background ketika di-hover di mobile */
        color: #181230; /* warna teks ketika di-hover di mobile */
      }
    }

    /* Nonaktifkan hover di desktop */
    @media (min-width: 768px) {
      .hover-mobile:hover {
        background-color: transparent;
        color: inherit;
      }
    }
  }
</style>
