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
                    <h3>Subscription Payment</h3>
                    <p>
                      <router-link to="/superadmin-dashboard/home"
                        ><a
                          ><i class="bi bi-arrow-left"></i> Dashboard</a
                        ></router-link
                      >
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!--Boxes Section-->
        <div class="row justify-content-center mt-3 secForm">
          <div class="col-lg-11 secFormHead">
            <h5>All subscription payment</h5>
          </div>
          <div class="col-lg-11 filterSelect">
            <input type="text" placeholder="Search..." />
          </div>
          <div class="col-lg-11 mt-3">
            <div class="white_card card_height_100 mb_30">
              <div class="white_card_body">
                <div class="QA_section">
                  <div class="QA_table mb_30">
                    <table class="table lms_table_active">
                      <thead>
                        <tr>
                          <th scope="col">Subscription ID</th>
                          <th scope="col">Payee Name</th>
                          <th scope="col">Subscription Plan ID</th>
                          <th scope="col">Organisation Name</th>
                          <th scope="col">Amount</th>
                          <th scope="col">Reference</th>
                          <th scope="col">Fee</th>
                          <th scope="col">Channel</th>
                          <th scope="col">IP Address</th>
                        </tr>
                      </thead>
                      <tbody v-if="!subscriptions || !subscriptions.length">
                        <tr>
                          <td class="align-enter text-dark font-13" colspan="9">
                            No Subscription Payment
                          </td>
                        </tr>
                      </tbody>
                      <tbody>
                        <tr
                          v-for="(row, index) in subscriptions"
                          v-bind:key="index"
                        >
                          <th scope="row">{{ row.id }}</th>
                          <td>
                            {{
                              row.individual.firstname +
                              " " +
                              row.individual.lastname
                            }}
                          </td>
                          <td>
                            <span v-if="row.user.type == 'individual'">
                              {{ row.subscription_plan.id }}</span
                            >
                          </td>
                          <td>{{ row.organization.name }}</td>
                          <td>{{ row.payment.amount }}</td>
                          <td>{{ row.payment.reference }}</td>
                          <td>{{ row.payment.fees }}</td>
                          <td>{{ row.payment.channel }}</td>
                          <td>{{ row.payment.ip_address }}</td>
                        </tr>
                      </tbody>
                    </table>
                  </div>
                </div>
              </div>
            </div>
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
      subscriptions: [],
      pagination: {},
    };
  },

  methods: {
    loadAllSubscriptionPayments(page = 1) {
      axios
        .get("admin/payments/subscriptions" + "?page=" + page, {
          headers: {
            Authorization: `Bearer ${localStorage.getItem("token")}`,
          },
        })
        .then((response) => {
          this.prepPagination(response.data);
          this.subscriptions = response.data.data;
        })
        .catch((error) => {
          this.$notify({
            type: "error",
            title: error.response.data.message,
            duration: 5000,
            speed: 1000,
          });
        });
    },

    prepPagination(data) {
      this.pagination = {
        data: data.data,
        current_page: data.meta.current_page,
        first_item: data.meta.first_item,
        last_item: data.meta.last_item,
        last_page: data.meta.last_page,
        next_page_url: data.meta.next_page_url,
        per_page: data.meta.per_page,
        previous_page_url: data.meta.previous_page_url,
        total: data.meta.total,
      };
    },
  },

  created() {
    this.loadAllSubscriptionPayments();
  },

  mounted() {
    this.loadAllSubscriptionPayments();

    window.scrollTo(0, 0);
  },
};
</script>
