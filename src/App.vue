<template>
  <div id="app">
  		<head>
  			<meta charset="utf-8">
  			<meta name="viewport"
  				content="width=device-width, initial-scale=1, shrink-to-fit=no">
  			<meta name="description" content="Bic Order Indexing project">
  			<meta name="author" content="">

  			<title>BIC Graphic Order Indexing</title>

  		</head>

  		<!-- Navigation -->
  		<body>
  			   <Header> </Header>
           <Messages> </Messages>
           <MessagePagination> </MessagePagination>
           <Footer> </Footer>
  		</body>
  </div>
</template>

<script>
  import Header from './components/Header'
  import Footer from './components/Footer'
  import Messages from './components/Messages'
  import MessagePagination from './components/MessagePagination'
  export default {
    name: 'App',
    components: {
           Header,
           Footer,
           Messages,
           MessagePagination
    }
  }
</script>

<style>


</style>
