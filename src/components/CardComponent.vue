 <template>
  <div>
    <card class="card-section" style="width: 450px; margin: auto">
      <h1>Contact Form</h1>
      <form ref="values" @submit.prevent="sendEmail">
        <div class="form-group">
          <KInput
            class="form-input"
            :style="{ width: '290px' }"
            name="name"
            v-model="user_name"
            placeholder="Name"
          ></KInput>
        </div>
        <div class="form-group">
          <KInput
            class="form-input"
            :style="{ width: '290px' }"
            name="email"
            v-model="user_email"
            placeholder="email address"
          ></KInput>
        </div>
        <div class="form-group">
          <k-textarea
            class="form-input"
            :style="{ width: '290px' }"
            name="message"
            v-model="user_message"
            placeholder="Message"
            :rows="4"
          />
        </div>
        <div class="example-col">
          <kbutton
            :style="{ width: '100px' }"
            id="submit-btn"
            >Submit form</kbutton
          >
        </div>
      </form>
    </card>
  </div>
</template>
 
<script>
import emailjs from 'emailjs-com';

import {
  Card,
} from "@progress/kendo-vue-layout";
// ES2015 module syntax
import { Input, TextArea } from "@progress/kendo-vue-inputs";
import "@progress/kendo-theme-default";
import { Button } from "@progress/kendo-vue-buttons";

export default {
  name: "CardComponent",
  components: {
    card: Card,
    KInput: Input,
    "k-textarea": TextArea,
    kbutton: Button,
  },
  data() {
    return {
      user_name: "",
      user_email: "",
      user_message: "",
    };
  },
  methods: {
    sendEmail() {
      emailjs
        .sendForm(
          "service_itnunld",
          "template_gshkqzp",
          this.$refs.values,
          "ZoU1vlRuUeYlHiRYA"
        )
        .then(
          (result) => {
            console.log(
              "You have successfully submitted your message",
              result.text
            );
          },
          (error) => {
            console.log(
              "This form failed to submit, please kindly check your internet connection",
              error.text
            );
          }
        );
    },
  },
};
</script>
<style>
.form-input{
  margin: 10px 15px;
  border-radius: 0px;
  padding: 10px 0px;
}

#submit-btn{
  margin: 10px 0px;
  padding: 10px 20px;
  background-color: lightcoral;
}
</style>

