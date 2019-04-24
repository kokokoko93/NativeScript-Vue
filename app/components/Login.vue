<template>
    <Page>
        <StackLayout class="login-area">
            <TextField
                hint="Email Address"
                keyboardType="email"
                returnKeyType="next"
                v-model="email"
                row="0" class="textfield"></TextField>
            <TextField ref="password"
                hint="Password"
                secure="true"
                v-model="acc"
                row="1" class="textfield"></TextField>
            <StackLayout @tap="login()" class="login-button">
                <Label text="Login" class="login-button-label"></Label>
            </StackLayout>
        </StackLayout>
    </Page>
</template>

<script >
    import App from '@/components/App'
    export default {
        data() {
            return {
                msg: 'Login頁',
                AppPage: App,
                email: 'Test',
                acc: '123'
            }
        },
        methods: {
            login(){
                let getEMail = this.email;
                let getAcc = this.acc;
                console.log(getEMail+' '+getAcc);
                if(getEMail=='Test'&&getAcc=='123'){
                    console.log('Success Login');
                    this.$navigateTo(App);
                }else{
                    alert({
                        title: "提醒",
                        message: "帳號密碼錯誤",
                        okButtonText: "OK"
                    }).then(() => {
                        console.log('Fail Login');
                    });
                    
                }
            }
        },
    }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .title {
        text-align: left;
        padding-left: 16;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }

    .drawer-header {
        padding: 50 16 16 16;
        margin-bottom: 16;
        background-color: #53ba82;
        color: #ffffff;
        font-size: 24;
    }

    .drawer-item {
        padding: 8 16;
        color: #333333;
        font-size: 30;
    }

    .login-area {
        background-color: white;
        height: 200;
        width: 275;
        vertical-align: center;
    }

    .login-button {
        background-color: rgb(197, 199, 195);
        color: #CB1D00;
        height: 45;
        width: 275;
        vertical-align: center;
        margin-top: 1;
    }

    .login-button-label {
        horizontal-align: center;
        font-weight: bold;
    }

    .textfield{
        background-color: gray;
        color: #000000;
        height: 45;
        margin-top: 1;
    }

</style>
