<template>
  <div class="home">
    <Title msg="VMail Inbox" />

   <!--  <h2>{{ emailSelection.emails.size }} emails selected</h2> -->

    <Suspense>
      <template #default><MailTable /></template>
      <template #fallback>
        ...Loading
      </template>
    </Suspense>

  </div>
</template>

<script>
import Title from '@/components/Title.vue'
import { format } from 'date-fns'
import MailTable from '@/components/MailTable.vue'
import useEmailSelection from '@/composables/use-email-selection'

export default {
  name: 'Home',
  components: {
    Title,
    MailTable
  },
  setup() {
    return {
      emailSelection: useEmailSelection()
    }
  }
};
</script>