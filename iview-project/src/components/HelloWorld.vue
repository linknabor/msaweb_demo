<template>
  <div class="login" @keydown.enter="handleSubmit">
  <div class="login-con">
  	<Card>
  <p slot="title">
  	<Icon type="md-log-in"></Icon>
  	欢迎登录
  </p>
  <div class="form-con">
  	  <Form ref="loginForm" :model="form" :rules="rules">
                        <FormItem prop="userName">
                            <Input v-model="form.userName" placeholder="请输入用户名">
                                <span slot="prepend">
                                    <Icon :size="16" type="ios-person"></Icon>
                                </span>
                            </Input>
                        </FormItem>
                        <FormItem prop="password">
                            <Input type="password" v-model="form.password" placeholder="请输入密码">
                                <span slot="prepend">
                                    <Icon :size="14" type="md-lock"></Icon>
                                </span>
                            </Input>
                        </FormItem>
                        <FormItem>
                            <Button @click="handleSubmit" type="primary" long>登录</Button>
                        </FormItem>
                    </Form>
  </div>
  </Card>
  </div>
  </div>
</template>

<script>
	import Cookies from 'js-cookie'
export default {
  name: 'HelloWorld',
   data () {
        return {
            form: {
                userName: '',
                password: ''
            },
            rules: {
                userName: [
                    { required: true, message: '账号不能为空',minlength:6, trigger: 'blur' }
                ],
                password: [
                    { required: true, message: '密码不能为空', minlength:10,trigger: 'blur' }
                ]
            }
        };
    },
    methods: {
        handleSubmit () {
            this.$refs.loginForm.validate((valid) => {
                if (valid) {
                    Cookies.set('user', this.form.userName);
                    Cookies.set('password', this.form.password);
                    this.$store.commit('setAvator', 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3448484253,3685836170&fm=27&gp=0.jpg');
                    if (this.form.userName === 'iview_admin') {
                        Cookies.set('access', 0);
                    } else {
                        Cookies.set('access', 1);
                    }
                    
                }
               
            });
             this.$router.push('/demo');
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.login{
	width:100%;
	height: 100vh;
	background-image: url('https://file.iviewui.com/iview-admin/login_bg.jpg');
  background-size: cover;
  background-position: center;
  position: relative;
  &-con{
  	position:absolute;
  	top: 50%;
  	left: 50%;
  	transform: translate(-50%,-50%);
  	width: 300px;
  	height: 280px;
  	border-radius: 4px;
  	background:#fff;
  	&-header{
  		text-align:center;
  		font-weight: 300;
  		padding: 20px 0;
  	}
  	.form-con{
  		padding:10px 0 0
  	}
  	.login-tip{
  		font-size:10px;
  		text-align:center;
  		color:#c3c3c3
  	}
  }
}
</style>
