<script>
  let menuActive = false;
</script>

<div class="d-flex" id="wrapper" class:toggled={menuActive}>
  <div class="border-right" id="sidebar-wrapper">
    <slot name="sidebar-heading">
      <div class="sidebar-heading">TITLE</div>
    </slot>

    <div class="list-group list-group-flush">
      <slot name="sidebar" />
    </div>
  </div>

  <div id="page-content-wrapper">
    <nav class="navbar">
      <button
        class="navbar-toggler no-border"
        id="menu-toggle"
        on:click={() => (menuActive = !menuActive)}
      >
        {#if menuActive}
          sidebar
          <img
            class="filter"
            src="static/images/right-chevron.svg"
            width="10px"
            alt="close chevron"
          />
        {:else}
          <img
            class="filter"
            src="static/images/left-chevron.svg"
            width="10px"
            alt="open chevron"
          />
          sidebar
        {/if}
      </button>
      <slot name="top-content">
        <div class="navbar-brand">Menu Items</div>
      </slot>
    </nav>
    <div class="container-fluid content-container">
      <slot name="content" />
    </div>
  </div>
</div>

<style>
  #sidebar-wrapper {
    min-height: 100vh;
    width: 24rem;
    max-width: 24rem;
    /* margin-left: -20rem; */
    padding-top: 2rem;
    background-color: white;
    -webkit-transition: margin 0.25s ease-out;
    -moz-transition: margin 0.25s ease-out;
    -o-transition: margin 0.25s ease-out;
    transition: margin 0.25s ease-out;
  }

  .sidebar-heading {
    color: #000;
    font-family: "Varela Round";
    font-weight: bold;
    font-size: 2.2rem;
    padding-left: 30px;
    padding-top: 10px;
    padding-bottom: 10px;
    padding-right: 20px;
  }

  .list-group {
    color: #000;
    width: 24rem;
    font-size: 20px;
    /* padding-left: 50px; */
    /* padding-right: 20px; */
    padding-bottom: 6px;
  }

  .navbar-toggler {
    color: #264653;
    font-weight: bold;
    font-size: 14px;
    padding-top: 15px;
    padding-left: 25px;
  }

  #page-content-wrapper {
    min-width: 100vw;
  }

  #wrapper.toggled #sidebar-wrapper {
    margin-left: 0;
  }

  .navbar {
    background-color: #00000000;
    margin: 0px;
    padding: 0px;
  }

  .content-container {
    margin-top: 30px;
    margin-left: 5%;
  }

  #menu-toggle {
    /* margin-left: -20px; */
    margin-top: -20px;
  }
  .no-border {
    outline: none;
    border: none;
    background: none;
  }

  @media (min-width: 768px) {
    #sidebar-wrapper {
      margin-left: 0;
    }

    #page-content-wrapper {
      min-width: 0;
      width: 100%;
    }

    #wrapper.toggled #sidebar-wrapper {
      margin-left: -24rem;
    }

    .navbar {
      background-color: #00000000;
    }
  }
  .filter {
    filter: invert(22%) sepia(41%) saturate(520%) hue-rotate(151deg) brightness(94%) contrast(91%);
    /* filter: invert(27%) sepia(33%) saturate(4088%) hue-rotate(326deg) brightness(87%) contrast(102%); */
  }
</style>
