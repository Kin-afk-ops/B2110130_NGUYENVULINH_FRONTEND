<template>
  <div class="page">
    <h4>Thêm liên hệ</h4>
    <ContactForm :contact="contact" @submit:contact="createContact" />
    <p>{{ message }}</p>
  </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
  components: {
    ContactForm,
  },

  data() {
    return {
      contact: {
        name: "",
        email: "",
        address: "",
        phone: "",
        favorite: false,
      },
      message: "",
    };
  },
  methods: {
    async createContact(contact) {
      try {
        await ContactService.create(contact);
        this.message = "Liên hệ được thêm thành công.";
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
