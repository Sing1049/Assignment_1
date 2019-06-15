<template>
<div>
    <!-- dialog box opens here -->
<el-dialog
  title="Form Submition!"
  :visible.sync="dialogVisible"
  width="40%"
  :before-close="handleClose">
    <!-- Div inside dialog box to display data entered in form -->
  <div class="formSubmit">
    <ul>
    <li><span>First Name :</span> {{ this.form.inputs.firstName }}</li>
    <li><span>Last Name :</span> {{ this.form.inputs.lastName }}</li>
    <li><span>Email :</span> {{ this.form.inputs.email }}</li>
    <li><span>Subject :</span> {{ this.form.inputs.subject }}</li>
    <li><span>Claim Request :</span> {{ this.form.inputs.claim }}</li>
    <li><span>Accepted Terms and Conditions :</span> {{ this.form.inputs.agree }}</li>
    </ul>
  </div>
    <!-- Dialog Box Button -->
  <span slot="footer" class="dialog-footer">
      <!-- Both Button will close the dialog -->
    <el-button type="primary" @click="dialogVisible = false">Close</el-button>
  </span>
</el-dialog>

<!-- Claim Form Starts here -->
  <el-form :model="form.inputs" :rules="form.rules" ref="form" label-width="120px" class="demo-dynamic">

<!-- First Name input here -->  
  <el-form-item
    prop="firstName"
    label="First Name"
    :rules="form.rules.notEmpty"
  >
    <el-input v-model="form.inputs.firstName"></el-input>
  </el-form-item>

<!-- Last Name input here -->  
  <el-form-item
    prop="lastName"
    label="Last Name"
    :rules="form.rules.notEmpty"
  >
    <el-input v-model="form.inputs.lastName"></el-input>
  </el-form-item>

<!-- Email input here -->
  <el-form-item
    prop="email"
    label="Email"
    :rules="form.rules.validEmail"
  >
    <el-input v-model="form.inputs.email"></el-input>
  </el-form-item>

<!-- Subject input here -->  
  <el-form-item
    prop="subject"
    label="Subject"
    :rules="form.rules.wordLimit"
  >
    <el-input v-model="form.inputs.subject"  ></el-input>
  </el-form-item>

<!-- Claim Request input here -->  
  <el-form-item
    prop="claim"
    label="Comment "
    :rules="form.rules.notEmpty"
  >
    <el-input v-model="form.inputs.claim"  ></el-input>
  </el-form-item>
 

  
<!-- Terms and condition agreement -->
<el-form-item >
      <el-checkbox aria-required="required" value="One" label="Agree to terms and Conditions" v-model="form.inputs.agree" name="agree"></el-checkbox>
  </el-form-item>


  <!-- Form Buttons -->
  <el-form-item>
      <!-- Submit Button -->
    <el-button type="primary" @click="submitForm('form')">Submit</el-button>
      <!-- Reset Button -->
    <el-button @click="resetForm('form')">Reset</el-button>
  </el-form-item>

</el-form>

<!-- form ends here -->
</div>
</template>

<script>
  export default {
    data() {
      return {
      dialogVisible: false,
      form: {
        inputs: {
          firstName: '',
          lastName: '',
          email: '',
          subject: '',
          claim:'',
          agree: false
          },
        rules: {
             validEmail : [
                { required: true, message: 'Please input email address', trigger: ['blur','change'] },
                { type: 'email', message: 'Please input correct email address', trigger: ['blur', 'change'] }
                    ],
             notEmpty : [
                 { required : true,  message: 'You cannot leave it Blank', trigger: ['blur','change']}
             ],
             wordLimit: [
               { required:true,  message: 'Please enter a Claim Tittle', trigger: ['blur','change']},
               { max: 30, message: 'Length cannot exceed 30 words', trigger: 'blur'}
             ],
             agree: [
                {required: true, message: 'Please select activity resource', trigger: ['blur', 'change'] }
             ]
            }
             
    }
        }
      },
    methods: {
      // This will submit the form or open the dialog box and reset all the fields
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            this.dialogVisible = true;
          } else {
  // this is console that sumition did not happened
            console.log('error submit!!');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      },
    }
  }
</script>

<!-- Styling for my dialog box data-->
<style>
.formSubmit ul {
  font-size: 1rem;
  list-style: none;
  padding: 5px;
  border: 2px solid grey;
  border-radius: 20px;
  margin-top: 5px;
  text-align: left;
}
.formSubmit ul li {
  padding: 10px;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.formSubmit ul li:last-child {
  border-bottom: 0;
}
.formSubmit span {
  text-transform: uppercase;
  font-weight: bold;
  padding-right: 10px;
  min-width: 200px;
  display: inline-block;
}
</style>
