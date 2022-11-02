<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: { ContactForm },

    data() {
        return {
            contact: {
                _id: "",
                address: "",
                email: "",
                favorite: null,
                name: "",
                phone: "",
            },
            message: "",
        };
    },
    methods: {
        async contactAdd(data) {
            try {
                await ContactService.create(data);
                this.message = "Thêm liện hệ thành công";
            } catch (error) {
                console.log(error);
            }
        },
    },
};
</script>

<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm :contact="contact" @submit:contact="contactAdd" />
        <p>{{ message }}</p>
    </div>
</template>

<style>

</style>