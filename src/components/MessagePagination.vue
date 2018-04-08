<template>
  <div class="row">
    <div class="col-md-8">
       {{currentMessageIndex}} of {{totalNumberOfMessages}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'MessagePagination',
  data () {
    return {
            currentMessageIndex:  0,
            totalNumberOfMessages: 0
      }
    },
    created: function () {
                 console.log('pag');
                 this.$eventHub.$on('messageUpdate',  this.messageUpdateHandler);
              },
    methods: {
              messageUpdateHandler(currentMessageIndex, totalNumberOfMessages)
              {
                  this.currentMessageIndex = currentMessageIndex,
                  this.totalNumberOfMessages = totalNumberOfMessages,
                  console.log('messageUpdateHandler')
              }
    }
  }
</script>
