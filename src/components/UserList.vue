<template>
  <div class="container">
    <div class="page-title">
      <h3>{{ message }}</h3>
    </div>
    <div class="row">
      <div
        class="col-md-4"
        v-for="user in users"
        :key="user.id"
        data-user="user"
      >
        <div class="m-portlet m-portlet--full-height">
          <div class="m-portlet__body">
            <div class="tab-content">
              <div class="tab-pane active" id="m_widget4_tab1_content">
                <div class="m-widget4 m-widget4--progress">
                  <div class="m-widget4__item">
                    <div class="m-widget4__img m-widget4__img--pic">
                      <img
                        src="https://bootdey.com/img/Content/avatar/avatar1.png"
                        alt=""
                      />
                    </div>
                    <div class="m-widget4__info">
                      <span class="m-widget4__title"> {{ user.name }} </span>
                      <br />
                      <span class="m-widget4__sub">
                        {{ user.title }}
                      </span>
                    </div>
                    <div class="m-widget4__ext">
                      <button
                        @click="deleteUser(user)"
                        class="btn btn-primary"
                        data-cy="taskDelete"
                        id="deleteForm"
                      >
                        Delete
                      </button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="row">
      <form id="form" @submit.prevent="createUser">
        <input id="new-user" v-model="newUser" class="form-control" />
      </form>
    </div>
  </div>
</template>

<script>
export default {
  props: ["message"],
  data() {
    return {
      newUser: "",
      users: [
        {
          id: 1,
          name: "Anna Strong",
          title: "Software Engineer",
        },
        {
          id: 2,
          name: "John Doe",
          title: "Technical Writer",
        },
      ],
    };
  },
  methods: {
    createUser() {
      this.users.push({
        id: 3,
        name: this.newUser,
        title: "Crypto Expert",
      });
      this.newUser = "";
    },
    deleteUser(user) {
      const newList = this.users.filter((u) => user.id !== u.id);
      this.users = newList;
    },
  },
};
</script>

<style>
.m-portlet {
  margin-bottom: 2.2rem;
}
.m-portlet {
  -webkit-box-shadow: 0 1px 15px 1px rgba(113, 106, 202, 0.08);
  -moz-box-shadow: 0 1px 15px 1px rgba(113, 106, 202, 0.08);
  box-shadow: 0 1px 15px 1px rgba(113, 106, 202, 0.08);
  background-color: #fff;
}
.m-portlet .m-portlet__head {
  border-bottom: 1px solid #ebedf2;
}
.m-widget4 .m-widget4__item {
  display: table;
  padding-top: 1.15rem;
  padding-bottom: 1.25rem;
}
.m-widget4 .m-widget4__item .m-widget4__img {
  display: table-cell;
  vertical-align: middle;
}
.m-widget4 .m-widget4__item .m-widget4__img.m-widget4__img--logo img {
  width: 3.5rem;
  border-radius: 50%;
}
.m-widget4 .m-widget4__item .m-widget4__img.m-widget4__img--pic img {
  width: 4rem;
  border-radius: 50%;
}
.m-widget4 .m-widget4__item .m-widget4__img.m-widget4__img--icon img {
  width: 2.1rem;
}
.m-widget4 .m-widget4__item .m-widget4__info {
  display: table-cell;
  width: 100%;
  padding-left: 1.2rem;
  padding-right: 1.2rem;
  font-size: 1rem;
  vertical-align: middle;
}
.m-widget4 .m-widget4__item .m-widget4__info .m-widget4__title {
  font-size: 1rem;
  font-weight: bold;
}
.m-widget4.m-widget4--progress .m-widget4__info {
  width: 50%;
}
</style>
