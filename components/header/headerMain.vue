<template>
  <header class="header">
    <a href="/" class="header__logo">
      <img src="@/assets/images/LogoHorisontal.svg" alt="logo" />
    </a>
    <div class="header__buttons">
      <ui-button type="outline" text="Вхід" @click="showPopup('popup1')" />
      <ui-button text="Реєстрація" @click="showPopup('popup2')" />
    </div>

    <uiModal :show="popups.popup1" :id="'popup1'" @close="closePopup">
      <div class="modal__data">
        <div class="modal__heading">
          <div class="modal__icon">
            <span class="icon-lock"></span>
          </div>
          <h3 class="h5">Вхід</h3>
        </div>
        <form class="modal__form">
          <ui-input v-model="model" placeholder="Ваш email" />
          <ui-input
            v-model="model"
            type="password"
            placeholder="Ваш пароль"
            suffix="icon-eye"
          />
          <ui-button text="Війти" size="medium" />
        </form>
      </div>
    </uiModal>
    <uiModal :show="popups.popup2" :id="'popup2'" @close="closePopup">
      <div class="modal__info">
        <div class="modal__info-content">
          <div class="modal__info-title">
            Зможеш обрати <br />
            свій варіант
          </div>
          <UiCarousel></UiCarousel>
          <!-- <div class="modal__slider">
            <div class="modal__slider-container">
              <div class="modal__info-row">
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">CPA</div>
                    <div class="modal__item-title">$25 і вище</div>
                  </div>
                </div>
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">REVSHARE</div>
                    <div class="modal__item-title">Піднімай до 60%</div>
                  </div>
                </div>
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">Гібрід</div>
                    <div class="modal__item-title">Зробимо як скажеш</div>
                  </div>
                </div>
              </div>
              <div class="modal__info-row">
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">CPA</div>
                    <div class="modal__item-title">$25 і вище</div>
                  </div>
                </div>
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">REVSHARE</div>
                    <div class="modal__item-title">Піднімай до 60%</div>
                  </div>
                </div>
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">Гібрід</div>
                    <div class="modal__item-title">Зробимо як скажеш</div>
                  </div>
                </div>
              </div>
              <div class="modal__info-row">
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">CPA</div>
                    <div class="modal__item-title">$25 і вище</div>
                  </div>
                </div>
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">REVSHARE</div>
                    <div class="modal__item-title">Піднімай до 60%</div>
                  </div>
                </div>
                <div class="modal__item">
                  <div class="modal__item-icon"></div>
                  <div class="modal__item-text">
                    <div class="modal__item-title">Гібрід</div>
                    <div class="modal__item-title">Зробимо як скажеш</div>
                  </div>
                </div>
              </div>
            </div>
            <div class="slider-dots"></div>
          </div> -->
        </div>
      </div>
      <div class="modal__data">
        <div class="modal__heading">
          <div class="modal__icon modal__icon_reg">
            <span class="icon-user"></span>
          </div>
          <h3 class="h5">Реєстрація</h3>
        </div>
        <form class="modal__form">
          <ui-input v-model="model" placeholder="Вашe ім'я" />
          <ui-input v-model="model" placeholder="Ваш email" />
          <ui-input
            v-model="model"
            type="password"
            placeholder="Ваш пароль"
            suffix="icon-eye"
          />
          <ui-input
            v-model="model"
            type="password"
            placeholder="Повторіть пароль"
            suffix="icon-eye"
          />
          <div class="modal__social">
            <div class="modal__social-title">
              <p>Оберіть спосіб звязку</p>
            </div>
            <div class="modal__social-row">
              <a
                href="#"
                @click.prevent="chooseCommunication('telegram')"
                class="modal__social-icon"
                :class="{ active: communication === 'telegram' }"
              >
                <img src="@/assets/images/telegram.svg" alt="" />
              </a>
              <a
                href="#"
                @click.prevent="chooseCommunication('skype')"
                class="modal__social-icon"
                :class="{ active: communication === 'skype' }"
              >
                <img src="@/assets/images/skype.svg" alt="" />
              </a>
              <KeepAlive>
                <ui-input
                  v-if="communication === 'telegram'"
                  placeholder="@телеграм_адреса"
                  suffix="icon-check"
                  success
                />
              </KeepAlive>
              <KeepAlive>
                <ui-input
                  v-if="communication === 'skype'"
                  placeholder="@скайп_адреса"
                  suffix="icon-check"
                  success
                />
              </KeepAlive>
            </div>
          </div>
          <ui-button text="Реєстрація" size="medium" />
        </form>
      </div>
    </uiModal>
  </header>
</template>

<script>
import uiModal from '../ui/ui-modal.vue';
import UiCarousel from '../ui/ui-carousel.vue';
export default {
  components: {
    uiModal,
  },

  data() {
    return {
      popups: {
        popup1: false,
        popup2: false,
      },
      currentIndex: 0,
      currentPosition: 0,
      timerId: null,
      communication: 'telegram',
    };
  },
  mounted() {
    if (this.autoPlay) {
      this.startAutoPlay();
    }
  },
  methods: {
    chooseCommunication(value) {
      this.communication = value;
    },
    showPopup(id) {
      this.popups[id] = true;
    },
    closePopup(id) {
      this.popups[id] = false;
    },
  },
};
</script>

<style lang="scss">
.header {
  position: relative;
  z-index: 2;
  padding: 24px 26.5px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
  align-items: center;
  @media screen and (max-width: 767px) {
    padding: 10px 15px;
  }

  &__logo {
    grid-column: 2 / 3;
    justify-self: center;
    @media screen and (max-width: 767px) {
      grid-column: 1 / 3;
    }
  }

  &__buttons {
    grid-column: 3 / 4;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    gap: 10px;
  }
}
</style>
