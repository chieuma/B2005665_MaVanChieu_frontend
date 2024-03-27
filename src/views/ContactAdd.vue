<template>
    <div class="page">
      <h2>Thêm liên hệ mới</h2>
      <ContactForm :contact="newContact"
                    @addContact:contact="addContact"
      />
      <!-- <div class="form-group">
            <button class="btn btn-primary" @click="addContact">Thêm</button>
      </div> -->

        <p>{{ message }}</p>
    </div>
  </template>
  
  <script>
  import ContactForm from "@/components/ContactForm.vue";
  import ContactService from "@/services/contact.service";
  export default {
    components: {
      ContactForm
    },
    data() {
      return {
        newContact: {
          name: "",
          email: "",
          address: "",
          phone: "",
        },
        message : "",
      };
    },
    methods: {
      async addContact() {
        try{
                await ContactService.create(this.newContact);
                this.message = "Danh bạ mới đã được thêm vào.";
        } catch (error) {
            console.log(error);
        }
      }
    }
  };
  </script>
