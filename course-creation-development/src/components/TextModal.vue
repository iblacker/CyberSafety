<template>
     <modal ref= "textM" id= "textM">
        <header>
            <h2>{{moduleTitle}}</h2>
        </header>
        <body>
            {{content}}        
        </body>
        <footer>
            {{courseID}} {{moduleID}}   {{contentType}}
        </footer>
    </modal>
</template>

<script>
    export default {
        props: {
            courseID: Number,
            moduleID: Number,
            contentType: String,
            moduleTitle: String,
            content: Object,
            submitted: Boolean
        },
        methods: {
            show () {
                this.$modal.show('textM');
            },
            hide () {
                this.$modal.hide('textM');
            }
        },
        mounted: function () {
            this.$nextTick(function () {
                this.$modal.show('textM');
            })
        }
    }   
</script>
