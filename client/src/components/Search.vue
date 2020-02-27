<template>
  <section class="search">
    <h1>Track Player Stats</h1>
    <form v-on:submit.prevent="onSubmit">
      <div class="form-group">
        <label for="platform">Platform</label>
        <select type="text" name="platform" id="platform" v-model="platform">
          <option value="steam">Steam</option>
        </select>
      </div>
      <div class="form-group">
        <label for="gamertag">Gamertag</label>
        <input type="text" name="text" v-model="gamertag" id="gamertag" placeholder="Steam ID (64)" />
        <small>
          <a href="https://steamid.io/" target="_blank">How do I find my Steam ID (64)?</a>
        </small>
      </div>
      <div class="form-group">
        <input type="submit" value="Submit" class="btn" />
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      platform: "steam",
      gamertag: ""
    };
  },
  beforeCreate() {
    document.body.className = "body-bg-image";
  },
  methods: {
    onSubmit() {
      if (!this.gamertag) {
        this.$toasted.show("Please enter your SteamID(64)", {
          duration: 4000,
          icon: "exclamation-circle"
        });
      } else {
        this.$router.push(`/profile/${this.platform}/${this.gamertag}`);
      }
    }
  }
};
</script>

<style scoped>
</style>