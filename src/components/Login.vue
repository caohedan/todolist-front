<template>
  <el-form :model="ruleForm2"  :rules="rules2" ref="ruleForm2" label-width="30%" :label-position="top" >
    <el-form-item label="User Id " prop="age">
      <el-input v-model.number="ruleForm2.age" STYLE="width:50%;float:left;"></el-input>
    </el-form-item>
    <el-form-item label="password:" prop="pass">
      <el-input type="password" v-model="ruleForm2.pass" autocomplete="off" STYLE="width:50%;float:left;" ></el-input>
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="submitForm('ruleForm2')" style="float:left;margin-left: 20%;">login</el-button>
    </el-form-item>
  </el-form>

</template>
<script>
  export default {
      name: "Login",
      data() {
        var checkAge = (rule, value, callback) => {
          if (!value) {
            return callback(new Error('年龄不能为空'));
          }
          setTimeout(() => {
            if (!Number.isInteger(value)) {
              callback(new Error('请输入数字值'));
            } else {
              if (value < 18) {
                callback(new Error('必须年满18岁'));
              } else {
                callback();
              }
            }
          }, 1000);
        };
        var validatePass = (rule, value, callback) => {
          if (value === '') {
            callback(new Error('请输入密码'));
          } else {
            if (this.ruleForm2.checkPass !== '') {
              this.$refs.ruleForm2.validateField('checkPass');
            }
            callback();
          }
        };
        var validatePass2 = (rule, value, callback) => {
          if (value === '') {
            callback(new Error('请再次输入密码'));
          } else if (value !== this.ruleForm2.pass) {
            callback(new Error('两次输入密码不一致!'));
          } else {
            callback();
          }
        };
        return {
          ruleForm2: {
            pass: '',
            checkPass: '',
            age: ''
          },
          rules2: {
            pass: [
              { validator: validatePass, trigger: 'blur' }
            ],
            checkPass: [
              { validator: validatePass2, trigger: 'blur' }
            ],
            age: [
              { validator: checkAge, trigger: 'blur' }
            ]
          }
        };
      },
      methods: {
        submitForm(formName) {
          this.$refs[formName].validate((valid) => {
            if (valid) {
              alert('submit!');
            } else {
              console.log('error submit!!');
              return false;
            }
          });
        },
        resetForm(formName) {
          this.$refs[formName].resetFields();
        }

    }
    }

</script>


<style scoped>

</style>
