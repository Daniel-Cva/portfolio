<script>
    import { onMount } from 'svelte';

    onMount(() => {
        const lines = [
            "Initializing workspace environment...",
            "Loading dependencies: [HTML5, TailwindCSS, Vanilla JS]...",
            "Pulling credentials: Daniel Jabaraj V",
            "> Role: Full Stack Developer & Designer",
            "> Education: B.E. CSE Final Year",
            "> Status: Freelancer & Ex-MLSA",
            "Compiling creative assets...",
            "Injecting fluid animations...",
            "Building interface...",
            "Deployment Successful. Welcome."
        ];

        const typewriter = document.getElementById("typewriter");
        const cursor = document.getElementById("cursor");
        const preloader = document.getElementById("preloader");
        const appContent = document.getElementById("app-content");
        const terminalAnim = document.getElementById("terminal-anim");
        
        if (!typewriter) return;

        let lineIndex = 0;
        let charIndex = 0;
        let isTyping = true;
        
        function typeText() {
            if (lineIndex < lines.length) {
                if (charIndex < lines[lineIndex].length) {
                    typewriter.innerHTML += lines[lineIndex].charAt(charIndex);
                    charIndex++;
                    
                    const speed = lines[lineIndex].charAt(charIndex-1) === '.' ? 150 : (Math.random() * 30 + 10);
                    setTimeout(typeText, speed);
                } else {
                    typewriter.innerHTML += "<br>";
                    lineIndex++;
                    charIndex = 0;
                    setTimeout(typeText, 250); 
                }
            } else {
                isTyping = false;
                setTimeout(transitionToApp, 800);
            }
        }

        function transitionToApp() {
            if (!terminalAnim || !preloader || !appContent) return;
            terminalAnim.style.transition = "all 0.8s cubic-bezier(0.85, 0, 0.15, 1)";
            terminalAnim.style.transform = "scale(1.5) translateY(-50px) perspective(500px) rotateX(20deg)";
            terminalAnim.style.opacity = "0";
            terminalAnim.style.filter = "blur(10px) brightness(2)";
            
            setTimeout(() => {
                preloader.style.opacity = "0";
                preloader.style.pointerEvents = "none";
                
                setTimeout(() => {
                    preloader.style.display = "none";
                    appContent.classList.add("visible");
                    initParticles();
                }, 500);
            }, 600);
        }

        setTimeout(typeText, 500);

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

<!-- Spectacular Developing Animation Preloader -->
<div id="preloader">
    <div class="terminal-box" id="terminal-anim">
        <div class="terminal-header">
            <div class="terminal-dot dot-red"></div>
            <div class="terminal-dot dot-yellow"></div>
            <div class="terminal-dot dot-green"></div>
            <div class="ml-4 text-xs text-gray-400 font-mono">daniel_cva_portfolio.sh</div>
        </div>
        <div class="typewriter-text" id="typewriter"></div>
        <div class="cursor" id="cursor"></div>
    </div>
</div>

<div id="app-content" class="min-h-screen flex flex-col relative">
    <!-- Navigation -->
    <nav class="fixed w-full z-50 glass-panel border-b-0 rounded-none bg-dark/80 px-6 py-4">
        <div class="max-w-7xl mx-auto flex justify-between items-center">
            <a href="#top" class="text-2xl font-bold tracking-tighter">
                Daniel <span class="text-primary">Jabaraj</span>
            </a>
            <div class="hidden md:flex space-x-8 text-sm font-medium">
                <a href="#about" class="nav-link text-gray-300 hover:text-white transition-colors">About</a>
                <a href="#education" class="nav-link text-gray-300 hover:text-white transition-colors">Education</a>
                <a href="#skills" class="nav-link text-gray-300 hover:text-white transition-colors">Skills</a>
                <a href="#experience" class="nav-link text-gray-300 hover:text-white transition-colors">Experience</a>
                <a href="#certifications" class="nav-link text-gray-300 hover:text-white transition-colors">Certificates</a>
                <a href="#projects" class="nav-link text-gray-300 hover:text-white transition-colors">Projects</a>
                <a href="#collaboration" class="nav-link text-gray-300 hover:text-white transition-colors">Services</a>
            </div>
            <div>
                <a href="mailto:danieljabaraj218@gmail.com" class="px-5 py-2.5 rounded-full bg-linear-to-r from-primary to-accent text-white font-semibold text-sm hover:shadow-[0_0_20px_rgba(139,92,246,0.6)] transition-all duration-300">Hire Me</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <main class="grow flex items-center justify-center pt-32 pb-20 px-6" id="top">
        <div class="max-w-7xl w-full mx-auto grid md:grid-cols-2 gap-12 items-center">
            <div class="space-y-6 relative z-10">
                <div class="inline-flex items-center space-x-2 px-3 py-1 rounded-full border border-primary/30 bg-primary/10 text-primary text-xs font-mono mb-4 backdrop-blur-sm">
                    <span class="w-2 h-2 rounded-full bg-primary animate-pulse"></span>
                    <span>Available for Freelance & Immediate Join</span>
                </div>
                <h1 class="text-5xl md:text-7xl font-bold leading-tight tracking-tighter">
                    I conceptualize, <br>
                    design, and <br>
                    <span class="gradient-text">Develop ideas.</span>
                </h1>
                <p class="text-lg text-gray-400 max-w-lg leading-relaxed">
                    Final year CSE student from <span class="text-white">Mayiladuthurai</span>, Ex-Microsoft Learn Student Ambassador, and an ever-learning Full Stack Developer. I build exceptional, high-performance digital experiences from raw concepts with a focus on leadership and motivation.
                </p>
                <div class="flex flex-col gap-2 pb-2">
                    <div class="flex items-center gap-3 text-sm text-gray-400">
                        <i class="fa-solid fa-earth-americas text-primary w-4"></i>
                        <span>Tamil & English</span>
                    </div>
                    <div class="flex items-center gap-3 text-sm text-gray-400">
                        <i class="fa-solid fa-location-dot text-primary w-4"></i>
                        <span>Mayiladuthurai, Tamil Nadu</span>
                    </div>
                </div>
                <div class="flex flex-wrap gap-4 pt-4">
                    <a href="#projects" class="group px-6 py-3 rounded-xl bg-white text-dark font-semibold hover:bg-gray-200 transition-all flex items-center gap-2">
                        View Work <i class="fa-solid fa-arrow-right group-hover:translate-x-1 transition-transform"></i>
                    </a>
                    <a href="/docs/Daniel_Jabaraj_Resume.pdf" download class="group px-6 py-3 rounded-xl border border-primary/40 bg-primary/5 text-primary font-semibold hover:bg-primary/10 transition-all flex items-center gap-2">
                        <i class="fa-solid fa-file-pdf"></i> Resume
                    </a>
                    <a href="https://github.com/Daniel-Cva" target="_blank" rel="noopener noreferrer" class="px-6 py-3 rounded-xl glass-panel text-white font-semibold hover:bg-white/10 transition-all flex items-center gap-2">
                        <i class="fa-brands fa-github text-xl"></i> GitHub
                    </a>
                    <a href="https://www.linkedin.com/in/daniel-jabaraj/" target="_blank" rel="noopener noreferrer" class="px-6 py-3 rounded-xl glass-panel text-white font-semibold hover:text-[#0a66c2] hover:bg-white/10 transition-all flex items-center gap-2">
                        <i class="fa-brands fa-linkedin text-xl"></i> LinkedIn
                    </a>
                    <a href="https://wa.me/918778752448" target="_blank" rel="noopener noreferrer" class="px-6 py-3 rounded-xl border border-green-500/30 bg-green-500/5 text-green-500 font-semibold hover:bg-green-500/10 transition-all flex items-center gap-2">
                        <i class="fa-brands fa-whatsapp text-xl"></i> WhatsApp
                    </a>
                </div>
            </div>
            
            <div class="relative flex justify-center mt-12 md:mt-0 perspective-1000">
                <!-- Glassmorphic ID Card -->
                <div class="relative w-80 h-[420px] glass-panel rounded-3xl p-6 flex flex-col items-center border-t border-l border-white/20 shadow-2xl transform hover:rotate-y-12 transition-transform duration-500 overflow-hidden group">
                    <div class="absolute inset-0 bg-linear-to-br from-primary/10 to-accent/10 opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                    
                    <div class="w-32 h-32 rounded-full border-4 border-primary/40 overflow-hidden shadow-[0_0_30px_rgba(59,130,246,0.5)] mb-6 relative">
                        <!-- Abstract Placeholder for Avatar since we don't have user image -->
                        <div class="w-full h-full bg-linear-to-tr from-dark to-gray-800 flex items-center justify-center text-4xl font-bold text-white/50">
                            D<span class="text-primary">J</span>
                        </div>
                    </div>
                    
                    <h3 class="text-2xl font-bold mb-1">Daniel Jabaraj V</h3>
                    <p class="text-primary font-mono text-sm mb-6">@Daniel-Cva</p>
                    
                    <div class="w-full space-y-3">
                        <div class="flex justify-between items-center text-sm">
                            <span class="text-gray-400">Role</span>
                            <span class="font-medium">Full Stack & Designer</span>
                        </div>
                        <div class="flex justify-between items-center text-sm">
                            <span class="text-gray-400">Education</span>
                            <span class="font-medium">B.E. CSE (Final Year)</span>
                        </div>
                        <div class="flex justify-between items-center text-sm">
                            <span class="text-gray-400">Experience</span>
                            <span class="font-medium">Intern @ Ahopez</span>
                        </div>
                    </div>
                    <div class="mt-auto w-full pt-4 border-t border-white/10 text-center">
                        <span class="text-xs text-gray-500 flex items-center justify-center gap-2">
                            <i class="fa-solid fa-gem text-accent"></i> Ex-MLSA
                        </span>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Dynamic Tech Stack Marquees -->
    <div id="skills" class="py-12 space-y-8">
        <!-- Technical Skills Marquee -->
        <div class="py-6 border-y border-white/5 bg-white/2 overflow-hidden whitespace-nowrap relative">
            <div class="absolute left-0 top-0 w-32 h-full bg-linear-to-r from-dark to-transparent z-10"></div>
            <div class="absolute right-0 top-0 w-32 h-full bg-linear-to-l from-dark to-transparent z-10"></div>
            
            <div class="inline-block animate-[scroll_30s_linear_infinite]">
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-primary transition-colors cursor-default tracking-widest">JAVA</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-accent transition-colors cursor-default tracking-widest">SPRING BOOT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#ff3e00] transition-colors cursor-default tracking-widest">SVELTEKIT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#f7df1e] transition-colors cursor-default tracking-widest">JAVASCRIPT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#0052cc] transition-colors cursor-default tracking-widest">RESTFUL API</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#003B57] transition-colors cursor-default tracking-widest">MYSQL</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#f38020] transition-colors cursor-default tracking-widest">CLOUDFLARE D1</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#38bdf8] transition-colors cursor-default tracking-widest">TAILWIND CSS</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#f05032] transition-colors cursor-default tracking-widest">GIT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#a259ff] transition-colors cursor-default tracking-widest">FIGMA</span>
            </div>
            <!-- Duplicated for seamless loop -->
            <div class="inline-block animate-[scroll_30s_linear_infinite]">
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-primary transition-colors cursor-default tracking-widest">JAVA</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-accent transition-colors cursor-default tracking-widest">SPRING BOOT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#ff3e00] transition-colors cursor-default tracking-widest">SVELTEKIT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#f7df1e] transition-colors cursor-default tracking-widest">JAVASCRIPT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#0052cc] transition-colors cursor-default tracking-widest">RESTFUL API</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#003B57] transition-colors cursor-default tracking-widest">MYSQL</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#f38020] transition-colors cursor-default tracking-widest">CLOUDFLARE D1</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#38bdf8] transition-colors cursor-default tracking-widest">TAILWIND CSS</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#f05032] transition-colors cursor-default tracking-widest">GIT</span>
                <span class="mx-8 text-2xl font-bold text-white/20 hover:text-[#a259ff] transition-colors cursor-default tracking-widest">FIGMA</span>
            </div>
        </div>

        <!-- AI Automation Tools Marquee (Reverse Scroll) -->
        <div class="py-6 border-y border-white/5 bg-white/2 overflow-hidden whitespace-nowrap relative">
            <div class="absolute left-0 top-0 w-32 h-full bg-linear-to-r from-dark to-transparent z-10"></div>
            <div class="absolute right-0 top-0 w-32 h-full bg-linear-to-l from-dark to-transparent z-10"></div>
            
            <div class="inline-block animate-[scroll-reverse_25s_linear_infinite]">
                <span class="mx-8 text-2xl font-bold text-accent px-4 border border-accent/20 rounded-lg">GEMINI</span>
                <span class="mx-8 text-2xl font-bold text-white px-4 border border-white/20 rounded-lg">GITHUB COPILOT</span>
                <span class="mx-8 text-2xl font-bold text-[#d97757] px-4 border border-[#d97757]/20 rounded-lg">CLAUDE</span>
                <span class="mx-8 text-2xl font-bold text-[#10a37f] px-4 border border-[#10a37f]/20 rounded-lg">STITCH</span>
                <span class="mx-8 text-2xl font-bold text-primary px-4 border border-primary/20 rounded-lg">MICROSOFT COPILOT</span>
            </div>
            <!-- Duplicated for seamless loop -->
            <div class="inline-block animate-[scroll-reverse_25s_linear_infinite]">
                <span class="mx-8 text-2xl font-bold text-accent px-4 border border-accent/20 rounded-lg">GEMINI</span>
                <span class="mx-8 text-2xl font-bold text-white px-4 border border-white/20 rounded-lg">GITHUB COPILOT</span>
                <span class="mx-8 text-2xl font-bold text-[#d97757] px-4 border border-[#d97757]/20 rounded-lg">CLAUDE</span>
                <span class="mx-8 text-2xl font-bold text-[#10a37f] px-4 border border-[#10a37f]/20 rounded-lg">STITCH</span>
                <span class="mx-8 text-2xl font-bold text-primary px-4 border border-primary/20 rounded-lg">MICROSOFT COPILOT</span>
            </div>
        </div>
    </div>

    <!-- Soft Skills & Values - PREMIUM REDESIGN -->
    <section class="py-24 px-6 max-w-7xl mx-auto w-full">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
            <div class="glass-panel p-8 text-center border border-white/5 hover:border-primary/50 transition-all group relative overflow-hidden">
                <div class="absolute inset-0 bg-linear-to-b from-primary/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                <div class="relative z-10">
                    <div class="w-16 h-16 mx-auto mb-6 bg-primary/10 rounded-2xl flex items-center justify-center group-hover:scale-110 group-hover:rotate-6 transition-transform duration-500">
                        <i class="fa-solid fa-brain text-4xl text-primary"></i>
                    </div>
                    <h4 class="text-lg font-bold text-white mb-2 uppercase tracking-tighter">Analytical</h4>
                    <p class="text-[10px] uppercase tracking-widest text-gray-500 font-bold">Problem Solving</p>
                </div>
            </div>

            <div class="glass-panel p-8 text-center border border-white/5 hover:border-accent/50 transition-all group relative overflow-hidden">
                <div class="absolute inset-0 bg-linear-to-b from-accent/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                <div class="relative z-10">
                    <div class="w-16 h-16 mx-auto mb-6 bg-accent/10 rounded-2xl flex items-center justify-center group-hover:scale-110 group-hover:-rotate-6 transition-transform duration-500">
                        <i class="fa-solid fa-people-group text-3xl text-accent"></i>
                    </div>
                    <h4 class="text-lg font-bold text-white mb-2 uppercase tracking-tighter">Teamwork</h4>
                    <p class="text-[10px] uppercase tracking-widest text-gray-500 font-bold">Global Collaboration</p>
                </div>
            </div>

            <div class="glass-panel p-8 text-center border border-white/5 hover:border-neon/50 transition-all group relative overflow-hidden">
                <div class="absolute inset-0 bg-linear-to-b from-neon/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                <div class="relative z-10">
                    <div class="w-16 h-16 mx-auto mb-6 bg-neon/10 rounded-2xl flex items-center justify-center group-hover:scale-110 group-hover:rotate-6 transition-transform duration-500">
                        <i class="fa-solid fa-rocket text-3xl text-neon"></i>
                    </div>
                    <h4 class="text-lg font-bold text-white mb-2 uppercase tracking-tighter">Proactive</h4>
                    <p class="text-[10px] uppercase tracking-widest text-gray-500 font-bold">Self Motivated</p>
                </div>
            </div>

            <div class="glass-panel p-8 text-center border border-white/5 hover:border-orange-400/50 transition-all group relative overflow-hidden">
                <div class="absolute inset-0 bg-linear-to-b from-orange-400/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity"></div>
                <div class="relative z-10">
                    <div class="w-16 h-16 mx-auto mb-6 bg-orange-400/10 rounded-2xl flex items-center justify-center group-hover:scale-110 group-hover:-rotate-6 transition-transform duration-500">
                        <i class="fa-solid fa-lightbulb text-3xl text-orange-400"></i>
                    </div>
                    <h4 class="text-lg font-bold text-white mb-2 uppercase tracking-tighter">Creative</h4>
                    <p class="text-[10px] uppercase tracking-widest text-gray-500 font-bold">Solution Designer</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Education Section -->
    <section id="education" class="py-24 px-6 max-w-7xl mx-auto w-full">
        <h2 class="text-sm text-accent font-mono tracking-widest uppercase mb-2">Academics</h2>
        <h3 class="text-4xl font-bold mb-12 uppercase">Education Path</h3>
        <div class="relative border-l border-white/10 pl-8 ml-4 space-y-16">
            <!-- College -->
            <div class="relative">
                <span class="absolute -left-[41px] top-0 w-5 h-5 rounded-full bg-accent shadow-[0_0_15px_rgba(139,92,246,0.6)] border-4 border-dark"></span>
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-2 mb-4">
                    <h4 class="text-xl font-bold uppercase">B.E. in Computer Science and Engineering (Anna University)</h4>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-accent whitespace-nowrap">2022 – 2026</span>
                </div>
                <p class="text-white font-medium mb-1">As-Salam College of Engineering & Technology</p>
                <div class="flex items-center gap-2 mb-2">
                    <span class="text-xs bg-accent/20 text-accent px-2 py-0.5 rounded">CGPA: 8.0</span>
                </div>
            </div>

            <!-- HSC -->
            <div class="relative">
                <span class="absolute -left-[41px] top-0 w-5 h-5 rounded-full bg-white/20 border-4 border-dark"></span>
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-2 mb-4">
                    <h4 class="text-xl font-bold uppercase">HSC: Vocational (Basic Mechanical Engineering)</h4>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-gray-400 whitespace-nowrap">Graduated: 2022</span>
                </div>
                <p class="text-white font-medium mb-1">Sambantham Higher Secondary School</p>
                <div class="flex items-center gap-2 mb-2">
                    <span class="text-xs bg-white/5 text-gray-400 px-2 py-0.5 rounded">Marks: 447/600 (74.5%)</span>
                </div>
            </div>

            <!-- SSLC -->
            <div class="relative">
                <span class="absolute -left-[41px] top-0 w-5 h-5 rounded-full bg-white/10 border-4 border-dark"></span>
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-2 mb-4">
                    <h4 class="text-xl font-bold uppercase">SSLC</h4>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-gray-500 whitespace-nowrap">Graduated: 2020</span>
                </div>
                <p class="text-white font-medium mb-1">Kalaimahal Matriculation School</p>
                <div class="flex items-center gap-2 mb-2">
                    <span class="text-xs bg-white/5 text-gray-500 px-2 py-0.5 rounded">Marks: 342/500 (68%)</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Experience & Projects Grid -->
    <section id="experience" class="py-24 px-6 max-w-7xl mx-auto w-full">
        <h2 class="text-sm text-primary font-mono tracking-widest uppercase mb-2">Journey</h2>
        <h3 class="text-4xl font-bold mb-12">Experience <span class="text-gray-600">&</span> Engagements</h3>
        
        <div class="grid md:grid-cols-2 gap-8">
            <!-- Ahopez Internship -->
            <div class="glass-panel p-8 relative overflow-hidden group">
                <div class="absolute top-0 right-0 w-32 h-32 bg-primary/10 rounded-full blur-3xl -mr-10 -mt-10 group-hover:bg-primary/20 transition-all duration-500"></div>
                <div class="flex justify-between items-start mb-6">
                    <div>
                        <h4 class="text-2xl font-bold">Full Stack Intern</h4>
                        <p class="text-primary font-medium mt-1">Ahopez Innovation</p>
                    </div>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-gray-300">Dec 2025 – Present</span>
                </div>
                <ul class="space-y-3 text-gray-400 text-sm leading-relaxed">
                    <li class="flex gap-3"><i class="fa-solid fa-check text-primary mt-1 text-xs"></i> <span>Developed responsive client-facing web apps using Svelte, SvelteKit & TailwindCSS.</span></li>
                    <li class="flex gap-3"><i class="fa-solid fa-check text-primary mt-1 text-xs"></i> <span>Integrated serverless backend architecture utilizing Cloudflare D1 databases.</span></li>
                    <li class="flex gap-3"><i class="fa-solid fa-check text-primary mt-1 text-xs"></i> <span>Collaborated extensively with internal teams to establish robust company workflows.</span></li>
                </ul>
            </div>

            <!-- Microsoft MLSA -->
            <div class="glass-panel p-8 relative overflow-hidden group">
                <div class="absolute top-0 right-0 w-32 h-32 bg-accent/10 rounded-full blur-3xl -mr-10 -mt-10 group-hover:bg-accent/20 transition-all duration-500"></div>
                <div class="flex justify-between items-start mb-6">
                    <div>
                        <h4 class="text-2xl font-bold uppercase tracking-tight">Student Ambassador</h4>
                        <p class="text-accent font-medium mt-1 uppercase text-xs tracking-widest">Microsoft Learn</p>
                    </div>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-gray-300">Jun 2024 – Sep 2025</span>
                </div>
                <ul class="space-y-3 text-gray-400 text-sm leading-relaxed">
                    <li class="flex gap-3"><i class="fa-solid fa-check text-accent mt-1 text-xs"></i> <span>Organized and conducted <strong>10+ in-person technical workshops</strong> in college campus.</span></li>
                    <li class="flex gap-3"><i class="fa-solid fa-check text-accent mt-1 text-xs"></i> <span>Mentored peers in foundational programming and cloud concepts.</span></li>
                    <li class="flex gap-3"><i class="fa-solid fa-check text-accent mt-1 text-xs"></i> <span>Collaborated with a global network to foster a thriving local developer community.</span></li>
                </ul>
            </div>

            <!-- Career Guidance Collaboration -->
            <div class="glass-panel p-8 relative overflow-hidden group border-blue-500/10 hover:border-blue-500/30 transition-colors">
                <div class="absolute top-0 right-0 w-32 h-32 bg-blue-500/5 rounded-full blur-3xl -mr-10 -mt-10 group-hover:bg-blue-500/10 transition-all duration-500"></div>
                <div class="flex justify-between items-start mb-6">
                    <div>
                        <h4 class="text-2xl font-bold uppercase tracking-tight">Career Guidance Session</h4>
                        <p class="text-blue-400 font-medium mt-1 uppercase text-xs tracking-widest">Collab with Christober S (MLSA)</p>
                    </div>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-gray-400">Sep 2024</span>
                </div>
                <p class="text-gray-400 text-sm leading-relaxed mb-4">
                    Co-hosted an impactful career guidance session focused on navigating the tech industry, building a professional brand, and leveraging student opportunities.
                </p>
                <div class="pt-2">
                     <a href="https://www.linkedin.com/posts/christobers_every-single-talk-i-give-is-special-every-activity-7236395351648129026-Duui" target="_blank" rel="noopener noreferrer" class="text-xs font-mono text-blue-400 hover:text-white transition-colors flex items-center gap-2">
                        <i class="fa-brands fa-linkedin text-lg"></i> LINKEDIN POST <i class="fa-solid fa-arrow-right -rotate-45"></i>
                     </a>
                </div>
            </div>

            <!-- AWS Workshop Spotlight -->
            <div class="glass-panel p-8 relative overflow-hidden group border-orange-500/10 hover:border-orange-500/30 transition-colors">
                <div class="absolute top-0 right-0 w-32 h-32 bg-orange-500/5 rounded-full blur-3xl -mr-10 -mt-10 group-hover:bg-orange-500/10 transition-all duration-500"></div>
                <div class="flex justify-between items-start mb-6">
                    <div>
                        <h4 class="text-2xl font-bold uppercase tracking-tight">AWS Cloud Workshop</h4>
                        <p class="text-orange-400 font-medium mt-1 uppercase text-xs tracking-widest">In-Person Technical Session</p>
                    </div>
                    <span class="text-xs font-mono px-3 py-1 glass-panel rounded-full text-gray-400">Nov 2023</span>
                </div>
                <p class="text-gray-400 text-sm leading-relaxed mb-4">
                    Spearheaded an intensive AWS Cloud session at As-Salam College with Christober S, covering infrastructure, serverless tech, and IAM security for 100+ students.
                </p>
                <div class="pt-2">
                     <a href="https://christobers.medium.com/unveiling-the-power-of-aws-in-a-student-centric-event-7a896bf5ff32" target="_blank" rel="noopener noreferrer" class="text-xs font-mono text-orange-400 hover:text-white transition-colors flex items-center gap-2">
                        <i class="fa-brands fa-medium text-lg"></i> MEDIUM BLOG <i class="fa-solid fa-arrow-right -rotate-45"></i>
                     </a>
                </div>
            </div>
        </div>
    </section>

    <!-- Selected Projects -->
    <section id="projects" class="py-24 px-6 max-w-7xl mx-auto w-full">
        <h2 class="text-sm text-neon font-mono tracking-widest uppercase mb-2">Portfolio</h2>
        <h3 class="text-4xl font-bold mb-12">Selected Projects</h3>

        <div class="space-y-10">
            <!-- Project 1 -->
            <div class="glass-panel p-1 rounded-2xl bg-linear-to-r from-primary/20 via-transparent to-transparent group hover:from-primary/40 transition-all duration-500">
                <div class="bg-dark/90 backdrop-blur-xl rounded-xl p-8 flex flex-col md:flex-row gap-8 items-center border border-white/5">
                    <div class="flex-1 space-y-4">
                        <div class="flex gap-2 mb-2">
                            <span class="px-2 py-1 bg-white/5 rounded text-xs text-gray-300 font-mono">SvelteKit</span>
                            <span class="px-2 py-1 bg-white/5 rounded text-xs text-gray-300 font-mono">Cloudflare D1</span>
                        </div>
                        <h4 class="text-3xl font-bold text-white group-hover:text-transparent group-hover:bg-clip-text group-hover:bg-linear-to-r group-hover:from-white group-hover:to-primary transition-all">Hyper-Local Reverse E-Commerce</h4>
                        <p class="text-gray-400 leading-relaxed text-sm">
                            A revolutionary platform empowering local Indian shops against e-commerce giants by reversing the flow. Users post requirements, and nearby providers send targeted quotes. Includes real-time founder networking, live location sharing, and completely seller-spam-free neighborhood commerce.
                        </p>
                        <div class="pt-4 flex items-center gap-4 text-sm font-medium">
                            <span class="text-primary"><i class="fa-solid fa-building mr-2"></i>Ahopez Collab</span>
                            <a href="#projects" class="text-gray-400 hover:text-white transition-colors">Ongoing <i class="fa-solid fa-arrow-right ml-1 -rotate-45"></i></a>
                        </div>
                    </div>
                    <div class="w-full md:w-1/3 aspect-video bg-linear-to-br from-gray-900 to-black rounded-xl border border-white/10 relative overflow-hidden shadow-2xl flex items-center justify-center">
                        <i class="fa-solid fa-store text-6xl text-white/10 group-hover:scale-110 group-hover:text-primary/20 transition-all duration-500"></i>
                        <div class="absolute inset-0 bg-blue-500/5 mix-blend-overlay"></div>
                    </div>
                </div>
            </div>

            <!-- Project 2 -->
            <div class="glass-panel p-1 rounded-2xl bg-linear-to-r from-transparent via-transparent to-accent/20 group hover:to-accent/40 transition-all duration-500">
                <div class="bg-dark/90 backdrop-blur-xl rounded-xl p-8 flex flex-col md:flex-row-reverse gap-8 items-center border border-white/5">
                    <div class="flex-1 space-y-4 text-right">
                        <div class="flex gap-2 mb-2 justify-end">
                            <span class="px-2 py-1 bg-white/5 rounded text-xs text-gray-300 font-mono">Java</span>
                            <span class="px-2 py-1 bg-white/5 rounded text-xs text-gray-300 font-mono">Spring Boot</span>
                            <span class="px-2 py-1 bg-white/5 rounded text-xs text-gray-300 font-mono">MySQL</span>
                        </div>
                        <h4 class="text-3xl font-bold text-white group-hover:text-transparent group-hover:bg-clip-text group-hover:bg-linear-to-l group-hover:from-white group-hover:to-accent transition-all">EMS REST API</h4>
                        <p class="text-gray-400 leading-relaxed text-sm">
                            A highly robust Employee Management System backend. Engineered using Java and Spring Boot, establishing highly scalable RESTful endpoints. Showcases standardized CRUD operations, complex cross-table queries using MySQL via JDBC, and a secure modular integration structure.
                        </p>
                        <div class="pt-4 flex items-center justify-end gap-4 text-sm font-medium">
                            <a href="https://github.com/Daniel-Cva" target="_blank" rel="noopener noreferrer" class="text-gray-400 hover:text-white transition-colors"><i class="fa-brands fa-github mr-2"></i>Source Code</a>
                        </div>
                    </div>
                    <div class="w-full md:w-1/3 aspect-video bg-linear-to-br from-gray-900 to-black rounded-xl border border-white/10 relative overflow-hidden shadow-2xl flex items-center justify-center">
                        <i class="fa-solid fa-server text-6xl text-white/10 group-hover:scale-110 group-hover:text-accent/20 transition-all duration-500"></i>
                        <div class="absolute inset-x-0 bottom-0 h-1 bg-accent/50 shadow-[0_0_20px_rgba(139,92,246,0.8)]"></div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Collaboration & Community Services -->
    <section id="collaboration" class="py-24 px-6 max-w-7xl mx-auto w-full">
        <h2 class="text-sm text-neon font-mono tracking-widest uppercase mb-2">Team Effort</h2>
        <h3 class="text-4xl font-bold mb-4 uppercase">Community <span class="text-gray-600">&</span> Collaboration</h3>
        <p class="text-gray-400 mb-12 max-w-2xl">I work alongside a talented network of developer friends to deliver high-quality digital solutions. Together, we bring diverse expertise to every project.</p>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-6">
            <div class="glass-panel p-6 border-l-4 border-primary hover:bg-white/5 transition-colors">
                <i class="fa-solid fa-code text-2xl text-primary mb-4 block"></i>
                <h5 class="font-bold text-white mb-2 uppercase">Web Solutions</h5>
                <p class="text-xs text-gray-400">Website building & High-performance Web Applications using Svelte and SvelteKit.</p>
            </div>
            <div class="glass-panel p-6 border-l-4 border-accent hover:bg-white/5 transition-colors">
                <i class="fa-solid fa-mobile-screen-button text-2xl text-accent mb-4 block"></i>
                <h5 class="font-bold text-white mb-2 uppercase">App Development</h5>
                <p class="text-xs text-gray-400">Robust Android Applications and multi-platform solutions for modern businesses.</p>
            </div>
            <div class="glass-panel p-6 border-l-4 border-green-500 hover:bg-white/5 transition-colors">
                <i class="fa-solid fa-bullhorn text-2xl text-green-500 mb-4 block"></i>
                <h5 class="font-bold text-white mb-2 uppercase">Marketing Mastery</h5>
                <p class="text-xs text-gray-400">WhatsApp Marketing, Digital Marketing, and AI-driven Video Marketing strategies.</p>
            </div>
            <div class="glass-panel p-6 border-l-4 border-blue-400 hover:bg-white/5 transition-colors">
                <i class="fa-solid fa-file-invoice-dollar text-2xl text-blue-400 mb-4 block"></i>
                <h5 class="font-bold text-white mb-2 uppercase">Business Systems</h5>
                <p class="text-xs text-gray-400">Professional POS, Billing, and Invoice Softwares tailored for your growth.</p>
            </div>
            <div class="glass-panel p-6 border-l-4 border-orange-400 hover:bg-white/5 transition-colors">
                <i class="fa-solid fa-palette text-2xl text-orange-400 mb-4 block"></i>
                <h5 class="font-bold text-white mb-2 uppercase">Visual Design</h5>
                <p class="text-xs text-gray-400">Creative Poster design and digital assets that capture attention instantly.</p>
            </div>
        </div>
    </section>

    <!-- Certifications & Recognition - PREMIUM REDESIGN -->
    <section id="certifications" class="py-32 px-6 max-w-7xl mx-auto w-full relative">
        <div class="absolute top-0 left-1/2 -translate-x-1/2 w-1/2 h-1/2 bg-accent/5 blur-[120px] pointer-events-none"></div>
        
        <div class="flex flex-col md:flex-row md:items-end justify-between mb-16 gap-4">
            <div>
                <h2 class="text-sm text-accent font-mono tracking-[0.3em] uppercase mb-4 pl-1 border-l-2 border-accent">Recognition</h2>
                <h3 class="text-5xl md:text-6xl font-black uppercase tracking-tighter leading-none italic">Success <span class="text-gray-700 not-italic">&</span> Achievements</h3>
            </div>
            <p class="text-gray-500 font-mono text-xs uppercase tracking-widest max-w-[200px] text-right">Validated through global standards and community impact.</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <!-- MLSA Certificate -->
            <div class="group relative h-full">
                <div class="absolute inset-0 bg-accent/20 blur-2xl opacity-0 group-hover:opacity-40 transition-opacity duration-700"></div>
                <div class="glass-panel p-1 rounded-2xl relative border border-white/5 group-hover:border-accent/30 transition-all duration-500 h-full flex flex-col">
                    <div class="aspect-video rounded-xl overflow-hidden mb-6 relative bg-dark">
                        <img src="/images/swag_box.jpg" alt="MLSA Recognition" class="w-full h-full object-cover grayscale group-hover:grayscale-0 group-hover:scale-105 transition-all duration-700">
                        <div class="absolute inset-0 bg-linear-to-t from-dark via-transparent to-transparent opacity-60"></div>
                        <div class="absolute bottom-4 left-4">
                            <span class="px-2 py-1 bg-accent/20 border border-accent/30 text-[10px] font-bold text-accent uppercase rounded backdrop-blur-sm">BETA AMBASSADOR</span>
                        </div>
                    </div>
                    <div class="px-6 pb-8 space-y-4 grow flex flex-col">
                        <h4 class="text-xl font-bold uppercase tracking-tight group-hover:text-accent transition-colors">Microsoft Learn Student Ambassador</h4>
                        <p class="text-gray-400 text-xs leading-relaxed grow">Highest tier recognition for leading technical communities, conducting sessions, and fostering innovation globally.</p>
                        <div class="pt-4 border-t border-white/5">
                            <a href="/docs/MLSA/Beta MLSA.pdf" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 text-[10px] font-bold tracking-[0.2em] text-white hover:text-accent transition-colors">
                                VERIFY CREDENTIAL <i class="fa-solid fa-arrow-right -rotate-45"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Java Certificate -->
            <div class="group relative h-full">
                <div class="absolute inset-0 bg-primary/20 blur-2xl opacity-0 group-hover:opacity-40 transition-opacity duration-700"></div>
                <div class="glass-panel p-1 rounded-2xl relative border border-white/5 group-hover:border-primary/30 transition-all duration-500 h-full flex flex-col">
                    <div class="aspect-video rounded-xl overflow-hidden mb-6 relative bg-dark">
                        <img src="/images/java_certificate.png" alt="Java Certification" class="w-full h-full object-cover grayscale group-hover:grayscale-0 group-hover:scale-105 transition-all duration-700">
                        <div class="absolute inset-0 bg-linear-to-t from-dark via-transparent to-transparent opacity-60"></div>
                        <div class="absolute bottom-4 left-4">
                            <span class="px-2 py-1 bg-primary/20 border border-primary/30 text-[10px] font-bold text-primary uppercase rounded backdrop-blur-sm">BACKEND CORE</span>
                        </div>
                    </div>
                    <div class="px-6 pb-8 space-y-4 grow flex flex-col">
                        <h4 class="text-xl font-bold uppercase tracking-tight group-hover:text-primary transition-colors">Java Backend Development</h4>
                        <p class="text-gray-400 text-xs leading-relaxed grow">Certified in persistent storage, JDBC integration, and complex backend architecture logic for Java applications.</p>
                        <div class="pt-4 border-t border-white/5">
                            <div class="inline-flex items-center gap-2 text-[10px] font-bold tracking-[0.2em] text-primary uppercase">
                                VERIFIED SKILL <i class="fa-solid fa-certificate"></i>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Meta Specialization -->
            <div class="group relative h-full">
                <div class="absolute inset-0 bg-neon/20 blur-2xl opacity-0 group-hover:opacity-40 transition-opacity duration-700"></div>
                <div class="glass-panel p-1 rounded-2xl relative border border-white/5 group-hover:border-neon/30 transition-all duration-500 h-full flex flex-col">
                    <div class="aspect-video rounded-xl overflow-hidden mb-6 relative bg-linear-to-br from-gray-900 to-black flex items-center justify-center">
                        <i class="fa-solid fa-graduation-cap text-5xl text-neon/20 group-hover:text-neon group-hover:scale-110 transition-all duration-500"></i>
                        <div class="absolute bottom-4 left-4">
                            <span class="px-2 py-1 bg-neon/20 border border-neon/30 text-[10px] font-bold text-neon uppercase rounded backdrop-blur-sm">META CERTIFIED</span>
                        </div>
                    </div>
                    <div class="px-6 pb-8 space-y-4 grow flex flex-col">
                        <h4 class="text-xl font-bold uppercase tracking-tight group-hover:text-neon transition-colors">Meta Professional Specialization</h4>
                        <p class="text-gray-400 text-xs leading-relaxed grow">Authorized by Meta to build, test and deploy professional-grade full stack applications using industry-best practices.</p>
                        <div class="pt-4 border-t border-white/5">
                            <a href="/docs/COURSERA META.pdf" target="_blank" rel="noopener noreferrer" class="inline-flex items-center gap-2 text-[10px] font-bold tracking-[0.2em] text-white hover:text-neon transition-colors">
                                EXPLORE SYLLABUS <i class="fa-solid fa-arrow-right -rotate-45"></i>
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="py-24 px-6 max-w-3xl mx-auto w-full">
        <div class="glass-panel p-10 relative overflow-hidden">
            <div class="absolute -top-24 -right-24 w-48 h-48 bg-primary/20 rounded-full blur-3xl"></div>
            <h3 class="text-4xl font-bold mb-2 uppercase">Get in touch</h3>
            <p class="text-gray-400 mb-8">Discuss a project or just say hello.</p>
            
            <form class="space-y-6">
                <div class="grid md:grid-cols-2 gap-6">
                    <div class="space-y-2">
                        <label for="name" class="text-xs font-mono text-gray-500 uppercase">Name</label>
                        <input type="text" id="name" placeholder="John Doe" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-hidden focus:border-primary transition-colors">
                    </div>
                    <div class="space-y-2">
                        <label for="email" class="text-xs font-mono text-gray-500 uppercase">Email</label>
                        <input type="email" id="email" placeholder="john@example.com" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-hidden focus:border-primary transition-colors">
                    </div>
                </div>
                <div class="space-y-2">
                    <label for="message" class="text-xs font-mono text-gray-500 uppercase">Message</label>
                    <textarea id="message" rows="4" placeholder="How can I help you?" class="w-full bg-white/5 border border-white/10 rounded-xl px-4 py-3 text-white focus:outline-hidden focus:border-primary transition-colors"></textarea>
                </div>
                <button type="submit" class="w-full py-4 rounded-xl bg-linear-to-r from-primary to-accent text-white font-bold hover:shadow-[0_0_30px_rgba(59,130,246,0.4)] transition-all">
                    Send Message <i class="fa-solid fa-paper-plane ml-2"></i>
                </button>
            </form>
        </div>
    </section>

    <!-- Floating WhatsApp Button -->
    <a href="https://wa.me/918778752448" target="_blank" rel="noopener noreferrer" class="fixed bottom-8 right-8 z-100 w-14 h-14 bg-green-500 rounded-full flex items-center justify-center text-white text-3xl shadow-[0_0_20px_rgba(34,197,94,0.6)] hover:scale-110 hover:rotate-12 transition-all group">
        <i class="fa-brands fa-whatsapp"></i>
        <span class="absolute right-full mr-4 bg-dark/80 px-4 py-2 rounded-lg text-sm font-medium opacity-0 group-hover:opacity-100 transition-opacity pointer-events-none whitespace-nowrap border border-white/10">Chat on WhatsApp</span>
    </a>

    <!-- Footer -->
    <footer class="mt-auto border-t border-white/10 bg-dark/50 py-8 relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center text-gray-500 text-sm">
            <p>&copy; 2026 Daniel Jabaraj V. Designed & Coded from scratch.</p>
            <div class="flex flex-col md:flex-row gap-4 mt-4 md:mt-0 font-mono text-center md:text-right">
                <div class="flex flex-col">
                    <a href="mailto:danieljabaraj218@gmail.com" class="hover:text-primary transition-colors">danieljabaraj218@gmail.com</a>
                    <a href="mailto:danieljabarajv@gmail.com" class="hover:text-primary transition-colors">danieljabarajv@gmail.com</a>
                </div>
                <div class="hidden md:block">/</div>
                <div class="flex flex-col">
                    <a href="tel:+918778752448" class="hover:text-primary transition-colors">+91 877 875 2448</a>
                    <a href="tel:+919442673911" class="hover:text-primary transition-colors">+91 944 267 3911</a>
                </div>
            </div>
        </div>
    </footer>
</div>
