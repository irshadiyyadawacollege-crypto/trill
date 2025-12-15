<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>3D Bus</title>
<style>
  body { margin: 0; overflow: hidden; }
</style>
</head>
<body>

<script src="https://cdn.jsdelivr.net/npm/three@0.158/build/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/three@0.158/examples/js/controls/OrbitControls.js"></script>

<script>
// Scene
const scene = new THREE.Scene();
scene.background = new THREE.Color(0x87ceeb);

// Camera
const camera = new THREE.PerspectiveCamera(
  75, window.innerWidth / window.innerHeight, 0.1, 1000
);
camera.position.set(6, 4, 8);

// Renderer
const renderer = new THREE.WebGLRenderer({ antialias: true });
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// Controls
const controls = new THREE.OrbitControls(camera, renderer.domElement);

// Lights
scene.add(new THREE.AmbientLight(0xffffff, 0.6));
const light = new THREE.DirectionalLight(0xffffff, 1);
light.position.set(5, 10, 5);
scene.add(light);

// Bus body
const bodyGeo = new THREE.BoxGeometry(6, 2, 2.5);
const bodyMat = new THREE.MeshStandardMaterial({ color: 0xffcc00 });
const busBody = new THREE.Mesh(bodyGeo, bodyMat);
busBody.position.y = 1.5;
scene.add(busBody);

// Wheels
function createWheel(x, z) {
  const wheelGeo = new THREE.CylinderGeometry(0.5, 0.5, 0.6, 32);
  const wheelMat = new THREE.MeshStandardMaterial({ color: 0x222222 });
  const wheel = new THREE.Mesh(wheelGeo, wheelMat);
  wheel.rotation.z = Math.PI / 2;
  wheel.position.set(x, 0.5, z);
  scene.add(wheel);
}

createWheel(-2.5, 1.2);
createWheel(2.5, 1.2);
createWheel(-2.5, -1.2);
createWheel(2.5, -1.2);

// Ground
const ground = new THREE.Mesh(
  new THREE.PlaneGeometry(50, 50),
  new THREE.MeshStandardMaterial({ color: 0x555555 })
);
ground.rotation.x = -Math.PI / 2;
scene.add(ground);

// Animate
function animate() {
  requestAnimationFrame(animate);
  busBody.rotation.y += 0.005;
  controls.update();
  renderer.render(scene, camera);
}
animate();

// Resize
window.addEventListener('resize', () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateProjectionMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
</script>

</body>
</html>
