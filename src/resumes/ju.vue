<template>
  <div class="resume">
    <div class="content">
      <div class="content__left">
        <div class="section section-picture">
          <img class="picture">
        </div>

        <div class="section">
          <div class="section-headline">
            <i class="section-link__icon fa fa-user"></i>
            {{ lang.about }}
          </div>

          <div class="section-content">
            {{ person.about1 }}
            <br>
            {{ person.about2 }}
          </div>
        </div>

        <div class="section">
          <div class="section-headline">{{ lang.contact }}</div>

          <div class="section-content section-content--plain">
            <div class="section-link">
              <i class="section-link__icon material-icons">business</i>
              {{ person.contact.street }}
              <br>
              {{ person.contact.city }}
            </div>

            <a class="section-link" :href="'mailto:' + person.contact.email">
              <i class="section-link__icon material-icons">mail</i>
              {{ person.contact.email }}
            </a>

            <div class="section-link">
              <i class="section-link__icon material-icons">phone</i>
              {{ person.contact.phone }}
            </div>

            <a v-if="person.contact.website" class="section-link" :href="person.contact.website">
              <i class="section-link__icon fa fa-globe"></i>
              {{ person.contact.website }}
            </a>

            <a
              v-if="person.contact.linkedin"
              class="section-link"
              :href="'https://linkedin.com/in/' + person.contact.linkedin"
            >
              <i class="section-link__icon fa fa-linkedin"></i>
              {{ person.contact.linkedin }}
            </a>

            <a
              v-if="person.contact.github"
              class="section-link"
              :href="'https://github.com/' + person.contact.github"
            >
              <i class="section-link__icon fa fa-github"></i>
              {{ person.contact.github }}
            </a>

            <a
              v-if="person.contact.medium"
              class="section-link"
              :href="'https://medium.com/@' + person.contact.medium"
            >
              <i class="section-link__icon fa fa-medium"></i>
              {{ person.contact.medium }}
            </a>
          </div>
        </div>

        <div v-if="person.skills" class="section">
          <div class="section-headline">{{ lang.skills }}</div>

          <div class="section-content-grid">
            <a
              v-for="(skill, index) in person.skills"
              class="grid-item"
              :key="index"
              :href="skill.url"
            >
              <span class="squarred-grid-item">{{ skill.name }}</span>
            </a>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">{{ lang.languages }}</div>
          <div class="section-content section-content--plain">
            <div v-for="(language, index) in person.languages" :key="index" class="lang-item">
              <span>{{ language.name }}</span>
              <span>{{ language.level }}</span>
            </div>
          </div>
        </div>

        <div v-if="person.hobbies" class="section">
          <div class="section-headline">{{ lang.hobbies }}</div>

          <div class="section-content-grid">
            <a
              v-for="(hobby, index) in person.hobbies"
              class="grid-item"
              :key="index"
              :href="hobby.url"
            >
              <span class="squarred-grid-item">{{ hobby.name }}</span>
            </a>
          </div>
        </div>
      </div>

      <div class="content__right">
        <div
          class="banner__fullname"
        >{{ person.name.first }} {{ person.name.middle }} {{ person.name.last }}</div>
        <div class="banner__position">{{ person.position }}</div>
        <div class="banner__location">{{person.birth.age}} {{ lang.age }}</div>

        <div class="section section-top">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">work</i>
            {{ lang.experience }}
          </div>

          <div class="section-content">
            <a
              v-for="(experience, index) in person.experience"
              :key="index"
              class="section-content__item"
              :href="experience.website"
            >
              <span
                class="section-content__header"
              >{{ experience.position }}, {{ experience.company }}</span>
              <span class="section-content__subheader">
                <span class="section-content__plain">{{ experience.location }}</span>
              </span>

              <div class="section-content__text">{{ experience.timeperiod }}</div>
              <span class="section-content__text--light">{{ experience.description }}</span>
              <ul class="section-content" v-if="experience.list">
                <li
                  v-for="(item, index) in experience.list"
                  :key="index"
                  class="section-content__li"
                >
                  <span class="section-content__text--light">{{item}}</span>
                </li>
              </ul>
            </a>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">school</i>
            {{ lang.education }}
          </div>

          <div class="section-content">
            <a
              v-for="(education, index) in person.education"
              class="section-content__item"
              :key="index"
              :href="education.website"
            >
              <span class="section-content__header">{{ education.degree }}</span>
              <span class="section-content__subheader">{{ education.school }}</span>
              <span class="section-content__text">{{ education.timeperiod }}</span>
              <span class="section-content__text--light">{{ education.description }}</span>
            </a>
          </div>
        </div>

        <div v-if="person.projects" class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">code</i>
            {{ lang.projects }}
          </div>

          <div class="section-content-grid">
            <a
              v-for="(project, index) in person.projects"
              :key="index"
              class="section-content__item-grid"
              :href="project.url"
            >
              <span class="section-content__header">{{ project.name }}</span>
              <span class="section-content__subheader">{{ project.platform }}</span>
              <span class="section-content__text">{{ project.description }}</span>
            </a>
          </div>
        </div>

        <div v-if="person.contributions" class="section">
          <div class="section-headline">
            <i class="section-headline__icon fa fa-heart"></i>
            {{lang.contributions}}
          </div>

          <div class="section-content-grid">
            <a
              v-for="(contribution, index) in person.contributions"
              class="section-content__item-grid"
              :key="index"
              :href="contribution.url"
            >
              <span class="section-content__header">{{ contribution.name }}</span>
              <span class="section-content__text">{{ contribution.description }}</span>
              <span
                class="section-content__text--light"
                style="word-break: break-all;"
              >{{ contribution.url }}</span>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import { getVueOptions } from "./options";

const name = "ju";

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>
@accent-color: #fff1c0;
@banner-color: #d2d9e0;
@text-color: #000;
@text-color-a: rgba(0, 0, 0, 0.75);
@font-size: 13px;
@banner-height: 120px;
@picture-size: 120px;
@picture-offset: 35px;
@base-padding: 30px;
@left-column-width: 240px;

a {
  color: inherit;
  cursor: pointer;
  text-decoration-line: none;

  &:visited {
    color: inherit;
  }
}

.resume {
  position: relative;
  // font-family:'Roboto' !important;
  font-family: "Montserrat", sans-serif !important;
  font-size: 0.9em;
}

.picture {
  position: relative;
  height: @picture-size;
  width: @picture-size;
  border-radius: 50%;
  content: url("../../resume/id.jpg");
  z-index: 2;
}

.banner {
  width: calc(100% - @base-padding * 2);
  height: @banner-height;
  padding: @base-padding;
  background-color: @banner-color;
  /*
    background-image: url('../../resume/banner.png');
    background-repeat: no-repeat;
    background-size: cover;
  */
  color: @text-color;

  &__fullname {
    font-size: 32px;
  }

  &__position {
    font-size: 16px;
  }

  &__location {
    font-size: @font-size;
  }
}

.content {
  display: flex;
  width: 100%;
  height: 100%;

  &__left,
  &__right {
    height: 100%;
    padding: @base-padding;
  }

  &__left {
    display: flex;
    flex-direction: column;
    width: @left-column-width;
    color: @text-color-a;
    background-color: @accent-color;

    .section-headline {
      color: #000;
    }
  }

  &__right {
    flex: 1;
  }
}

.section-picture {
  text-align: center;
}

.section {
  margin: 20px 0;
  line-height: 17px;
}

.section-top {
  margin-top: 36px;
}

.section-link,
.section-headline {
  display: flex !important;
  align-items: center;
  color: @text-color;
  display: inline-block;
  font-size: 1.2em;
  margin: 8px 0 12px;

  &__icon {
    margin-right: 8px;
    font-size: 1.4em;
  }
}

.section-link {
  font-size: 1.1em;
  color: @text-color-a !important;

  &__icon {
    color: #000;
  }
}

.section-content {
  margin-top: 5px;
  font-size: @font-size;

  &__item {
    display: block;
    margin-bottom: 16px;
  }

  &__header {
    display: block;
    font-size: 1.1em;
    font-weight: 700;
  }

  &__subheader {
    display: block;
    font-weight: 400;
  }

  &__plain,
  &__text {
    display: block;
    font-size: @font-size;

    &--light {
      font-size: @font-size;
    }
  }

  &__plain {
    display: inline;
    font-weight: 300;
  }

  &__item-grid {
    flex: 1 1 0;
    margin-bottom: 5px;
    padding-right: 5px;
  }

  &--plain {
    padding: 0;
  }

  &__li {
    list-style-type: none;
  }

  &__li:before {
    content: "-";
    position: absolute;
    margin-left: -16px;
  }
}

ul.section-content {
  padding-left: 16px;
  list-style-position: outside;
  margin-bottom: 0;
}

.section-content-grid {
  display: flex;
  flex-wrap: wrap;
  margin-top: 5px;
  margin-bottom: 5px;
}

.grid-item {
  padding-right: 5px;
}

.squarred-grid-item {
  display: block;
  border: 1px solid @text-color;
  color: @text-color;
  margin-top: 5px;
  padding: 5px;
}

.lang-item {
  display: flex;
  font-size: 1.1em;
  border-bottom: 1px solid @text-color;
  padding-bottom: 5px;
  width: 93%;
  justify-content: space-between;
}

.lang-item:last-child {
  margin-top: 12px;
}
</style>
