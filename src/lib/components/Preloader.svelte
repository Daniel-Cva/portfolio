<script>
    import { onMount, createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    let isTransitioning = false;

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
        const terminalAnim = document.getElementById("terminal-anim");
        const preloader = document.getElementById("preloader");
        
        if (!typewriter) return;

        let lineIndex = 0;
        let charIndex = 0;
        let stopTyping = false;
        
        function typeText() {
            if (stopTyping) return;
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
                setTimeout(transitionToApp, 800);
            }
        }

        function transitionToApp() {
            if (isTransitioning || !terminalAnim || !preloader) return;
            isTransitioning = true;
            stopTyping = true;

            terminalAnim.style.transition = "all 0.8s cubic-bezier(0.85, 0, 0.15, 1)";
            terminalAnim.style.transform = "scale(1.5) translateY(-50px) perspective(500px) rotateX(20deg)";
            terminalAnim.style.opacity = "0";
            terminalAnim.style.filter = "blur(10px) brightness(2)";
            
            setTimeout(() => {
                preloader.style.opacity = "0";
                preloader.style.pointerEvents = "none";
                
                setTimeout(() => {
                    preloader.style.display = "none";
                    dispatch('animationDone');
                }, 500);
            }, 600);
        }

        window.skipPreloader = transitionToApp;
        setTimeout(typeText, 500);
    });
</script>

<div id="preloader" class="flex flex-col items-center justify-center">
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
    
    <button 
        on:click={() => window.skipPreloader?.()}
        class="mt-8 px-6 py-2 rounded-full border border-primary/20 bg-primary/5 text-primary text-[10px] font-bold uppercase tracking-[0.2em] hover:bg-primary/10 hover:border-primary/40 transition-all duration-300 animate-pulse"
    >
        Skip Intro <i class="fa-solid fa-angles-right ml-2 opacity-50"></i>
    </button>
</div>
