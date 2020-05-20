<template>
  <div
    class="card"
    :style="[this.card.new || this.card.featured ? cardBorder : card]"
  >
    <div class="card-logo">
      <img :src="companyImage" alt="Logo" />
    </div>
    <div class="information">
      <div class="first-row">
        <p class="bold company-name">
          {{ card.company }}
        </p>

        <p class="icon new-icon" v-if="card.new">new!</p>

        <p class="icon featured-icon" v-if="card.featured">featured</p>
      </div>
      <div class="second-row">
        <p class="bold">{{ card.position }}</p>
      </div>
      <div class="light-text third-row">
        <p>{{ card.postedAt }}</p>
        <div class="dot"></div>
        <p>{{ card.level }}</p>
        <div class="dot"></div>
        <p>{{ card.location }}</p>
      </div>
    </div>
    <div class="splitter"></div>
    <div class="tags">
      <a v-on:click="jobFilter(tool)" v-for="tool in card.tools" :key="tool.id">
        {{ tool }}
      </a>
      <a
        v-on:click="jobFilter(lang)"
        v-for="lang in card.languages"
        :key="lang.id"
      >
        {{ lang }}
      </a>
      <a v-on:click="jobFilter(card.role)">{{ card.role }}</a>
      <a v-on:click="jobFilter(card.level)"> {{ card.level }}</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "JobCard",
  props: ["card"],
  computed: {
    companyImage: function() {
      return require(`.././assets/${this.card.logo}`);
    },
  },
  data() {
    return {
      cardBorder: {
        borderLeft: "4px solid hsl(180, 29%, 50%)",
      },
    };
  },
  methods: {
    jobFilter(data) {
      if (data) {
        this.$emit("clicked", data);
      }
    },
  },
};
</script>

<style scoped>
/* Variables */
* {
  --primary-green: rgb(91, 164, 164);
  --dark-green: hsl(180, 6%, 35%);
  --bold: 700;
  --med-bold: 500;
  --small-text: 13px;
  --light-green: rgb(239, 250, 250);
}

/* Classes */
.company-name {
  font-weight: var(--bold);
  color: var(--primary-green);
  font-size: var(--small-text);
}

.icon {
  color: #fff;
  margin-left: 0.75rem;
  padding: 0.45rem 0.4rem 0.3rem 0.4rem;
  font-size: 0.65rem;
  font-weight: var(--bold);
  border-radius: 15px;
}

.featured-icon {
  background: var(--dark-green);
  text-transform: uppercase;
}

.new-icon {
  background: var(--primary-green);
  text-transform: uppercase;
}

.white-txt {
  color: #fff;
}

.bold {
  font-weight: var(--bold);
}

.light-text {
  color: rgb(182, 182, 182);
}

.card {
  box-shadow: 2px 3px 20px 1px rgba(142, 223, 223, 0.75);
  /* border-left: 4px solid hsl(180, 29%, 50%); */
  border-radius: 7px;
  padding: 2rem 1.25rem 0.9rem 1.25rem;
  background: #fff;
  display: flex;
  flex-direction: column;
  position: relative;
}

/* Card Logo */
.card-logo {
  position: absolute;
  top: -20px;
  left: 20px;
}

.card-logo img {
  width: 50%;
}

.first-row {
  display: flex;
  align-items: center;
  margin-bottom: 0.55rem;
}

.second-row {
  margin-bottom: 1rem;
  font-size: 0.9rem;
}

.second-row p:hover {
  color: var(--primary-green);
}

.third-row {
  font-size: var(--small-text);
  font-weight: var(--med-bold);
  display: flex;
  position: relative;
  align-items: center;
  margin-bottom: 1rem;
}

.dot {
  content: "";
  display: block;
  height: 4px;
  width: 4px;
  background: rgb(182, 182, 182);
  border-radius: 50%;
  margin: 0 0.5rem;
}

.splitter {
  background: rgb(182, 182, 182);
  height: 1px;
  width: 100%;
}

.tags {
  margin-top: 1rem;
  padding-right: 1rem;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  font-size: 0.85rem;
}

.tags a {
  color: var(--primary-green);
  font-weight: var(--bold);
  background: var(--light-green);
  text-align: center;
  padding: 0.5rem 0.5rem;
  margin-bottom: 0.85rem;
  border-radius: 5px;
  text-decoration: none;
  margin-right: 1.25rem;
  cursor: pointer;
}

.tags a:hover {
  background: var(--primary-green);
  color: #fff;
}

/* Desktop Media */
@media (min-width: 900px) {
  .card {
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }

  .tags {
    display: inline-block;
    margin-bottom: 2rem;
  }

  .splitter {
    display: none;
  }
}
</style>
