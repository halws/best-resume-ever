<template>
  <div class="resume">
    <div class="banner">
      <div class="banner__fullname">
        {{ person.name.first }} {{ person.name.middle }} {{ person.name.last }}
      </div>
      <div class="banner__position">{{ person.position }}</div>
      <div v-if="person.birth" class="banner__location">
        {{ lang.born }} {{ person.birth.year }} {{ lang.bornIn }}
        {{ person.birth.location }}
      </div>
    </div>

    <div class="content">
      <div class="content__left">
        <div class="section">
          <div class="section-headline">
            {{ lang.about }}
          </div>

          <div
            class="section-content section-content--plain"
            v-html="person.about"
          >
            <br />
            <br />
            {{ person.knowledge }}
          </div>
        </div>

        <div v-if="person.skills" class="section">
          <div class="section-headline">
            {{ lang.skills }}
          </div>

          <div class="section-content-grid">
            <a
              v-for="(skill, index) in person.skills"
              class="grid-item"
              :key="index"
              :class="{ link: skill.url !== undefined }"
              :href="skill.url"
            >
              <span class="squarred-grid-item">
                {{ skill.name }}
              </span>
            </a>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">
            {{ lang.contact }}
          </div>

          <div class="section-content section-content--plain">
            <div class="section-link">
              <i class="section-link__icon material-icons">business</i
              >{{ person.contact.city }}
            </div>

            <a class="section-link link" :href="contactLinks.email">
              <i class="section-link__icon material-icons">mail</i
              >{{ person.contact.email }}
            </a>

            <a class="section-link link" :href="`tel:${person.contact.phone}`">
              <i class="section-link__icon material-icons">phone</i
              >{{ person.contact.phone }}
            </a>

            <a
              v-if="person.contact.website"
              class="section-link link"
              :href="person.contact.website"
            >
              <i class="section-link__icon fa fa-globe"></i
              >{{ person.contact.website }}
            </a>

            <a
              v-if="person.contact.linkedin"
              class="section-link link"
              :href="contactLinks.linkedin"
            >
              <i class="section-link__icon fa fa-linkedin"></i
              >{{ person.contact.linkedin }}
            </a>

            <a
              v-if="person.contact.github"
              class="section-link link"
              :href="contactLinks.github"
            >
              <i class="section-link__icon fa fa-github"></i
              >{{ person.contact.github }}
            </a>

            <a
              v-if="person.contact.medium"
              class="section-link link"
              :href="contactLinks.medium"
            >
              <i class="section-link__icon fa fa-medium"></i
              >{{ person.contact.medium }}
            </a>
          </div>
        </div>
      </div>

      <div class="content__right">
        <div class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">work</i
            >{{ lang.experience }}
          </div>

          <div class="section-content">
            <span
              v-for="(experience, index) in person.experience"
              :key="index"
              class="section-content__item"
            >
              <span class="section-content__header">{{
                experience.position
              }}</span>
              <span class="section-content__subheader">
                {{ experience.company }}
                <span class="section-content__plain">{{
                  experience.location
                }}</span>
              </span>

              <div class="section-content__text">
                {{ experience.timeperiod }}
              </div>
              <span class="section-content__text--light">{{
                experience.description
              }}</span>

              <br />

              <span class="section-content__subheader"
                >My main duties are:</span
              >

              <ul style="padding-left: 1rem;" class="mt-5 mb-0">
                <li
                  v-for="(duty, dutyIndex) in experience.duties"
                  :key="`duty-${dutyIndex}`"
                >
                  <span class="section-content__text--light">{{ duty }}</span>
                </li>
              </ul>
              <br />
            </span>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">trending_up</i>My
            strengths are:
          </div>

          <div class="section-content">
            <span class="section-content__item">
              <ul style="padding-left: 1rem;">
                <li
                  v-for="(strength, strengthIndex) in person.strengths"
                  :key="strengthIndex"
                >
                  <span class="section-content__text--light">{{
                    strength
                  }}</span>
                </li>
              </ul>
            </span>
          </div>
        </div>

        <!-- <div
          v-if="person.projects"
          class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">code</i>{{ lang.projects }}
          </div>

          <div class="section-content-grid">
            <a v-for="(project, index) in person.projects" :key="index"
              class="section-content__item-grid"
              :class="{ link: project.url !== undefined}"
              :href="project.url">
              <span class="section-content__header"> {{ project.name }} </span>
              <span class="section-content__subheader">{{ project.platform }}</span>
              <span class="section-content__text"> {{ project.description }} </span>
            </a>
          </div>
        </div> -->

        <div class="section">
          <!-- <div class="section-headline">
            <i class="section-headline__icon material-icons">fitness_center</i
            >Hobby
          </div> -->

          <div class="section-content-grid">
            <a
              v-for="(contribution, index) in person.contributions"
              class="section-content__item-grid"
              :key="index"
              :class="{ link: contribution.url !== undefined }"
              :href="contribution.url"
            >
              <span class="section-content__header">
                {{ contribution.name }}
              </span>
              <span class="section-content__text">
                {{ contribution.description }}
              </span>
              <span
                class="section-content__text--light"
                style="word-break: break-all;"
              >
                {{ contribution.url }}
              </span>
            </a>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">translate</i
            >Languages
          </div>

          <div class="section-content-grid">
            <a
              v-for="(contribution, index) in person.languages"
              class="section-content__item-grid"
              :key="index"
            >
              <span class="section-content__header" style="color: black;">
                {{ contribution.name }}
              </span>
              <span class="section-content__text">
                {{ contribution.level }}
              </span>
            </a>
          </div>
        </div>
      </div>
    </div>

    <img class="picture" />
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'cool';

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>
@accent-color: #34495e;
@banner-color: #42b883;
@banner-height: 120px;
@picture-size: 120px;
@picture-offset: 35px;
@base-padding: 30px;
@left-column-width: 240px;

.link {
  color: inherit;
  cursor: pointer;
  text-decoration-line: none;

  &:visited {
    color: inherit;
  }
}

.resume {
  position: relative;
  font-family: 'Roboto' !important;
  font-size: 0.9em;
}

.picture {
  position: absolute;
  top: @banner-height - @picture-offset;
  left: @left-column-width + @base-padding * 2 - @picture-size / 2;
  height: @picture-size;
  width: @picture-size;
  border-radius: 50%;
  border: 5px solid @accent-color;
  content: url('../../resume/id.jpg');
  z-index: 2;
}

.banner {
  width: calc(100% - @base-padding * 2);
  height: @banner-height;
  padding: @base-padding;
  background-color: @banner-color;
  color: white;

  &__fullname {
    font-size: 32px;
  }

  &__position {
    font-size: 16px;
  }

  &__location {
    font-size: 12px;
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
    width: @left-column-width;
    color: rgba(255, 255, 255, 0.59);
    background-color: @accent-color;

    .section-headline {
      color: white;
    }
  }

  &__right {
    flex: 1;
  }
}

.section {
  margin: 20px 0;
}

.section-link,
.section-headline {
  display: flex !important;
  align-items: center;
  color: @accent-color;
  display: inline-block;
  font-size: 1.2em;
  margin: 8px 0;

  &__icon {
    margin-right: 8px;
    font-size: 1.4em;
  }
}

.section-link {
  font-size: 1.1em;
  color: rgba(255, 255, 255, 0.59) !important;

  &__icon {
    color: white;
  }
}

.section-content {
  margin-top: 5px;
  padding-left: 32px;
  font-size: 14px;

  &__item {
    display: block;
    margin-bottom: 5px;
  }

  &__header {
    display: block;
    font-size: 1.1em;
    font-weight: 500;
    color: @banner-color;
  }

  &__subheader {
    display: block;
    font-size: 0.9em;
    font-weight: 500;
  }

  &__plain,
  &__text {
    display: block;
    font-size: 12px;

    &--light {
      font-size: 12px;
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
  border: 1px solid white;
  color: white;
  margin-top: 5px;
  padding: 5px;
}

.mt-5 {
  margin-top: 5px;
}

.mb-0 {
  margin-bottom: 0;
}

.mb-5 {
  margin-bottom: 5px;
}
</style>
