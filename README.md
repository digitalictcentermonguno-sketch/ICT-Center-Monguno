<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>ICT Center - Auto Email & Excel Fixed</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',Arial,sans-serif;scroll-behavior:smooth;}
body, html{height:100%;}
body{
  background:url('https://images.unsplash.com/photo-1519389950473-47ba0277781c?auto=format&fit=crop&w=1950&q=80') center/cover no-repeat;
  position:relative; color:white;
}
body::before{
  content:'';
  position:absolute;
  top:0; left:0; width:100%; height:100%;
  background:linear-gradient(-45deg,rgba(13,71,161,0.6),rgba(25,118,210,0.6),rgba(41,182,246,0.6),rgba(13,71,161,0.6));
  background-size:400% 400%;
  animation: gradientBG 15s ease infinite;
  z-index:0;
  pointer-events:none;
}
@keyframes gradientBG{0%{background-position:0% 50%;}50%{background-position:100% 50%;}100%{background-position:0% 50%;}}

nav{
  position:fixed;top:0;width:100%;
  background:rgba(0,0,0,0.7);
  display:flex;justify-content:space-between;
  padding:15px 30px;
  z-index:10;backdrop-filter:blur(5px);
}
nav b{font-size:1.3em;}
nav div{
  display:flex;
  gap:25px; /* clean spacing between links */
  align-items:center;
}
nav a{color:white;text-decoration:none;font-weight:500;transition:0.3s;}
nav a:hover{color:#ffeb3b;text-shadow:0 0 8px #ffeb3b;}

section{display:none;min-height:100vh;padding:150px 20px 50px;position:relative;z-index:1;}
section.active{display:block;}
h1,h2,h3{margin-bottom:20px;}
p{margin-bottom:20px;line-height:1.5;}

.box{background:rgba(0,0,0,0.7);max-width:600px;margin:auto;padding:25px;border-radius:15px;text-align:left;box-shadow:0 8px 25px rgba(0,0,0,0.5);}
input,select,textarea,button{width:100%;padding:12px;margin:8px 0;border-radius:8px;border:none;outline:none;font-size:1em;}
textarea{resize:none;}
button{background:#0d47a1;color:white;cursor:pointer;font-weight:bold;transition:0.3s;box-shadow:0 0 10px rgba(0,0,0,0.3);}
button:hover{background:#1976d2;box-shadow:0 0 15px #ffeb3b,0 0 25px #ffeb3b inset;transform:translateY(-2px);}

.student-card{background:rgba(255,255,255,0.9);color:black;border-radius:15px;padding:15px;margin:15px;text-align:center;width:220px;display:inline-block;vertical-align:top;box-shadow:0 5px 20px rgba(0,0,0,0.5);transition:0.3s;}
.student-card:hover{transform:translateY(-5px);box-shadow:0 10px 30px rgba(0,0,0,0.7);}
.student-card img{width:80px;height:80px;border-radius:50%;object-fit:cover;border:2px solid #0d47a1;margin-bottom:10px;}
.student-card button{margin-top:5px;font-size:0.85em;padding:4px 10px;}

#idcard{margin:20px auto;}
.card{width:300px;background:white;color:black;border-radius:15px;padding:15px;text-align:center;box-shadow:0 5px 20px rgba(0,0,0,.5);}
.card-header{background:#0d47a1;color:white;padding:10px 0;border-top-left-radius:15px;border-top-right-radius:15px;font-weight:bold;font-size:1.2em;}
.card-body p{margin:6px 0;}
.card-body img{width:80px;height:80px;border-radius:50%;object-fit:cover;border:2px solid #0d47a1;margin-bottom:10px;}
#qr{margin-top:10px;}

@media(max-width:600px){nav{flex-direction:column;align-items:flex-start;}nav div{gap:10px;}.box{padding:20px;}.student-card{width:100%;margin:10px 0;}.card{width:90%;}}

@media print{body *{visibility:hidden;}#idcard,#idcard *{visibility:visible;}#idcard{position:absolute;left:0;top:0;width:100%;}}
</style>
</head>
<body>

<nav>
<img src="logo-light-p.png" alt="ICT Logo"> 
<h2><b>Borno State Information and Communication Technology Development Agency</b></h2>
<div>
<a href="#" onclick="showPage('home')">Home</a>
<a href="#" onclick="showPage('register')">Register</a>
<a href="#" onclick="showPage('login')">Admin</a>
</div>
</nav>

<section id="home" class="active">
<h1>Welcome to Digital Literacy Center, Monguno</h1>
<p>Apply now to register as a student</p>
<button onclick="showPage('register')">Apply Now</button>
<button onclick="showPage('login')">Admin Login</button>
</section>

<section id="register">
<h2>Student Registration</h2>
<div class="box">
<label>Full Name *</label><input id="rname" placeholder="Full Name" required>
<label>Gender *</label><select id="rgender" required><option value="">Select Gender</option><option>Male</option><option>Female</option></select>
<label>Category / Program *</label><select id="rcategory" required><option value="">Select</option><option>Out of School</option><option>LGA Staff</option><option>Adult</option></select>
<label>Date of Birth / Age *</label><input type="date" id="rdob" required>
<label>NIN *</label><input id="rnin" placeholder="National ID Number" required>
<label>Phone Number </label><input id="rphone" placeholder="Phone Number" required>
<label>Disability</label><input id="rdisability" placeholder="If Any">
<label>Ward </label><input id="rward" placeholder="Ward" required>
<label>Residential Address *</label><textarea id="raddress" placeholder="Residential Address" required></textarea>
<label>Guardian / Parent Name *</label><input id="rguardian" placeholder="Guardian Name" required>
<label>Guardian / Parent Address *</label><textarea id="rguardianaddress" placeholder="Guardian Address" required></textarea>
<label>Guardian / Parent Phone Number *</label><input id="rguardianphone" placeholder="Guardian Phone" required>
<label>Email Address </label><input id="remail" type="email" placeholder="Email Address" required>
<label>Upload Photo *</label><input type="file" id="rphoto" accept="image/*" required>
<label>Username </label><input id="rusername" placeholder="Username" required>
<label>Password </label><input type="password" id="rpassword" placeholder="Password" required>
<button onclick="register()">Register Student</button>
<p id="rmsg"></p>
<button onclick="showPage('home')">Back to Home</button>
</div>
</section>

<section id="login">
<h2>Admin Login</h2>
<div class="box">
<input id="lusername" placeholder="Username" required>
<input type="password" id="lpassword" placeholder="Password" required>
<button onclick="login()">Login</button>
<p id="lmsg"></p>
<button onclick="showPage('home')">Back to Home</button>
</div>
</section>

<section id="dashboard">
<h2>Admin Dashboard</h2>
<div class="box">
<button onclick="exportExcel()">Export All Students to Excel</button>
</div>
<div id="studentCards"></div>
<div id="idcard"></div>
<button onclick="printID()">Print ID Card</button>
<button onclick="logout()">Logout</button>
</section>

<script src="https://cdn.jsdelivr.net/npm/qrcodejs/qrcode.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/emailjs-com@3/dist/email.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/html2canvas@1.4.1/dist/html2canvas.min.js"></script>
<script>
emailjs.init("YOUR_PUBLIC_KEY"); // Replace with your EmailJS public key
localStorage.adminPass="admin123";

function showPage(id){
  document.querySelectorAll("section").forEach(s=>s.classList.remove("active"));
  document.getElementById(id).classList.add("active");
}

// REGISTER
function register(){
  let reader=new FileReader();
  reader.onload=function(){
    let students=JSON.parse(localStorage.students||"[]");
    let student={
      name:rname.value, gender:rgender.value, category:rcategory.value,
      dob:rdob.value, nin:rnin.value, phone:rphone.value, disability:rdisability.value,
      ward:rward.value, address:raddress.value,
      guardian:rguardian.value, guardianAddress:rguardianaddress.value, guardianPhone:rguardianphone.value,
      email:remail.value, photo:reader.result, user:rusername.value, pass:rpassword.value, id:"ICT"+Date.now()
    };
    students.push(student);
    localStorage.students=JSON.stringify(students);
    rmsg.innerHTML="✅ Student Registered Successfully!";
    sendIDEmail(student);
    rname.value=""; rusername.value=""; rpassword.value=""; rphoto.value=""; remail.value="";
  };
  if(rphoto.files[0]) reader.readAsDataURL(rphoto.files[0]);
}

// SEND EMAIL
function sendIDEmail(s){
  let cardDiv=document.createElement("div");
  cardDiv.style.width="300px"; cardDiv.style.padding="10px"; cardDiv.style.textAlign="center";
  cardDiv.innerHTML=`<h3>ICT Center ID Card</h3><img src="${s.photo}" style="width:80px;height:80px;border-radius:50%;"><p>Name: ${s.name}</p><p>Gender: ${s.gender}</p><p>Category: ${s.category}</p><p>ID: ${s.id}</p>`;
  html2canvas(cardDiv).then(canvas=>{
    let imgData=canvas.toDataURL("image/png");
    emailjs.send("YOUR_SERVICE_ID","YOUR_TEMPLATE_ID",{
      to_email: s.email,
      student_name: s.name,
      message: "Here is your updated ICT Center ID card",
      attachment: imgData
    }).then(()=>console.log("Email sent"),err=>console.error(err));
  });
}

// LOGIN
function login(){
  let u=lusername.value.trim(),p=lpassword.value.trim();
  if(u==="admin" && p===localStorage.adminPass){showDashboard();showPage('dashboard'); return;}
  let students=JSON.parse(localStorage.students||"[]");
  let s=students.find(x=>x.user===u && x.pass===p);
  if(s){ showID(s); showPage('dashboard'); } else lmsg.innerHTML="❌ Invalid login";
}

// DASHBOARD
function showDashboard(){let students=JSON.parse(localStorage.students||"[]");renderCards(students);}

function renderCards(students){
  let container=document.getElementById("studentCards");
  container.innerHTML="";
  students.forEach((s,i)=>{
    container.innerHTML+=`<div class="student-card">
      <img src="${s.photo}" alt="Photo">
      <h4>${s.name}</h4>
      <p>${s.gender}</p>
      <p>${s.category}</p>
      <button onclick='showID(${JSON.stringify(s)})'>View ID</button>
      <button onclick='editStudent(${i})'>Edit</button>
      <button onclick='deleteStudent(${i})'>Delete</button>
    </div>`;
  });
}

// DELETE
function deleteStudent(i){if(confirm("Delete this student?")){let s=JSON.parse(localStorage.students);s.splice(i,1);localStorage.students=JSON.stringify(s);showDashboard();}}

// EDIT
function editStudent(i){
  let students=JSON.parse(localStorage.students);
  let s=students[i];
  let n=prompt("Full Name",s.name); if(n)s.name=n;
  let g=prompt("Gender (Male/Female)",s.gender); if(g)s.gender=g;
  let c=prompt("Category",s.category); if(c)s.category=c;
  let e=prompt("Email",s.email); if(e)s.email=e;
  students[i]=s;
  localStorage.students=JSON.stringify(students);
  showDashboard();
  showID(s);
  sendIDEmail(s);
}

// SHOW ID
function showID(s){
  idcard.innerHTML=`<div class="card">
    <div class="card-header">ICT CENTER</div>
    <div class="card-body">
    <img src="${s.photo}" alt="Photo">
    <p><b>Name:</b> ${s.name}</p>
    <p><b>Gender:</b> ${s.gender}</p>
    <p><b>Category:</b> ${s.category}</p>
    <p><b>ID:</b> ${s.id}</p>
    <div id="qr"></div>
    </div></div>`;
  new QRCode(document.getElementById("qr"), s.id);
}

// PRINT
function printID(){if(!idcard.innerHTML.trim()){alert("Generate ID card first");return;}window.print();}

// LOGOUT
function logout(){showPage('home'); idcard.innerHTML=""; lusername.value=""; lpassword.value="";}

// EXPORT EXCEL FIXED
function exportExcel(){
  let students=JSON.parse(localStorage.students||"[]");
  if(students.length===0){alert("No students to export"); return;}
  let exportData = students.map(s => ({
    ID: s.id,
    Name: s.name,
    Gender: s.gender,
    Category: s.category,
    DateOfBirth: s.dob,
    NIN: s.nin,
    Phone: s.phone,
    Disability: s.disability,
    Ward: s.ward,
    Address: s.address,
    GuardianName: s.guardian,
    GuardianAddress: s.guardianAddress,
    GuardianPhone: s.guardianPhone,
    Email: s.email,
    Username: s.user
  }));
  let ws = XLSX.utils.json_to_sheet(exportData);
  let wb = XLSX.utils.book_new();
  XLSX.utils.book_append_sheet(wb, ws, "Students");
  XLSX.writeFile(wb, "Students.xlsx");
}
</script>
</body>
</html>
