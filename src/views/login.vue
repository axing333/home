<template>
<div class="web" style="">
  <div class="web2">
    <div>
      <span style="color: blue">登录</span>
    </div>

    <div>
      <span>用户名：</span>
      <input id="loginName" type="text" placeholder="请输入用户名" v-model="loginName" style="border: 1px black solid;"/>
    </div>
    <div>
      <span>密码： </span>
      <input id="loginPsd" type="password" placeholder="请输入密码" v-model="loginPsd" style="border: 1px black solid;"/>
    </div>
    <div>
      <button @click="login" style="border: 1px black solid; font-weight: 800;font-size: 102%;">登录</button>
      <a href="register" style="border: 1px black solid;">注册</a>
    </div>
    
  </div>
</div>
</template>
<script>
export default {
  data() {
    return {
      loginName: "",
      loginPsd: "",
    };
  },
  methods: {
    login() {
      if (this.isNone()) {
        if (localStorage.user) {
          // 从localStorage取出键为user的数据模型
          let arr;
          arr = eval(localStorage.user);
          console.log(arr);
          let k = 0;
          // 循环取出，可用其他方法代理，数据量多的情况下，不建议使用for循环
          for (var e in arr) {
            console.log(e);
            // 判断用户名，密码是否和localStorage中的数据一致，兼容性写法必须添加trim(),不需要兼容可以不写
            if (this.loginName === arr[e].loginName) {
              if (this.loginPsd === arr[e].loginPsd) {
                alert("登录成功");
                // 成功后清除用户名和密码
                this.clear();
                k = 0;
                window.location.href = "homepage";
                // 成功之后对整个登录页面ID为web的部分重新换为成功的标识（也可以选择跳转到成功页面）
                return;
              } else {
                alert("密码错误");
                // 失败后清除用户名和密码
                this.clear();
                k = 0;
                return;
              }
            } else {
              k = 1;
            }
          }
          if (k === 1) {
            alert("用户名不存在");
            this.clear();
          }
        } else {
          alert("用户名不存在，正在跳转到注册页面！");
          window.location.href = "register";
          this.clear();
        }
      }
    },
    isNone() {
      if (this.loginName === "") {
        alert("用户名不能为空");
        return false;
      } else if (this.loginPsd === "") {
        alert("密码不能为空");
        return false;
      }
      return true;
    },
    clear() {
      this.loginName = "";
      this.loginPsd = "";
    },
  },
};

/**
 * 登录的验证方法
 * 是否为空的判断
 */
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