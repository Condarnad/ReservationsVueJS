<template>
    <div class="reservations">
        <button @click="updateData">Add</button><br><br>
        <reservation-list-item v-for="reservation in reservations" :reserve-info="reservation"  :swipeable="swipeable" @accept="handleAccept" />
    </div>
</template>

<script>
    import ReservationListItem from "./ReservationListItem";

    export default {
        components: {ReservationListItem},
        props:{
            swipeable:{
                type:Boolean,
                default:false
            }
        },
        data(){
           return { reservations:[
                   {'number':1,'name':'mo4a','dateTime':new Date(),'accepted':null},
                   {'number':2,'name':'mo5a','dateTime':new Date().setMonth(4),'accepted':null},
                   {'number':3,'name':'mo6a','dateTime':0,'accepted':null},
                   {'number':4,'name':'mo7a','dateTime':0,'accepted':null}
           ] }
        },
        methods:{
            updateData(){
                this.reservations.push( {'number':4,'name':'mo7a','dateTime':0});
            },
            handleAccept(val){
                let id = this.reservations.indexOf(val.reservation);
                this.$set(this.reservations[id],'accepted',val.accepted);
            }
        }
    }
</script>

<style scoped>
    .reservations{
        display: flex;
        flex-direction: column;
        align-items: baseline;
    }
</style>