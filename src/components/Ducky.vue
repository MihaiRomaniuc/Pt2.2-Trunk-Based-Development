<script setup>
import * as THREE from 'three'
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';
//import { TrackballControls } from 'three/examples/jsm/controls/TrackballControls'
import { RoomEnvironment } from '../assets/RoomEnvironment.js'
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { ref, onMounted } from 'vue'

const container = ref(null)
let scene
let camera
let renderer
let ducky

onMounted(() => {
    //Create Scene
    scene = new THREE.Scene({ alpha: true })    //Alpha -> Antialiasing

    //Camera Setup
    camera = new THREE.PerspectiveCamera(50, window.innerWidth / window.innerHeight, 0.1, 200);
    camera.position.z = 10;

    //Renderer
    renderer = new THREE.WebGLRenderer({ antialias: true });
    renderer.setSize(window.innerWidth, window.innerHeight);    // Render Size
    renderer.setClearColor(0x000000, 0);                        // Transparent Background

    //Lights and Enviroment
    const environment = new RoomEnvironment();
    const pmremGenerator = new THREE.PMREMGenerator(renderer);
    scene.environment = pmremGenerator.fromScene(environment).texture;
    renderer.toneMapping = THREE.ACESFilmicToneMapping;
    renderer.toneMappingExposure = 1.2;
    renderer.outputColorSpace = THREE.SRGBColorSpace;

    //Apend renderer to DOM
    container.value.appendChild(renderer.domElement);

    //Controls
    //const controls = new TrackballControls(camera, renderer.domElement)

    //Load Duck
    const loader = new GLTFLoader();
    loader.load('scene.gltf', gltf => {
        scene.add(gltf.scene)
        ducky = gltf.scene;
        ducky.rotation.y += 0.75
    }, undefined, error => console.error(error));
    camera.position.y += 2;
    camera.position.x = -6;


    function animate() {
        requestAnimationFrame(animate);
        //ducky.rotation.y += 0.01
        //controls.update()
        renderer.render(scene, camera);
    }
    animate();

    //GSAP SCROLL
    gsap.registerPlugin(ScrollTrigger);
    ScrollTrigger.defaults({
        immediateRender: false,
        ease: "power1.inOut",
        scrub: true
    });

    let duck_anim = gsap.timeline()

    // Full Height
    camera.position.x = -6;
    duck_anim.to(camera.position, {
        x: 6,
        scrollTrigger: { trigger: ".section-1", start: "center center", end: "top center", endTrigger: ".section-2", scrub: 1 }
    })
    duck_anim.to(scene.rotation, {
        y: -4.5,
        scrollTrigger: { trigger: ".section-1", start: "center center", end: "top center", endTrigger: ".section-2", scrub: 1 }
    })

    duck_anim.to(camera.position, {
        x: -6,
        scrollTrigger: { trigger: ".section-2", start: "bottom center", end: "center center", endTrigger: ".section-3", scrub: 1 }
    })
    duck_anim.to(scene.rotation, {
        x: -0.5, y: 0,
        scrollTrigger: { trigger: ".section-2", start: "bottom center", end: "center center", endTrigger: ".section-3", scrub: 1 }
    })

    duck_anim.to(camera.position, {
        x: 0,
        scrollTrigger: { trigger: ".section-3", start: "bottom center", end: "center center", endTrigger: ".section-4", scrub: 1 }
    })

    duck_anim.to(scene.rotation, {
        x: 0.5, y: 0,
        scrollTrigger: { trigger: ".section-4", start: "bottom center", end: "center center", endTrigger: ".section-5", scrub: 1 }
    })

})
</script>

<template>
    <div class="fixed pointer-events-none w-screen" ref="container"></div>
</template>