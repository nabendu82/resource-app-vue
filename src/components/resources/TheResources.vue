<template>
    <base-card>
        <base-button @click="setSelectedTab('resource-list')" :mode="storedResButtonMode">Resources</base-button>
        <base-button @click="setSelectedTab('add-resource')" :mode="addResButtonMode">Add Resource</base-button>
    </base-card>
    <component :is="selectedTab"></component>
</template>

<script>
import ResourceList from './ResourceList.vue'
import AddResource from './AddResource.vue';

export default {
    components: {
        ResourceList,
        AddResource,
    },
    data() {
        return { 
            selectedTab: 'resource-list',
            storedResources: [
                {
                    id: 'vue-guide',
                    title: 'Vue Guide',
                    description: 'The official Vue.js guide',
                    link: 'https://vuejs.org'
                },
                {
                    id: 'google',
                    title: 'Google',
                    description: 'Learn to google',
                    link: 'https://google.com'
                },
            ] 
        }
    },
    provide() {
        return {
            resources: this.storedResources,
            addResource: this.addResource,
            deleteResource: this.removeResource
        };
    },
    computed: {
        storedResButtonMode() {
            return this.selectedTab === 'resource-list' ? null : 'flat';
        },
        addResButtonMode() {
            return this.selectedTab === 'add-resource' ? null : 'flat';
        },
    },
    methods: {
        setSelectedTab(tab) {
            this.selectedTab = tab;
        },
        addResource(title, description, url) {
            const newResource = {
                id: new Date().toISOString(),
                title: title,
                description: description,
                link: url,
            };
            this.storedResources.unshift(newResource);
            this.selectedTab = 'resource-list';
        },
        removeResource(resId) {
            const resIndex = this.storedResources.findIndex(res => res.id === resId);
            this.storedResources.splice(resIndex, 1);
        },
    }
}
</script>