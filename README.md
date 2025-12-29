<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Foodies Delight</title>

<!-- Bootstrap CSS -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
<!-- Bootstrap JS -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>

<style>
body{
  font-family: Arial;
  background:#f4f4f4;
  scroll-behavior: smooth;
}

.navbar{
  background:#111;
}

.navbar-brand{
  font-weight:bold;
  color:#f8a32f !important;
}

.hero{
  background:linear-gradient(to right,#210d16,#b82869,#e50914);
  color:white;
  padding:80px 20px;
  text-align:center;
}

.menu{
  background:#111;
  color:white;
  padding:40px;
}

.menu-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:20px;
}

.card{
  background:#222;
  border:none;
  border-radius:12px;
  color:white;
}

.card img{
  height:160px;
  object-fit:cover;
  border-radius:12px 12px 0 0;
}

.price{
  color:#f8a32f;
  font-weight:bold;
}

.order-section{
  padding:40px;
}

.about,.contact{
  padding:50px;
  background:white;
}

.contact input,.contact textarea{
  margin-bottom:10px;
}

footer{
  background:#111;
  color:white;
  text-align:center;
  padding:10px;
}
</style>
</head>
<body>

<!-- NAVBAR -->
<nav class="navbar navbar-expand-lg navbar-dark fixed-top">
  <div class="container">
    <a class="navbar-brand" href="#">🍴 Foodies Delight</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navMenu">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navMenu">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link" href="#menu">Menu</a></li>
        <li class="nav-item"><a class="nav-link" href="#order">Order</a></li>
        <li class="nav-item"><a class="nav-link" href="#about">About</a></li>
        <li class="nav-item"><a class="nav-link" href="#contact">Contact</a></li>
      </ul>
    </div>
  </div>
</nav>

<!-- SPACE FOR FIXED NAVBAR -->
<div style="margin-top:70px"></div>

<!-- HERO -->
<section class="hero">
  <h1>Delicious Food Delivered</h1>
  <p>Fresh • Tasty • Fast</p>
  <a href="#menu" class="btn btn-warning">Explore Menu</a>
</section>

<!-- MENU -->
<section class="menu" id="menu">
  <div class="container">
    <h2 class="text-center mb-4">Our Menu</h2>
    <div class="menu-grid" id="menuItems"></div>
  </div>
</section>

<!-- ORDER -->
<section class="order-section" id="order">
  <div class="container">
    <h2 class="text-center mb-3">Place Your Order</h2>
    <div class="card p-3">
      <form id="orderForm">
        <input class="form-control mb-2" id="custName" placeholder="Your Name" required>
        <input class="form-control mb-2" id="custPhone" placeholder="Phone Number" required>

        <select class="form-control mb-2" id="dishSelect" required></select>

        <input type="number" class="form-control mb-2" id="qty" value="1" min="1">

        <select class="form-control mb-3" id="payment">
          <option>Cash on Delivery</option>
          <option>UPI</option>
        </select>

        <button class="btn btn-warning w-100">Confirm Order</button>
      </form>
    </div>

    <div class="mt-4">
      <h4>Your Orders</h4>
      <div id="orderList"></div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="about">
  <div class="container">
    <h2 class="text-center mb-3">About Us</h2>
    <p class="text-center">
      Foodies Delight is your one-stop destination for delicious and hygienic food.
      We serve fresh meals made with quality ingredients at affordable prices.
      Our mission is to deliver happiness with every bite 🍕🍔
    </p>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="container">
    <h2 class="text-center mb-3">Contact Us</h2>
    <div class="row justify-content-center">
      <div class="col-md-6">
        <form>
          <input class="form-control" placeholder="Your Name">
          <input class="form-control" placeholder="Email">
          <textarea class="form-control" rows="4" placeholder="Message"></textarea>
          <button class="btn btn-warning w-100 mt-2">Send Message</button>
        </form>
        <p class="text-center mt-3">
          📞 9687345180 <br>
          📍 Jamnagar, Gujarat
        </p>
      </div>
    </div>
  </div>
</section>

<footer>
  © 2025 Foodies Delight
</footer>

<script>
// Dishes data
const dishes=[
{name:"Pizza",price:100,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR2l4NgkA2M9hpqOCRADV7hgi3Lex8ekEKgb9OAvHvj6G8s7IaCInRnCJY&s=10"},
{name:"Burger",price:99,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRiHbhLJm2TwhwpqsRiXZBW30goUSjGAYHXZG2IciTRXw&s=10"},
{name:"Dosa",price:80,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTze0UVPwonimXWMpXFbvG9ozuuAjgs06lWH7KcA94yYg&s=10"},
{name:"Pav Bhaji",price:120,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS90qqn2-AvgLG584J4YfGJDq85y-Vfw0P0mCRqIoCW8w&s=10"},
{name:"Samosa",price:20,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRpZ9lI58FKBJaUo_JvZx8OeR6ByWvsDGfjK9lPjVscaw&s=10"},
{name:"Sandwich",price:70,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRyFc2D2eKCw70zyZmHwgX2BBE-5Qxi7nz9ZCT3hDBeNQ&s=10"},
{name:"Paneer Tikka",price:180,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSDMAVkkfxLOWpdhCi2k8F_SRv1BZTd-wx1Y8IM99BU6Q&s=10"},
{name:"Manchurian",price:90,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS9E_OvjnGuAfVzWrcTa1o2QZiUNIoFMgsA0XGrBjJsvA&s=10"},
{name:"Vadapav",price:40,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTZmPt9j7wNsRUx3P-RClYW0ShcQyxilm9eGjPcgOjKSh9vLlm5sUrTCE0&s=10"},
{name:"Pani Puri",price:50,img:"https://www.livingsmartandhealthy.com/wp-content/uploads/2025/02/3-flavored-pani-puri.jpg"},
{name:"Chole Bhature",price:130,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQLUVIXFng3Z2QCxi0GZTMBiHhPUUo-dPBRQoM6JCTqnv4uRb8BJ3WCHy8&s=10"},
{name:"Ice Cream",price:60,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR2mHr4p5RZgddbfyGQZEYVvxLy5czHZ9OcTQZ0isazsmIEks1LPUObO8We&s=10"},
{name:"Chocolate Cake",price:150,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRwziOfd2QX3-BC1pRbJEwz79fetsRNR0tS0Ia9I5UO2LyBcpMJxpZ_0BxY&s=10"},
{name:"Juice",price:40,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTUx0GvPr0r9DXSCmYwkHjOQl7D56MZe_9IdslUA7pmzUkDd8fROP2QgtrI&s=10"},
{name:"Coffee",price:50,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSUngoJILBkJtehBIehDfp1PXiJzXu78Hhp-pVr1nmCjQfr9WrDxnjWQfo&s=10"},
{name:"Tea",price:20,img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS_v_eUyjkX3-1axzPtXFrUWUJwpD1YkebZhOXb6pzfXR16znJDr52Pt2iLS_ONlAOr-I9y-OwB_kofEFcTNRYCiFA1FxYuq2AQTmy38Q&s=10"}
];

const menu=document.getElementById("menuItems");
const dishSelect=document.getElementById("dishSelect");
const orderList=document.getElementById("orderList");

// Populate menu and select
dishes.forEach((d,i)=>{
  menu.innerHTML+=`
  <div class="card">
    <img src="${d.img}">
    <div class="card-body text-center">
      <h5>${d.name}</h5>
      <p class="price">₹${d.price}</p>
      <button class="btn btn-warning btn-sm" onclick="selectDish(${i})">Order</button>
    </div>
  </div>`;
  dishSelect.innerHTML+=`<option value="${i}">${d.name}</option>`;
});

// Select dish and scroll to order
function selectDish(index){
  dishSelect.value = index;
  window.location.href="#order";
}

// Order form
document.getElementById("orderForm").onsubmit = e => {
  e.preventDefault();
  const d = dishes[dishSelect.value];
  const total = d.price * document.getElementById("qty").value;
  orderList.innerHTML += `
  <div class="alert alert-success">
    <b>${document.getElementById("custName").value}</b> ordered <b>${d.name}</b> x${document.getElementById("qty").value}<br>
    Payment: ${document.getElementById("payment").value} | Total: ₹${total}
  </div>`;
  alert("Order Placed Successfully!");
};

// Navbar auto-close on mobile after click
document.querySelectorAll('.navbar-nav .nav-link').forEach(link => {
  link.addEventListener('click', () => {
    const navbar = document.querySelector('.navbar-collapse');
    if (navbar.classList.contains('show')) {
      new bootstrap.Collapse(navbar).toggle();
    }
  });
});
</script>

</body>
</html>