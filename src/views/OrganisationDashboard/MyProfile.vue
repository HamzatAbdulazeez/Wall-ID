<template>
  <DashboardSidebar />

  <section class="main_content dashboard_part large_header_bg">
    <DashboardNavbar />

    <!--Main Content-->
    <div class="main_content_iner overly_inner">
      <div class="container-fluid p-0">
        <!--Breadcrumb-->
        <div class="row">
          <div class="col-12">
            <div class="dashboard_header mb-3">
              <div class="row">
                <div class="col-lg-12">
                  <div class="dashboard_header_title">
                    <h3>My Profile</h3>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!--Profile Details-->
        <div class="row pd-section">
          <div class="col-lg-10 mb-4">
            <div class="profile-img">
              <img v-if="!user.details.image" src="@/assets/img/dp.jpg" />
              <img
                v-else
                :src="this.baseURL + user.details.image"
                alt="Profile Picture"
              />
            </div>
          </div>
          <div class="col-12 mb-4">
            <input style="color: #a221fc; font-weight: 700; cursor: copy; border: none; background-color: transparent; resize: none; outline: none;"
            v-on:focus="$event.target.select()" 
            ref="clone" 
            readonly 
            @click="copy"
            :value="user.details.id_card_number"/>
          </div>
          <div class="col-lg-6 mb-4">
            <span>Company Name</span>
            <p>{{ user.details.name }}</p>
          </div>
          <div class="col-lg-6 mb-4">
            <span>Email</span>
            <p>{{ user.email }}</p>
          </div>
          <div class="col-lg-6 mb-4">
            <span>Phone</span>
            <p>{{ user.details.phone }}</p>
          </div>
          <div class="col-lg-6 mb-4">
            <span>Registered</span>
            <p>{{ new Date(user.details.created_at).toLocaleString() }}</p>
          </div>
          <div class="col-lg-6 mb-4">
            <span>Type</span>
            <p>Organisation</p>
          </div>
          <div class="col-lg-6 mb-4">
            <span>Access Type</span>
            <p v-if="user.details.type == 1">Restricted / Closed</p>
            <p v-else>Free Pass / Open</p>
          </div>
          <div class="col-lg-6 mb-4 mt-2">
            <router-link to="/organisation-dashboard/settings"
              ><a class="editProfile">Edit Profile</a></router-link
            >
          </div>
        </div>
      </div>
    </div>

    <DashboardFooter />
  </section>

  <div id="back-top" style="display: none">
    <a title="Go to Top" href="#">
      <i class="ti-angle-up"></i>
    </a>
  </div>
</template>

<style scoped src="@/assets/css/styleDashboard.css"></style>
<script>
import DashboardSidebar from "./DashboardSidebar.vue";
import DashboardNavbar from "./DashboardNavbar.vue";
import DashboardFooter from "./DashboardFooter.vue";

import axios from "axios";

export default {
  components: { DashboardSidebar, DashboardNavbar, DashboardFooter },

  data() {
    return {
      baseURL: axios.defaults.baseURL.slice(0, -5),
      user: JSON.parse(localStorage.getItem('user')) || [],
    };
  },

  methods: {
    copy() {
      this.$refs.clone.focus();
      document.execCommand('copy');
      this.$notify({
        type: "success",
        title: "Wall ID Number",
        text: "Copied Successsfully!",
        duration: 5000,
        speed: 1000,
      });
    }
  },

  mounted() {
    window.scrollTo(0, 0);
  },
};
</script>
