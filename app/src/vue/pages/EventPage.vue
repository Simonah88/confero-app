
<template>
    <v-ons-page>
        <top-toolbar backLabel="Home" :title="event.Name"></top-toolbar>

        <v-ons-tabbar position="bottom"
                      :tabs="tabs"
                      :visible="true"
                      :index.sync="activeIndex"
        >
        </v-ons-tabbar>
    </v-ons-page>
</template>

<script>
    import EventSessions from './EventSessions.vue';
    import EventFavorites from './EventFavorites.vue';
    import EventPeople from './EventPeople.vue';
    import EventPapers from './EventPapers.vue';
    import EventInfo from './Info.vue';


    import { mapGetters, mapActions } from 'vuex'

    //this is really just a wrapper for the tabbar loads eventsession by default because it is index 0 in tabs
    export default {
        computed: mapGetters({
            event: 'events/selectedEvent'
        }),
        data(){
            return {
                activeIndex: 0,
                tabs: [
                    {
                        label: 'Sessions',
                        icon: 'fa-clock-o',
                        page: EventSessions
                    },
                    {
                        label: 'People',
                        icon: 'fa-users',
                        page: EventPeople
                    },
                    {
                        label: 'Papers',
                        icon: 'fa-clone',
                        page: EventPapers
                    },
                    {
                        label: 'Favorites',
                        icon: 'fa-star',
                        page: EventFavorites
                    }
                ]
            }
        }
    };
</script>