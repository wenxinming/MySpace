<template>
  <div class="card">
    <div class="card-body">
      <div class="row">
        <div class="col-3 img-field">
          <img
            class="img-fluid"
            src="https://cdn.acwing.com/media/user/profile/photo/205914_lg_73920572fb.jpg"
            alt=""
          />
        </div>

        <div class="col-9">
          <div class="username">{{ fullName }}</div>
          <div class="fans">粉丝：{{ user.followedCont }}</div>
          <button
            v-if="!user.is_followed"
            v-on:click="follow"
            type="button"
            class="btn btn-secondary btn-sm"
          >
            +关注
          </button>
          <button
            v-if="user.is_followed"
            v-on:click="unfollow"
            type="button"
            class="btn btn-secondary btn-sm"
          >
            取消关注
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from "vue";

export default {
  name: "UserProfileInfo",
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  setup(props, context) {
    let fullName = computed(
      () => props.user.firstName + " " + props.user.lastName
    );

    const follow = () => {
      context.emit("follow");
    };

    const unfollow = () => {
      context.emit("unfollow");
      console.log("unfollow");
    };

    return {
      fullName,
      follow,
      unfollow,
    };
  },
};
</script>

<style scoped>
img {
  border-radius: 50%;
}

.username {
  font-weight: bold;
}

.fans {
  font-size: 12px;
  color: gray;
}

button {
  padding: 2px 4px;
  font-size: 12px;
}
</style>