<template>
  <b-card
    img-src="@/my_content/avatar.jpg"
    img-alt="avatar"
    img-top
    style="min-width: 15rem; max-width: 25rem"
    class="m-3"
  >
    <b-card-title>Internet Paspoort</b-card-title>
    <b-card-sub-title class="m-2"
      >aangemaakt op 17-10-20</b-card-sub-title
    >
    <b-card-text>
        Tim Brouwer
    </b-card-text>
    <b-card-text>
      <p><b>Stamps</b></p>
      <p>github.nl.stamp</p>
      <p>linkedin.nl.stamp</p>
    </b-card-text>
  </b-card>
</template>

<script lang="ts">
export default {
  name: "CourseCard",
  props: ["course"],
  computed: {
    audience() {
      return this.course.audience ? this.course.audience : "Iedereen";
    },
    cost() {
      return this.course.cost ? this.course.cost : "Onbekend";
    },
    description() {
      return this.course.description
        ? this.course.description
        : "Geen beschrijving beschikbaar";
    },
    duration() {
      return this.course.duration ? this.course.duration : "Onbekend";
    },
    isInternal() {
      return this.course.link === null || this.course.link === undefined
    },
    link() {
      const defaultURL = "/courses/" + this.course.name.short
      const defaultText = "Lees verder!"
      if (this.course.link === undefined) {
        return { url: defaultURL, text: defaultText };
      } else {
        return {
          url: this.course.link.url ? this.course.link.url : defaultURL,
          text: this.course.link.text
            ? this.course.link.text
            : defaultText,
        };
      }
    },
    name() {
      // name is used as key, so it should not be missing
      if( this.course.name === undefined ) {
        return ""
      } else if( this.course.name.full ) {
        return this.course.name.full   
      } else {
        return this.course.name
      }
    },
    start() {
      return this.course.start ? this.course.start : "Onbekend";
    },
    mentor() {
      if (this.course.mentor === undefined) {
        return { name: "Onbekend", role: "Mentor", avatar: this.randomPic() };
      } else {
        return {
          name: this.course.mentor.name ? this.course.mentor.name : "Onbekend",
          role: this.course.mentor.role ? this.course.mentor.role : "Mentor",
          avatar: this.course.mentor.avatar
            ? this.course.mentor.avatar
            : this.randomPic(),
        };
      }
    },
  },
  methods: {
    randomPic() {
      return "https://picsum.photos/200/200?random=" + Math.random();
    },
  },
};
</script>

<style scoped>
</style>