# Montu
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Civilian Restaurant</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Outfit:wght@300;400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --bg: #1A1008;
  --surface: #241A0E;
  --surface2: #2E2010;
  --gold: #E8A020;
  --gold-light: #F5C660;
  --gold-dim: rgba(232,160,32,0.12);
  --red: #C0392B;
  --text: #F5EDD8;
  --muted: rgba(245,237,216,0.5);
  --border: rgba(232,160,32,0.25);
  --radius: 14px;
}

body {
  background: var(--bg);
  background-image:
    radial-gradient(ellipse 80% 60% at 50% -10%, rgba(232,160,32,0.08) 0%, transparent 70%),
    radial-gradient(ellipse 40% 40% at 90% 90%, rgba(192,57,43,0.06) 0%, transparent 60%);
  min-height: 100vh;
  font-family: 'Outfit', sans-serif;
  color: var(--text);
  padding: 2rem 1rem 4rem;
}

/* ── Header ── */
.hero {
  text-align: center;
  padding: 2.5rem 0 2rem;
  animation: fadeDown 0.8s ease both;
}
.hero-tag {
  display: inline-block;
  font-size: 11px;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: var(--gold);
  border: 1px solid var(--border);
  padding: 5px 18px;
  border-radius: 100px;
  margin-bottom: 1.2rem;
}
.hero h1 {
  font-family: 'Playfair Display', serif;
  font-size: clamp(2.8rem, 8vw, 5rem);
  font-weight: 700;
  line-height: 1;
  color: var(--text);
  letter-spacing: -0.01em;
}
.hero h1 span { color: var(--gold); font-style: italic; }
.hero-divider {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin: 1.5rem auto 0;
  max-width: 320px;
}
.hero-divider::before, .hero-divider::after {
  content: '';
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--border), transparent);
}
.hero-divider span { color: var(--gold); font-size: 18px; }
.welcome {
  font-family: 'Playfair Display', serif;
  font-style: italic;
  font-size: 1rem;
  color: var(--muted);
  margin-top: 0.75rem;
}

/* ── Card ── */
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 2rem;
  margin-bottom: 1.25rem;
  animation: fadeUp 0.7s ease both;
  position: relative;
  overflow: hidden;
}
.card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, var(--gold), transparent);
  opacity: 0.6;
}
.card:nth-child(2) { animation-delay: 0.1s; }
.card:nth-child(3) { animation-delay: 0.2s; }
.card:nth-child(4) { animation-delay: 0.3s; }
.card:nth-child(5) { animation-delay: 0.4s; }

.section-title {
  font-size: 11px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 1.5rem;
  display: flex;
  align-items: center;
  gap: 10px;
}
.section-title::after {
  content: '';
  flex: 1;
  height: 1px;
  background: var(--border);
}

/* ── Inputs ── */
.field-group { display: grid; gap: 1rem; }
.field-group.two { grid-template-columns: 1fr 1fr; }
@media (max-width: 500px) { .field-group.two { grid-template-columns: 1fr; } }

.field {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.field label {
  font-size: 12px;
  color: var(--muted);
  letter-spacing: 0.05em;
  font-weight: 500;
}
.field input, .field select {
  background: var(--surface2);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 12px 16px;
  color: var(--text);
  font-family: 'Outfit', sans-serif;
  font-size: 15px;
  outline: none;
  transition: border-color 0.2s, box-shadow 0.2s;
  -webkit-appearance: none;
  appearance: none;
}
.field input:focus, .field select:focus {
  border-color: var(--gold);
  box-shadow: 0 0 0 3px rgba(232,160,32,0.12);
}
.field input::placeholder { color: rgba(245,237,216,0.25); }
.field select { cursor: pointer; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='8' viewBox='0 0 12 8'%3E%3Cpath d='M1 1l5 5 5-5' stroke='%23E8A020' stroke-width='1.5' fill='none' stroke-linecap='round'/%3E%3C/svg%3E"); background-repeat: no-repeat; background-position: right 14px center; padding-right: 40px; }
.field select option { background: #241A0E; color: var(--text); }

/* ── Menu cards ── */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(130px, 1fr));
  gap: 10px;
}
.menu-item {
  position: relative;
  cursor: pointer;
}
.menu-item input[type="checkbox"] {
  position: absolute;
  opacity: 0;
  width: 0; height: 0;
}
.menu-label {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  padding: 14px 10px;
  background: var(--surface2);
  border: 1px solid var(--border);
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s;
  text-align: center;
}
.menu-label:hover {
  border-color: rgba(232,160,32,0.5);
  background: rgba(232,160,32,0.06);
}
.menu-item input:checked + .menu-label {
  border-color: var(--gold);
  background: var(--gold-dim);
  box-shadow: 0 0 0 2px rgba(232,160,32,0.2);
}
.menu-item input:checked + .menu-label .menu-icon { transform: scale(1.15); }
.menu-icon { font-size: 28px; transition: transform 0.2s; }
.menu-name { font-size: 12px; font-weight: 500; color: var(--text); }
.menu-price { font-size: 11px; color: var(--gold); }
.menu-check {
  position: absolute;
  top: 7px; right: 7px;
  width: 18px; height: 18px;
  background: var(--gold);
  border-radius: 50%;
  display: none;
  align-items: center;
  justify-content: center;
}
.menu-item input:checked ~ .menu-check { display: flex; }
.menu-check svg { width: 10px; height: 10px; }

/* ── Quantity ── */
.qty-control {
  display: flex;
  align-items: center;
  gap: 0;
  background: var(--surface2);
  border: 1px solid var(--border);
  border-radius: 10px;
  overflow: hidden;
  width: fit-content;
}
.qty-btn {
  width: 42px; height: 42px;
  background: none;
  border: none;
  color: var(--gold);
  font-size: 22px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.15s;
  font-weight: 300;
}
.qty-btn:hover { background: var(--gold-dim); }
.qty-num {
  min-width: 40px;
  text-align: center;
  font-size: 16px;
  font-weight: 500;
  color: var(--text);
  border-left: 1px solid var(--border);
  border-right: 1px solid var(--border);
  padding: 0 8px;
  line-height: 42px;
}

/* ── Payment ── */
.payment-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
@media (max-width: 500px) { .payment-grid { grid-template-columns: 1fr; } }
.pay-option { position: relative; }
.pay-option input { position: absolute; opacity: 0; width: 0; height: 0; }
.pay-label {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  padding: 14px 8px;
  border: 1px solid var(--border);
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.2s;
  text-align: center;
  position: relative;
}
.pay-label:hover:not(.disabled) { border-color: rgba(232,160,32,0.5); }
.pay-label.disabled { opacity: 0.35; cursor: not-allowed; }
.pay-option input:checked + .pay-label { border-color: var(--gold); background: var(--gold-dim); }
.pay-icon { font-size: 24px; }
.pay-name { font-size: 12px; font-weight: 500; }
.pay-badge {
  font-size: 9px;
  padding: 2px 8px;
  border-radius: 100px;
  letter-spacing: 0.06em;
  font-weight: 500;
}
.pay-badge.available { background: rgba(40,167,69,0.2); color: #5dca7e; }
.pay-badge.unavailable { background: rgba(200,200,200,0.1); color: rgba(245,237,216,0.3); }

/* ── Submit ── */
.submit-btn {
  width: 100%;
  padding: 16px;
  background: var(--gold);
  border: none;
  border-radius: 12px;
  color: #1A1008;
  font-family: 'Outfit', sans-serif;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  letter-spacing: 0.03em;
  transition: all 0.2s;
  position: relative;
  overflow: hidden;
  margin-top: 0.5rem;
}
.submit-btn:hover { background: var(--gold-light); transform: translateY(-1px); box-shadow: 0 8px 24px rgba(232,160,32,0.3); }
.submit-btn:active { transform: translateY(0); }
.submit-btn::after {
  content: '';
  position: absolute;
  inset: 0;
  background: linear-gradient(120deg, transparent 30%, rgba(255,255,255,0.2) 50%, transparent 70%);
  transform: translateX(-100%);
  transition: transform 0.5s;
}
.submit-btn:hover::after { transform: translateX(100%); }

/* ── Success toast ── */
.toast {
  display: none;
  position: fixed;
  bottom: 2rem; left: 50%;
  transform: translateX(-50%) translateY(20px);
  background: #1a3a1a;
  border: 1px solid rgba(93,202,126,0.4);
  color: #5dca7e;
  padding: 14px 28px;
  border-radius: 100px;
  font-size: 14px;
  font-weight: 500;
  z-index: 999;
  animation: toastIn 0.4s ease forwards;
}
@keyframes toastIn { to { transform: translateX(-50%) translateY(0); opacity: 1; } }

/* ── Animations ── */
@keyframes fadeDown { from { opacity:0; transform:translateY(-20px); } to { opacity:1; transform:translateY(0); } }
@keyframes fadeUp { from { opacity:0; transform:translateY(24px); } to { opacity:1; transform:translateY(0); } }

.wrap { max-width: 580px; margin: 0 auto; }
</style>
</head>
<body>
    
<!--<form action="https://formspree.io/f/mlgpaely" method="POST">-->

<div class="wrap">

  <!-- Hero -->
  <div class="hero">
    <div class="hero-tag">scince 1990</div>
    <h1>Civilian<br><span>Restaurant</span></h1>
    <div class="hero-divider"><span>✦</span></div>
    <p class="welcome">&#10024; Welcome to all of you — order fresh, eat happy &#10024;<br></br></p>
    
  </div>

  <!-- Personal Info -->
  <div class="card">
    <div class="section-title">Your Details</div>
    <div class="field-group">
      <div class="field">
        <label for="name">Full Name</label>
        <input type="text" id="name" name="name" placeholder="enter your name">
      </div>
      <div class="field">
        <label for="mobile">Mobile Number</label>
        <input type="tel" id="mobile" name="mobile" placeholder="+91XXXXXXXXXX" maxlength="10">
      </div>
    </div>
  </div>

  <!-- Address -->
  <div class="card">
    <div class="section-title">Delivery Address</div>
    <div class="field-group">
      <div class="field">
        <label for="flat">Flat / Apartment</label>
        <input type="text" id="flat" name="flat" placeholder="flat/Apartment">
      </div>
      <div class="field">
        <label for="street">Street / Area</label>
        <input type="text" id="street" name="street" placeholder="street/Area">
      </div>
      <div class="field-group two">
        <div class="field">
          <label for="city">City</label>
          <input type="text" id="city" name="city" placeholder="city name">
        </div>
        <div class="field">
          <label for="state">State</label>
          <input type="text" id="state" name="state" placeholder="--state name--">
        </div>
      </div>
      <div class="field">
        <label for="pincode">Pincode</label>
        <input type="number" id="pincode" name="pincode" placeholder="Enter pincode" maxlength="6">
      </div>
    </div>
  </div>

  <!-- Menu -->
  <div class="card">
    <div class="section-title">Choose Your Order</div>
    <div class="menu-grid">

      <div class="menu-item">
        <input type="checkbox" id="m-tea" name="menu" value="Tea">
        <label class="menu-label" for="m-tea">
          <span class="menu-icon">☕</span>
          <span class="menu-name">Chai</span>
          <span class="menu-price">₹15</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-coffee" name="menu" value="Coffee">
        <label class="menu-label" for="m-coffee">
          <span class="menu-icon">🍵</span>
          <span class="menu-name">Coffee</span>
          <span class="menu-price">₹20</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-vadapav" name="menu" value="Vada Pav">
        <label class="menu-label" for="m-vadapav">
          <span class="menu-icon">🍔</span>
          <span class="menu-name">Vada Pav</span>
          <span class="menu-price">₹30</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-momos" name="menu" value="Momos">
        <label class="menu-label" for="m-momos">
          <span class="menu-icon">🥟</span>
          <span class="menu-name">Momos</span>
          <span class="menu-price">₹60</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-samosa" name="menu" value="Samosa">
        <label class="menu-label" for="m-samosa">
          <span class="menu-icon">🔺</span>
          <span class="menu-name">Samosa</span>
          <span class="menu-price">₹15</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-vegthali" name="menu" value="Veg Thali">
        <label class="menu-label" for="m-vegthali">
          <span class="menu-icon">🍛</span>
          <span class="menu-name">Veg Thali</span>
          <span class="menu-price">₹120</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-nonveg" name="menu" value="Non Veg Thali">
        <label class="menu-label" for="m-nonveg">
          <span class="menu-icon">🍗</span>
          <span class="menu-name">Non-Veg Thali</span>
          <span class="menu-price">₹160</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-daal" name="menu" value="Daal Chawal">
        <label class="menu-label" for="m-daal">
          <span class="menu-icon">🥘</span>
          <span class="menu-name">Daal Chawal</span>
          <span class="menu-price">₹80</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

      <div class="menu-item">
        <input type="checkbox" id="m-roti" name="menu" value="Roti/Chapati">
        <label class="menu-label" for="m-roti">
          <span class="menu-icon">🫓</span>
          <span class="menu-name">Roti / Chapati</span>
          <span class="menu-price">₹10</span>
        </label>
        <div class="menu-check"><svg viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-5" stroke="#1A1008" stroke-width="1.5" stroke-linecap="round"/></svg></div>
      </div>

    </div>

    <!-- Quantity -->
    <div style="margin-top:1.5rem;">
      <div class="section-title" style="margin-bottom:1rem;">Quantity</div>
      <div class="qty-control">
        <button class="qty-btn" id="qty-minus">−</button>
        <div class="qty-num" id="qty-display">1</div>
        <button class="qty-btn" id="qty-plus">+</button>
      </div>
    </div>
  </div>

  <!-- Payment -->
  <div class="card">
    <div class="section-title">Payment Method</div>
    <div class="payment-grid">

      <div class="pay-option">
        <input type="radio" name="payment" id="cod" value="Cash on Delivery" checked>
        <label class="pay-label" for="cod">
          <span class="pay-icon">💵</span>
          <span class="pay-name">Cash on Delivery</span>
          <span class="pay-badge available">Available</span>
        </label>
      </div>

      <div class="pay-option">
        <input type="radio" name="payment" id="netbanking" value="Net Banking" disabled>
        <label class="pay-label disabled" for="netbanking">
          <span class="pay-icon">🏦</span>
          <span class="pay-name">Net Banking</span>
          <span class="pay-badge unavailable">Coming Soon</span>
        </label>
      </div>

      <div class="pay-option">
        <input type="radio" name="payment" id="card" value="Credit/Debit Card" disabled>
        <label class="pay-label disabled" for="card">
          <span class="pay-icon">💳</span>
          <span class="pay-name">Card</span>
          <span class="pay-badge unavailable">Coming Soon</span>
        </label>
      </div>

    </div>
  </div>

  <!-- Submit -->
  <div class="card" style="animation-delay:1s">
    <button class="submit-btn" id="submit-btn" onclick="placeOrder()" action="https://www.google.com">
      Place Order →
    </button>
  </div>

</div>
<h3 align="center"><i>&#10024; created by montoo jatav &#10024;</i></h3>

<div class="toast" id="toast">✓ Order placed successfully! We'll deliver soon.</div>
</form>   

<script>
  let qty = 1;
  document.getElementById('qty-minus').addEventListener('click', () => {
    if (qty > 1) { qty--; document.getElementById('qty-display').textContent = qty; }
  });
  document.getElementById('qty-plus').addEventListener('click', () => {
    qty++;
    document.getElementById('qty-display').textContent = qty;
  });

  function placeOrder() {
    const name = document.getElementById('name').value.trim();
    const mobile = document.getElementById('mobile').value.trim();
    const items = [...document.querySelectorAll('input[name="menu"]:checked')].map(el => el.value);

    if (!name || !mobile || items.length === 0) {
      document.getElementById('submit-btn').style.background = '#C0392B';
      document.getElementById('submit-btn').textContent = 'Please fill name, mobile & select an item!';
      setTimeout(() => {
        document.getElementById('submit-btn').style.background = '';
        document.getElementById('submit-btn').textContent = 'Place Order →';
      }, 2500);
      return;
    }

    const toast = document.getElementById('toast');
    toast.style.display = 'block';
    setTimeout(() => { toast.style.display = 'none'; }, 3500);
  }
</script>

</body>
</html>
