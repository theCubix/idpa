<template>
  <div class="container mx-auto">
    
    <h1 class="font-thin text-grey-dark text-5xl text-center my-4">Shops.</h1>

    <div
      class="max-w-sm sm:rounded-none rounded overflow-hidden shadow-lg mx-auto my-8 bg-white"
      v-for="record in records"
      :key="record.id"
      v-if="record.fields.Category === 'Published'">

      <div class="px-6 pb-4 pt-5">
        <div class="font-bold text-xl mb-2">{{ record.fields.Name }}</div>
        <p class="text-grey-darker text-base">
          {{ record.fields.Description }}
        </p>
      </div>
      <div class="flex">
        <div
          class="flex-1"
          v-for="image in record.fields.Image"
          :key="image.id">
          <img :src="image.url" class="block" />
        </div>
      </div>
    </div>

  <nuxt-link to="/new-shop/" tag="button" class="bg-blue hover:bg-blue-dark text-white font-bold py-2 px-4 rounded-full mb-4 mx-auto block">
    Add New Shop
  </nuxt-link>

  </div>
</template>

<script>
import TheShopList from '@/components/TheShopList/TheShopList'

export default {
  head: {
    bodyAttrs: {
      class: 'bg-grey-lightest'
    }
  },
  components: {
    TheShopList
  },
  asyncData(context) {
    var app_id = 'appQYj69gppLZwlvn'
    var app_key = 'keyTiycvkXZLfi2WO'

    return context.$axios.$get(
      `https://api.airtable.com/v0/${app_id}/Shops?view=Grid%20view`,
      {
        headers: {
          Authorization: `Bearer ${app_key}`
        }
      }
    )
      .then(res => {
        var records = res.records
        return { records }
      })
      .catch(err => {
        console.log(err)
      })
  }
}
</script>

<style>

</style>
