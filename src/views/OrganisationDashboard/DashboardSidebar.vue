<template>
  <nav class="sidebar">
    <div class="logo d-flex justify-content-between">
      <router-link to="/organisation-dashboard/home"
        ><a class="large_logo"><img src="@/assets/img/logo.png" alt="" /></a
      ></router-link>
      <router-link to="/organisation-dashboard/home"
        ><a class="small_logo"
          ><img src="@/assets/img/mini_logo.png" alt="" /></a
      ></router-link>
      <div class="sidebar_close_icon d-lg-none">
        <i class="ti-close"></i>
      </div>
    </div>
    <ul id="sidebar_menu">
      <!--Dashboard-->
      <li class="">
        <router-link to="/organisation-dashboard/home" class="menuRouter">
          <a aria-expanded="false">
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-dash.png" />
            </div>
            <div class="nav_title">
              <span>Dashboard</span>
            </div>
          </a>
        </router-link>
      </li>
      <!--ID Card Management-->
      <li class="">
        <router-link to="#" class="has-arrow menuRouter">
          <a aria-expanded="false">
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-card.png" />
            </div>
            <div class="nav_title">
              <span>ID Card Management</span>
            </div>
          </a>
        </router-link>
        <ul>
          <li>
            <router-link
              to="/organisation-dashboard/id-card-management"
              class="menuRouter"
              ><a>Overview</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/create-template"
              class="menuRouter"
              ><a>Create Template</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/created-template"
              class="menuRouter"
              ><a>Created Template</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/add-card"
              class="menuRouter"
              ><a>Add ID Card</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/member-id"
              class="menuRouter"
              ><a>Member ID</a></router-link
            >
          </li>
        </ul>
      </li>
      <!--Event Management-->
      <li class="">
        <router-link to="#" class="has-arrow menuRouter">
          <a aria-expanded="false">
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-event.png" />
            </div>
            <div class="nav_title">
              <span>Event Management</span>
            </div>
          </a>
        </router-link>
        <ul>
          <li>
            <router-link
              to="/organisation-dashboard/event-management"
              class="menuRouter"
              ><a>Overview</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/upcoming-event"
              class="menuRouter"
              ><a>Upcoming Event</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/event-gallery"
              class="menuRouter"
              ><a>Event Gallery</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/create-event"
              class="menuRouter"
              ><a>Create Event</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/invitation"
              class="menuRouter"
              ><a>Invitations</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/event-history"
              class="menuRouter"
              ><a>History</a></router-link
            >
          </li>
        </ul>
      </li>
      <!--Membership & Subscription-->
      <li class="">
        <router-link to="#" class="has-arrow menuRouter">
          <a aria-expanded="false">
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-member.png" />
            </div>
            <div class="nav_title">
              <span
                >Membership & <br />
                Subscription</span
              >
            </div>
          </a>
        </router-link>
        <ul>
          <li>
            <router-link
              to="/organisation-dashboard/membership-subscription"
              class="menuRouter"
              ><a>Overview</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/memberships"
              class="menuRouter"
              ><a>Membership</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/subscriptions"
              class="menuRouter"
              ><a>Subscription</a></router-link
            >
          </li>
          <li>
            <router-link to="/organisation-dashboard/history" class="menuRouter"
              ><a>History</a></router-link
            >
          </li>
        </ul>
      </li>
      <!--Verification-->
      <li class="">
        <router-link to="#" class="has-arrow menuRouter">
          <a aria-expanded="false">
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-verify.png" />
            </div>
            <div class="nav_title">
              <span>Verification</span>
            </div>
          </a>
        </router-link>
        <ul>
          <li>
            <router-link
              to="/organisation-dashboard/verification"
              class="menuRouter"
              ><a>Overview</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/create-verifier"
              class="menuRouter"
              ><a>Create Verifier</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/view-verifier"
              class="menuRouter"
              ><a>View Verifier</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/event-verifier"
              class="menuRouter"
              ><a>Event Verifier</a></router-link
            >
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/pending-request"
              class="menuRouter"
              ><a>Pending Request</a></router-link
            >
          </li>
        </ul>
      </li>
      <!--Profile -->
      <li class="">
        <router-link to="#" class="has-arrow menuRouter">
          <a aria-expanded="false">
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-card.png" />
            </div>
            <div class="nav_title">
              <span>Profile</span>
            </div>
          </a>
        </router-link>
        <ul>
          <li>
            <router-link
              to="/organisation-dashboard/my-profile"
              class="menuRouter"><a>My Profile</a></router-link>
          </li>
          <li>
            <router-link
              to="/organisation-dashboard/settings"
              class="menuRouter"><a>Settings</a></router-link>
          </li>
        </ul>
      </li>
      <!--Log Out-->
      <li class="">
        <router-link to="#" class="menuRouter">
          <a
            aria-expanded="false"
            href="javascript:void(0)"
            @click="logoutClick"
          >
            <div class="nav_icon_small">
              <img src="@/assets/img/dashAssets/menu-logout.png" />
            </div>
            <div class="nav_title">
              <span>Log Out</span>
            </div>
          </a>
        </router-link>
      </li>
    </ul>
  </nav>
</template>
<style scoped src="@/assets/css/styleDashboard.css"></style>
<script>
export default {
  methods: {
    logoutClick() {
      localStorage.removeItem("token", "user");
      // this.$store.dispatch("user", null);
      axios.post("logout");
      this.$router.replace("/");
    },
  },
};
</script>
