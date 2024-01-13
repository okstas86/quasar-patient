<template>
  <div class="q-pa-md">
    <q-toolbar class="q-ma-sm">
      <q-input
        outlined
        v-model="text"
        label="Search"
        :dense="dense"
        rounded
        class="search"
      >
        <template v-slot:append>
          <q-icon name="search" />
        </template>
      </q-input>
      <q-space></q-space>
      <q-btn color="white" text-color="black" icon="fas fa-moon"></q-btn>
    </q-toolbar>
    <q-toolbar>
      <h6 class="text-weight-bolder">Dashboard</h6>
      <q-space></q-space>
      <q-btn
        @click="showCalendar"
        icon="fas fa-calendar-minus"
        class="q-mr-sm"
        size="10px"
      ></q-btn>

      <div class="text-overline">{{ showDate }}</div>
    </q-toolbar>

    <div
      v-if="isVisibleCal"
      class="q-gutter-md"
      style="position: absolute; top: 200px; right: 350px; z-index: 100"
    >
      <q-date color="green-7" v-model="date"></q-date>
    </div>

    <div class="row q-col-gutter-md top">
      <div class="col-3">
        <q-card class="q-mx-md" bordered>
          <div class="flex flex-center column">
            <q-circular-progress
              show-value
              font-size="12px"
              value="70"
              size="100px"
              :thickness="0.22"
              color="green-7"
              track-color="green-2"
              class="q-ma-md"
              >78 Patients</q-circular-progress
            >
            <div>
              <q-badge color="green-2" rounded class="q-mr-sm" />Woman 40%
            </div>
            <div class="q-mb-xl">
              <q-badge color="green-7" rounded class="q-mr-sm" />Man 60%
            </div>
          </div>
        </q-card>
      </div>
      <div class="col-3">
        <q-card class="q-mx-md q-pa-md" bordered>
          <div class="text-overline text-center">New Patients</div>
          <div class="flex flex-center row">
            <div class="text-h4 text-weight-bolder q-mr-md">54</div>
            <q-chip
              color="green-1"
              text-color="green-3"
              icon="fas fa-chevron-up"
              >71%</q-chip
            >
          </div>
        </q-card>
        <q-card class="q-mx-md q-pa-md q-mt-sm" bordered>
          <div class="text-overline text-center">Old Patients</div>
          <div class="flex flex-center row">
            <div class="text-h4 text-weight-bolder q-mr-md">22</div>
            <q-chip color="red-1" text-color="red-3" icon="fas fa-chevron-down"
              >29%</q-chip
            >
          </div>
        </q-card>
      </div>
      <div class="col-6">
        <q-card class="q-mx-md q-pa-md doctors" borders>
          <div class="text-overline">Statistic</div>
          <div>
            <q-carousel
              v-model="slide"
              vertical
              transition-prev="slide-down"
              transition-next="slide-up"
              swipeable
              animated
              control-color="green-7"
              navigation-icon="radio-button_unchecked"
              navigation
              arrows
              height="160px"
              class="text-black shadow-1 rounded-borders"
            >
              <q-carousel-slide
                name="style"
                class="column no-wrap flex flex-center"
              >
                <q-icon name="style" size="36px " />
                <div class="q-mt-md text-center">
                  {{ stat1 }}
                </div>
              </q-carousel-slide>
              <q-carousel-slide name="tv" class="column no-wrap flex-center">
                <q-icon name="live_tv" size="36px " />
                <div class="q-mt-md text-center">
                  {{ stat2 }}
                </div>
              </q-carousel-slide>
              <q-carousel-slide
                name="layers"
                class="column no-wrap flex-center"
              >
                <q-icon name="layers" size="36px " />
                <div class="q-mt-md text-center">
                  {{ stat3 }}
                </div>
              </q-carousel-slide>
            </q-carousel>
          </div>
        </q-card>
      </div>
    </div>
    <q-toolbar>
      <div class="text-overline">Events</div>
      <q-space></q-space>
      <div class="text-overline">Yor patients today</div>
      <div class="text-caption text-green q-ml-md">All patients</div>
      <q-icon name="fas fa-chevron-right" size="10px" color="green-7" />
    </q-toolbar>
    <div class="row q-col-gutter-md">
      <div class="q-col flex">
        <div>
          <q-card class="card1 q-mx-md q-pa-sm q-mr-lg" bordered>
            <div class="row q-col-gutter-md">
              <div class="col-6">
                <div class="text-caption">Team meeting</div>
                <div class="text-caption text-grey-5">10:00-11.00</div>
                <q-avatar
                  v-for="n in 10"
                  :key="n"
                  size="40px"
                  class="overlapping"
                  :style="`left: ${n * 25}px`"
                >
                  <img
                    :src="`https://randomuser.me/api/portraits/med/men/${
                      n + 1
                    }.jpg`"
                  />
                </q-avatar>
              </div>
              <div class="col-6">
                <div class="flex justify-end row">
                  <q-toggle color="green" v-model="selection" val="" />
                </div>
                <div class="flex justify-end row">
                  <q-btn
                    round
                    icon="fas fa-pencil-alt"
                    size="10px"
                    color="black"
                    class="q-mr-sm"
                  ></q-btn>
                  <q-btn
                    round
                    icon="fas fa-chevron-right"
                    size="10px"
                    color="green"
                  ></q-btn>
                </div>
              </div>
            </div>
          </q-card>
          <q-card class="card1 q-mx-md q-pa-sm q-mr-lg" bordered>
            <div class="row q-col-gutter-md">
              <div class="col-6">
                <div class="text-caption">Team meeting</div>
                <div class="text-caption text-grey-5">16:00-16.30</div>
                <q-avatar
                  v-for="n in 5"
                  :key="n"
                  size="40px"
                  class="overlapping"
                  :style="`left: ${n * 25}px`"
                >
                  <img :src="`https://cdn.quasar.dev/img/avatar${n + 1}.jpg`" />
                </q-avatar>
              </div>
              <div class="col-6">
                <div class="flex justify-end row">
                  <q-toggle color="green" v-model="selection2" val="" />
                </div>
                <div class="flex justify-end row">
                  <q-btn
                    round
                    icon="fas fa-pencil-alt"
                    size="10px"
                    color="black"
                    class="q-mr-sm"
                  ></q-btn>
                  <q-btn
                    round
                    icon="fas fa-chevron-right"
                    size="10px"
                    color="green"
                  ></q-btn>
                </div>
              </div>
            </div>
          </q-card>
        </div>
        <div class="col-6">
          <q-card class="q-mx-lg q-pa-sm" bordered>
            <div class="row q-col-gutter-md">
              <div class="col-3">
                <div class="text-caption text-weight-bolder q-mt-lg">
                  11:00 am
                </div>
              </div>
              <div class="col-9">
                <q-card class="q-px-sm colorCard" bordered flat>
                  <q-item>
                    <q-item-section avatar>
                      <q-avatar>
                        <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
                      </q-avatar>
                    </q-item-section>

                    <q-item-section>
                      <q-item-label>Sarah Hosten</q-item-label>
                      <q-item-label caption>Diagnosis: Stroke</q-item-label>
                    </q-item-section>
                    <q-item-section side>
                      <q-icon name="fas fa-ellipsis-v" color="" />
                    </q-item-section>
                  </q-item>
                </q-card>
              </div>
            </div>
            <div class="row q-col-gutter-md q-mt-md">
              <div class="col-3">
                <div class="text-caption text-weight-bolder q-mt-lg">
                  11:30 am
                </div>
              </div>
              <div class="col-9">
                <q-card class="q-px-sm colorCard" bordered flat>
                  <q-item>
                    <q-item-section avatar>
                      <q-avatar>
                        <img src="https://cdn.quasar.dev/img/avatar1.jpg" />
                      </q-avatar>
                    </q-item-section>

                    <q-item-section>
                      <q-item-label>John Smith</q-item-label>
                      <q-item-label caption>Diagnosis</q-item-label>
                    </q-item-section>
                    <q-item-section side>
                      <q-icon name="fas fa-ellipsis-v" color="" />
                    </q-item-section>
                  </q-item>
                </q-card>
              </div>
            </div>
            <div class="row q-col-gutter-md q-mt-md">
              <div class="col-3">
                <div class="text-caption text-weight-bolder q-mt-lg">
                  12:00 am
                </div>
              </div>
              <div class="col-9">
                <q-card class="q-px-sm colorCard" bordered flat>
                  <q-item>
                    <q-item-section avatar>
                      <q-avatar>
                        <img
                          src="https://randomuser.me/api/portraits/med/men/79.jpg"
                        />
                      </q-avatar>
                    </q-item-section>

                    <q-item-section>
                      <q-item-label>Joseph Mayer</q-item-label>
                      <q-item-label caption>Diagnosis</q-item-label>
                    </q-item-section>
                    <q-item-section side>
                      <q-icon name="fas fa-ellipsis-v" color="" />
                    </q-item-section>
                  </q-item>
                </q-card>
              </div>
            </div>
          </q-card>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineComponent } from "vue";

const today = new Date();
const formattedToday = today.toISOString().split("T")[0].replace(/-/g, "/");
const options = {
  weekday: "long",
  year: "numeric",
  month: "long",
  day: "numeric",
};

const showToday = today.toLocaleDateString("en-US", options);

const showDate = ref(showToday);
const date = ref(formattedToday);

const isVisibleCal = ref(false);
const slide = ref("style");
const stat1 = `Disease Incidence Statistics:

1. Total number of cases of various diseases such as influenza, viral infections, chronic illnesses, and others.
2. Distribution of diseases among different age groups.
3. Dynamics of disease incidence over time.`;
const stat2 = `Patient Statistics:

Overall number of patients visiting the medical facility.
Level of satisfaction among patients with medical services.`;
const stat3 = `Vaccination and Prevention:

Percentage of vaccination coverage in different populations.
Vaccine effectiveness and research results.`;

const selection = ref(["green"]);
const selection2 = ref(["green"]);

const showCalendar = () => {
  isVisibleCal.value = !isVisibleCal.value;
};
</script>

<style scoped>
.search {
  width: 700px;
}
.doctors {
  height: 220px;
}
.overlapping {
  border: 2px solid white;
  position: absolute;
  margin-left: -20px;
}
.card1 {
  height: 100px;
  width: 380px;
}
.top {
  margin-top: -40px;
}
.colorCard {
  background: #f8f8f8;
}
</style>
