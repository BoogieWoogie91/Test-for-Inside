<template>
<!-- footer -->
		<footer class="footer">
				<!-- footer__container -->
				<div class="container responsive footer__container">
						<div class="footer__item">
								<div class="footer__copyright">Copyright    &#169; 2020 MyStartup</div>
								<div class="footer__copyright">Все права защищены.</div>
						</div>
						<div class="footer__item">
								<ul class="footer__menu">
										<li><a href="#">Главная</a></li>
										<li><a href="#">Наша миссия</a></li>
										<li><a href="#">Наша команда</a></li>
										<li><a href="#">Контакты</a></li>
								</ul>
								<div class="footer__socials">
										<a href="#"><i class="icon icon-vk"></i></a>
										<a href="#"><i class="icon icon-instagram"></i></a>
										<a href="#"><i class="icon icon-facebook"></i></a>
										<a href="#"><i class="icon icon-twitter"></i></a>
										<a href="#"><i class="icon icon-telegram"></i></a>
								</div>
						</div>
						<ul class="footer__item _mobile footer__menu">
										<li><a href="#">Главная</a></li>
										<li><a href="#">Наша миссия</a></li>
										<li><a href="#">Наша команда</a></li>
										<li><a href="#">Контакты</a></li>
						</ul>
						<div class="footer__item">
								<a href="#" class="radius-button support-button dotted">Поддержка</a>
								<a href="#" class="footer__link">Пользовательское соглашение</a>
								<a href="#" class="footer__link">Политика конфиденциальности</a>
						</div>
						<div class="footer__item _mobile">
								<div class="footer__copyright _mobile">Copyright    &#169; 2020 Bitswap.</div>
								<div class="footer__copyright _mobile">Все права защищены.</div>
						</div>
				</div>
				<!-- /footer__container -->
		</footer>
		<!-- /footer -->
</template>

<script>
export default {
  name: 'Footer',
  props: {
  },
}
</script>

<style scoped>
/* '' */
.icon-telegram:before {
  content: '\e80f';
}

/* '' */
.icon-instagram:before {
  content: '\e810';
}

/* '' */
.icon-facebook:before {
  content: '\e811';
}

/* '' */
.icon-twitter:before {
  content: '\e812';
}

/* '' */
.icon-vk:before {
  content: '\e813';
}

.map-page .footer__socials {
  justify-content: space-between;
}

.map-page .footer__socials a {
  margin: 0;
  width: 32px;
  height: 32px;
  font-size: 18px;
}


.footer {
  padding: 76px 0;
  background: #131722;
}

.footer ._mobile {
  display: none;
}

.footer__container {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-gap: 40px 0;
  align-items: center;
}

.footer__logo {
  margin-bottom: 60px;
  height: 40px;
}

.footer__copyright {
  opacity: 0.5;
  margin-bottom: 30px;
  font-size: 0.85rem;
}

.footer__copyright:last-child {
  margin-bottom: 0;
}

.footer__menu {
  display: flex;
  font-weight: 400;
  margin-bottom: 80px;
}

.footer__menu a {
  margin: 0 15px;
}

.footer__socials {
  display: flex;
  justify-content: center;
}

.footer__socials a {
  margin: 0 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 40px;
  height: 40px;
  border: 1px solid transparent;
  transition: none;
  font-size: 24px;
  -o-border-image: linear-gradient(90deg, #583f2b 0%, #e4b273 100%);
  border-image: linear-gradient(90deg, #583f2b 0%, #e4b273 100%);
  border-image-slice: 1;
}

.footer__socials a .icon::before {
  background: linear-gradient(90deg, #583f2b 0%, #e4b273 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #583f2b;
}

.footer__socials a:hover {
  -o-border-image: linear-gradient(90deg, #8b6444 0%, #f0d5b3 100%);
  border-image: linear-gradient(90deg, #8b6444 0%, #f0d5b3 100%);
  border-image-slice: 1;
}

.footer__socials a:hover .icon::before {
  background: linear-gradient(90deg, #8b6444 0%, #f0d5b3 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #8b6444;
}

.footer__link {
  display: block;
  margin-bottom: 30px;
  text-decoration: underline;
  font-size: 0.85rem;
}

.footer__link:last-child {
  margin-bottom: 0;
}

.footer__item:nth-child(2) {
  justify-self: center;
}

.footer__item:nth-child(4) {
  justify-self: end;
  display: flex;
  align-items: flex-end;
  text-align: right;
  flex-direction: column;
}

.footer .support-button {
  margin-bottom: 60px;
  font-size: 0.85rem;
  padding: 7px 31px;
  display: block;
}

.footer .support-button:hover {
  padding: 8px 32px;
}




</style>