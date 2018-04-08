<template>
  <div class="container">

    <!-- Portfolio Item Heading -->
    <h2 class="my-4">
      <!--[BULK] PO 92803 - RUSH W/ PROOF 102197023-->
      <small>{{messages[currentMessageIndex].subject}}</small>
    </h2>

    <!-- Portfolio Item Row -->
    <div class="row">
      <div class="col-md-8">
        <img width="1075" height="450"  v-bind:src="messages[currentMessageIndex].selectedImage" />
      </div>
    </div>

    <!-- Related Projects Row -->
    <h3 class="my-4"></h3>

    <div class="row">
        <div v-for='image in messages[currentMessageIndex].images'>
        <div class="col-md-3 col-sm-6 mb-4">
            <a v-on:click='toggleImage(image)' >
              <img type="text/html"
               style="overflow: hidden; width: 250px; height: 150px"
               v-bind:src="image" />
            </a>
        </div>
        </div>
    </div>
    <div class="row">
    <div class="col-md-3 col-sm-6 mb-4">
      <div class="btn-group">
        <button type="button" class="btn btn-primary" v-on:click='deleteMessage()'>Indexing</button>
        <button type="button" class="btn btn-primary" v-on:click='deleteMessage()'>Clarifications</button>
        <button type="button" class="btn btn-primary" v-on:click='pickNextMessage()'>Next</button>
      </div>
    </div>
    </div>

    <div class="row">
      <div class="col-md-8">

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Messages',
  data () {
    return {
            pageTitle: 'Message List',
            currentMessageIndex:  0,
            messages: [
              {
              "messageId": 1,
              "from": "Norwood Orders",
              "subject": "Purchase Order 1",
              "received": "GDN-0023",
              "selectedImage": "http://dinara.me/wp-content/uploads/2017/08/format-of-invoice-bill-in-excel-rental-invoice-billing-statement-template-travel-bill-format-in-excel-download.jpg",
              "images":
              ["http://dinara.me/wp-content/uploads/2017/08/format-of-invoice-bill-in-excel-rental-invoice-billing-statement-template-travel-bill-format-in-excel-download.jpg",
               "https://www.purchasecontrol.com/wp-content/uploads/2017/08/Example-PO-1.png",
               "http://www.charlapuryear.com/wp-content/uploads/discount1gif-invoice-with-discount.gif",
               "https://www.purchasecontrol.com/wp-content/uploads/2017/08/Example-Invoice.png"]
              },
              {
              "messageId": 2,
              "from": "Bruce Mincus",
              "subject": "Purchase Order 2",
              "received": "Wed 03/22/2018 10:24 AM",
              "selectedImage": "http://dinara.me/wp-content/uploads/2017/08/format-of-invoice-bill-in-excel-rental-invoice-billing-statement-template-travel-bill-format-in-excel-download.jpg",
              "images":
              ["http://dinara.me/wp-content/uploads/2017/08/format-of-invoice-bill-in-excel-rental-invoice-billing-statement-template-travel-bill-format-in-excel-download.jpg",
               "https://www.purchasecontrol.com/wp-content/uploads/2017/08/Example-PO-1.png",
               "http://www.charlapuryear.com/wp-content/uploads/discount1gif-invoice-with-discount.gif",
               "https://www.purchasecontrol.com/wp-content/uploads/2017/08/Example-Invoice.png"]
              },
              {
              "messageId": 3,
              "from": "Bruce Mincus",
              "subject": "Purchase Order 3",
              "received": "Wed 03/22/2018 10:24 AM",
              "selectedImage": "http://dinara.me/wp-content/uploads/2017/08/format-of-invoice-bill-in-excel-rental-invoice-billing-statement-template-travel-bill-format-in-excel-download.jpg",
              "images":
              ["http://dinara.me/wp-content/uploads/2017/08/format-of-invoice-bill-in-excel-rental-invoice-billing-statement-template-travel-bill-format-in-excel-download.jpg",
               "https://www.purchasecontrol.com/wp-content/uploads/2017/08/Example-PO-1.png",
               "http://www.charlapuryear.com/wp-content/uploads/discount1gif-invoice-with-discount.gif",
               "https://www.purchasecontrol.com/wp-content/uploads/2017/08/Example-Invoice.png"]
              }
              ]
      }
    },
    created: function () {
          console.log('mes-'+(this.currentMessageIndex+1)+'-'+this.messages.length);
          this.$eventHub.$emit('messageUpdate', (this.currentMessageIndex+1), this.messages.length);
    },
    methods: {
        toggleImage: function (image) {
          console.log('1');
          this.messages[this.currentMessageIndex].selectedImage = image
        },
        deleteMessage: function () {
           console.log('2');
           if(this.messages != null && this.messages.length > 0)
           {
               this.messages.splice(this.currentMessageIndex, 1);
               console.log(this.messages);
               this.currentMessageIndex = this.currentMessageIndex - 1;
               this.pickNextMessage();
           }
        },
        pickNextMessage: function () {
           console.log('3');
           console.log('Index-'+this.currentMessageIndex);
           console.log(this.messages);
           if(this.messages != null && this.messages.length >  (this.currentMessageIndex+1))
           {
                 this.currentMessageIndex = this.currentMessageIndex+1;
                 console.log('1');
           }else if(this.messages != null && this.messages.length === (this.currentMessageIndex+1))
           {
                 this.currentMessageIndex = 0;
                 console.log('2');
           }
           console.log('After Index-'+this.currentMessageIndex);
           this.$eventHub.$emit('messageUpdate', this.currentMessageIndex+1, this.messages.length);
        }
    }
  }
</script>
