<template>
  <div class="landing-page">
   

    <section class="hero">
      <div class="hero-overlay">
        <h1>Supercharge Your Restaurant's Reviews!</h1>
        <p>Get more 5-star reviews with just a simple tap. Quick, easy, and effective!</p>
        <button @click="scrollToSignup">Order Now</button>
      </div>
    </section>
    
    <header class="header">
      <h1 class="title">Collect Reviews in Seconds</h1>
      <p class="subtitle">Say goodbye to complex review requests. It’s as easy as a tap with our NFC Cards!</p>
    </header>

    <h2 ref="signup" style="margin-top: 3rem; ">Available Cards</h2>
    <div class="services-section"  >
      <div class="services-container">
        
     
    <!-- Loop through the products array -->
    <div 
      v-for="(product, index) in products" 
      :key="index" 
      class="service-card itemCard product-card"
    >
      <div class="product-header">{{ product.name }}</div>
      <img :src="require(`@/assets/${product.image}`)" :alt="product.name" class="product-image"  />
      <div class="product-body">
        <p 
          class="product-description" 
          :class="{ 'truncated': !product.isDescriptionVisible }" 
          @click="toggleDescription(index)"
        >
          {{ product.description }}
        </p>
        <div class="product-price">AED {{ product.price }}</div> <!-- Price Section -->
        <button class="order-btn" @click="orderProduct(product.name)">Order Now</button>
      </div>
    
  </div>

        
      </div>
    </div>


    <h2>Why Our NFC Card is a Must-Have</h2>
    <div class="services-section">
      <div class="services-container">
        <div class="service-card">
  <div class="card-header">Free Delivery Included</div>
  <div class="card-body">
    Enjoy free delivery on every order—no extra charges. Get your NFC card delivered right to your door at no cost!
  </div>
</div>

        <div class="service-card">
          <div class="card-header">Instant Google Reviews</div>
          <div class="card-body">
            Customers can tap and leave a review instantly—no app required, no effort needed.
          </div>
        </div>
        <div class="service-card">
          <div class="card-header">Boost Your Reputation</div>
          <div class="card-body">
            A steady stream of positive reviews leads to higher rankings, making your restaurant more visible and attractive.
          </div>
        </div>
        <div class="service-card">
          <div class="card-header">Works on Any Smartphone</div>
          <div class="card-body">
            No downloads or complicated setups. Just tap the card and leave a review—works on any smartphone.
          </div>
        </div>
        
      </div>
    </div>

    

    <footer class="contact-info">
      <div class="contact-container">
        <div class="contact-item">
          <span><i class="fas fa-phone"></i></span> 
          <span class="info">+971 54 780 0635</span>
        </div>
        <div class="contact-item">
          <span><i class="fas fa-envelope"></i></span> 
          <span class="info">nfctechnology@gmail.com</span>
        </div>
      </div>
      <div class="footer-divider"></div>
      <h2 style="text-align: center; padding-top: 1rem;">About NFC Cards</h2>
      <div class="about" style="margin: auto; width: 100%;">
        <p>Our NFC cards are designed to simplify and enhance your online presence. By making it effortless for your customers to leave reviews, we help you attract more attention and increase your reputation with minimal effort.</p>
      </div>
      <div class="footer-links" style="margin: auto;">
        <p style="text-align: center; color: #E5B700;">© 2025 NFC Technology LTD. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>


<script>
export default {
  data() {
    return {
      isDescriptionVisible: false, 
      products: [
        {
          name: 'Plain NFC Card (best seller)',
          image: 'plain.png',
          description: 'Customers can tap and leave a review instantly—no app required, no effort needed.',
          price: '10',
          isDescriptionVisible: false,
        },
        {
          name: 'NFC + QR  Code Card',
          image: 'QR.png',
          description: 'A premium NFC card for your restaurant to gain more customer reviews effortlessly.',
          price: '19',
          isDescriptionVisible: false,
        },
        {
          name: 'NFC + QR + Brand Card',
          image: 'brand.png',
          description: 'A premium NFC card for your restaurant to gain more customer reviews effortlessly.',
          price: '24',
          isDescriptionVisible: false,
        },
        {
          name: 'NFC + Any Customization',
          image: 'creative.png',
          description: 'A premium NFC card for your restaurant to gain more customer reviews effortlessly.',
          price: '50',
          isDescriptionVisible: false,
        },
        // Add more products as needed
      ]
// Track description visibility
    };
  },
  
  methods: {
    orderProduct(productName) {
      const message = encodeURIComponent(`Hello, I'm interested in ordering the ${productName}.`);
      window.open(`https://wa.me/971547800635?text=${message}`, "_blank");
    },
    scrollToSignup() {
      this.$refs.signup.scrollIntoView({ behavior: 'smooth' });
    },
    toggleDescription(index) {
    this.products[index].isDescriptionVisible = !this.products[index].isDescriptionVisible;
    }
    
  },
  
 
    
};
</script>

<style scoped>

.landing-page {
  margin: -7px;
  font-family: 'Poppins', sans-serif;
  text-align: center;
  padding: 20px;
  background: #1E1E1E;
  color: #ffffff;
}
.hero {
  background: url('../assets/hero.jpg') center/cover no-repeat;
  height: 70vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  position: relative;
}
.hero-overlay {
  background: rgba(0, 0, 0, 0.7);
  padding: 40px;
  border-radius: 10px;
}
.hero h1 {
  font-size: 3em;
  font-weight: 700;
  margin-bottom: 15px;
}
.hero p {
  font-size: 1.4em;
  margin-bottom: 20px;
}
.hero button {
  background: #FFCC00;
  color: #1E1E1E;
  border: none;
  padding: 15px 30px;
  font-size: 1.2em;
  cursor: pointer;
  border-radius: 5px;
  font-weight: bold;
}
.hero button:hover {
  background: #E5B700;
}
.header {
  margin-top: 30px;
}
button {
  background: #FFCC00;
  color: #1E1E1E;
  font-weight: bold;
  transition: background 0.3s;
}
button:hover {
  background: #E5B700;
}
.contact-info {
  background: #222;
  padding: 20px;
  text-align: center;
  color: #FFCC00;
  margin-top: 30px;
  border-top: 3px solid #FFCC00;
}
.contact-container {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
}
.contact-item {
  display: flex;
  align-items: center;

  gap: 10px;
  font-size: 1.2em;
}

.about {
  margin-top: 20px;
  padding: 10px;
  font-size: 1em;
  color: #fff;
}
@media (max-width: 768px) {
  .contact-info {

   
    background: #1E1E1E;
    padding: 30px 15px;
    text-align: left;
    border-top: 1px solid rgba(255, 255, 255, 0.2);
    font-size: 14px;
    color: rgba(255, 255, 255, 0.7);
  }

  .contact-container {
    display: flex;
    flex-direction: column;
    gap: 10px;
  }

  .contact-item {
    display: flex;
    align-items: start;
    justify-content: start;
    gap: 8px;
    font-size: 0.9em;
  }

  .contact-item span {
    font-size: 1.2em;
    opacity: 0.7;
  }

  .contact-item .info{
    font-size: 1.2em;
    opacity: 0.7;
    margin-left: .3rem;

  }

  
  .about {
    margin-top: 20px;
    font-size: 0.8em;
    color: rgba(255, 255, 255, 0.6);
    max-width: 100%;
    padding:0 -10px;
    line-height: 1.5;
  }

  .footer-divider {
    width: 100%;
    height: 1px;
    background: rgba(255, 255, 255, 0.2);
    margin: 15px 0;
  }

  .footer-links {
    font-size: 0.8em;
    color: rgba(255, 255, 255, 0.5);
  }
}
/* Services Section */
.services-section {
    width: 100%;
   
  
}

/* Horizontal Scrollable Container */
.services-container {
    

    display: flex;
    
    overflow-x: auto; /* Enables horizontal scrolling */
    gap: 16px; /* Space between cards */
    scroll-snap-type: x mandatory;
    padding-bottom: 10px;
}

/* Hide Scrollbar */
.services-container::-webkit-scrollbar {
    display: none;
}

/* Service Card */
.service-card {

    flex-shrink: 0;
    width: 280px;
    border: 1px solid white;
     /* Orange background */
    color: #fff; /* White text */
    border-radius: 10px;
    padding: 15px;
    scroll-snap-align: start;
    margin-right: 1rem;
}

/* Card Header */
.card-header {
    background:  #E5B700; /* White background */
    color: #fff; /* Orange text */
    font-weight: bold;
    padding: 10px;
    border-radius: 8px;
    text-align: center;
    margin-bottom: 10px;
}

/* Card Body */
.card-body {
    font-size: 14px;
}

/* Responsive Scroll Effect */
@media (max-width: 768px) {
    .services-container {
        overflow-x: scroll;
    }
    .service-card{
      width: 230px;
    }

    /* Ensure next card is slightly visible */
    .service-card:nth-child(2) {
        margin-left: -3px;
    }
}
a{
  color: inherit;
 
}
i{
  color:#E5B700; ;
}

/* Container Styling */
.product-card {
  background: #ffffff; /* White background */
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  text-align: center;
  width: 60%;
  max-width: 320px;
  margin: auto;
  padding-top: 1.3rem;
  transition: transform 0.2s ease-in-out;
  border: 1px solid #ddd; /* Light gray border */
  
}

.product-card:hover {
  transform: translateY(5px);
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
}

/* Header */
.product-header {
  background: #000000; /* Black header */
  color: #ffffff; /* White text */
  font-size: 1.2rem;
  font-weight: 600;
  padding:12px;
  border-radius: 5px;
  border-bottom: 3px solid #E5B700; /* Yellow accent */
}

/* Image */
.product-image {
  width: 100%;
  height: 180px;
  border-radius: 4px;
  object-fit: cover;
  border-bottom: 1px solid #ddd; /* Subtle border under the image */
}

@media (min-width: 768px) {
  /* Adjust layout for tablets */
  .product-image{
    padding-top: 1.2rem;

  }
  }
/* Body */
.product-body {
  padding: 15px;
  text-align: center;
}

/* Description */
.product-description {
  font-size: 0.95rem;
  color: #333; /* Dark gray for readability */
  cursor: pointer;
  transition: all 0.3s ease;
}

.product-description.truncated {
  overflow: hidden;
  display: -webkit-box;
  -webkit-line-clamp: 2; /* Limits to 2 lines */
  -webkit-box-orient: vertical;
  text-overflow: ellipsis;
}

/* Price */
.product-price {
  font-size: 1.1rem;
  font-weight: 500;
  color: #333; /* Dark gray */
  margin-top: 12px;
  margin-bottom: 10px;
  text-align: center;
  opacity: 0.9;
}

/* Order Button */
.order-btn {
  background: #E5B700; /* Gold */
  color: #000000; /* Black text */
  font-size: 1rem;
  font-weight: 600;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  width: 100%;
  margin-top: 10px;
  transition: background 0.3s ease-in-out, transform 0.2s;
}

.order-btn:hover {
  background: #c9a000; /* Darker gold */
  transform: scale(1.05);
}


</style>
