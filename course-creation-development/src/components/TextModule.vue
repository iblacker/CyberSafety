<template>
    <main>
        <form id="textStuff" @submit.prevent= "addText">
            <input type="text" name= "ttl" id= "ttl"  v-model= "moduleTitle" />
            <VueTrix v-model= "editorContent"/>
            <input type="submit" value= "Submit">
        </form>
        <TextModal v-if= "submitted" v-bind:moduleTitle= "moduleTitle" v-bind:editorContent= "editorContent" ></TextModal>
    </main>
</template>

<script>
    import TextModal from './TextModal.vue';
    export default {
        components: {
            TextModal
        },
        data() {
            return {
                moduleTitle: '',
                courseID: 0,
                moduleID: 0,
                contentType: '',
                editorContent: '',
                submitted: false
            }
        },
        methods: {
           
            addText: function(){
                this.courseID = 5;
                this.moduleID = 9;
                this.contentType = 'text';
                submitted: true;
                console.log(this);
                this.$emit('shows');
            }
        },
        mounted: function () {
            this.$nextTick(function () {
                this.$modal.show('textM');
            })
        }
    }   
</script>