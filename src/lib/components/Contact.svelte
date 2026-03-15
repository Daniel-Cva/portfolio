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
            <button type="submit" class="w-full py-4 rounded-xl bg-linear-to-r from-primary to-accent text-white font-bold hover:shadow-[0_0_30px_rgba(168,85,247,0.4)] transition-all">
                Send Message <i class="fa-solid fa-paper-plane ml-2"></i>
            </button>
        </form>
    </div>
</section>