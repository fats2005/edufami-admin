<template>
  <v-container grid-list-xl fluid>
    <v-layout row wrap>
      <v-flex lg10 sm10 xs10>
        <h4>Lesson</h4>
      </v-flex>
      <v-flex lg2 sm2 xs2></v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex lg12>
        <LessonCard :lesson="lesson"/>
        <LessonForm label="Edit Lesson"/>
      </v-flex>
    </v-layout>
    <v-layout row wrap>
      <v-flex lg12>
        <StepsTable/>
        <StepForm :lessonId="lesson.id" label="Add Step"/>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
import LessonCard from "@/components/cards/LessonCard";
import LessonForm from "@/components/forms/LessonForm";
import StepsTable from "@/components/tables/StepsTable";
import StepForm from "@/components/forms/StepForm";

export default {
  components: {
    LessonCard,
    StepForm,
    StepsTable,
    LessonForm
  },
  data: () => ({}),
  computed: {
    ...mapGetters(["lesson", "unit", "training"])
  },
  methods: {
    ...mapActions(["getLesson", "getStepsbyLesson"])
  },
  beforeMount() {
    const { lessonId } = this.$route.params;
    this.getLesson(lessonId);
    this.getStepsbyLesson(lessonId);
  }
};
</script>
