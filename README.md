<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Steph’s Drone & Revamping Services</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    function handleSubmit(event) {
      event.preventDefault();
      const form = event.target;
      const button = form.querySelector('button[type="submit"]');
      const originalText = button.innerHTML;
      button.disabled = true;
      button.innerHTML = 'Sending…';
      
      const data = new FormData(form);
      fetch(form.action, {
        method: form.method,
        body: data,
        headers: { 'Accept': 'application/json' }
      }).then(response => {
        if (response.ok) {
          window.location.href = 'thank-you.html';
        } else {
          alert('Oops! Something went wrong. Please try again.');
          button.disabled = false;
          button.innerHTML = originalText;
        }
      }).catch(() => {
        alert('Oops! There was a problem sending your message.');
        button.disabled = false;
        button.innerHTML = originalText;
      });
    }
  </script>
</head>
<body class="bg-gray-50 text-gray-800">

  <!-- Hero Section -->
  <section class="text-center py-20 bg-gradient-to-r from-blue-600 to-indigo-700 text-white">
    <h1 class="text-5xl font-bold mb-4">Steph’s Drone & Revamping Services</h1>
    <p class="text-lg mb-6">Professional Drone Shots • Property Revamps • Creative Visuals</p>
    <a href="#contact" class="px-6 py-3 bg-white text-blue-700 font-semibold rounded-lg shadow hover:bg-gray-200">Book Now</a>
  </section>

  <!-- Services Section -->
  <section id="services" class="py-16 px-6">
    <h2 class="text-3xl font-bold text-center mb-12">Our Services</h2>
    <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
      <div class="bg-white p-6 rounded-2xl shadow hover:scale-105 transition">
        <h3 class="text-xl font-semibold mb-2">Drone Photography & Videography</h3>
        <p>Stunning aerial shots for real estate, events, and landscapes.</p>
      </div>
      <div class="bg-white p-6 rounded-2xl shadow hover:scale-105 transition">
        <h3 class="text-xl font-semibold mb-2">Property Revamping</h3>
        <p>Transform spaces with modern styling, staging, and improvements.</p>
      </div>
      <div class="bg-white p-6 rounded-2xl shadow hover:scale-105 transition">
        <h3 class="text-xl font-semibold mb-2">Creative Projects</h3>
        <p>Custom visuals for social media, promotions, and special occasions.</p>
      </div>
    </div>
  </section>

  <!-- Reviews Section -->
  <section id="reviews" class="py-16 bg-gray-100 px-6">
    <h2 class="text-3xl font-bold text-center mb-12">What Clients Say</h2>
    <div class="max-w-3xl mx-auto space-y-6">
      <blockquote class="bg-white p-6 rounded-2xl shadow">“Amazing shots! My property never looked better.”</blockquote>
      <blockquote class="bg-white p-6 rounded-2xl shadow">“Professional and reliable service. Highly recommended!”</blockquote>
    </div>
  </section>

  <!-- About Section -->
  <section id="about" class="py-16 px-6">
    <h2 class="text-3xl font-bold text-center mb-12">About Us</h2>
    <div class="max-w-3xl mx-auto text-center">
      <p>At Steph’s Drone & Revamping Services, we specialize in delivering breathtaking aerial photography, stunning property transformations, and creative visuals that stand out. Our mission is to help clients showcase their properties and projects in the best light possible.</p>
    </div>
  </section>

  <!-- Contact Section -->
  <section id="contact" class="py-16 bg-gray-100 px-6">
    <h2 class="text-3xl font-bold text-center mb-12">Contact Us</h2>
    <div class="max-w-2xl mx-auto">
      <form action="https://formsubmit.co/stephsdronerevampingservices@gmail.com" method="POST" onsubmit="handleSubmit(event)" class="bg-white p-8 rounded-2xl shadow space-y-4">
        
        <!-- Hidden fields for redirect + spam protection -->
        <input type="hidden" name="_captcha" value="false">
        <input type="hidden" name="_next" value="thank-you.html">

        <input type="text" name="name" placeholder="Your Name" class="w-full p-3 border rounded-lg" required>
        <input type="email" name="email" placeholder="Your Email" class="w-full p-3 border rounded-lg" required>
        <textarea name="message" placeholder="Your Message" class="w-full p-3 border rounded-lg h-32" required></textarea>
        <button type="submit" class="w-full bg-blue-600 text-white py-3 rounded-lg font-semibold hover:bg-blue-700">Send Message</button>
      </form>
      <div class="text-center mt-6">
        <p>Email: <a href="mailto:stephsdronerevampingservices@gmail.com" class="text-blue-600">stephsdronerevampingservices@gmail.com</a></p>
        <p>Instagram: <a href="https://instagram.com/stephsdronerevampingservices" target="_blank" class="text-blue-600">@stephsdronerevampingservices</a></p>
      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer class="py-6 text-center bg-blue-700 text-white">
    <p>© 2025 Steph’s Drone & Revamping Services. All rights reserved.</p>
  </footer>

</body>
</html>
