<template>
  <div>
    <Card>
      <iview-admin> Title text
        </iview-admin>    
        </Card>
    <Card style="margin-top: 20px;">
      <Row>
        <i-col span="8">
          <Button @click="click" style="display: block">Test error trigger</Button>
          <Button @click="ajaxClick" style="margin-top:10px;">Test tirgger error</Button>
        </i-col>
        <i-col span="16">
          ajaxRequest 
        </i-col>
      </Row>
    </Card>
  </div>
</template>

<script>
import { errorReq } from '@/api/data'
export default {
  name: 'error_store_page',
  methods: {
    click () {
      console.log(admin)
    },
    ajaxClick () {
      errorReq()
    }
  }
}
</script>

<style>

</style>
