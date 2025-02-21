<template>
  <template v-if="error">
    <ErrorCard :retry="fetchBookings">Failed to fecth bookings. Please try again.</ErrorCard>
  </template>
  <template v-else>
    <section class="grid grid-cols-1 gap-8">
      <template v-if="!loading">
        <BookingItem
          v-for="booking in bookings"
          :key="booking.id"
          :title="booking.eventTitle"
          :status="booking.status"
          @cancelled="cancelBooking(booking.id)"
        />
      </template>
      <template v-else>
        <LoadingBookingItem />
      </template>
    </section>
  </template>
</template>

<script setup>
import BookingItem from '@/components/BookingItem.vue';
import { onMounted } from 'vue';
import LoadingBookingItem from '@/components/LoadingBookingItem.vue';
import { useBookings } from '@/composables/useBookings';
import ErrorCard from '@/components/ErrorCard.vue';

const { bookings, loading, fetchBookings, cancelBooking, error } = useBookings();

onMounted(() => {
  fetchBookings();
});
</script>
