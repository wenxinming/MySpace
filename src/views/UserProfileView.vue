<template>
  <ContentBase>
    <div class="row">
      <div class="col-3">
        <UserProfileInfo
          v-bind:user="user"
          @follow="follow"
          @unfollow="unfollow"
        ></UserProfileInfo>
        <UserProfileWrite @post_a_post="post_a_post" />
      </div>
      <div class="col-9">
        <UserProfilePosts :posts="posts"></UserProfilePosts>
      </div>
    </div>
  </ContentBase>
</template>
  
  <script>
import ContentBase from "../components/ContentBase.vue";
import UserProfileInfo from "@/components/UserProfileInfo.vue";
import UserProfilePosts from "@/components/UserProfilePosts.vue";
import { reactive } from "vue";
import UserProfileWrite from "@/components/UserProfileWrite.vue";

export default {
  name: "UserProfileView",
  components: {
    ContentBase,
    UserProfileInfo,
    UserProfilePosts,
    UserProfileWrite,
  },
  setup() {
    const user = reactive({
      userName: "Smart 7",
      lastName: "7",
      firstName: "Smart",
      followedCont: 2,
      is_followed: false,
    });

    const follow = () => {
      if (user.is_followed) return;
      console.log("bbb");
      user.is_followed = true;
      user.followedCont++;
    };

    const unfollow = () => {
      if (!user.is_followed) return;
      console.log("aaaa");
      user.is_followed = false;
      user.followedCont--;
    };

    const post_a_post = (content) => {
      posts.count++;
      posts.posts.unshift({ id: posts.count, userId: 1, content: content });
    };

    const posts = reactive({
      conunt: 3,
      posts: [
        {
          id: 1,
          userId: 1,
          content: "今天学习了css课",
        },
        {
          id: 2,
          userId: 1,
          content: "今天学习了html课",
        },
        {
          id: 3,
          userId: 1,
          content: "今天学习了js课",
        },
      ],
    });

    return {
      user,
      follow,
      unfollow,
      posts,
      post_a_post,
    };
  },
};
</script>
  
  <style scoped>
</style>
  