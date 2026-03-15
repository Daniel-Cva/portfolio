<script>
    import { onMount } from 'svelte';
    import Preloader from '$lib/components/Preloader.svelte';

    import FloatingWhatsApp from '$lib/components/FloatingWhatsApp.svelte';
    import Footer from '$lib/components/Footer.svelte';
    import Contact from '$lib/components/Contact.svelte';
    import Certifications from '$lib/components/Certifications.svelte';
    import Collaboration from '$lib/components/Collaboration.svelte';
    import Projects from '$lib/components/Projects.svelte';
    import Experience from '$lib/components/Experience.svelte';
    import Education from '$lib/components/Education.svelte';
    import SoftSkills from '$lib/components/SoftSkills.svelte';
    import Skills from '$lib/components/Skills.svelte';
    import Hero from '$lib/components/Hero.svelte';
    import Navigation from '$lib/components/Navigation.svelte';

    let appVisible = false;

    onMount(() => {
        function initParticles() {
            const main = document.querySelector("main");
            if (!main) return;
            for(let i=0; i<15; i++) {
                createParticle(main);
            }
        }

        function createParticle(container) {
            const particle = document.createElement("div");
            particle.classList.add("particle");
            
            const size = Math.random() * 100 + 50;
            particle.style.width = `${size}px`;
            particle.style.height = `${size}px`;
            particle.style.left = `${Math.random() * 100}%`;
            particle.style.top = `${Math.random() * 100}%`;
            
            const duration = Math.random() * 20 + 10;
            particle.style.transition = `all ${duration}s linear`;
            
            container.appendChild(particle);
            
            setTimeout(() => moveParticle(particle), 100);
        }

        function moveParticle(particle) {
            if (!particle) return;
            particle.style.transform = `translate(${Math.random() * 200 - 100}px, ${Math.random() * 200 - 100}px) scale(${Math.random() * 0.5 + 0.8})`;
            particle.style.opacity = Math.random() * 0.3 + 0.1;
            
            setTimeout(() => moveParticle(particle), parseFloat(particle.style.transitionDuration) * 1000);
        }
    });

    function handleAnimationDone() {
        appVisible = true;
        const appContent = document.getElementById("app-content");
        if (appContent) {
            appContent.classList.add("visible");
            // The initParticles function from onMount is not automatically called, 
            // so we might need to trigger it here if it's still needed.
            // For now, let's assume it should be called when the app becomes visible.
            const main = document.querySelector("main");
            if (!main) return;
            for(let i=0; i<15; i++) {
                createParticle(main);
            }
        }
    }

    function createParticle(container) {
        const particle = document.createElement("div");
        particle.classList.add("particle");
        
        const size = Math.random() * 100 + 50;
        particle.style.width = `${size}px`;
        particle.style.height = `${size}px`;
        particle.style.left = `${Math.random() * 100}%`;
        particle.style.top = `${Math.random() * 100}%`;
        
        const duration = Math.random() * 20 + 10;
        particle.style.transition = `all ${duration}s linear`;
        
        container.appendChild(particle);
        
        setTimeout(() => moveParticle(particle), 100);
    }

    function moveParticle(particle) {
        if (!particle) return;
        particle.style.transform = `translate(${Math.random() * 200 - 100}px, ${Math.random() * 200 - 100}px) scale(${Math.random() * 0.5 + 0.8})`;
        particle.style.opacity = Math.random() * 0.3 + 0.1;
        
        setTimeout(() => moveParticle(particle), parseFloat(particle.style.transitionDuration) * 1000);
    }
</script>

<svelte:head>
    <title>Daniel Jabaraj V - Full Stack Developer</title>
</svelte:head>

<!-- Ambient Background -->
<div class="fixed inset-0 z-[-1] overflow-hidden pointer-events-none">
    <div class="absolute top-0 left-1/4 w-96 h-96 bg-primary/20 rounded-full mix-blend-screen filter blur-[100px] animate-blob"></div>
    <div class="absolute top-1/4 right-1/4 w-96 h-96 bg-accent/20 rounded-full mix-blend-screen filter blur-[100px] animate-blob" style="animation-delay: 2s;"></div>
    <div class="absolute -bottom-32 left-1/3 w-96 h-96 bg-neon/20 rounded-full mix-blend-screen filter blur-[100px] animate-blob" style="animation-delay: 4s;"></div>
</div>

<Preloader on:animationDone={handleAnimationDone} />

<div id="app-content" class="min-h-screen flex flex-col relative {appVisible ? 'visible' : ''}">
    <Navigation />

        <Hero />

        <Skills />

        <SoftSkills />

        <Education />

        <Experience />

        <Projects />

        <Collaboration />

        <Certifications />

        <Contact />

        <FloatingWhatsApp />

        <Footer />
</div>
