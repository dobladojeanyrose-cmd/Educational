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
      transition: all 0.3s ease;
    }

    .card:hover {
      transform: scale(1.05);
      background: rgba(0, 200, 255, 0.2);
      cursor: pointer;
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
  const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
  camera.position.z = 25;

  // Renderer
  const renderer = new THREE.WebGLRenderer({ alpha: true, antialias: true });
  renderer.setSize(window.innerWidth, window.innerHeight);
  document.getElementById("bg3d").appendChild(renderer.domElement);

  // Torus Knot
  const geometry = new THREE.TorusKnotGeometry(6, 1.5, 50, 16);
  const material = new THREE.MeshStandardMaterial({ color: 0x00c8ff, metalness: 0.5, roughness: 0.5 });
  const torusKnot = new THREE.Mesh(geometry, material);
  scene.add(torusKnot);

  // Lights
  const light1 = new THREE.PointLight(0xffffff, 1.5);
  light1.position.set(20, 20, 20);
  scene.add(light1);

  const light2 = new THREE.PointLight(0xffffff, 1.5);
  light2.position.set(-20, -20, -20);
  scene.add(light2);

  scene.add(new THREE.AmbientLight(0xffffff, 0.8));

  // Stars
  const starsGeometry = new THREE.BufferGeometry();
  const starCount = 500;
  const positions = [];
  for(let i=0; i<starCount; i++){
    positions.push((Math.random()-0.5)*200);
    positions.push((Math.random()-0.5)*200);
    positions.push((Math.random()-0.5)*200);
  }
  starsGeometry.setAttribute('position', new THREE.Float32BufferAttribute(positions, 3));
  const starsMaterial = new THREE.PointsMaterial({ color: 0xffffff, size: 0.5 });
  const stars = new THREE.Points(starsGeometry, starsMaterial);
  scene.add(stars);

  // Animation
  function animate() {
    requestAnimationFrame(animate);

    torusKnot.rotation.x += 0.01;
    torusKnot.rotation.y += 0.01;

    // Rotating camera
    const time = Date.now() * 0.0005;
    camera.position.x = Math.sin(time) * 25;
    camera.position.z = Math.cos(time) * 25;
    camera.lookAt(scene.position);

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


