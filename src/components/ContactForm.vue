<template>
    <div class="container">
        <form @submit.prevent="sendEmail">
          <label>Name</label>
          <input 
            type="text" 
            v-model="name"
            name="name"
            placeholder="Your Name"
          >
          <label>Phone Number</label>
          <input 
            type="number" 
            v-model="number"
            name="number"
            placeholder="Your Mobile Number"
            >
            
          <label>Email</label>
          <input 
            type="email" 
            v-model="email"
            name="email"
            placeholder="Your Email"
            >
          <label>Message</label>
          <textarea 
            name="message"
            v-model="message"
            cols="30" rows="5"
            placeholder="Message">
          </textarea>
          
          <input type="submit" value="Send"  >
        </form>
    </div>
</template>

<script>
 
    import emailjs from 'emailjs-com';
    export default {
      data() {
    return {
      name: '',    // Define name property in the data option
      number: '',  // Define number property in the data option
      email: '',   // Define email property in the data option
      message: ''  // Define message property in the data option
    };
  },
        
        mounted() {
    // Initialize EmailJS with your public key
    emailjs.init('WpKtim6_gHYTg9w7u');
  },
  methods: {
    sendEmail() {
      console.log('Sending email...');
      // Define template parameters
      const templateParams = {
        name: this.name,
        number: this.number,
        email: this.email,
        message: this.message
      };

      // Send email using EmailJS
      emailjs.send('service_df8e9ji', 'template_zko7iy7', templateParams)
        .then((response) => {
          console.log('Email sent successfully:', response);
          // Handle success, e.g., show a success message
        })
        .catch((error) => {
          console.error('Email sending failed:', error);
          // Handle error, e.g., show an error message
        });
    }
  }
    
    }
</script>


<style scoped>
* {box-sizing: border-box;}

.container {
  display: block;
  margin:auto;
  text-align: center;
  border-radius: 5px;
  background-color: darkgrey;
  padding: 20px;
  
}

label {
  float: left;
}

input[type=text], [type=email],[type=number], textarea {
  width: 100%;
  padding: 12px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  margin-top: 6px;
  margin-bottom: 16px;
  resize: vertical;
}

input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
</style>
