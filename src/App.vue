<template>
  <div id="app">
    <Header/>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Footer/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Header,
    Footer,
  }
}
</script>

<style>
/* @charset "UTF-8"; */
@font-face {
  font-family: 'ish-exo';
  src: url("~@/assets/fonts/Exo2-Regular.ttf");
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: 'ish-open';
  src: url("~@/assets/fonts/OpenSans-Regular.ttf");
  font-weight: 400;
  font-style: normal;
}

@font-face {
  font-family: 'ish-open';
  src: url("~@/assets/fonts/OpenSans-Italic.ttf");
  font-weight: 400;
  font-style: italic;
}

/* @font-face {
  font-family: 'ish-open';
  src: url("~@/assets/fonts/OpenSans-Bold.ttf");
  font-weight: 700;
  font-style: normal;
} */

@font-face {
  font-family: 'ruble';
  /* src: url("~@/assets/fonts/ruble.eot?88535217"); */
   src: /*url("~@/assets/fonts/ruble.eot?88535217#iefix") format("embedded-opentype"), */
    /* url("~@/assets/fonts/ruble.woff2?88535217") format("woff2"), */
    url("~@/assets/fonts/ruble.woff") format("woff"),
    /* url("~@/assets/fonts/ruble.ttf?88535217") format("truetype"), */
    url("~@/assets/fonts/ruble.woff?88535217#ruble") format("svg");
  font-weight: normal;
  font-style: normal;
}

/* '' */
* {
  margin: 0;
  padding: 0;
}

body {
  font-family: 'ish-open', sans-serif;
  font-size: 16px;
  background-color: #0d1019;
  color: #fff;
  letter-spacing: 0.02em;
  margin: 0;
}

[class^="icon-"]:before, [class*=" icon-"]:before {
  font-family: "ruble";
  font-style: normal;
  font-weight: normal;
  speak: never;
  display: inline-block;
  text-decoration: inherit;
  text-align: center;
  font-variant: normal;
  text-transform: none;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1 {
  font-size: 1.75rem;
}

h2 {
  font-size: 1.5rem;
}

ul li {
  list-style: none;
}

a {
  text-decoration: none;
}

address {
  font-style: normal;
}

img {
  max-width: 100%;
}

article, p {
  line-height: 1.8;
}

article img, p img {
  max-width: 100%;
  display: block;
  margin: 15px 0;
}

article h1, article h2, article h3, article h4, article h5, article h6, p h1, p h2, p h3, p h4, p h5, p h6 {
  font-weight: 500;
  margin-bottom: 1.2em;
  margin-top: 2em;
  line-height: 1.2;
}

article h1:first-child, article h2:first-child, article h3:first-child, article h4:first-child, article h5:first-child, article h6:first-child, p h1:first-child, p h2:first-child, p h3:first-child, p h4:first-child, p h5:first-child, p h6:first-child {
  margin-top: 0;
}

article h1 + .subtitle, article h2 + .subtitle, article h3 + .subtitle, article h4 + .subtitle, article h5 + .subtitle, article h6 + .subtitle, p h1 + .subtitle, p h2 + .subtitle, p h3 + .subtitle, p h4 + .subtitle, p h5 + .subtitle, p h6 + .subtitle {
  margin-top: -1.5rem;
  margin-bottom: 3rem;
}

article a, p a {
  text-decoration: underline;
}

article p, p p {
  margin-bottom: 1rem;
}

article p:last-child, p p:last-child {
  margin-bottom: 0;
}

article b, p b {
  font-weight: 700;
}

article ul, p ul {
  padding-left: 1rem;
}
article ul li, p ul li {
  list-style: disc;
}

article ol li, p ol li {
  list-style-position: inside;
}

article ul, article ol, p ul, p ol {
  margin-bottom: 1rem;
}

article ul li, article ol li, p ul li, p ol li {
  margin-bottom: 1rem;
}

article ul li:last-child, article ol li:last-child, p ul li:last-child, p ol li:last-child {
  margin-bottom: 0;
}

/* Chrome, Safari, Edge, Opera */
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

/* Firefox */
input[type=number] {
  -moz-appearance: textfield;
}

.container {
  max-width: 1160px;
  padding: 0 20px;
  margin: 0 auto;
}

.container.medium {
  max-width: 1000px;
}

.container.responsive {
  max-width: none;
  padding: 0 76px;
}

.light {
  opacity: .5;
}

.green {
  color: #1C8A7F;
}

.red {
  color: #E44C54;
}

.bg-green {
  background-color: #1C8A7F;
}

.bg-red {
  background-color: #E44C54;
}

.d-none {
  display: none;
}

.clear {
  display: block;
  clear: both;
}

.text-center {
  text-align: center;
}

.text-right {
  text-align: right;
}

.text-left {
  text-align: left;
}

.radius-button {
  letter-spacing: 0.04em;
  font-family: 'ish-exo', sans-serif;
  color: #fff;
  border-radius: 2em;
  text-transform: uppercase;
  background: #1ab4ed;
  background: linear-gradient(90deg, #1ab4ed 0%, #0956c6 100%);
  box-sizing: border-box;
  font-weight: 400;
  display: inline-block;
  border: none;
  cursor: pointer;
}

.radius-button:focus {
  border: none;
  outline: none;
}

.radius-button:hover {
  color: #fff;
  box-shadow: rgba(23, 189, 236, 0.5) 0 0 1.5em;
}

.radius-button.standart {
  padding: 12px 40px;
  font-size: .85rem;
}

.radius-button.standart.dotted {
  padding: 11px 31px;
}

.radius-button.standart.dotted:hover {
  padding: 12px 40px;
}

.radius-button.outlined {
  background: none;
  color: #1ab4ed;
  border: 1px solid #1ab4ed;
}

.radius-button.outlined:hover {
  color: #fff;
  box-shadow: none;
  background: #1ab4ed;
}

.radius-button.dotted {
  background: rgba(26, 180, 237, 0);
  background: linear-gradient(90deg, rgba(26, 180, 237, 0) 0%, rgba(9, 86, 198, 0) 100%);
  color: #1ab4ed;
  border: 1px dashed #1ab4ed;
  transition: none;
}

.radius-button.dotted:hover {
  color: #fff;
  border: none;
  background: #1ab4ed;
  background: linear-gradient(90deg, #1ab4ed 0%, #0956c6 100%);
}

.radius-button.rounded {
  border-radius: 5px;
}

.radius-button.break {
  text-transform: none;
  background: none;
  border: 2px solid transparent;
  -o-border-image: linear-gradient(90deg, #EF513C 0%, #701010 100%);
  border-image: linear-gradient(90deg, #EF513C 0%, #701010 100%);
  border-image-slice: 1;
  background: linear-gradient(90deg, #EF513C 0%, #701010 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #EF513C;
  transition: none;
}

.radius-button.break:hover {
  -o-border-image: linear-gradient(90deg, #f59083 0%, #b31a1a 100%);
  border-image: linear-gradient(90deg, #f59083 0%, #b31a1a 100%);
  border-image-slice: 1;
  background: linear-gradient(90deg, #f59083 0%, #b31a1a 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  color: #f59083;
  box-shadow: none;
}

body.block {
  overflow: hidden;
}

a {
  transition: 0.3s ease;
  color: #fff;
}

a:hover {
  color: #E4B273;
}

.d-none {
  display: none;
}

@media (max-width: 1199px) {
  .container {
    max-width: 984px;
  }
  .container.medium {
    max-width: 984px;
  }
  .container.responsive {
    padding: 0 20px;
  }
  .header__logo {
    margin-right: 30px;
  }
  .header__menu li {
    margin-right: 20px;
  }
  .header__menu li .icon {
    margin-right: 8px;
  }
  .header__currency {
    margin-right: 30px !important;
  }
  .home-features__items {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 50px 80px;
  }
  .personal-menu__row {
    grid-gap: 20px;
    grid-template-columns: 1fr 1fr 1fr 350px;
    margin-bottom: 20px;
    grid-auto-rows: 170px;
  }
  .personal-menu__item {
    font-size: 1.2rem;
  }
  .footer__container {
    grid-template-columns: 1fr 1fr;
  }
  .footer__item:first-child {
    grid-row: 2;
  }
  .footer__item:nth-child(2) {
    grid-column: 1/3;
  }
}

@media (max-width: 1023px) {
  .article-page h1, .article-page h2, .article-page h3, .article-page h4, .article-page h5, .article-page h6 {
    text-align: center;
  }
  .article-page h1 + .subtitle, .article-page h2 + .subtitle, .article-page h3 + .subtitle, .article-page h4 + .subtitle, .article-page h5 + .subtitle, .article-page h6 + .subtitle {
    text-align: center;
  }
  .container {
    max-width: 728px;
  }
  .container.medium {
    max-width: 728px;
  }
  .mobile-d-none {
    display: none;
  }
  .mobile-d-flex {
    display: flex;
  }
  .mobile-d-block {
    display: block;
  }
  .header {
    background: #0d1019;
  }
  .header__logo {
    margin-right: 0;
  }
  .header__end {
    width: 30px;
  }
  .footer__link, .footer__copyright {
    margin-bottom: 10px;
  }
  .main-table {
    font-size: .85rem !important;
  }
  .main-table__header {
    font-size: 0.85rem !important;
  }
  .main-table._mobilized .row {
    display: block;
    width: 90%;
    border-bottom: 1px solid transparent;
    -o-border-image: linear-gradient(90deg, #1ab4ed 0%, rgba(26, 180, 237, 0.2) 100%);
    border-image: linear-gradient(90deg, #1ab4ed 0%, rgba(26, 180, 237, 0.2) 100%);
    border-image-slice: 1;
  }
  .main-table._mobilized .cell {
    width: auto !important;
    text-align: left;
    padding: 5px 0;
  }
  .main-table._mobilized .cell .prefix {
    display: block;
    opacity: 1;
  }
  .main-table._mobilized .cell * {
    opacity: 0.5;
  }
  .home-first__title {
    padding: 70px 0;
  }
  .home-graph__table {
    padding: 15px 0;
  }
  .home-graph__item {
    grid-template-columns: 1fr 1fr;
    border-bottom: 1px solid #282836;
    padding: 15px;
  }
  .home-graph__item .cell {
    margin-bottom: 15px;
    text-align: left;
  }
  .home-graph__item .cell:first-child {
    grid-column: 1/3;
    padding-bottom: 10px;
  }
  .home-graph__item .cell:last-child {
    margin-bottom: 0;
    grid-column: span 2;
    padding-top: 10px;
  }
  .home-graph__item .name {
    justify-content: flex-start;
  }
  .home-graph__item .name .name {
    margin-right: 8px;
  }
  .home-graph__item:last-child {
    border-bottom: none;
  }
  .home-features {
    padding: 70px 0;
  }
  .home-features__items {
    grid-template-columns: 1fr;
    grid-gap: 40px;
    margin-bottom: 80px;
  }
  .message-list__button .radius-button {
    font-size: 0.85rem;
  }
  .message-list .main-table__container .row .cell:first-child {
    text-align: left;
  }
  .message-list .main-table .row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
  }
  .message-list .main-table .row .cell {
    width: auto !important;
  }
  .message-list .main-table .row.empty {
    display: block;
  }
  .flash-page__bg .big-cube {
    top: -100px;
    left: -100px;
  }
  .flash-page__bg .small-cube {
    left: 180px;
    top: 85%;
  }
  .flash-page__bg .big-sexangle {
    right: -20%;
    top: 30%;
  }
  .support-request__header {
    grid-template-columns: 40px 1fr 30px;
    margin-bottom: 25px;
  }
  .deals-history .double-aut-page__header .back.active .icon {
    display: block;
  }
  .deals-history__header {
    margin-bottom: 20px;
    flex-direction: column-reverse;
    display: none;
  }
  .deals-history__header.active {
    display: flex;
  }
  .deals-history__header .tabs {
    font-size: 0.85rem;
    width: 100%;
  }
  .deals-history__header .tabs .tab {
    text-align: left;
  }
  .deals-history__header .tabs .tab:last-child {
    text-align: right;
  }
  .deals-history__header .break {
    margin-bottom: 30px;
  }
  .deals-history .main-table {
    display: none;
  }
  .deals-history .main-table.active {
    display: block;
  }
  .deals-history .main-table__header {
    background: rgba(143, 133, 202, 0.25);
  }
  .deals-history .main-table__container {
    background: rgba(30, 37, 60, 0.5);
  }
  .deals-history .main-table .row {
    padding: 10px 15px;
    display: grid;
    grid-gap: 10px;
    grid-template-columns: repeat(4, 1fr);
  }
  .deals-history .main-table .row.empty {
    padding: 130px 0;
    display: block;
  }
  .deals-history .main-table .cell {
    text-align: left;
    width: auto !important;
  }
  .deals-history .main-table .cell:last-child {
    text-align: right;
  }
  .deals-history__bottom {
    display: none;
  }
  .deals-history__bottom.active {
    display: block;
  }
  .custom-page {
    padding: 70px 0;
  }
  .custom-page__bg {
    opacity: 0.3;
  }
  .double-aut-page .duble-authentication__form {
    display: grid;
    justify-items: center;
  }
  .double-aut-page .duble-authentication__form input {
    width: 100%;
  }
  .double-aut-page .duble-authentication__form .radius-button {
    margin-top: 20px;
  }
  .double-aut-page .qr {
    margin-left: 0;
  }
  .about-page__container {
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 50px;
  }
  .about-page__item:first-child {
    grid-row: 2;
  }
  .about-page__credits {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }
  .input-page__input-method {
    margin-bottom: 50px;
    display: grid;
    grid-gap: 30px;
    grid-template-columns: 115px 115px;
    grid-auto-rows: 115px;
  }
  .input-page .continue-button {
    display: block;
  }
  .input-page .main-form {
    width: 100% !important;
    min-width: 100% !important;
  }
  .input-page .separator {
    grid-template-columns: 1fr !important;
  }
  .input-page .separator .right {
    justify-content: stretch !important;
  }
  .input-page .somehow-edited .refill-separator {
    grid-template-columns: 1fr;
    grid-gap: 25px;
  }
  .input-page .somehow-edited .refill-separator .part:last-child {
    justify-self: center;
  }
  .input-page .somehow-edited .main-form__item:nth-child(2) {
    display: flex;
    justify-content: center;
  }
  .input-page .left, .input-page .right {
    display: none !important;
  }
  .input-page .left.active, .input-page .right.active {
    display: grid !important;
  }
  .map-page {
    padding-top: 450px;
  }
  .map-page__content {
    width: 100%;
  }
  .personal-menu__row {
    grid-auto-rows: 160px;
    grid-template-columns: 1fr 1fr 1fr 1fr !important;
  }
  .personal-menu__item {
    font-size: 1rem;
  }
  .personal-menu__item .icon {
    font-size: 30px !important;
  }
  .modal {
    background: #131722;
  }
  .modal__header {
    display: block;
    display: grid;
    grid-template-columns: 50px 1fr;
    grid-gap: 15px;
    height: 50px;
    align-items: center;
    padding-right: 20px;
    position: relative;
  }
  .modal__header .back {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50px;
    height: 100%;
  }
  .modal__container {
    top: 50px;
  }
  .modal__desc-back {
    display: none;
  }
  .modal__item {
    padding: 20px !important;
    margin: 0 !important;
    top: 0;
    box-shadow: none;
    background: none !important;
    min-width: 0;
  }
  .modal .main-title + .subtitle {
    margin-top: 10px;
  }
  .security-modal .title {
    display: none;
  }
  .security-modal .subtitle {
    margin-top: 0;
  }
  .confirm-modal .title {
    font-size: 1.3rem;
  }
  .white-modal {
    color: #fff !important;
    width: 100%;
  }
  .main-form .email-checker .separator {
    display: block;
  }
  .main-form .email-checker .addition-button {
    margin-top: 10px;
  }
}

@media (max-width: 767px) {
  .personal-menu__row {
    grid-gap: 15px;
    grid-template-columns: 1fr 1fr !important;
    margin-bottom: 115px;
  }
  .personal-menu__row:last-child {
    margin-bottom: 0;
  }
  .personal-menu__row:last-child .personal-menu__item.wide {
    margin-top: -100px;
  }
  .personal-menu__item.wide {
    height: 260px;
  }
}

@media (max-width: 599px) {
  .home-first__bg .bb {
    left: -80px;
    top: -80px;
  }
  .home-first__bg .bo {
    right: -10%;
  }
  .home-first__bg .sb {
    left: 50px;
  }
  .home-first__bg .so {
    bottom: -2%;
    right: 10px;
  }
  .home-features__bg .bo {
    right: -60px;
  }
  .home-features__bg .sb {
    left: 20px;
    bottom: 50%;
  }
  .custom-page {
    padding-top: 40px;
    padding-bottom: 70px;
  }
  .support-page .main-form {
    max-width: 300px;
  }
  .support-page .main-form .first-separator {
    display: block;
  }
  .support-page .main-form__submit {
    text-align: center;
  }
  .chat-box__message {
    margin-bottom: 30px;
  }
  .chat-box__message .name {
    font-size: 0.85rem;
  }
  .chat-box__messages {
    margin-bottom: 10px;
    font-size: 0.85rem;
  }
  .chat-box__form .row {
    flex-direction: column;
    align-items: center;
  }
  .chat-box__form textarea {
    height: 100px;
  }
  .chat-box__form .main-form__submit {
    margin-top: 40px;
  }
  .chat-box__form .file-field {
    font-size: 0.9rem;
    align-self: flex-start;
  }
  .main-form .select-input {
    grid-template-columns: 50% 50%;
  }
  .main-form .select-input .select-list {
    font-size: .75rem;
  }
  .main-form .select-input .select-list .current .big {
    font-size: .85rem;
  }
  .main-form .select-input .select-list ul.list li {
    padding: 0 10px;
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
    margin-left: 0px;
  }
  .footer {
    padding: 30px 0;
  }
  .footer ._mobile {
    display: block;
  }
  .footer__menu {
    display: none;
    margin-bottom: 0px;
  }
  .footer__menu a {
    margin: 0;
    display: block;
    margin-bottom: 12px;
  }
  .footer__socials {
    justify-content: space-between;
  }
  .footer__socials a {
    margin: 0;
  }
  .footer__item:first-child {
    grid-row: 1;
    grid-column: 1/3;
    justify-self: center;
  }
  .footer__item:nth-child(2) {
    grid-row: 3;
    justify-self: stretch;
  }
  .footer__item:nth-child(3) {
    grid-row: 2;
  }
  .footer__item:nth-child(4) {
    align-items: flex-start;
    text-align: left;
  }
  .footer__item:last-child {
    grid-row: 4;
    text-align: center;
    grid-column: 1/3;
    justify-self: stretch;
  }
  .footer .support-button {
    margin-bottom: 15px;
  }
  .footer__copyright {
    display: none;
    margin-bottom: 0;
  }
  .footer__container {
    align-items: stretch;
    grid-gap: 40px 20px;
  }
  .footer__link {
    margin-bottom: 12px;
  }
  .footer__logo {
    margin-bottom: 0px;
  }
}

</style>
