1puncturewala/
│
├─ index.html
├─ customer.html
├─ mechanic.html
├─ contact.html
└─ assets/
   └─ logo.png
   <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>PunctureWala - Fast Repair, Anywhere in Morbi & Rajkot</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-50 text-gray-800">
  <!-- Header -->
  <header class="bg-white shadow-md">
    <div class="max-w-4xl mx-auto px-4 py-4 flex items-center">
      <img src="assets/logo.png" alt="PunctureWala" class="h-12 w-auto mr-3" />
      <div>
        <h1 class="text-2xl font-bold text-orange-600">PunctureWala</h1>
        <p class="text-sm text-gray-600">Fast Repair, Anywhere in Morbi & Rajkot</p>
      </div>
      <div class="ml-auto text-right">
        <a href="contact.html" class="text-sm text-gray-600 hover:text-orange-600">Contact</a>
      </div>
    </div>
  </header>

  <!-- Hero -->
  <main class="max-w-4xl mx-auto px-4 py-12 text-center">
    <h2 class="text-3xl font-semibold mb-4">Book a Puncture Mechanic in Minutes</h2>
    <p class="text-gray-600 mb-6">Select your role to get started — customers can book a mechanic quickly, mechanics can register to receive orders.</p>

    <div class="flex justify-center gap-4">
      <a href="customer.html" class="px-6 py-3 bg-orange-500 text-white rounded shadow">I am a Customer</a>
      <a href="mechanic.html" class="px-6 py-3 bg-black text-white rounded shadow">I am a Mechanic</a>
    </div>

    <section class="mt-10 bg-white rounded shadow p-6 text-left">
      <h3 class="font-semibold mb-2">Serving Cities</h3>
      <p>Morbi &amp; Rajkot</p>

      <div class="mt-4">
        <h3 class="font-semibold mb-2">How it works</h3>
        <ol class="list-decimal list-inside text-gray-700">
          <li>Customer fills booking form and presses Book Now.</li>
          <li>Booking opens WhatsApp to <strong>+91 9099911545</strong> with the booking details.</li>
          <li>Mechanic receives the message and reaches the customer location.</li>
        </ol>
      </div>
    </section>
  </main>

  <footer class="text-center py-6 text-gray-600">
    © <span id="year"></span> PunctureWala — Morbi & Rajkot
  </footer>

  <script>document.getElementById('year').innerText = new Date().getFullYear();</script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Book Mechanic - PunctureWala</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-50 text-gray-800">
  <header class="bg-white shadow">
    <div class="max-w-3xl mx-auto px-4 py-3 flex items-center">
      <a href="index.html"><img src="assets/logo.png" alt="PunctureWala" class="h-10 mr-3"></a>
      <h1 class="text-xl font-bold text-orange-600">Book a Mechanic</h1>
      <a href="contact.html" class="ml-auto text-sm text-gray-600">Contact</a>
    </div>
  </header>

  <main class="max-w-3xl mx-auto px-4 py-10">
    <div class="bg-white p-6 rounded shadow">
      <form id="bookingForm" onsubmit="submitBooking(event)" class="space-y-3">
        <div>
          <label class="block text-sm font-medium mb-1">Name</label>
          <input id="name" required class="w-full border p-2 rounded" placeholder="Your name">
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Mobile Number</label>
          <input id="mobile" type="tel" required class="w-full border p-2 rounded" placeholder="e.g. 90999xxxxx">
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">City</label>
          <select id="city" required class="w-full border p-2 rounded">
            <option value="">Select City</option>
            <option value="Morbi">Morbi</option>
            <option value="Rajkot">Rajkot</option>
          </select>
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Location / Landmark</label>
          <input id="location" required class="w-full border p-2 rounded" placeholder="Street, area or landmark">
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Vehicle Type</label>
          <select id="vehicle" required class="w-full border p-2 rounded">
            <option value="">Select Vehicle</option>
            <option>Car</option>
            <option>Bike</option>
            <option>Auto</option>
          </select>
        </div>

        <div class="flex gap-3">
          <button type="submit" class="bg-orange-500 text-white px-4 py-2 rounded">Book Now (WhatsApp)</button>
          <button type="button" onclick="fillTest()" class="bg-gray-200 px-4 py-2 rounded">Test Fill</button>
        </div>
      </form>

      <p class="mt-4 text-sm text-gray-600">After you press Book Now, WhatsApp will open with the booking message to our mechanic team.</p>
    </div>
  </main>

  <footer class="text-center py-6 text-gray-600">© <span id="yr"></span> PunctureWala</footer>

  <script>
    document.getElementById('yr').innerText = new Date().getFullYear();

    function submitBooking(e){
      e.preventDefault();
      const name = encodeURIComponent(document.getElementById('name').value.trim());
      const mobile = encodeURIComponent(document.getElementById('mobile').value.trim());
      const city = encodeURIComponent(document.getElementById('city').value);
      const location = encodeURIComponent(document.getElementById('location').value.trim());
      const vehicle = encodeURIComponent(document.getElementById('vehicle').value);

      const msg = `New Booking Request:%0AName: ${name}%0AMobile: ${mobile}%0ACity: ${city}%0ALocation: ${location}%0AVehicle: ${vehicle}`;
      const wa = '919099911545';
      window.open(`https://wa.me/${wa}?text=${msg}`, '_blank');
    }

    function fillTest(){
      document.getElementById('name').value = 'Test User';
      document.getElementById('mobile').value = '9099911545';
      document.getElementById('city').value = 'Morbi';
      document.getElementById('location').value = 'Near Bus Stand';
      document.getElementById('vehicle').value = 'Bike';
    }
  </script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Register as Mechanic - PunctureWala</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-50 text-gray-800">
  <header class="bg-white shadow">
    <div class="max-w-3xl mx-auto px-4 py-3 flex items-center">
      <a href="index.html"><img src="assets/logo.png" alt="PunctureWala" class="h-10 mr-3"></a>
      <h1 class="text-xl font-bold text-black">Mechanic Registration</h1>
      <a href="contact.html" class="ml-auto text-sm text-gray-600">Contact</a>
    </div>
  </header>

  <main class="max-w-3xl mx-auto px-4 py-10">
    <div class="bg-white p-6 rounded shadow">
      <form action="mailto:saurabhrathod454@gmail.com" method="POST" enctype="text/plain" class="space-y-3">
        <div>
          <label class="block text-sm font-medium mb-1">Full Name</label>
          <input name="Name" required class="w-full border p-2 rounded" placeholder="Your full name">
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Mobile Number</label>
          <input name="Mobile" type="tel" required class="w-full border p-2 rounded" placeholder="e.g. 90999xxxxx">
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">City</label>
          <select name="City" required class="w-full border p-2 rounded">
            <option value="">Select City</option>
            <option value="Morbi">Morbi</option>
            <option value="Rajkot">Rajkot</option>
          </select>
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Area / Landmark</label>
          <input name="Area" required class="w-full border p-2 rounded" placeholder="Shop area or landmark">
        </div>

        <div>
          <label class="block text-sm font-medium mb-1">Experience / Shop Details</label>
          <textarea name="Experience" required class="w-full border p-2 rounded" rows="4" placeholder="Works you do, tools available, timings, charges etc."></textarea>
        </div>

        <div class="flex gap-3">
          <button type="submit" class="bg-black text-white px-4 py-2 rounded">Register (Send Email)</button>
          <button type="reset" class="bg-gray-200 px-4 py-2 rounded">Reset</button>
        </div>
      </form>

      <p class="mt-4 text-sm text-gray-600">After you submit, we will contact you and add your shop to PunctureWala listings.</p>
    </div>
  </main>

  <footer class="text-center py-6 text-gray-600">© <span id="yrm"></span> PunctureWala</footer>
  <script>document.getElementById('yrm').innerText = new Date().getFullYear();</script>
</body>
</html>
