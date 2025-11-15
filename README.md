<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Glo C.C. — Beauty Salon (Improved JS)</title>
  <style>
    :root {
      --pink: #eabbbb;
      --green: #9fd1a5;
      --accent: #f3e5e5;
      --text: #222;
    }

    body { margin:0; font-family:Arial; }
    header { display:flex; justify-content:space-between; padding:20px 60px; border-bottom:1px solid #eee; }
    nav ul { list-style:none; display:flex; gap:30px; padding:0; }
    nav a { text-decoration:none; color:#000; }

    .services { text-align:center; padding:40px; }
    .cards { display:flex; justify-content:center; flex-wrap:wrap; gap:25px; }
    .card { width:200px; text-align:center; cursor:pointer; }
    .card img { width:200px; height:220px; object-fit:cover; border-radius:6px; transition:.3s; }

    .hidden { display:none !important; }

    footer { padding:20px 60px; background:#f7f7f7; text-align:center; }
    .contact-btn { padding:12px 20px; background:var(--pink); color:#fff; border:none; cursor:pointer; border-radius:6px; }
  </style>
</head>
<body>

<header>
  <div class="logo">Glo C.C.</div>
  <nav>
    <ul>
      <li><a href="#">Services</a></li>
      <li><a href="#">About</a></li>
    </ul>
  </nav>
  <div class="search-icon" id="searchIcon">🔍</div>
</header>

<section class="services">
  <h2>Choose Your Services:</h2>
  <label>
    <span>Woman</span>
    <input type="checkbox" id="genderToggle" />
    <span>Man</span>
  </label>

  <div class="cards" id="serviceCards">
    <div class="card woman"><img src="https://via.placeholder.com/200x220?text=Hair"/><p>Hair</p></div>
    <div class="card woman"><img src="https://via.placeholder.com/200x220?text=Makeup"/><p>Makeup</p></div>
    <div class="card woman"><img src="https://via.placeholder.com/200x220?text=Nails"/><p>Nail Service</p></div>
    <div class="card man hidden"><img src="https://via.placeholder.com/200x220?text=Hair+Men"/><p>Men Hair</p></div>
    <div class="card man hidden"><img src="https://via.placeholder.com/200x220?text=Beard"/><p>Beard</p></div>
  </div>
</section>

<footer>
  <button class="contact-btn" id="questionBtn">Have a question?</button>
</footer>

<script>
  // ALERT + CONFIRM + PROMPT
  document.getElementById("questionBtn").addEventListener("click", function () {
    const ask = confirm("Would you like to contact the salon?");
    if (ask) alert("Call us: +380 779 856 7432");
  });

  // SEARCH ICON
  document.getElementById("searchIcon").addEventListener("click", function () {
    const search = prompt("Search for a service:");
    if (!search) return;

    const cards = document.querySelectorAll(".card p");
    let found = false;

    cards.forEach((el) => {
      if (el.textContent.toLowerCase().includes(search.toLowerCase())) found = true;
    });

    alert(found ? "Service found!" : "No such service.");
  });

  // TOGGLE WOMAN / MAN
  const toggle = document.getElementById("genderToggle");
  const womanCards = document.querySelectorAll(".card.woman");
  const manCards = document.querySelectorAll(".card.man");

  toggle.addEventListener("change", () => {
    if (toggle.checked) {
      womanCards.forEach(c => c.classList.add("hidden"));
      manCards.forEach(c => c.classList.remove("hidden"));
    } else {
      womanCards.forEach(c => c.classList.remove("hidden"));
      manCards.forEach(c => c.classList.add("hidden"));
    }
  });
</script>

</body>
</html>
