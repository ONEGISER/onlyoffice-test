<template>
    <DocumentEditor id="docEditor" documentServerUrl="http://1.6.6.1:28081" :config="config"
        :events_onDocumentReady="onDocumentReady" :onLoadComponentError="onLoadComponentError" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { DocumentEditor } from "@onlyoffice/document-editor-vue";

export default defineComponent({
    name: 'ExampleComponent',
    components: {
        DocumentEditor
    },
    data() {
        return {
            config: {
                document: {
                    fileType: "docx",
                    key: "cd9eb84d1bae4d348ebe8dc77a80ec7a.docx",
                    title: "Example Document Title.docx",
                    url: "http://1.6.6.1:28089/shiyanghe/file/emerPlan/4284ba7dfcb14641a9982048fd54de40.docx",
                    permissions: {
                        edit: true
                    }
                },
                documentType: "word",
                editorConfig: {
                    callbackUrl: "http://1.6.6.1:28089/shiyanghe/bus/emer/plan/onlyOffice/callback",
                    mode: 'edit',// 'view' 'edit'
                    // coEditing: {
                    //     "mode": "fast",
                    //     "change": true
                    // },
                }
            }
        }
    },
    methods: {
        onDocumentReady() {
            console.log("Document is loaded");
        },
        onLoadComponentError(errorCode, errorDescription) {
            switch (errorCode) {
                case -1: // Unknown error loading component
                    console.log(errorDescription);
                    break;

                case -2: // Error load DocsAPI from http://documentserver/
                    console.log(errorDescription);
                    break;

                case -3: // DocsAPI is not defined
                    console.log(errorDescription);
                    break;
            }
        }
    },
});
</script>