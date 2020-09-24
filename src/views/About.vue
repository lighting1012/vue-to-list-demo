<template>
  <div class="about">
    <h2>Nested Comment Components</h2>
    <div style="width:80%;margin:auto">
      <Comment :record="comments"/>
    </div>
  </div>
</template>
<script>
import Comment from '@/components/Comment.vue'
export default {
  data() {
    return {
      comments: [
        {
          fromUser: "Alice",
          toUser: "Bob",
          content: "Hey, how is it going?",
          time: "2020-09-24 13:45",
          cList: [
            {
              fromUser: "Bob",
              toUser: "Alice",
              content: "Hey, I am doing well.",
              time: "2020-09-24 13:49",
              cList: [
                {
                  fromUser: "Alice",
                  toUser: "Bob",
                  content: "It's good to hear that.",
                  time: "2020-09-24 13:55",
                }
              ]
            }
          ]
        },
        {
          fromUser: "Alice",
          toUser: "Bob",
          content: "Hey, how is it going?",
          time: "2020-09-24 13:45",
        },
        {
          fromUser: "Alice",
          toUser: "Bob",
          content: "Hey, how is it going?",
          time: "2020-09-24 13:45",
          cList: [
            {
              fromUser: "Bob",
              toUser: "Alice",
              content: "Hey, I am doing well.",
              time: "2020-09-24 13:49"
            }
          ]
        },
      ]
    }
  },
  components: {
    Comment
  }
}
</script>