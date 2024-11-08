<script>
  import logo from "$lib/assets/logo.png";
  import { ChevronDownOutline } from "flowbite-svelte-icons";
  import bg3 from "$lib/assets/31701.jpg";
  import Student from "$lib/assets/student.png";
  import Teacher from "$lib/assets/teacher.png";
  import {
    Navbar,
    NavBrand,
    NavHamburger,
    NavUl,
    NavLi,
    MegaMenu,
    Button,
  } from "flowbite-svelte";
  import { Drawer, CloseButton, Label, Input, Textarea } from 'flowbite-svelte';
  import { UserSolid, LockOpenSolid, CalendarEditSolid } from 'flowbite-svelte-icons';
  import { sineIn } from 'svelte/easing';

  let hidden4 = true;
  let transitionParams = {
    x: -320,
    duration: 500,
    easing: sineIn
  };

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
        <Button on:click={() => (hidden4 = false)} size="sm" style="background-color: #2447F9;">
          <span class="login">Login</span>
        </Button>
        <Button size="sm" color="primary">
          <span>Sign Up</span>
        </Button>
      </div>
    </NavLi>
  </NavUl>
</Navbar>


<Drawer transitionType="fly" {transitionParams} bind:hidden={hidden4} id="sidebar4" class="w-96"  style="background-image: url({bg3});" >
  <div class="flex items-center">
    <h5 id="drawer-label" class="inline-flex items-center mb-6 text-base font-bold text-customWhite uppercase dark:text-gray-400">
      <UserSolid class="w-5 h-5 me-2.5 text-customWhite" />Sign In
    </h5>
    <CloseButton on:click={() => (hidden4 = true)} class="mb-4 dark:text-white" />
  </div>
  <form action="#" class="mb-6">
    <div class="mb-6">
      <Label for="title" class="block mb-2 text-customWhite">Email</Label>
      <Input id="email" name="email" required placeholder="johndoe@example.com"  />
    </div>

    <div class="mb-6">
      <Label for="title" class="block mb-2 text-customWhite">Password</Label>
      <Input type="password" id="password" name="password" required placeholder="******" />
    </div>

    <div class="mb-6">
      <label for="title" class="block mb-2 text-customWhite">Login Sebagai</label>
      <ul class="flex justify-between">
        <li class="flex flex-col items-center">
          <input type="radio" name="login_as" id="cb1" />
          <label class="lbl_login_as" for="cb1">
            <img src="{Teacher}" alt="teacher image" class="w-40" />
            <span>Instructor</span>
          </label>
        </li>
        <li class="flex flex-col items-center">
          <input type="radio" name="login_as" id="cb2" />
          <label class="lbl_login_as" for="cb2">
            <img src="{Student}" alt="student image" class="w-40" />
            <span>Student</span>
          </label>
        </li>
      </ul>
    </div>
    


    <Button type="submit" class="w-full bg-customeBlue text-customWhite">
      <LockOpenSolid class="w-3.5 h-3.5 me-2.5 text-customWhite" /> Sign In
    </Button>
  </form>
</Drawer>

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

  ul {
  list-style-type: none;
}

li {
  display: inline-block;
}

input[type="radio"][id^="cb"] {
  display: none;
}

.lbl_login_as {
  
  padding: 10px;
  display: block;
  position: relative;
  margin: 10px;
  cursor: pointer;
}

.lbl_login_as:before {
  background-color: white;
  color: white;
  content: " ";
  display: block;
  border-radius: 50%;
  border: 1px solid grey;
  position: absolute;
  top: -5px;
  left: -5px;
  width: 25px;
  height: 25px;
  text-align: center;
  line-height: 28px;
  transition-duration: 0.4s;
  transform: scale(0);
}

.lbl_login_as img {

  transition-duration: 0.2s;
  transform-origin: 50% 50%;
}

:checked + label {
  border-color: #ddd;
}

:checked + label:before {
  content: "✓";
  background-color: grey;
  transform: scale(1);
}

:checked + label img {
  transform: scale(0.9);
  box-shadow: 0 0 5px #333;
  z-index: -1;
}

</style>
