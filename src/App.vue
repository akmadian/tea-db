<template>
  <div id="app">
    <Header/>
    <div class="columns">
      <div class="column is-narrow">
        <SideMenu/>
      </div>
      <div class="column">
        <MainView :isTeaComponentActive="teaComponentActive"/>
      </div>
    </div>
    <Footer
        @about="aboutModalActive = true"
        @legal="legalModalActive = true"/>

    <b-modal :active.sync="aboutModalActive" :width="640" scroll="keep">
      <div class="card">
        <div class="card-content">
          <div class="content">
            <h3 class="subtitle is-3">Tea-DB</h3>
            <p>Tea-DB is a free and open source tea stash tracker</p>
            <a href="#">Contribute or check out the source code on GitHub</a>
            <a href="#"></a>
            <br><br>
            <b>Some Legal Stuff</b>
            <p>
              Some technologies used in this site are licensed under various copyright licenses. 
              Check out the "Legal" link on the bottom right of this page for more information.
            </p>
            <p>
              Privacy Policy and Terms of Service can also be found in the "Legal" link on the
              bottom right of this page.
            </p>
            <br>
            <hr>
            <small>Designed and Built by <a href="#">Ari Madian</a></small>
          </div>
        </div>
      </div>
    </b-modal>
    <b-modal :active.sync="legalModalActive" :width="640" scroll="keep">
      <div class="card">
        <div class="card-content">
          <div class="content">
            <h3 class="subtitle is-3">Legal Stuff</h3>
            <b>Privacy</b>
            <p>
                Long story short, neither I (Ari Madian), or TeaDB will ever share
                any of your information with anyone.
                <br><br>
                There is one exception to this, which is MongoDB. TeaDB uses MongoDB for 
                storing user data such as each user's stash, along with passwords, emails, 
                and usernames. As far as I know, MongoDB does not share the contents of 
                their user's databases with anyone else.
            </p>
            <b>What information does TeaDB collect about me?</b>
            <p>
                TeaDB, at minimum, collects a password, a username, and your stash.
                Providing an email at signup is optional, but reccommended.
                <br><br>
                You can download your the data that TeaDB stores about you in the 
                "My Account" tab.
            </p>
            <b>Encryption</b>
            <p>
                <ul>
                    <li>Passwords: Hashed and salted, never stored or transmitted in plaintext.</li>
                    <li>Emails: Not Encrypted</li>
                    <li>Usernames: Not Encrypted</li>
                    <li>Stash: Not Encrypted</li>
                </ul>
            </p>
            <b>Terms of Service</b>
            <p>
                I (Ari Madian), as developer and operator of TeaDB, reserve the right to
                deny use of TeaDB to anyone, at any time, for any reason. I also reserve
                the right to terminate the account of any TeaDB user, at any time, for 
                any reason.
                <br><br>
                If your account is terminated, you will receive an email including a notice 
                of the termination, and a link to download your user data so your stash 
                won't be lost. In the case that you did not provide an email at signup,
                you will not recieve this notification email.
            </p>
          </div>
        </div>
      </div>
    </b-modal>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import SideMenu from './components/SideMenu.vue'
import Footer from './components/Footer.vue'
import MainView from './components/MainView.vue'

export default {
  name: 'app',
  components: {
    Header,
    SideMenu,
    Footer,
    MainView
  },
  data: function() {
    return {
      legalModalActive: false,
      aboutModalActive: false,
      teaComponentActive: false
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
