<template>
    <div class="page">
        <h4>Thêm Liên Hệ</h4>
        <ContactForm
            :contact = "contact"
            @submit:contact = "addContact"
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service.js";

    export default {
        components: {
            ContactForm,
        },
        data() {
            return{
                contact: { name: null, email: null, address: null, phone: null, favorite: false, _id: null },
                message: "", 
            };
            
        },
        methods: {
            async addContact(data) {
                try {
                    await ContactService.create(data);
                    this.message = "Thêm liên hệ thành công";
                } catch (error) {
                    console.log(error);
                }
            }
        },
    }
</script>