<template>
  <div id="app">
    <Header></Header>
    <transition name="fade">
      <section v-if="filterData.length > 0" class="filterCard">
        <ul class="jobs">
          <li v-for="job in filterData" :key="job.key" class="job-link">
            <p class="name ">{{ job }}</p>
            <a class="clear" @click="removeFilter(tool)"
              ><svg xmlns="http://www.w3.org/2000/svg" width="14" height="14">
                <path
                  fill="#fff"
                  fill-rule="evenodd"
                  d="M11.314 0l2.121 2.121-4.596 4.596 4.596 4.597-2.121 2.121-4.597-4.596-4.596 4.596L0 11.314l4.596-4.597L0 2.121 2.121 0l4.596 4.596L11.314 0z"
                /></svg
            ></a>
          </li>
        </ul>

        <div class="clear-section">
          <a @click="clearFilters()">Clear</a>
        </div>
      </section>
    </transition>
    <section class="cards">
      <!-- <a
        v-for="tool in filterData"
        :key="tool.id"
        @click="removeFilter(tool)"
        >{{ tool }}</a
      > -->
      <ul>
        <li v-for="card in filteredJobs" :key="card.id">
          <JobCard @clicked="filterJob" :card="card" />
        </li>
      </ul>
    </section>
  </div>
</template>

<script>
import Header from "./components/Header";
import JobCard from "./components/JobCard";

export default {
  name: "App",
  components: {
    Header,
    JobCard,
  },
  methods: {
    filterJob(tool) {
      return this.filterData.includes(tool)
        ? false
        : this.filterData.push(tool);
    },
    removeFilter(tool) {
      this.filterData.splice(this.filterData.indexOf(tool), 1);
    },
    clearFilters() {
      return this.filterData.splice(0, this.filterData.length);
    },
  },
  computed: {
    filteredJobs: function() {
      return this.companies.filter((el) => {
        return this.filterData <= 0
          ? this.companies
          : el.attributes.some((v) => this.filterData.includes(v));
      });
    },
  },
  data() {
    return {
      filterData: [],
      companies: [
        {
          id: 1,
          company: "Photosnap",
          logo: "photosnap.svg",
          new: true,
          featured: true,
          position: "Senior Frontend Developer",
          role: "Frontend",
          level: "Senior",
          postedAt: "1d ago",
          contract: "Full Time",
          location: "USA Only",
          languages: ["HTML", "CSS", "JavaScript"],
          tools: [],
          attributes: ["HTML", "CSS", "JavaScript", "Senior", "Frontend"],
        },
        {
          id: 2,
          company: "Manage",
          logo: "manage.svg",
          new: true,
          featured: true,
          position: "Fullstack Developer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "1d ago",
          contract: "Part Time",
          location: "Remote",
          languages: ["Python"],
          tools: ["React"],
          attributes: ["Midweight", "Fullstack", "React", "Python"],
        },
        {
          id: 3,
          company: "Account",
          logo: "account.svg",
          new: true,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2d ago",
          contract: "Part Time",
          location: "USA Only",
          languages: ["JavaScript"],
          tools: ["React", "Sass"],
          attributes: ["Frontend", "Junior", "JavaScript", "React", "Sass"],
        },
        {
          id: 4,
          company: "MyHome",
          logo: "myhome.svg",
          new: false,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "5d ago",
          contract: "Contract",
          location: "USA Only",
          languages: ["CSS", "JavaScript"],
          tools: [],
          attributes: ["Frontend", "Junior", "CSS", "JavaScript"],
        },
        {
          id: 5,
          company: "Loop Studios",
          logo: "loop-studios.svg",
          new: false,
          featured: false,
          position: "Software Engineer",
          role: "FullStack",
          level: "Midweight",
          postedAt: "1w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["JavaScript"],
          tools: ["Ruby", "Sass"],
          attributes: ["Ruby", "Sass", "JavaScript", "Midweight", "FullStack"],
        },
        {
          id: 6,
          company: "FaceIt",
          logo: "faceit.svg",
          new: false,
          featured: false,
          position: "Junior Backend Developer",
          role: "Backend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "UK Only",
          tools: ["RoR"],
          attributes: ["RoR", "Backend", "Junior"],
        },
        {
          id: 7,
          company: "Shortly",
          logo: "shortly.svg",
          new: false,
          featured: false,
          position: "Junior Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["HTML", "JavaScript"],
          tools: ["Sass"],
          attributes: ["Frontend", "Junior", "HTML", "JavaScript", "Sass"],
        },
        {
          id: 8,
          company: "Insure",
          logo: "insure.svg",
          new: false,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "USA Only",
          languages: ["JavaScript"],
          tools: ["Vue", "Sass"],
          attributes: ["Frontend", "Junior", "JavaScript", "Vue", "Sass"],
        },
        {
          id: 9,
          company: "Eyecam Co.",
          logo: "eyecam-co.svg",
          new: false,
          featured: false,
          position: "Full Stack Engineer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "3w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["JavaScript", "Python"],
          tools: ["Django"],
          attributes: [
            "Fullstack",
            "Midweight",
            "JavaScript",
            "Python",
            "Django",
          ],
        },
        {
          id: 10,
          company: "The Air Filter Company",
          logo: "the-air-filter-company.svg",
          new: false,
          featured: false,
          position: "Front-end Dev",
          role: "Frontend",
          level: "Junior",
          postedAt: "1mo ago",
          contract: "Part Time",
          location: "Worldwide",
          languages: ["JavaScript"],
          tools: ["React", "Sass"],
          attributes: ["Frontend", "Junior", "JavaScript", "React", "Sass"],
        },
      ],
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Spartan:wght@500;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Spartan", sans-serif;
  --primary-green: #5ba4a4;
  --dark-green: hsl(180, 6%, 35%);
  --bold: 700;
  --med-bold: 500;
  --small-text: 13px;
  --light-green: rgb(239, 250, 250);
}

ul li {
  list-style-type: none;
}

a {
  text-decoration: none;
}

#app {
  height: 100vh;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background: hsl(180, 52%, 96%);
}

.filterCard {
  background-color: #fff;
  margin: 0 1.25rem;
  transform: translateY(-2rem);
  border-radius: 7px;
  padding: 2rem 1.25rem;
  display: flex;
  box-shadow: 2px 3px 20px 1px rgba(142, 223, 223, 0.75);
}

.filterCard .jobs {
  flex-grow: 1;
  display: flex;
  flex-wrap: wrap;
}

.job-link {
  background: var(--light-green);
  border-radius: 7px;
  display: flex;
  align-items: center;
  margin: 0.45rem 1.25rem 0.45rem 0;
}

.job-link .name {
  margin-right: 0.5rem;
  padding: 0.45rem;
  color: var(--primary-green);
  font-weight: 700;
  font-size: var(--small-text);
}

.job-link .clear {
  background: var(--primary-green);
  padding: 0.45rem;
  height: 100%;
  border-top-right-radius: 7px;
  border-bottom-right-radius: 7px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}

.job-link .clear:hover {
  background: var(--dark-green);
}

.clear-section {
  display: flex;
  justify-content: center;
  align-items: center;
}

.clear-section a {
  color: rgb(105, 103, 103);
  font-weight: var(--bold);
}

.clear-section a:hover {
  color: var(--primary-green);
  text-decoration: underline;
}

.cards {
  margin: 4rem 1.25rem;
}

.cards ul li {
  list-style: none;
  margin-top: 3rem;
}

/* Transitions */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
