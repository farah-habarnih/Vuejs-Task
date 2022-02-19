<template>
  <div class="fix-m-header">
    <span>Get Facebook for Android and browse faster</span>
  </div>

  <div class="container">
    <!-- main container -->
    <div class="content">
      <!-- logo container -->
      <div class="left-content">
        <div class="f-logo">
          <img
            src="https://static.xx.fbcdn.net/rsrc.php/y8/r/dF5SId3UHWd.svg"
            alt="Facebook"
          />
        </div>
        <h2 class="f-quote">
          Connect with friends and the world around you on Facebook.
        </h2>
      </div>
      <!-- login form -->
      <div class="right-content">
        <div class="card">
          <form>
            <div class="input-container">
              <input
                type="email"
                placeholder="Email or phone number"
                v-model="email"
              />
            </div>
            <div class="input-container">
              <input
                type="password"
                placeholder="Password"
                v-model="password"
              />
            </div>
            <div class="login-btn-container">
              <button
                class="login-btn"
                :disabled="!(email && password)"
                @click="login"
              >
                Log In
              </button>
            </div>
            <div class="input-container">
              {{ message }}
            </div>
          </form>

          <div class="forgotten-password">
            <a
              href="https://web.facebook.com/login/identify/?ctx=recover&ars=facebook_login&from_login_screen=0"
              >Forgot password?</a
            >
          </div>

          <div class="divider"></div>

          <div class="" style="text-align: center">
            <button
              class="crt-new-ac"
              @click="(e) => TogglePopup('buttonTrigger')"
            >
              Create new account
            </button>
            <Popup
              v-if="popupTriggers.buttonTrigger"
              :TogglePopup="() => TogglePopup('buttonTrigger')"
            ></Popup>
          </div>
        </div>
        <div class="crt-page">
          <a
            href="https://web.facebook.com/pages/create/?ref_type=registration_form"
            >Create a Page
          </a>
          <span>for a celebrity, band or business.</span>
        </div>
      </div>
    </div>
  </div>

  <footer class="f-lg-footer">
    <ul>
      <li><a href="#">English (US)</a></li>
      <li><a href="https://ar-ar.facebook.com/"> العربية</a></li>
      <li><a href="https://fr-fr.facebook.com/">Français (France)</a></li>
      <li><a href="https://ru-ru.facebook.com/">Русский </a></li>
      <li><a href="https://de-de.facebook.com/">Deutsch </a></li>
      <li><a href="https://id-id.facebook.com/">Bahasa Indonesia </a></li>
      <li><a href="https://es-la.facebook.com/">Español</a></li>
      <li><a href="https://tr-tr.facebook.com/">Türkçe</a></li>
      <li><a href="https://th-th.facebook.com/">ภาษาไทย </a></li>
      <li><a href="https://pt-br.facebook.com/">Português (Brasil) </a></li>
      <li><a href="https://it-it.facebook.com/">Italiano</a></li>
    </ul>
    <div class="divider"></div>
    <ul>
      <li><a href="#">Sign Up</a></li>
      <li><a href="#">Log In</a></li>
      <li><a href="https://www.messenger.com/">Messenger</a></li>
      <li><a href="https://web.facebook.com/lite/">Facebook Lite</a></li>
      <li><a href="https://web.facebook.com/watch/">Watch</a></li>
      <li><a href="https://web.facebook.com/places/">Places</a></li>
      <li><a href="https://web.facebook.com/games/">Games</a></li>
      <li>
        <a href="https://web.facebook.com/login/?next=%2Fmarketplace%2F"
          >Marketplace</a
        >
      </li>
      <li><a href="https://pay.facebook.com/">Facebook Pay</a></li>
      <li><a href="https://www.oculus.com/">Oculus</a></li>
      <li><a href="https://portal.facebook.com/">Portal</a></li>
      <li><a href="https://www.instagram.com/">Instagram</a></li>
      <li><a href="https://www.bulletin.com/">Bulletin</a></li>
      <li>
        <a href="https://web.facebook.com/local/lists/245019872666104/"
          >Local</a
        >
      </li>
      <li><a href="https://web.facebook.com/fundraisers/">Fundraisers</a></li>
      <li><a href="https://web.facebook.com/biz/directory/">Services</a></li>
      <li>
        <a href="https://web.facebook.com/votinginformationcenter/"
          >Voting Information Centre</a
        >
      </li>
      <li><a href="https://web.facebook.com/groups/explore/">Groups</a></li>
      <li><a href="https://about.facebook.com/">About</a></li>
      <li>
        <a
          href="https://web.facebook.com/login.php?next=https%3A%2F%2Fweb.facebook.com%2Fads%2Fcreate%2F%3Fnav_source%3Dunknown%26campaign_id%3D402047449186%26placement%3Dpflo%26extra_1%3Dnot-admgr-user"
          >Create Ad</a
        >
      </li>
      <li>
        <a href="https://web.facebook.com/pages/create/?ref_type=site_footer"
          >Create Page</a
        >
      </li>
      <li><a href="https://developers.facebook.com/?ref=pf">Developers</a></li>
      <li><a href="https://www.metacareers.com/">Careers</a></li>
      <li>
        <a href="https://web.facebook.com/privacy/explanation/">Privacy</a>
      </li>
      <li><a href="https://web.facebook.com/policies/cookies/">Cookies</a></li>
      <li>
        <a href="https://web.facebook.com/help/568137493302217">Ad Choices</a>
      </li>
      <li><a href="https://web.facebook.com/policies_center/">Terms</a></li>
      <li><a href="https://web.facebook.com/help/?ref=pf">Help</a></li>
    </ul>
  </footer>
</template>

<script>
import { ref } from "vue";
import Popup from "./components/Popup";
export default {
  setup() {
    const popupTriggers = ref({
      buttonTrigger: false,
    });
    const TogglePopup = (trigger) => {
      popupTriggers.value[trigger] = !popupTriggers.value[trigger];
    };
    return { Popup, popupTriggers, TogglePopup };
  },
  name: "App",
  data() {
    return {
      error: [],
      email: "",
      password: "",
      message: "Email and Password required",
    };
  },
  components: { Popup },
  methods: {
    login(e) {
      if (this.email && this.password) {
        this.message = "login success";
      }
      this.error = [];
      if (!this.email) {
        this.error.push("Email is required");
      }
      if (!this.password) {
        this.error.push("Password is required");
      }
      console.warn("errors", this.error);
      e.preventDefault();
    },
  },
};
</script>

<style>
#app {
}
* {
  margin: 0;
  padding: 0;
}
body {
  font-family: "Open Sans", sans-serif;
  font-size: 14px;
  background: #fff;
}

.container {
  background: #f0f2f5;
  padding-top: 72px;
  padding-bottom: 112px;
}

.content {
  width: 980px;
  margin: 20px auto;
}

.content > div {
  display: inline-block;
  vertical-align: top;
}

.left-content {
  width: 580px;
  padding-right: 32px;
  box-sizing: border-box;
}
.f-logo {
  margin: 112px 0 16px;
}
.f-logo > img {
  height: 106px;
  margin: -28px;
}

.f-quote {
  font-size: 28px;
  font-weight: 500;
  color: #333;
}

.card {
  background: #fff;
  width: 396px;
  border-radius: 10px;
  box-shadow: 0 2px 4px rgb(0 0 0 / 10%), 0 8px 16px rgb(0 0 0 / 10%);
  padding: 10px 15px;
  box-sizing: border-box;
  margin-top: 40px;
}

.input-container > input[type="email"],
.input-container > input[type="password"] {
  width: 100%;
  padding: 14px 16px;
  box-sizing: border-box;
  outline: none;
  border: 1px solid #dddfe2;
  border-radius: 6px;
  margin: 5px 0;
  font-size: 17px;
}

.input-container > input[type="text"]:focus,
.input-container > input[type="password"]:focus {
  border: 1px solid #1877f2;
  box-shadow: 0 0 0 2px #e7f3ff;
}

.login-btn {
  background: #1877f2;
  color: #fff;
  border-radius: 6px;
  width: 100%;
  font-size: 20px;
  font-weight: 600;
  border: none;
  box-sizing: border-box;
  padding: 14px 16px;
  margin: 10px 0;
  cursor: pointer;
}

.forgotten-password {
  text-align: center;
}

.forgotten-password > a {
  font-weight: 600;
  font-size: 14px;
  color: #1877f2;
  display: inline-block;
  margin: 20px 0;
  text-decoration: none;
}

.forgotten-password > a:hover {
  text-decoration: underline;
}

.divider {
  width: 100%;
  height: 1px;
  background: #d2d2d2;
}

.crt-new-ac {
  display: inline-block;
  background: #42b72a;
  border-radius: 6px;
  color: #fff;
  text-decoration: none;
  padding: 10px 16px;
  font-weight: 600;
  font-size: 17px;
  margin: 20px 0 7px;
}

.crt-page {
  color: #000;
  text-align: center;
  padding: 20px 0;
}

.crt-page > a {
  text-decoration: none;
  font-weight: 600;
  color: #000;
}

.f-lg-footer {
  width: 980px;
  margin: 30px auto;
}

.f-lg-footer > ul {
  margin-bottom: 10px;
  margin-top: 10px;
}

.f-lg-footer > ul > li {
  display: inline-block;
  margin: 0 5px;
}

.f-lg-footer > ul > li > a {
  text-decoration: none;
  color: #777;
  font-size: 12px;
}

.fix-m-header {
  background: #fffbe2;
  color: #3b5998;
  text-align: center;
  height: 50px;
  font-size: 16px;
  font-weight: 500;
  position: relative;
  display: none;
}

.fix-m-header > span,
.fix-m-header > img {
  vertical-align: top;
}

.fix-m-header > span {
  line-height: 50px;
}

.fix-m-header > img {
  position: relative;
  top: 10px;
}

.m-footer {
  display: none;
}

@media (max-width: 980px) {
  .container {
    padding-top: 0px;
    padding-bottom: 20px;
    background: #fff;
  }
  .content {
    width: 100%;
    margin: 0 auto;
  }
  .left-content {
    width: 100%;
  }
  .right-content {
    width: 100%;
  }

  .f-lg-footer {
    display: none;
  }

  .f-logo {
    margin: 0 auto;
    text-align: center;
  }
  .f-logo > img {
    height: 50px;
    margin: -50px auto;
    display: inline-block;
  }

  .f-quote {
    display: none;
  }

  .card {
    width: 100%;
    box-shadow: none;
  }

  .input-container > input[type="text"],
  .input-container > input[type="password"] {
    background: #f5f6f7;
  }

  .fix-m-header {
    display: block;
  }

  .m-footer {
    display: block;
    width: 250px;
    margin: 0 auto;
  }
  .m-footer .m-f-lang > ul:first-child {
    float: left;
  }
  .m-footer .m-f-lang > ul:last-child {
    float: right;
  }
  .m-footer .m-f-lang > ul li {
    list-style: none;
  }

  .m-footer .m-f-lang > ul > li > a {
    text-decoration: none;
    color: #777;
  }

  .m-footer .links > a {
    display: inline-block;
    margin: 0 10px;
    text-decoration: none;
    color: #777;
    font-weight: 500;
  }
}
</style>
