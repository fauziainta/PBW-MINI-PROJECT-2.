# PBW-MINI-PROJECT-2
## Fauzia Inanta Aurelia/ 2409116044/ Sistem Informasi (B)

Website ini dikembangkan dari versi sebelumnya yang menggunakan Vue JS, kemudian diubah menjadi dinamis menggunakan PHP dan MySQL agar data dapat dikelola melalui database.

Struktur folder:

     images/
          fashion.jpg
          Profile Image.jpg
          mua.jpg
          photographer.jpg
      index.php
      koneksi.php
      style.css
    


# A. Tampilan Section/Fitur
## 1. Navbar
Menampilkan navigasi utama untuk berpindah ke setiap section: Home, About Me, Experience, dan     Contact.

<img width="1887" height="65" alt="image" src="https://github.com/user-attachments/assets/271eef58-8505-4f64-828a-a5f6254d53dd" />


## 2. Home (Hero Section)
Menampilkan perkenalan singkat berisi: 

・Judul: “Hi, I'm Fauzia”

・Role / profesi

・Deskripsi singkat

・Tombol navigasi ke About Me

・Foto profil

<img width="1893" height="815" alt="image" src="https://github.com/user-attachments/assets/f32567ed-f679-4732-8073-6d5b589526af" />


## 3. About Me
Berisi:

・Deskripsi diri

・Riwayat pendidikan

・Skills dengan progress bar

<img width="1888" height="656" alt="image" src="https://github.com/user-attachments/assets/770a6e58-1003-4188-93c4-fc1a78f181cd" />


## 4. Experiences Page
Menampilkan pengalaman dalam bentuk card grid:

<img width="1894" height="638" alt="image" src="https://github.com/user-attachments/assets/6a8a280f-89d9-4482-9996-2b95f42a152f" />

## 5. Contact Section 

Menampilkan sosial media dan email serta footer:

<img width="1892" height="506" alt="image" src="https://github.com/user-attachments/assets/b99b5d96-faf7-4ddd-9509-c06c8161be99" />

# B. Penjelasan Kode
## 1. Navbar

Menggunakan Bootstrap Navbar untuk navigasi responsif.

     <nav class="navbar navbar-expand-lg navbar-light custom-navbar fixed-top shadow-sm">

Nama pada navbar diambil dari database (tabel users):

     <a class="navbar-brand fw-bold" href="#home"><?php echo $user['name']; ?> Portfolio</a>

## 2. Homepage

Section ini menampilkan nama, role, deskripsi, tombol, dan foto profil.

     <section id="home" class="hero-section d-flex align-items-center">

Data diambil dari database:

     <p class="hero-subtitle"><?php echo $user['role']; ?></p>
     <p class="hero-desc"><?php echo $user['hero_description']; ?></p>

Tombol navigasi:

     <a href="#about" class="btn btn-light custom-btn mt-3">More about me!</a>

## 3. About Me Section

Berisi deskripsi diri dan riwayat pendidikan.

Deskripsi diambil dari database:

     <p><?php echo $user['about']; ?></p>

Data education menggunakan perulangan dari database:

    <ul>
    <?php while($edu = $education->fetch_assoc()) { ?>
    <li><?php echo $edu['text']; ?></li>
    <?php } ?> </ul>

Skills menggunakan progress bar dinamis:

     <?php while($skill = $skills->fetch_assoc()) { ?>

      <div class="mb-4">
      <div class="d-flex justify-content-between">
      <span><?php echo $skill['name']; ?></span>
      <span class="skill-percent"><?php echo $skill['level']; ?>%</span>
      </div>

      <div class="skill-bar-container">
      <div class="skill-bar" style="width: <?php echo $skill['level']; ?>%"></div>
      </div>
      </div> <?php } ?>

## 4. Experiences Section

Menampilkan pengalaman dalam bentuk card grid.

Data diambil dari database menggunakan looping:

    <?php while($exp = $experiences->fetch_assoc()) { ?>

    <div class="col-md-4"> <div class="card experience-card h-100 shadow-sm"> <img src="<?php echo $exp['image']; ?>" class="card-img-top" /> <div class="card-  
    body"> <h5 class="card-title"><?php echo $exp['title']; ?></h5> <p class="card-text"><?php echo $exp['description']; ?></p> </div> </div> </div> <?php } ?>

## 5. Contact Section

Menampilkan sosial media dan email.

Email diambil dari database:

     <p class="contact-info">
        <i class="bi bi-envelope-fill me-2"></i>

        <?php echo $user['email']; ?> </p>

Sosial media ditampilkan dalam bentuk button:

     <div class="social-icons">
        <a href="#" class="social-icon">Instagram</a>
        <a href="#" class="social-icon">Facebook</a>
        <a href="#" class="social-icon">TikTok</a>
        <a href="#" class="social-icon">Twitter</a>

    </div>
    
## 6. PHP & Database (Data Dinamis)

Website menggunakan PHP dan MySQL untuk mengambil data secara dinamis.

Koneksi database:

     include "koneksi.php";

Mengambil data:

     $user = $conn->query("SELECT * FROM users LIMIT 1")->fetch_assoc();
     $education = $conn->query("SELECT * FROM education");
     $skills = $conn->query("SELECT * FROM skills");
     $experiences = $conn->query("SELECT * FROM experiences");

Perulangan data menggunakan:

     while($edu = $education->fetch_assoc())
     while($skill = $skills->fetch_assoc())
     while($exp = $experiences->fetch_assoc())

## 7. Penjelasan Styling (CSS)

Hero Title Font

     .hero-title { font-family: 'Charmonman', cursive !important; font-size: 4.5rem; }

Menggunakan Google Fonts agar tampilan lebih menarik.

Skill Bar

     .skill-bar { background: linear-gradient(90deg, #6D6943, #8a865a); transition: width 0.6s ease; }

Memberikan efek visual dan animasi pada progress bar.

Skill Percentage

     .skill-percent { font-weight: 600; }

Menampilkan persen secara rapi di sisi kanan.

Custom Button

    .custom-btn { border-radius: 30px; background-color: #C8A1B1; color: #fff; }

Digunakan untuk tombol utama seperti “Book & Chat”.

Experience Card Image

    .experience-card img { height: 200px; object-fit: cover; }

Menjaga ukuran gambar tetap konsisten.

Contact Section Title

    .contact-section .section-title { color: #F4F3EE; }

Override warna khusus pada section contact.

# C. Teknologi yang Digunakan

1. `HTML5`
2. `CSS3`
3. `Bootstrap 5`
4. `PHP (Native)`
5. `Google Fonts`
6. `Bootstrap Icons (CDN)`
7. `MySQL Database`

# D. Fitur Utama

1. `Responsive Design (Bootstrap Grid System)`
2. `Dynamic Data Rendering (PHP + MySQL)`
3. `Progress Bar Skills (Dynamic dari Database)`
4. `Experience Card Layout (Looping Data)`
5. `Custom Font dari Google Fonts`
6. `Smooth Scroll Navigation`
7. `Reusable Component dengan PHP (Looping & Fetch Data)`
