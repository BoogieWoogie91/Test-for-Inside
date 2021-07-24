<template>
  <div class="hello">
		<!-- custom-page -->
		<div class="custom-page">
				<!-- custom-page__bg -->
				<div class="custom-page__bg message-page__bg">
				</div>
				<!-- /custom-page__bg -->
				<!-- container -->
				<div class="container medium">
						<!-- chat-box -->
						<div class="chat-box">
								<!-- chat-box__header -->
								<div class="chat-box__header">
										<a href="#" class="back"><i class="icon icon-left"></i></a>
										<h1 class="main-title">Добро пожаловать в онлаин-чат службы поддержки</h1>
										<div style="width: 12px;" class=""></div>
								</div>
								<!-- /chat-box__header -->
								<!-- chat-box__messages -->
								<div class="chat-box__messages">
										<div class="chat-box__separator">
												12 июля
										</div>

                      <div class="chat-box__message" v-bind:class="{ own: msg.own }" v-for="(msg, index) in messages" :key="index">
												<div class="name">{{msg.name}}</div>
												<div class="message">
														{{msg.message}}
														<div class="time">{{msg.time}}</div>
														<div class="clear"></div>
												</div>
                      </div>
                      <div class="clear"></div>


                    <!-- <div>
                      <div class="chat-box__message own">
												<div class="message">
														Добрый день, Дмитрий. <br>Опишите вашу проблему более подробно. У вас возникли ошибки (баги) на сайте?
														<div class="time">13:05</div>
														<div class="clear"></div>
												</div>
                      </div>
                      <div class="clear"></div>
                    </div> -->
								</div>
								<!-- /chat-box__messages -->
								<!-- chat-box__form -->
								<form class="chat-box__form main-form" @submit="sendMsg">
										<textarea class="input-style" rows="7"></textarea>
										<div class="row">
												<label class="main-form__item file-field">
												</label>
												<div class="main-form__submit">
														<button type="submit" class="radius-button standart rounded" >Отправить</button>
												</div>
										</div>
								</form>
								<!-- /chat-box__form -->
						</div>
						<!-- /chat-box -->
				</div>
				<!-- /container -->
		</div>
		<!-- /custom-page -->
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
  },
  data() {
    return {
      messages: [],
    }
  },
  methods: {
    sendMsg(e) {
      e.preventDefault();
      if (document.querySelector('.input-style').value) {
        this.openSocket();
      } else {
        document.querySelector('.input-style').value = 'Сюда надо бы чтото написать:)'
      }
    },

    openSocket() {
      const socket = new WebSocket('ws://skade.cc:38080');

      let obj = {
        name:'Denis',
        message: document.querySelector('.input-style').value,
        own: true,
        time: this.getCurrentDate()
      };
      
      const self = this;
      const json = JSON.stringify(obj);

      if(socket.readyState === 1) {
        this._data.messages.push(obj);
        socket.send(json);
      } else {
        socket.addEventListener('open', function () {
          self._data.messages.push(obj);
          socket.send(json);
        });
      }

      socket.addEventListener('close', function () {
        this.openSocket();
      });

      socket.addEventListener('error', function (event) {
        alert(`[error] ${event}`);
      });

      socket.addEventListener('message', function (event) {
        const response = JSON.parse(event.data);
        response.own = false;

        self._data.messages.push(response);
        console.log(self._data.messages);
      });
    },

    getCurrentDate() {
      const date = new Date();

      const hours = date.getHours();
      const minutes = date.getMinutes();

      return `${hours} : ${minutes}`
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.icon-ok:before {
  content: '\e800';
}

/* '' */
.icon-settings:before {
  content: '\e80b';
}

/* '' */
.icon-transfer:before {
  content: '\e80d';
}



/* '' */
.icon-arrow-down:before {
  content: '\e816';
}

/* '' */
.icon-arrow-left:before {
  content: '\e817';
}

/* '' */
.icon-arrow-right:before {
  content: '\e818';
}

/* '' */
.icon-arrow-up:before {
  content: '\e819';
}

/* '' */
.icon-star:before {
  content: '\e81a';
}

/* '' */
.icon-left:before {
  content: '\f104';
}

/* '' */
.icon-right:before {
  content: '\f105';
}

/* '' */
.icon-up:before {
  content: '\f106';
}

/* '' */
.icon-long-up:before {
  content: '\f176';
}

/* .main-settings__toggler {
  display: grid;
  grid-template-columns: 28px 1fr;
  align-items: center;
  grid-gap: 15px;
}

.main-settings__toggler .toggler {
  transition: .2s ease;
  background: #c4c4c4;
  height: 14px;
  border-radius: 7px;
  box-sizing: border-box;
  padding: 1px;
  position: relative;
}

.main-settings__toggler .toggler.active {
  background: #1ab4ed;
}

.main-settings__toggler .toggler.active .icon {
  right: 1px;
}

.main-settings__toggler .toggler .icon {
  position: absolute;
  display: block;
  background: #fff;
  width: 12px;
  height: 12px;
  border-radius: 6px;
}

.main-settings__item {
  margin-bottom: 25px;
}

.beautiful-button {
  font-family: 'ish-open', sans-serif;
  color: #fff;
  border-radius: 4px;
  box-sizing: border-box;
  font-weight: 400;
  display: inline-block;
  border: none !important;
  outline: none !important;
  box-shadow: none !important;
  cursor: pointer;
  padding: 11px;
  min-width: 210px;
  overflow: hidden;
  transition: .2s ease;
}

.beautiful-button:hover {
  -webkit-filter: brightness(1.2);
  filter: brightness(1.2);
}

.beautiful-button.greened {
  background: #1C5E5E;
  background: linear-gradient(90deg, #1C5E5E 0%, #28794C 100%);
}

.beautiful-button.reded {
  background: #622D32;
  background: linear-gradient(90deg, #622D32 0%, #913A38 100%);
}

.addition-button {
  border: 1px solid #fff;
  display: block;
  padding: 10px 15px;
  text-align: center;
  cursor: pointer;
}

.addition-button:hover {
  color: #1ab4ed;
  border: 1px solid #1ab4ed;
} */

.input-style {
  display: block;
  padding: 12px;
  font-size: .95rem;
  border: none;
  outline: none;
  box-shadow: none;
  box-sizing: border-box;
  max-width: 100%;
  font-family: inherit;
}

.input-style:focus {
  border: none;
  outline: 3px solid #1ab4ed;
  box-shadow: none;
}

.input-style.alt {
  border: 1px solid #000;
  padding: 7px 12px;
}

.main-title {
  text-align: center;
  margin-bottom: 2.2em;
  font-weight: 400;
  font-family: 'ish-exo', sans-serif;
}

.main-title + .subtitle {
  text-align: center;
  opacity: .5;
  font-size: .95rem;
  margin-bottom: 50px;
}

h1.main-title + .subtitle {
  margin-top: -40px;
}

/* .modal {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: 90;
  display: none;
}

.modal.active {
  display: block;
}

.modal__header {
  display: none;
}

.modal__container {
  overflow-y: auto;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  display: flex;
  justify-content: center;
}

.modal__container .title {
  font-size: 1.75rem;
}

.modal__container .title + .subtitle {
  margin-top: -35px;
  margin-bottom: 30px;
}

.modal__bg {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: #000;
  opacity: 0.7;
}

.modal__item {
  top: 50px;
  box-shadow: rgba(0, 0, 0, 0.7) 0 0 1000px 1000px;
  background: #131722;
  padding: 40px;
  position: absolute;
  z-index: 1;
  max-width: 500px;
  min-width: 400px;
  box-sizing: border-box;
  display: none;
  margin-bottom: 50px;
}

.modal__item.active {
  display: block;
}

.modal__desc-back {
  display: flex;
  justify-content: flex-end;
  margin-bottom: 0px;
}

.modal__desc-back .icon {
  font-size: 2rem;
  opacity: .5;
  text-align: right;
  display: block;
  transform: rotate(45deg);
  display: inline-block;
  cursor: pointer;
  text-align: right;
}

.modal__desc-back .icon:hover {
  opacity: 1;
  color: #fff;
} */

.custom-page {
  position: relative;
  padding: 100px 0;
}

.custom-page__bg {
  position: absolute;
  overflow: hidden;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}

.custom-page__bg img {
  position: absolute;
}

.custom-page .container {
  position: relative;
  z-index: 1;
}

/* .main-table__header {
  background: #191a28;
  font-size: .85rem;
  position: relative;
}

.main-table__container {
  padding: 15px 0;
}

.main-table__container .cell .prefix {
  display: none;
  color: #fff;
  font-size: .85rem;
  margin-bottom: 4px;
}

.main-table.big .main-table__header {
  font-size: 1rem;
  background: #27273c;
}

.main-table.big .main-table__header::after {
  content: '';
  display: block;
  height: 2px;
  background: #008dcc;
  background: linear-gradient(90deg, #008dcc 0%, #27248a 100%);
}

.main-table.big .row {
  padding: 15px 40px;
}

.main-table .row {
  display: flex;
  position: relative;
  padding: 10px 40px;
  align-items: center;
  justify-content: space-between;
}

.main-table .row.empty {
  text-align: center;
  justify-content: center;
  opacity: .5;
  padding: 150px 0;
}

.main-table a.row:hover {
  background: #191a28;
  background: linear-gradient(90.15deg, rgba(143, 133, 202, 0.2) 45.71%, rgba(143, 133, 202, 0) 104.38%);
  color: #fff;
}

.main-table .cell.blue {
  color: #1ab4ed;
}

.main-table .cell.light-blue {
  color: #D1ECFF;
  opacity: 1;
} */

/* .security-modal {
  padding-top: 15px;
}

.confirm-modal .title {
  margin-bottom: 30px;
}

.confirm-modal .text {
  opacity: 0.8;
  margin-bottom: 30px;
  text-align: center;
}

.confirm-modal__submit {
  text-align: center;
}

.white-modal {
  background: #f4f4f4;
  color: #000 !important;
}

.white-modal .modal__desc-back .icon:hover {
  color: #000 !important;
}

.white-modal__header {
  margin-bottom: 40px;
}

.white-modal__header .logo {
  max-width: 200px;
  margin-bottom: 10px;
}

.white-modal__header .subtitle {
  font-size: 0.85rem;
  margin-bottom: 20px;
} */

/* .home-first {
  position: relative;
}

.home-first .container {
  position: relative;
  z-index: 1;
}

.home-first__title {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 150px 0;
}

.home-first__title h1 {
  background: linear-gradient(90deg, #583f2b 0%, #e4b273 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #583f2b;
  font-weight: 400;
  font-size: 36px;
  text-transform: uppercase;
  text-align: center;
  margin-bottom: 15px;
  line-height: 1.2;
  font-family: "ish-exo", sans-serif;
}

.home-first__title .subtitle {
  text-align: center;
  font-weight: 400;
  font-family: "ish-open", sans-serif;
  font-size: 0.95rem;
}

.home-first__title .under-button {
  margin-top: 65px;
}

.home-first__bg {
  position: absolute;
  overflow: hidden;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}

.home-first__bg img {
  position: absolute;
}

.home-first__bg .sb {
  top: 65%;
  left: 20%;
}

.home-first__bg .bo {
  top: 0%;
  right: 20%;
}

.home-first__bg .so {
  bottom: 7%;
  right: 12%;
} */

/* .home-graph {
  font-size: 0.8rem;
  text-transform: uppercase;
}

.home-graph__header {
  background: rgba(228, 178, 115, 0.7);
  background: linear-gradient(90deg, rgba(228, 178, 115, 0.7) 0%, rgba(88, 63, 43, 0.7) 100%);
  height: 60px;
  display: grid;
  grid-template-columns: 170px 1fr 1fr 1fr 1fr 110px;
  grid-gap: 0 20px;
  padding: 0 15px;
  align-items: center;
  text-align: center;
  font-family: "ish-exo", sans-serif;
  font-size: 0.85rem;
}

.home-graph__table {
  background: rgba(30, 30, 40, 0.7);
  padding: 30px 0;
  box-shadow: rgba(30, 30, 40, 0.7) 0 0 100px;
}

.home-graph__item {
  display: grid;
  grid-template-columns: 170px 1fr 1fr 1fr 1fr 110px;
  align-items: center;
  grid-gap: 0 20px;
  padding: 0 15px;
  margin-bottom: 25px;
  font-size: 0.85rem;
}

.home-graph__item:last-child {
  margin-bottom: 0;
}

.home-graph__item .cell {
  line-height: 1;
  position: relative;
  text-align: center;
}

.home-graph__item .cell .prefix {
  font-size: 0.6rem;
  margin-bottom: 4px;
}

.home-graph__item .cell .graph {
  width: 100%;
}

.home-graph__item .name {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.home-graph__item .name .name {
  display: flex;
  align-items: center;
}

.home-graph__item .name .icon {
  margin-right: 12px;
  font-size: 25px;
}

.home-graph__item .name .icon::before {
  background: linear-gradient(90deg, #583f2b 0%, #e4b273 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #583f2b;
}

.home-graph__item .name .subname {
  font-weight: 700;
  color: #1ab4ed;
}

.home-features {
  position: relative;
  padding: 140px 0;
}

.home-features__bg {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  overflow: hidden;
}

.home-features__bg img {
  position: absolute;
}

.home-features__bg .so {
  top: 5%;
  left: 5%;
}

.home-features__bg .bo {
  right: 8%;
  bottom: 35%;
}

.home-features__bg .sb {
  left: 25%;
  bottom: 30%;
}

.home-features__container {
  position: relative;
  z-index: 1;
}

.home-features__items {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 100px 150px;
  margin-bottom: 120px;
}

.home-features__item h3 {
  font-size: 1rem;
  font-weight: 700;
  margin-bottom: 25px;
}

.home-features__item p {
  font-size: 1rem;
}

.home-features__buttons {
  display: flex;
  justify-content: center;
}

.home-features__buttons a {
  margin: 0 15px;
}

.home-features__buttons a.login {
  background: #555;
  transition: none;
}

.home-features__buttons a.login:hover {
  background: #1ab4ed;
  background: linear-gradient(90deg, #1ab4ed 0%, #0956c6 100%);
} */

/* .flash-page__bg .big-cube {
  top: 0;
  left: -6%;
}

.flash-page__bg .small-cube {
  top: 50%;
  left: 20%;
}

.flash-page__bg .big-sexangle {
  right: 10%;
  top: 5%;
} */

/* .support-page .main-form {
  max-width: 690px;
}

.support-page .main-form .first-separator {
  grid-gap: 30px;
}

.support-page .main-form .file-field .separator {
  max-width: 300px;
}

.support-page .main-form__submit {
  text-align: left;
} */

/* .support-request__header {
  display: grid;
  grid-template-columns: 60px 1fr 60px;
  margin-bottom: 40px;
}

.support-request__header .back {
  opacity: 0.5;
}

.support-request__header .back .icon {
  font-size: 26px;
  line-height: 20px;
}

.support-request__header .back:hover {
  opacity: 1;
  color: #fff;
}

.support-request__header .title {
  text-align: center;
  padding-bottom: 25px;
  border-bottom: 1px solid #fff;
} */

/* .deals-history .double-aut-page__header .back .icon {
  display: none;
}

.deals-history__header {
  margin-bottom: 40px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.deals-history__header .tabs {
  display: flex;
  width: 500px;
}

.deals-history__header .tabs .tab {
  display: block;
  flex-grow: 1;
  text-align: center;
  padding-bottom: 15px;
  border-bottom: 1px solid transparent;
}

.deals-history__header .tabs .tab:hover, .deals-history__header .tabs .tab.active {
  color: #E4B273;
  -o-border-image: linear-gradient(90deg, #e4b273 0%, rgba(228, 178, 115, 0) 100%);
  border-image: linear-gradient(90deg, #e4b273 0%, rgba(228, 178, 115, 0) 100%);
  border-image-slice: 1;
}

.deals-history__bottom {
  display: none;
  margin-top: 40px;
} */

/* .message-list__button {
  margin-bottom: 50px;
  text-align: center;
}

.message-list__button .radius-button {
  text-transform: none;
  font-size: 1rem;
  padding: 16px 24px;
} */

.message-page__bg .bo2 {
  top: -5%;
  right: 20%;
}

.message-page__bg .bo {
  top: 25%;
  left: -7%;
}

.message-page__bg .mo {
  top: 55%;
  left: 12%;
}

.message-page__bg .so {
  top: 25%;
  right: 5%;
}

.personal-page__bg .bo {
  top: -10%;
  right: 5%;
}

.personal-page__bg .so {
  left: 2%;
  top: 40%;
}

.personal-page__bg .so2 {
  left: 9%;
  top: 60%;
  width: 70px;
  opacity: 0.3;
}

/* .personal-menu__row {
  display: grid;
  grid-auto-rows: 175px;
  grid-gap: 35px;
  margin-bottom: 35px;
}

.personal-menu__row:first-child {
  grid-template-columns: 1fr 1fr 1fr 360px;
}

.personal-menu__row:last-child {
  grid-template-columns: 360px 1fr 1fr 1fr;
  margin-bottom: 0;
}

.personal-menu__item {
  position: relative;
  font-size: 1.3rem;
  font-family: "ish-exo", sans-serif;
}

.personal-menu__item .bg {
  position: absolute;
  bottom: 0;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  background: #3c1350;
  background: linear-gradient(90deg, #3c1350 0%, #db4935 100%);
  transition: 0.2s ease;
  opacity: 0;
}

.personal-menu__item .edge {
  position: absolute;
  bottom: 0;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  background: #3c1350;
  background: linear-gradient(90deg, #3c1350 0%, #db4935 100%);
  opacity: 0.5;
  transition: 0.3s ease;
}

.personal-menu__item .edge::after {
  display: block;
  content: "";
  bottom: 0;
  right: 0;
  position: absolute;
  border: 4px solid transparent;
  border-right: 4px solid #0d1019;
  border-bottom: 4px solid #0d1019;
  transform-origin: right bottom;
  transform: scale(0);
  transition: 0.3s ease;
}

.personal-menu__item .edge::before {
  display: block;
  content: "";
  top: 0;
  left: 0;
  position: absolute;
  border: 4px solid transparent;
  border-top: 4px solid #0d1019;
  border-left: 4px solid #0d1019;
  transform-origin: left top;
  transform: scale(0);
  transition: 0.3s ease;
}

.personal-menu__item .content {
  background: #27248a;
  background: linear-gradient(90deg, #27248a 0%, #008dcc 100%);
  position: absolute;
  width: 100%;
  height: 100%;
  transition: 0.3s ease;
  left: 0;
  bottom: 0;
}

.personal-menu__item .container {
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  box-sizing: border-box;
}

.personal-menu__item .icon {
  font-size: 35px;
  display: block;
  align-self: flex-end;
}

.personal-menu__item .icon::before {
  background: linear-gradient(90deg, #8e6e54 0%, #ffd59f 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #8e6e54;
}

.personal-menu__item.wide .icon {
  font-size: 45px;
}

.personal-menu__item:hover, .personal-menu__item.active {
  color: #fff;
}

.personal-menu__item:hover .edge, .personal-menu__item.active .edge {
  top: -8px;
  right: -8px;
}

.personal-menu__item:hover .edge::after, .personal-menu__item:hover .edge::before, .personal-menu__item.active .edge::after, .personal-menu__item.active .edge::before {
  transform: scale(1);
}

.personal-menu__item:hover .content, .personal-menu__item.active .content {
  bottom: 8px;
  left: 8px;
}

.personal-menu__item:hover .bg, .personal-menu__item.active .bg {
  opacity: 1;
} */

/* .input-page .conversion-page__container.separated .separator {
  grid-template-columns: 1fr 1px 1fr;
  grid-gap: 20px;
}

.input-page .conversion-page__container.separated .separator .left,
.input-page .conversion-page__container.separated .separator .right {
  padding-top: 50px;
  display: grid;
  justify-content: center;
}

.input-page .conversion-page__window {
  padding-bottom: 50px;
}

.input-page .continue-button {
  display: none;
}

.input-page .main-form {
  margin-bottom: 0;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  width: 440px;
  display: none;
}

.input-page .main-form.active {
  display: flex;
}

.input-page .main-form.no-wide {
  width: 300px;
}

.input-page .main-form__submit {
  margin-top: 20px;
}

.input-page .main-form .qr {
  margin-top: 20px;
  max-width: 140px;
}

.input-page .main-form .refill-separator {
  display: grid;
  grid-template-columns: 68% 1fr;
  grid-gap: 10px;
  align-items: end;
}

.input-page .main-form .refill-separator .addition-button {
  border-width: 2px;
  border-radius: 5px;
}

.input-page .main-form .refill-info {
  text-align: right;
}

.input-page .main-form .refill-info .item {
  margin-bottom: 15px;
}

.input-page .main-form .refill-info .prefix {
  display: inline;
  font-size: 0.85rem;
  margin-right: 20px;
}

.input-page .main-form .refill-info .value {
  opacity: 0.6;
}

.input-page__input-method {
  margin-bottom: 50px;
  display: grid;
  grid-gap: 30px;
  grid-template-columns: 150px 150px;
  grid-auto-rows: 150px;
}

.input-page__input-method .item {
  background: #405468;
  transition: 0.2s ease;
  display: block;
  cursor: pointer;
  padding: 25px;
}

.input-page__input-method .item:hover, .input-page__input-method .item.active {
  background: #e6e6e6;
}

.input-page__input-method .item .img {
  width: 100%;
  height: 100%;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
} */


/* .about-page__container {
  display: grid;
  grid-template-columns: 470px 1fr;
  grid-gap: 50px;
}

.about-page__title .main-title {
  text-align: left !important;
  margin-bottom: 0;
}

.about-page__title .title {
  margin-bottom: 10px;
}

.about-page__title .address {
  font-size: 1.35rem;
}

.about-page__article {
  margin-top: 35px;
  margin-bottom: 65px;
}

.about-page__credits {
  display: grid;
  grid-gap: 18px;
  grid-template-columns: repeat(4, 1fr);
}

.about-page__contact .name {
  margin-bottom: 5px;
}

.about-page__contact .link {
  color: #1ab4ed;
  font-size: 0.85rem;
} */

/* .map-page {
  padding: 130px 0;
}

.map-page__container {
  display: grid;
  justify-items: end;
}

.map-page__content {
  width: 390px;
  box-sizing: border-box;
  background: #1e253c;
  padding: 50px;
}

.map-page .main-title {
  text-align: left;
  margin-bottom: 2.2rem;
}

.map-page .about-page__credits {
  display: block;
  margin-bottom: 60px;
}

.map-page .about-page__contact {
  margin-bottom: 20px;
}

.map-page .about-page__contact:last-child {
  margin-bottom: 0;
}

.map-page .footer__socials {
  justify-content: space-between;
}

.map-page .footer__socials a {
  margin: 0;
  width: 32px;
  height: 32px;
  font-size: 18px;
} */

.main-form {
  max-width: 300px;
  position: relative;
  margin: 0 auto;
}

.main-form .select {
  display: block;
  position: relative;
}

.main-form .select select {
  -webkit-appearance: none;
  background: #fff;
}

.main-form .select .bg {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  color: #000;
  background: #fff;
  position: absolute;
  height: calc(100% - 4px);
  top: 2px;
  padding: 0 12px;
  right: 2px;
}

.main-form .checkbox-field label {
  display: grid;
  grid-template-columns: 16px 1fr;
  grid-gap: 8px;
}

.main-form .checkbox-field input {
  display: none;
}

.main-form .checkbox-field input:checked + label .icon {
  display: block;
}

.main-form .checkbox-field input:checked + label .checkbox {
  opacity: 1;
  border: 1px solid #1ab4ed;
}

.main-form .checkbox-field .checkbox {
  width: 16px;
  height: 16px;
  display: inline-block;
  box-sizing: border-box;
  border: 1px solid #fff;
  opacity: 0.5;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  position: relative;
}

.main-form .checkbox-field .checkbox .icon {
  display: none;
  position: absolute;
  font-size: 16px;
  color: #1ab4ed;
  top: -4px;
  left: -1px;
}

.main-form .checkbox-field .description {
  font-size: 0.85rem;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  opacity: 0.5;
  display: inline-block;
}

.main-form .file-field {
  font-size: 0.9rem;
}

.main-form .file-field input {
  display: none;
}

.main-form .file-field .separator {
  align-items: center;
  grid-template-columns: 60% 40%;
}

.main-form .file-field .addition-button {
  font-size: 0.85rem;
  cursor: pointer;
}

.main-form .file-field .info {
  opacity: 0.5;
  font-size: 0.85rem;
}

.main-form .currency-input {
  position: relative;
}

.main-form .currency-input input {
  padding: 7px;
  background: #e0e0e0;
  border: none;
  width: 100%;
  display: block;
  padding-right: 40px;
  box-sizing: border-box;
}

.main-form .currency-input input:focus {
  border: none;
  outline: 3px solid #1ab4ed;
  box-shadow: none;
}

.main-form .currency-input .currency {
  position: absolute;
  top: 7px;
  right: 7px;
  color: #000;
  opacity: 0.6;
}

.main-form .select-input {
  display: grid;
  grid-template-columns: 61.5% 38.5%;
}

.main-form .select-input .select-list {
  background: #252935;
  cursor: pointer;
  position: relative;
  border: none;
  outline: none;
  font-size: 0.85rem;
  box-shadow: none;
}

.main-form .select-input .select-list .icon {
  margin-right: 4px;
  font-size: 1rem;
  color: #E4B273;
}

.main-form .select-input .select-list .big {
  margin-right: 4px;
}

.main-form .select-input .select-list .img {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 8px;
}

.main-form .select-input .select-list .img img {
  max-height: 60%;
}

.main-form .select-input .select-list:focus ul.list {
  display: block;
}

.main-form .select-input .select-list .current {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  padding: 0 0px;
}

.main-form .select-input .select-list .current .big {
  font-size: 1rem;
}

.main-form .select-input .select-list .current .down {
  margin-left: 4px;
}

.main-form .select-input .select-list .current .img {
  justify-content: flex-start;
  width: auto;
  max-width: 40px;
}

.main-form .select-input .select-list .current .img img {
  max-height: 30px;
}

.main-form .select-input .select-list ul.list {
  z-index: 1;
  display: none;
  position: absolute;
  background: #252935;
  top: 100%;
  padding: 8px 0;
  width: 100%;
}

.main-form .select-input .select-list ul.list li {
  padding: 0 20px;
  line-height: 30px;
  display: flex;
}

.main-form .select-input .select-list ul.list li:hover, .main-form .select-input .select-list ul.list li.active {
  background: rgba(143, 133, 202, 0.2);
  background: linear-gradient(90.15deg, rgba(143, 133, 202, 0.2) 1.98%, rgba(143, 133, 202, 0) 104.38%);
}

.main-form .select-input .select-list ul.list li .img {
  height: 30px;
  width: 30px;
  margin-left: -10px;
}

.main-form .prefix {
  margin-bottom: 8px;
  display: block;
}

.main-form .prefix .icon {
  position: relative;
  z-index: 1;
  box-sizing: border-box;
  margin-top: 5px;
  float: right;
  font-style: normal;
  font-size: 0.55rem;
  border: 1px solid #fff;
  color: #fff;
  height: 12px;
  width: 12px;
  padding: 1px;
  border-radius: 1rem;
  display: inline-flex;
  justify-content: center;
  align-items: center;
}

.main-form .prefix .icon.black {
  border: 1px solid #000;
  color: #000;
}

.main-form .prefix .icon:hover .hint {
  display: block;
}

.main-form .prefix .icon .hint {
  display: none;
  position: absolute;
  background: #f4f4f4;
  color: #000;
  top: 100%;
  right: 0;
  width: 150px;
  font-size: 0.65rem;
  padding: 4px;
}

.main-form .prefix .light {
  opacity: 0.5;
}

.main-form .postfix {
  opacity: 0.5;
  font-size: 0.85rem;
  margin-top: 15px;
  text-align: center;
}

.main-form .input-info {
  text-transform: uppercase;
  font-size: 0.5rem;
  letter-spacing: 0.04em;
  display: block;
  margin-top: 8px;
}

.main-form .separator {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-gap: 15px;
}

.main-form__item {
  margin-bottom: 15px;
  display: block;
}

.main-form__item .addition-link {
  margin-top: 10px !important;
}

.main-form .input-style {
  width: 100%;
}

.main-form .warning {
  font-size: 0.8rem;
  text-align: center;
  padding: 8px 12px;
  opacity: 0.8;
  background: #4a184e;
  background: linear-gradient(0deg, rgba(74, 24, 78, 0.5) 0%, #db4935 100%);
}

.main-form__submit {
  text-align: center;
  margin-top: 50px;
}

.main-form .addition-button {
  font-size: 0.85rem;
  padding: 15px;
  line-height: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.main-form .addition-link {
  display: block;
  opacity: 0.5;
  text-decoration: underline;
  margin-top: 15px;
  font-size: 0.85rem;
  text-align: center;
}

.main-form .addition-link:hover {
  color: #fff;
  opacity: 1;
}

.main-form textarea {
  width: 100%;
  box-sizing: border-box;
  border: 2px solid #9b9b9b;
  margin-bottom: 25px;
}

.main-form textarea:focus {
  border: 2px solid #1ab4ed;
}

/* .duble-authentication .container {
  max-width: 768px;
}

.duble-authentication .qr {
  max-width: 150px;
}

.duble-authentication__form {
  margin-top: 20px;
}

.duble-authentication__form .input-style {
  width: 250px;
}

.duble-authentication__form .radius-button {
  margin-top: 50px;
} */

/* .settings-page__container {
  display: grid;
  grid-template-columns: 300px 1px 1fr;
}

.settings-page__container .line {
  background: #1f74a1;
  background: linear-gradient(0deg, rgba(31, 116, 161, 0.1) 0%, #1f74a1 50%, rgba(31, 116, 161, 0.1) 100%);
}

.settings-page__tabs {
  padding: 60px 0;
}

.settings-page__tab {
  padding: 8px 25px;
  cursor: pointer;
}

.settings-page__tab:hover, .settings-page__tab.active {
  background: rgba(143, 133, 202, 0.2);
  background: linear-gradient(90deg, rgba(143, 133, 202, 0.2) 0%, rgba(143, 133, 202, 0) 100%);
}

.settings-page__tab .postfix {
  font-size: 0.85rem;
  opacity: 0.8;
  margin-top: 5px;
}

.settings-page__header {
  padding-bottom: 15px;
  border-bottom: 1px solid transparent;
  -o-border-image: linear-gradient(90deg, #1dacec 0%, rgba(29, 172, 236, 0.1) 100%);
  border-image: linear-gradient(90deg, #1dacec 0%, rgba(29, 172, 236, 0.1) 100%);
  border-image-slice: 1;
}

.settings-page__settings {
  font-size: 0.85rem;
  padding: 40px 0;
}

.settings-page__content {
  padding-left: 50px;
  display: none;
}

.settings-page__content.active {
  display: block;
} */

/* .double-aut-page__container {
  max-width: 676px;
}

.double-aut-page__header {
  display: grid;
  grid-template-columns: 30px 1fr 30px;
  align-items: center;
  margin-bottom: 60px;
}

.double-aut-page__header .main-title {
  margin-bottom: 0;
}

.double-aut-page__header .back {
  opacity: 0.5;
  display: block;
}

.double-aut-page__header .back:hover {
  opacity: 1;
  color: #ffffff;
}

.double-aut-page__header .back .icon {
  font-size: 30px;
}

.double-aut-page .qr {
  max-width: 124px;
  margin-left: 30px;
} */

.chat-box {
  position: relative;
}

.chat-box__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 60px;
}

.chat-box__header .main-title {
  margin-bottom: 0;
}

.chat-box__header .back {
  font-size: 30px;
  line-height: 1.15em;
  opacity: 0.5;
}

.chat-box__header .back:hover {
  color: #fff;
  opacity: 1;
}

.chat-box__messages {
  min-height: 500px;
  margin-bottom: 40px;
}

.chat-box__separator {
  text-align: center;
  opacity: 0.5;
  margin: 25px 0;
}

.chat-box__separator + .chat-box__message {
  margin-top: 0;
}

.chat-box__separator:first-child {
  margin-top: 0;
}

.chat-box__message {
  width: 88%;
  margin-bottom: 50px;
  margin-top: -16px;
  float: left;
}

.chat-box__message.own {
  margin-top: 0;
  float: right;
}

/* .chat-box__message.own .name {
  display: none;
} */

.chat-box__message.own .message {
  color: #fff;
  background: #242279;
  background: linear-gradient(90deg, #242279 0%, #1dacec 100%);
}

.chat-box__message .name {
  font-size: 0.95rem;
  opacity: 0.5;
  white-space: nowrap;
  margin-bottom: 8px;
}

.chat-box__message .message {
  background: #fff;
  color: #000;
  padding: 24px;
  border-radius: 10px;
}

.chat-box__message .time {
  float: right;
  margin-right: -5px;
  margin-left: 15px;
  opacity: 0.5;
}

.chat-box__form {
  max-width: 100% !important;
}

.chat-box__form .separator {
  max-width: 280px;
}

.chat-box__form .row {
  display: flex;
  justify-content: space-between;
}

.chat-box__form .main-form__submit {
  margin-top: 0;
}

.chat-box__form textarea {
  width: 100%;
  box-sizing: border-box;
  border: 2px solid #9b9b9b;
  margin-bottom: 25px;
}

.chat-box__form textarea:focus {
  border: 2px solid #1ab4ed;
}





/*# sourceMappingURL=style.css.map */

</style>
