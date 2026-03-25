<!DOCTYPE html>
<html lang="am">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>እሮ ሽክ Juice House</title>

<style>
/* ===== Modern UI ===== */
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:'Segoe UI',sans-serif;background:#f4f4f4;color:#333;}
header{background:linear-gradient(90deg,#ff7f00,#ffb347);color:white;text-align:center;padding:20px;font-size:1.5em;}
nav{display:flex;justify-content:center;background:#333;}
nav a{color:white;padding:14px 20px;text-decoration:none;font-weight:bold;}
nav a:hover{background:#ff7f00;color:white;border-radius:5px;}

.section{padding:30px;text-align:center;}
.menu{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:20px;}
.card{background:white;padding:20px;border-radius:15px;box-shadow:0 4px 8px rgba(0,0,0,0.1);}
.btn{background:#ff7f00;color:white;padding:10px;border:none;border-radius:8px;cursor:pointer;transition:0.3s;}
.btn:hover{background:#ff9500;}

/* Cart & Admin */
#cart-list li,#orders li{background:white;margin:10px;padding:10px;border-radius:10px;box-shadow:0 2px 4px rgba(0,0,0,0.1);}

/* Gallery */
.gallery{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:15px;margin-top:20px;}
.gallery img{width:100%;border-radius:10px;transition:0.3s;cursor:pointer;}
.gallery img:hover{transform:scale(1.05);}

/* Delivery Tracker Map */
#map iframe{width:100%;height:300px;border-radius:10px;border:0;margin-top:20px;}
input,select{padding:10px;margin:5px;width:80%;max-width:300px;}
</style>
</head>

<body>

<header>
<h1>🍹 እሮ ሽክ Juice House</h1>
<p>Fresh • Natural • Delicious • Modern UI</p>
</header>

<nav>
<a href="#menu">Menu</a>
<a href="#cart">Cart</a>
<a href="#gallery">Gallery</a>
<a href="#map">Delivery Tracker</a>
<a href="#admin">Admin</a>
</nav>

<!-- ===== Menu Section ===== -->
<section class="section" id="menu">
<h2>🍹 Juice Menu</h2>
<div class="menu">
<div class="card"><h3>Avocado</h3><p>80 ETB</p><button onclick="addToCart('Avocado',80)" class="btn">Add</button></div>
<div class="card"><h3>Mango</h3><p>80 ETB</p><button onclick="addToCart('Mango',80)" class="btn">Add</button></div>
<div class="card"><h3>Pineapple</h3><p>80 ETB</p><button onclick="addToCart('Pineapple',80)" class="btn">Add</button></div>
<div class="card"><h3>Banana</h3><p>70 ETB</p><button onclick="addToCart('Banana',70)" class="btn">Add</button></div>
<div class="card"><h3>Papaya</h3><p>70 ETB</p><button onclick="addToCart('Papaya',70)" class="btn">Add</button></div>
<div class="card"><h3>Special Mix</h3><p>100 ETB</p><button onclick="addToCart('Special Mix',100)" class="btn">Add</button></div>
<div class="card"><h3>Oreo Milkshake</h3><p>120 ETB</p><button onclick="addToCart('Oreo Milkshake',120)" class="btn">Add</button></div>
<div class="card"><h3>Chocolate Juice</h3><p>120 ETB</p><button onclick="addToCart('Chocolate Juice',120)" class="btn">Add</button></div>
<div class="card"><h3>Lemon Juice</h3><p>60 ETB</p><button onclick="addToCart('Lemon Juice',60)" class="btn">Add</button></div>
<div class="card"><h3>Strawberry Juice</h3><p>100 ETB</p><button onclick="addToCart('Strawberry',100)" class="btn">Add</button></div>
</div>
</section>

<!-- ===== Cart Section ===== -->
<section class="section" id="cart">
<h2>🛒 Cart</h2>
<ul id="cart-list"></ul>
<h3>Total: <span id="total">0</span> ETB</h3>

<h2>Delivery Info</h2>
<input id="name" placeholder="Name">
<input id="address" placeholder="Address">
<select id="payment">
<option>Telebirr</option>
<option>CBE</option>
<option>Cash</option>
</select>
<br><br>
<button onclick="checkout()" class="btn">Order Now</button>
</section>

<!-- ===== Image Gallery ===== -->
<section class="section" id="gallery">
<h2>📸 Gallery</h2>
<div class="gallery">
<img src="https://image2url.com/r2/default/images/1774449924823-9926bfeb-c03b-4e34-91d0-ade66b839406.jfif" alt="Avocado Juice">
<img src="https://image2url.com/r2/default/images/1774450506286-eac2d235-c1de-4902-a2b9-81be8777cca3.jfif" alt="Mango Juice">
<img src="https://image2url.com/r2/default/images/1774450280034-3297f30d-41fd-4d1c-83b2-5b002ebdce82.jfif" alt="Pineapple Juice">
<img src="https://image2url.com/r2/default/images/1774450360198-ad512197-d00c-4bf4-abb1-17a4840bbde0.jfif" alt="Special Mix">
<img src="https://image2url.com/r2/default/images/1774450425055-3eb10cee-688f-498e-8f1e-3e1755e75dd5.jfif" alt="Banana Juice">
</div>
</section>

<!-- ===== Delivery Tracker ===== -->
<section class="section" id="map">
<h2>📦 Delivery Tracker</h2>
<iframe src="https://maps.google.com/maps?q=Jinka&t=&z=13&output=embed"></iframe>
</section>

<!-- ===== Admin Panel ===== -->
<section class="section" id="admin">
<h2>🧑‍💼 Admin Panel</h2>
<input type="password" id="adminPass" placeholder="Enter Password">
<button onclick="loginAdmin()" class="btn">Login</button>
<div id="adminPanel" style="display:none">
<h3>Orders</h3>
<ul id="orders"></ul>
<button onclick="clearOrders()" class="btn">Clear Orders</button>
</div>
</section>

<script>
// ===== Cart System =====
let cart = JSON.parse(localStorage.getItem("cart")) || [];
function saveCart(){ localStorage.setItem("cart",JSON.stringify(cart)); }
function addToCart(name,price){
 let item = cart.find(i=>i.name===name);
 if(item){item.qty++;} else{cart.push({name,price,qty:1});}
 updateCart();
}
function updateCart(){
 let list=document.getElementById("cart-list"); list.innerHTML="";
 let total=0;
 cart.forEach((item,i)=>{
  total+=item.price*item.qty;
  let li=document.createElement("li");
  li.innerHTML=`${item.name} x${item.qty} <button onclick="changeQty(${i},1)">+</button> <button onclick="changeQty(${i},-1)">-</button> <button onclick="removeItem(${i})">❌</button>`;
  list.appendChild(li);
 });
 document.getElementById("total").textContent=total;
 saveCart();
}
function changeQty(i,c){ cart[i].qty+=c; if(cart[i].qty<=0) cart.splice(i,1); updateCart(); }
function removeItem(i){ cart.splice(i,1); updateCart(); }
function checkout(){
 let name=document.getElementById("name").value;
 let address=document.getElementById("address").value;
 let payment=document.getElementById("payment").value;
 if(cart.length===0)return alert("Cart empty");
 if(!name||!address)return alert("Fill info");
 let msg="Order:%0A";
 cart.forEach(i=>{ msg+=`${i.name} x${i.qty} = ${i.price*i.qty} ETB%0A`; });
 let total=cart.reduce((s,i)=>s+i.price*i.qty,0);
 msg+=`Total:${total} ETB%0AName:${name}%0AAddress:${address}%0APayment:${payment}`;
 let orders=JSON.parse(localStorage.getItem("orders"))||[];
 orders.push(msg); localStorage.setItem("orders",JSON.stringify(orders));
 window.location.href="https://wa.me/251945900829?text="+msg;
 cart=[]; updateCart();
}

// ===== Admin =====
function loginAdmin(){
 let pass=document.getElementById("adminPass").value;
 if(pass==="1234"){
  document.getElementById("adminPanel").style.display="block"; loadOrders();
 }else{alert("Wrong password!");}
}
function loadOrders(){
 let orders=JSON.parse(localStorage.getItem("orders"))||[];
 let list=document.getElementById("orders"); list.innerHTML="";
 orders.forEach(o=>{ let li=document.createElement("li"); li.textContent=o; list.appendChild(li); });
}
function clearOrders(){ localStorage.removeItem("orders"); loadOrders(); }

window.onload=updateCart;
</script>

</body>
</html>
