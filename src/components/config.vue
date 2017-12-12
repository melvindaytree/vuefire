<script>

  // This line is new!
  import Firebase from 'firebase'

  /*
   * The config was copied and pasted straight from the Firebase Dashboard.
   * Simply click "Add Firebase to Your Web App" to access yours.
   */

  let config = {
    apiKey: 'AIzaSyCM9WGU4G-CjkZZmBGUlM8F0ZVG6MPI0KI',
    authDomain: 'vuejs-f6a57.firebaseapp.com',
    databaseURL: 'https://vuejs-f6a57.firebaseio.com',
    projectId: 'vuejs-f6a57',
    storageBucket: 'vuejs-f6a57.appspot.com',
    messagingSenderId: '221000683687'
  }

  // Here we are initializing the Firebase connection.
  let app = Firebase.initializeApp(config)
  let db = app.database()

  // Accessing the greetings reference; .ref() takes a URL as its parameter.
  let vueRef = db.ref('items')

  export default {
    name: 'config',

    firebase: {
      items: vueRef
    }
  }
</script>