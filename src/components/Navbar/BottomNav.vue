<template>
    <div>
        <nav class="navbar fixed-bottom navbar-light bg-light" :class="{ 'navbar-hidden': navbarHidden }">
            <div id="mobile bottomNav">
                <div class="bnav d-flex h-100">
                    <div class="bottom-nav w-100 position-fixed " style="bottom: 0px;">
                        <div class="bottom-nav w-100 position-absolute" style="height: 5%;">
                            <div class="btn-front position-absolute d-flex justify-content-evenly w-100 "
                                style="bottom:0; width: 100%; background-color: #f2f2f2; ">
                                <div class="d-grid">
                                    <RouterLink to="/OrderPage"  :class="{'text-danger' : currentRoute ==='OrderPage' }" style="text-decoration:none;color:black;text-align: center;" >
                                      <i class="bi bi-journal-text fs-4"></i>
                                        <p style="font-size: 14px;margin: 0">Orders</p>
                                    </RouterLink>
                                </div>
                                <div class="d-grid">
                                    <RouterLink to="/"  :class="{'text-danger' : currentRoute ==='DashboardPage' }" style="text-decoration:none;color:black;text-align: center;">
                                        <i class="bi bi-shop-window fs-4"></i>
                                        <p style="font-size: 14px;">Dashboard</p>
                                    </RouterLink>
                                </div>
                                <div class="d-grid">
                                    <RouterLink to="/CatalogPage"  :class="{'text-danger' : currentRoute ==='CatalogPage' }" style="text-decoration:none;color:black;text-align: center;">
                                        <i class="bi bi-layers fs-4"></i>
                                        <p style="font-size: 14px;">Catalogs</p>
                                    </RouterLink>
                                </div>
                                <!-- <div class="d-grid">
                                    <RouterLink to="/"  :class="{'text-danger' : currentRoute ==='' }" style="text-decoration:none;color:black;text-align: center;">
                                        <i class="bi bi-journal-arrow-down fs-4"></i>
                                        <p style="font-size: 14px;">SO</p>
                                    </RouterLink>
                                </div>
                                <div class="d-grid">
                                    <RouterLink to="/"  :class="{'text-danger' : currentRoute ==='' }" style="text-decoration:none;color:black;text-align: center;">
                                      <i class="bi bi-download fs-4"></i>
                                        <p style="font-size: 14px;">Receipts</p>
                                    </RouterLink>
                                </div> -->
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </nav>
    </div>
</template>

<script>
export default {
  data() {
    return {
      prevScroll: window.pageYOffset,
      navbarHidden: false
    };
  },
  computed:{
    currentRoute(){
      return this.$route.name;
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      const currentScroll = window.pageYOffset;
      if (this.prevScroll > currentScroll) {
        this.navbarHidden = false;
      } else {
        this.navbarHidden = true;
      }
      this.prevScroll = currentScroll;
    },
  }
};
</script>

<style scoped>
.navbar {
  background-color: #f1f1f1;
  height: 80px;
  transition: transform 0.5s;
  transform: translateY(0);
}

.navbar-hidden {
  transform: translateY(100%);
}
</style>