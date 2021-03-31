<template>
  <div className="main-content">
    <div className="main-content-grid">
      <div
        class="thumbnail"
        v-for="np in displayThumbnail()"
        :key="np.publicationId"
      >
        <Thumbnail :newspaper="np" />
      </div>
    </div>
  </div>
</template>

<script>
import Thumbnail from "@/components/Thumbnail";
import fullData from "@/json/category_quotidien.json";

const allNewsPapers = fullData.issues.filter(
  ({ publication }) => publication?.category?.name === "Quotidiens"
);

export default {
  name: "Content",
  props: {
    subCategorie: String,
  },
  components: {
    Thumbnail,
  },
  data() {
    return {
      allNewsPapers,
    };
  },
  methods: {
    displayThumbnail() {
      return this.subCategorie === "tout"
        ? allNewsPapers
        : allNewsPapers.filter(({ publication }) =>
            publication?.category?.subCategories.find(
              ({ name }) => name.toLowerCase() === this.subCategorie
            )
          );
    },
  },
};
</script>

<style>
.main-content {
  padding-bottom: 100px;
}

.main-content-grid {
  align-items: center;
  background-color: var(--cafeyn-bcg-color);
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin: 0 auto;
  max-width: 1274px;
  padding: 0 32px 0 0;
}

@media screen and (min-width: 768px) and (max-width: 1024px) {
  .main-content-grid {
    padding: 0 32px 0 16px;
  }
}
</style>
