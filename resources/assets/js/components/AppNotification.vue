<template>
<div class="text-xs-center">
    <v-menu offset-y>
        <v-btn icon slot="activator">
            <v-icon color="red">add_alert</v-icon>5
        </v-btn>
        <v-list>
            <v-list-tile v-for="item in unread" :key="item.id">
                <v-list-tile-title>{{item.data.question}}</v-list-tile-title>
            </v-list-tile>
        </v-list>
    </v-menu>
</div>
</template>

<script>
    export default {
        data() {
            return {
                read: {},
                unread: {},
                unreadCount: 0
            }
        },
        created() {
            if(User.loggedIn()) {
                console.log("aac");
                this.getNotifications()
            } else {
                console.log("aaa");
            }
        },
        methods: {
            getNotifications(){
                axios.post('/api/notifications')
                .then(res => {
                    this.read = res.data.read
                    this.unRead = res.data.unread
                    this.unreadCount = res.data.unread.length
                })
                console.log(this.read);
                console.log(this.unread);
            }
        }
    }
</script>