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
                    <h3>Event Gallery</h3>
                    <p>
                      <router-link to="/organisation-dashboard/event-management"
                        ><a
                          ><i class="bi bi-arrow-left"></i> Event Management</a
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
            <h5>All your created event</h5>
          </div>
          <div class="col-lg-11 mt-3">
            <div class="white_card card_height_100 mb_30">
              <div class="white_card_body">
                <div class="QA_section">
                  <form>
                    <div class="row">
                      <div class="col-lg-12">
                        <label class="mb-1">Search for event</label>
                        <input
                          type="text"
                          v-model="searchQuery"
                          class="input searchInput"
                          placeholder="Search for event with Name, Event ID"
                        />
                      </div>
                    </div>
                  </form>
                  <div class="QA_table mb_30">
                    <table class="table lms_table_active">
                      <thead>
                        <tr>
                          <th scope="col">ID</th>
                          <th scope="col">Name</th>
                          <th scope="col">Type</th>
                          <th scope="col">Category</th>
                          <th scope="col">Tickets</th>
                          <th scope="col">Ticket QTY</th>
                          <th scope="col">Start Date</th>
                          <th scope="col">End Date</th>
                          <th scope="col">Event ID</th>
                          <th scope="col">Image</th>
                          <th scope="col">Action</th>
                        </tr>
                      </thead>
                      <tbody>
                        <tr v-for="(item, i) in resultQuery" :key="item.id">
                          <th scope="row">
                            {{ i + 1 }}
                          </th>
                          <td>{{ item.name }}</td>
                          <td style="text-transform: capitalize">
                            {{ item.type }}
                          </td>
                          <td style="text-transform: capitalize">
                            {{ item.category.name }}
                          </td>
                          <td>
                            <span v-if="item.isFree == 'true'">Free</span>
                            <span v-if="item.isFree == 'false'">Paid</span>
                          </td>
                          <td>{{ item.tickets }}</td>
                          <td>
                            {{ getDate(item.start_date) }}
                          </td>
                          <td>
                            {{ getDate(item.end_date) }}
                          </td>
                          <td>
                            {{ item.unique_id }}
                          </td>
                          <td>
                            <span v-if="item.image == null">
                                None
                            </span>
                            <span v-else>
                            <img
                              :src="this.baseURL + '/storage/events/' + item.image"
                            />
                            </span>
                          </td>
                          <td>
                            <div class="action_btns d-flex">
                              <a href="#" title="View" class="action_btn">
                                <i class="bi bi-eye-fill"></i>
                              </a>
                              <a href="#" title="Delete" class="action_btn">
                                <i class="bi bi-trash-fill"></i>
                              </a>
                            </div>
                          </td>
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
  mounted() {
    window.scrollTo(0, 0);
    this.getAllEvent();
  },
  data() {
    return {
      events: "",
      baseURL: axios.defaults.baseURL.slice(0, -5),
      category: [],
      categoryName: "",
      searchQuery: null,
    };
  },

  computed: {
    resultQuery() {
      if (this.searchQuery) {
        const value= this.searchQuery.charAt(0).toUpperCase() + this.searchQuery.slice(1);
        return this.events.filter(function(event){
          return event.name.indexOf(value) > -1 ||
                event.unique_id.indexOf(value) > -1 
        })
      } else {
        return this.events;
      }
    },
  },

  methods: {
    getDate(value) {
      return new Date(value).toLocaleDateString("en-US");
    },
    getAllEvent() {
      axios
        .get(`/events/mine`, {
          headers: {
            Authorization: `Bearer ${localStorage.getItem("token")}`,
          },
        })
        .then((res) => {
          //console.log(res.data.data)
          this.events = res.data.data;
          this.category = res.data.data.category;
          for (let x of this.events) {
            this.category = x.category;
            console.log(this.category);
          }
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>
