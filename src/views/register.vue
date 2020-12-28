<template>
  <div class="web">
    <div class="web2">
      <div style="text-align:center">
        <span style="color: red;">注册</span>
      </div>

      <div>
        <span>用户名：&nbsp;&nbsp;&nbsp;&nbsp;</span>
        <input
          id="loginName"
          type="text"
          placeholder="请输入用户名"
          v-model="loginName"
          style="border: 1px black solid;"
        />
      </div>
      <div>
        <span>密码：&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span>
        <input
          id="loginPsd"
          type="password"
          placeholder="请输入密码"
          v-model="loginPsd"
          style="border: 1px black solid;"
        />
      </div>
      <div>
        <span>确认密码：&nbsp;</span>
        <input
          id="loginPsd2"
          type="password"
          placeholder="请再次输入密码"
          v-model="loginPsd2"
         style="border: 1px black solid;"
        />
      </div>
      <div>
        <button @click="register" style="font-size: 110%;
  font-weight: 800;border: 1px black solid;">注册</button>
      </div>
    </div>
  </div>
</template>

<script>

</script>
<script>
export default {
  data() {
    return {
      loginName: "",
      loginPsd: "",
      loginPsd2: "",
    };
  },
  methods: {
    register() {
      if (this.isNone()) {
        // 定义一个空数组
        let arr = [];
        if (localStorage.user) {
          arr = eval(localStorage.user);
          for (var e in arr) {
            // 取出数据判断是否注册过
            if (this.loginName === arr[e].loginName) {
              alert("该账号已被注册");
              this.clear();
              return;
            }
          }
        }
        const user = {
          loginName: this.loginName,
          loginPsd: this.loginPsd,
        };
        // 添加数据
        arr.push(user);
        localStorage.user = JSON.stringify(arr);
        alert("注册成功");
        window.location.href = "login";
        this.clear();
      }
    },
    isNone() {
      if (this.loginName === "") {
        alert("用户名不能为空");
        return false;
      } else if (this.loginPsd === "") {
        alert("密码不能为空");
        return false;
      } else if (this.loginPsd !== this.loginPsd2) {
        alert("两次密码不一致，请检查！");
        return false;
      }
      return true;
    },
    clear() {
      this.loginName='';
      this.loginPsd='';
      this.loginPsd2='';
    },
  },
};
</script>
<style>

.web2{
  margin: 0 auto;
  width: 600px;
  height: 400px;
  text-align: center;
  font-size: 120%;
  font-weight: 800;
}

</style>