<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>EduTools Hub</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Three.js -->
  <script src="https://cdn.jsdelivr.net/npm/three@0.152.2/build/three.min.js"></script>

  <style>
    body {
      margin: 0;
      font-family: Arial, Helvetica, sans-serif;
      background: black;
      color: white;
      overflow-x: hidden;
    }

    #bg3d {
      position: fixed;
      top: 0;
      left: 0;
      width: 100vw;
      height: 100vh;
      z-index: -1;
    }

    header, nav, section, footer {
      background: rgba(0,0,0,0.7);
      margin: 20px;
      padding: 20px;
      border-radius: 12px;
    }

    nav a {
      color: #00c8ff;
      margin: 0 15px;
      text-decoration: none;
      font-weight: bold;
    }

    nav a:hover {
      text-decoration: underline;
    }

    .hero {
      text-align: center;
      padding: 60px 20px;
    }

    .tools {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 20px;
    }

    .card {
      background: rgba(255,255,255,0.1);
      padding: 20px;
      border-radius: 10px;
      text-align: center;
    }

    .card a {
      color: #00c8ff;
      text-decoration: none;
    }
  </style>
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
</nav>

<section class="hero">
  <h1>Learn Smarter with Digital Tools</h1>
  <p>Explore free tools for students and teachers.</p>
</section>

<section id="tools">
  <h2>Educational Tools</h2>
  <div class="tools">
    <div class="card">Math Calculator</div>
    <div class="card">Flashcards</div>
    <div class="card">Study Planner</div>
    <div class="card">Quiz Generator</div>
  </div>
</section>

<footer>
  © 2026 EduTools Hub
</footer>

<script>
  // Scene
  const scene = new THREE.Scene();

  // Camera
  const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth / window.innerHeight,
    0.1,
    1000
  );
  camera.position.z = 20;

  // Renderer
  const renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.getElementById("bg3d").appendChild(renderer.domElement);

  // Geometry
  const geometry = new THREE.TorusKnotGeometry(6, 1.5, 100, 16);
  const material = new THREE.MeshStandardMaterial({ color: 0x00c8ff });
  const shape = new THREE.Mesh(geometry, material);
  scene.add(shape);

  // Lights
  const light1 = new THREE.PointLight(0xffffff, 1);
  light1.position.set(10, 10, 10);
  scene.add(light1);

  const light2 = new THREE.PointLight(0xffffff, 1);
  light2.position.set(-10, -10, -10);
  scene.add(light2);

  scene.add(new THREE.AmbientLight(0xffffff, 0.5));

  // Animation
  function animate() {
    requestAnimationFrame(animate);
    shape.rotation.x += 0.01;
    shape.rotation.y += 0.01;
    renderer.render(scene, camera);
  }

  animate();

  // Resize
  window.addEventListener("resize", () => {
    camera.aspect = window.innerWidth / window.innerHeight;
    camera.updateProjectionMatrix();
    renderer.setSize(window.innerWidth, window.innerHeight);
  });
</script>

</body>
</html>

