<template>
  <div>
    <div class="container" v-for="(item,index) in record" :key="index">
      <div class="commentHeader">
        <p><span class="bold">{{ item.fromUser }}</span> replies to <span class="bold">{{ item.toUser }}</span> : </p>
      </div>
      <div class="commentBody">
        <p>{{ item.content }}</p>
      </div>
      <div class="commentFooter">
        <span class="reply-btn" @click="handleClickReply">Reply</span>
        <span style="color:#969696">{{ item.time }}</span>
      </div>
      <nestComment v-if="item.cList" :record="item.cList" />
    </div>
  </div>
</template>
<script>
export default {
    name: 'nestComment',
    data() {
      return {}
    },
    props: ["record"],
    methods: {
      handleClickReply(e) {   // Click on reply button
        const parent = e.target.parentNode
        console.log(parent)
      }
    }
}
</script>
<style scoped>
  .container {
    background: #ffffff;
    margin: 20px auto 10px;
    padding: 10px 10px 10px 25px;
    border-radius: 10px;
  }
  .container:hover {
      box-shadow: 4px 4px 10px lightgrey;
  }
  .bold {
      font-weight: 500;
  }
  .commentBody {
      padding: 10px;
      margin: 10px 0;
      background: #f7f7f7;
  }
  .commentFooter {
      display: flex;
      justify-content: space-between;
  }
  .reply-btn {
      color: rgb(56, 159, 255);
  }
  .reply-btn:hover {
      cursor: pointer;
      color: rgb(115, 187, 255);
  }
  .reply-box {
    margin-left: 25px;
  }
  textarea {
    width: 100%;
    border: none;
    background: #f7f7f7;
  }
</style>