<script>
  import Sidebar from "./Sidebar.svelte";
  import Router from "svelte-spa-router";
  import active from "svelte-spa-router/active";
  import { link } from "svelte-spa-router";
  import Accordion from "svelte-accordion";
  $$IMPORTS$$

  const routes = {
    $$ROUTES$$
  };
</script>

<!-- Sources: https://github.com/sophana/svelte-spa-router-sidebar/tree/master/src -->
<Sidebar>
  <span slot="sidebar"> $$SIDEBAR$$ </span>
  <span slot="content">
    <div class="container-fluid">
      <div class="columns">
        <div class="col-md-1" />
        <div class="col-md-8">
          <Router {routes} />
        </div>
        <div class="col-md-3" />
      </div>
    </div>
  </span>
</Sidebar>
