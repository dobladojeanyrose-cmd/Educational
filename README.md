<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>EduTools Hub</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  
  <script src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.min.js"></script>


  <style>
    body {
     body {
  margin: 0;
  font-family: Arial, Helvetica, sans-serif;
  background: transparent;
  color: #333;
}

    }

    header {
      background: #2b6cb0;
      color: white;
      padding: 20px;
      text-align: center;
    }

    nav {
      background: #1a4f8b;
      padding: 10px;
      text-align: center;
    }

    nav a {
      color: white;
      margin: 0 15px;
      text-decoration: none;
      font-weight: bold;
    }

    nav a:hover {
      text-decoration: underline;
    }

    .hero {
      padding: 60px 20px;
      text-align: center;
      background: #eaf2ff;
    }

    .hero h1 {
      font-size: 36px;
      margin-bottom: 10px;
    }

    .hero p {
      font-size: 18px;
      color: #555;
    }

    .container {
      padding: 40px 20px;
      max-width: 1000px;
      margin: auto;
    }

    .tools {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
    }

    .card {
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      text-align: center;
    }

    .card h3 {
      color: #2b6cb0;
    }

    footer {
      background: #2b6cb0;
      color: white;
      text-align: center;
      padding: 15px;
      margin-top: 40px;
    }
    header, nav, .hero, .container, footer {
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(5px);
  margin: 20px;
  border-radius: 15px;
}

  </style>
  #bg3d {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
}

</head>

<body>
  
<div id="bg3d"></div>


  <header>
    <h1>EduTools Hub</h1>
    <p>Your All-in-One Educational Tools Website</p>
  </header>

  <nav>
    <a href="#">Home</a>
    <a href="#tools">Tools</a>
    <a href="#about">About</a>
    <a href="#contact">Contact</a>
  </nav>

  <section class="hero">
    <h1>Learn Smarter with Digital Tools</h1>
    <p>Explore free tools for students, teachers, and lifelong learners.</p>
  </section>

  <section class="container" id="tools">
    <h2>Educational Tools</h2>

    <div class="tools">
      <div class="card">
        <h3>Math Calculator</h3>
        <p>Quickly solve math problems.</p>
        <a href="#">Open Tool</a>
      </div>

      <div class="card">
        <h3>Flashcards</h3>
        <p>Review and memorize faster.</p>
        <a href="#">Open Tool</a>
      </div>

      <div class="card">
        <h3>Study Planner</h3>
        <p>Organize your daily study schedule.</p>
        <a href="#">Open Tool</a>
      </div>

      <div class="card">
        <h3>Quiz Generator</h3>
        <p>Create quizzes for practice.</p>
        <a href="#">Open Tool</a>
      </div>
    </div>
  </section>

  <section class="container" id="about">
    <h2>About EduTools Hub</h2>
    <p>
      EduTools Hub is a simple educational website designed to help students and teachers
      access useful digital learning tools anytime, anywhere.
    </p>
  </section>

  <footer id="contact">
    <p>© 2026 EduTools Hub | Made for Educational Purposes</p>
  </footer>
<script>
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
  );

  const renderer = new THREE.WebGLRenderer({ alpha: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.getElementById("bg3d").appendChild(renderer.domElement);

  const geometry = new THREE.TorusGeometry(10, 3, 16, 100);
  const material = new THREE.MeshStandardMaterial({ color: 0x2b6cb0 });
  const torus = new THREE.Mesh(geometry, material);
  scene.add(torus);

  const pointLight = new THREE.PointLight(0xffffff);
  pointLight.position.set(20, 20, 20);
  scene.add(pointLight);

  const ambientLight = new THREE.AmbientLight(0xffffff);
  scene.add(ambientLight);

  camera.position.z = 30;

  function animate() {
    requestAnimationFrame(animate);
    torus.rotation.x += 0.01;
    torus.rotation.y += 0.01;
    renderer.render(scene, camera);
  }

  animate();

  window.addEventListener("resize", () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
</script>

</body>
</html>
