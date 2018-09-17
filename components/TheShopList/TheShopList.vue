<template>
  <div>
  </div>
</template>

<script>
export default {
  // async asyncData({ app }) {
  //   var self = this
  //   var app_id = 'appQYj69gppLZwlvn'
  //   var app_key = 'keyTiycvkXZLfi2WO'
  //   const list = await app.$axios.$get(
  //     `https://api.airtable.com/v0/${app_id}/Menu?view=Grid%20view`,
  //     {
  //       headers: {
  //         Authorization: `Bearer ${app_key}`
  //       }
  //     }
  //   )
  //   .then(function(response){
  //     console.log(response.data.records)
  //   })
  //   .catch(function(error){
  //     console.log(error)
  //   })

  //   return {
  //     list
  //   }
  // },
  asyncData(context) {
    return context.$axios.$get('http://icanhazip.com')
      .then(res => {
        console.log(res)
      })
      .catch(err => {
        console.log(err)
      })
  }
}
</script>

