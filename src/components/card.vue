<template>
  <div class="main-card">
    <div class="header-card">
      <div class="rounded-image-div">
        <img src="../assets/vue.png" alt="image user" class="rounded-image" />
      </div>
      <div class="name">
        <p>vittormeneghini</p>
      </div>
      <div class="setting">
        <i class="fa fa-ellipsis-v" />
      </div>
    </div>
    <div class="content-card">
      <img src="../assets/vue.png" class="image-content" alt="image user" />
    </div>
    <div class="footer-card">
      <i class="fa fa-heart" @click="like" :class="isliked ? 'liked' : 'unliked'" />
      <i class="fa fa-comment" @click="setFocus" />
    </div>
    <div class="who-liked">
      <p>
        Curtido por
        <b v-show="youLike">você +</b>
        {{likes}} pessoas
      </p>
    </div>
    <div class="comment" v-for="comment in comments" :key="comment">
      <p>
        <b>{{comment.user}}</b>
      </p>
      <p>{{comment.comment}}</p>
    </div>
    <div class="div-input-comment">
      <img src="../assets/vue.png" alt="image user" class="rounded-image" />
      <input type="text" v-model="comment" ref="comment" placeholder="Adicione um comentário..." />
      <i class="fa fa-paper-plane" @click="sendComment" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      isliked: false,
      comment: "",
      comments: [],
      activatedComment: false,
      activatedShare: false,
      youLike: false,
      likes: 0
    };
  },
  methods: {
    like() {
      this.isliked = this.isliked ? false : true;
      this.youLike = this.isliked;
    },
    sendComment() {
      if (this.comment == "") {
        this.$refs.comment.focus();
        return;
      }
      this.comments.push({ user: "vittormeneghini", comment: this.comment });
      this.comment = "";
    },
    setFocus() {
      this.$refs.comment.focus();
    }
  }
};
</script>

<style>
.main-card {
  display: grid;
  grid-template-rows: 1fr 5fr 0.6fr 0.4fr 0.1fr 0.6fr;
  margin-bottom: 15%;
}

.header-card {
  display: grid;
  grid-template-columns: 1fr 2fr 1fr;
  grid-gap: 1fr;
  text-align: center;
}

.header-card div {
  align-self: center;
}

.name {
  text-align: initial;
}

.rounded-image {
  width: 50%;
  height: 50%;
  border-radius: 50%;
}
.rounded-image-div {
  margin: 10%;
  text-align: center;
}
.footer-card {
  align-self: center;
}

.footer-card i {
  margin: 0% 3% 0% 3%;
}

i:hover {
  cursor: pointer;
}

.image-content {
  width: 100%;
  height: 100%;
}

.liked {
  color: red;
}

.unliked {
  color: grey;
}

.who-liked p {
  margin-left: 3%;
}
.comment {
  display: grid;
  grid-template-columns: 1fr 5fr;
  margin-left: 3%;
  text-align: center;
}
.div-input-comment {
  display: grid;
  grid-template-columns: 1fr 5fr 1fr;
  margin-left: 3%;
  text-align: center;
}
.div-input-comment img {
  height: 20px;
  margin: 0 auto;
  align-self: center;
}
.div-input-comment input {
  width: 100%;
  border: none;
}
</style>