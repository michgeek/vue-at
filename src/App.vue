<template>
    <div id="app">
        <at :members="members" nameKey="name" v-model="model">
            <!-- custom: same as default slot -->
            <!-- <template slot="item" scope="s">
              <span v-text="s.item"></span>
            </template> -->

            <!-- custom: with avatars -->
            <template slot="item" scope="s">
                <img :src="s.item.avatar">
                <span v-text="s.item.name"></span>
            </template>
            <template slot="mention" scope="s">
                <strong v-text="'@'+s.item.name"></strong>
            </template>
        </at>

        <pre>
        {{ model }}
        </pre>
    </div>
</template>

<script>
    // import At from 'vue-at'
    // import At from '../dist'
    import At from './At.vue'

    let members = [
        "Roxie Miles", "grace.carroll",
        "小浩",
        "Helena Perez", "melvin.miller",
        "椿木",
        "myrtie.green", "elsie.graham", "Elva Neal",
        "肖逵",
        "amy.sandoval", "katie.leonard", "lottie.hamilton",
    ]
    members = members.map((v, i) => {
        return {
            avatar     : `https://randomuser.me/api/portraits/men/${i % 5}.jpg`,
            name       : v,
            description: `${v}@example.com`
        }
    })

    export default {
        components: {At},
        name      : 'app',
        data () {
            return {
                members,
                model: 'Hello world' // fix trailing abnormal nodes
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        margin: 60px;
    }

    .editor {
        width: 400px;
        min-height: 200px;
        white-space: pre-wrap;
        border: solid 2px rgba(0, 0, 0, .5);
    }

    .editor img {
        max-width: 10em;
        vertical-align: bottom;
    }

    /* override styles */
    #app .atwho-li {
        padding: 0 4px;
    }

    #app .atwho-li img {
        height: 100%;
        width: auto;
        -webkit-transform: scale(.8);
    }

    #app .atwho-li span {
        padding-left: 8px;
    }
</style>
