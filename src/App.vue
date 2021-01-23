<template>
  <div class="container column">
    <FormControl @add-block="addBlock" />
    <BlockContainer>
      <template #title v-if="resume.title">
        <BlockTitle :title="resume.title" />
      </template>
      <template #avatar v-if="resume.avatar">
        <BlockAvatar :src="resume.avatar" />
      </template>

      <template #content v-if="resume.content.length !== 0">
        <BlockContent v-for="block in resume.content" :key="block.subtitle">
          <template #subtitle v-if="block.subtitle">
            <BlockSubtitle :subtitle="block.subtitle"/>
          </template>
          <template #text v-if="block.text">
            <BlockText :text="block.text"/>
          </template>
        </BlockContent>
      </template>
    </BlockContainer>
  </div>
  <FeedbackSection />
</template>

<script>
import FormControl from "@/components/FormControl.vue";
import BlockContainer from "@/components/BlockContainer.vue";
import FeedbackSection from "@/components/FeedbackSection.vue";
import BlockTitle from "@/components/BlockTitle.vue";
import BlockAvatar from "@/components/BlockAvatar.vue";
import BlockSubtitle from "@/components/BlockSubtitle.vue";
import BlockText from "@/components/BlockText.vue";
import BlockContent from "@/components/BlockContent.vue";
export default {
  components: {
    FormControl,
    BlockContainer,
    FeedbackSection,
    BlockTitle,
    BlockAvatar,
    BlockSubtitle,
    BlockText,
    BlockContent
  },
  data: () => ({
    resume: {
      title: '',
      avatar: '',
      content: []
    }
  }),
  methods: {
    addBlock(value, type) {
      if (type === 'title' || type === 'avatar') {
        this.resume[type] = value
      } else {
        const tempContent = { subtitle: '', text: '' }
        tempContent[type] = value
        this.resume.content.push(tempContent)
        // Можно объединить логику Подзаголовка и Текста в один "контейнер" как в темплейте, но уже вымотался очень и сделал как-то так
        // по ТЗ вроде все сходится (функционал) :) Регните плиз, хочу до ТС скорее добраться и композишн апи
        // P.S: Спасибо за курсы, ревью и старания команды - рекомендую знакомым
      }
    },
  }
};
</script>

<style></style>
