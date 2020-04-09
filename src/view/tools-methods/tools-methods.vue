<template>
  <div>
    <Card shadow>
      <Row>
        <i-col span="4">
          <Button @click="createTagParams">Add Label</Button>
        </i-col>
        <i-col span="20">
          <p>Dynamic Router</p>
        </i-col>
      </Row>
    </Card>
    <Card shadow style="margin-top: 10px;">
      <Row>
        <i-col span="4">
          <Button @click="createTagQuery">Add a Label</Button>
        </i-col>
        <i-col span="20">
          <p>Dynamic Router</p>
        </i-col>
      </Row>
    </Card>
    <Card shadow style="margin-top: 10px;">
      <Row>
        <i-col span="4">
          <Button @click="handleCloseTag">Close</Button>
        </i-col>
        <i-col span="20">
          <p>Manual Close</p>
        </i-col>
      </Row>
    </Card>
  </div>
</template>

<script>
import { mapMutations } from 'vuex'
export default {
  name: 'tools_methods_page',
  methods: {
    ...mapMutations([
      'closeTag'
    ]),
    createTagParams () {
      const id = parseInt(Math.random() * 100000)
      const route = {
        name: 'params',
        params: {
          id
        },
        meta: {
          title: `动态路由-${id}`
        }
      }
      this.$router.push(route)
    },
    createTagQuery () {
      const id = parseInt(Math.random() * 100000)
      const route = {
        name: 'query',
        query: {
          id
        },
        meta: {
          title: `参数-${id}`
        }
      }
      this.$router.push(route)
    },
    handleCloseTag () {
      this.closeTag({
        name: 'tools_methods_page'
      })
    }
  }
}
</script>

<style>

</style>
