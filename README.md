import React, { useState } from 'react';
import { Github, Linkedin, Mail, Code, Download, DollarSign, Cpu, Monitor } from 'lucide-react';

const Portfolio = () => {
  const [activeTab, setActiveTab] = useState('all');

  return (
    <div className="min-h-screen bg-slate-900 text-slate-200 font-sans selection:bg-cyan-500 selection:text-white">
      
      {/* --- HERO SECTION --- */}
      <header className="container mx-auto px-6 py-24 flex flex-col items-center text-center">
        <div className="bg-gradient-to-r from-cyan-500 to-purple-600 p-1 rounded-full mb-6">
          <div className="bg-slate-900 rounded-full p-2">
            {/* Aquí iría tu foto */}
            <div className="w-32 h-32 rounded-full bg-slate-800 flex items-center justify-center text-4xl">👨‍💻</div>
          </div>
        </div>
        <h1 className="text-5xl md:text-7xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-cyan-400 to-purple-500 mb-4">
          Hola, soy [Tu Nombre]
        </h1>
        <p className="text-xl md:text-2xl text-slate-400 max-w-2xl">
          Desarrollador Full Stack & Diseñador UI/UX en formación.
        </p>
        <div className="mt-4 inline-block bg-slate-800/50 px-4 py-1 rounded-full border border-slate-700 backdrop-blur-sm">
          🎓 Estudiante de Informática @ <span className="text-cyan-400 font-semibold">Universidad de Oriente</span>
        </div>

        <div className="flex gap-4 mt-8">
          <SocialButton icon={<Github />} href="#" />
          <SocialButton icon={<Linkedin />} href="#" />
          <SocialButton icon={<Mail />} href="#" />
        </div>
      </header>

      {/* --- SKILLS SECTION --- */}
      <section className="container mx-auto px-6 py-16">
        <h2 className="text-3xl font-bold text-center mb-12 text-white">Mis Herramientas</h2>
        <div className="grid grid-cols-2 md:grid-cols-4 gap-6">
          <SkillCard title="React.js" icon={<Code className="text-cyan-400" />} desc="Hooks, Redux, Tailwind" />
          <SkillCard title="C# / .NET" icon={<Cpu className="text-purple-500" />} desc="Desktop Apps, Backend" />
          <SkillCard title="Python" icon={<Monitor className="text-yellow-400" />} desc="Scripting, Automatización" />
          <SkillCard title="Diseño Web" icon={<Monitor className="text-pink-400" />} desc="UI/UX, Responsive Design" />
        </div>
      </section>

      {/* --- PROJECTS SECTION (Highlight solicitado) --- */}
      <section className="bg-slate-900/50 py-16 relative">
        <div className="absolute inset-0 bg-gradient-to-b from-transparent via-cyan-900/10 to-transparent pointer-events-none" />
        <div className="container mx-auto px-6 relative z-10">
          <h2 className="text-4xl font-bold text-center mb-16 text-white">Proyectos Destacados</h2>
          
          <div className="grid md:grid-cols-2 gap-10">
            
            {/* PROYECTO 1: CONVERTIDOR DE DIVISAS */}
            <ProjectCard 
              title="VzlaCurrency Monitor"
              tags={["React", "API Integration", "Tailwind"]}
              icon={<DollarSign size={40} className="text-green-400" />}
              description="Aplicación web reactiva que monitorea y convierte Bolívares a Dólares/Euros en tiempo real. Integra APIs de tasas oficiales y paralelas para ofrecer cálculos precisos al usuario venezolano."
              gradient="from-green-500/20 to-emerald-500/5"
            />

            {/* PROYECTO 2: DESCARGADOR MULTIMEDIA */}
            <ProjectCard 
              title="PyMedia Downloader"
              tags={["Python", "FFmpeg", "Tkinter"]}
              icon={<Download size={40} className="text-red-400" />}
              description="Herramienta de escritorio robusta para la descarga y conversión de video/audio (MP4/MP3). Incluye gestión de rutas de guardado y metadatos automáticos para una biblioteca musical limpia."
              gradient="from-red-500/20 to-orange-500/5"
            />

          </div>
        </div>
      </section>

      {/* --- FOOTER --- */}
      <footer className="text-center py-10 text-slate-500 text-sm">
        <p>© 2026 [Tu Nombre]. Creado con React & Tailwind.</p>
        <p className="mt-2 opacity-50">Made by CannedStuna Studios</p>
      </footer>
    </div>
  );
};

// --- COMPONENTES AUXILIARES ---

const SocialButton = ({ icon, href }) => (
  <a href={href} className="p-3 bg-slate-800 rounded-full hover:bg-cyan-500 hover:text-white transition-all duration-300 hover:scale-110 border border-slate-700">
    {icon}
  </a>
);

const SkillCard = ({ title, icon, desc }) => (
  <div className="p-6 bg-slate-800/40 border border-slate-700/50 rounded-2xl hover:border-cyan-500/50 transition-all hover:bg-slate-800 group">
    <div className="mb-4 transform group-hover:scale-110 transition-transform duration-300">{icon}</div>
    <h3 className="text-xl font-bold text-slate-200">{title}</h3>
    <p className="text-slate-400 text-sm mt-2">{desc}</p>
  </div>
);

const ProjectCard = ({ title, tags, description, gradient, icon }) => (
  <div className={`rounded-3xl p-8 border border-slate-700/50 bg-gradient-to-br ${gradient} hover:border-slate-500 transition-all duration-300 hover:shadow-2xl hover:shadow-cyan-900/20 group`}>
    <div className="flex justify-between items-start mb-6">
      <div className="p-3 bg-slate-900 rounded-2xl border border-slate-700 group-hover:border-white/20 transition-colors">
        {icon}
      </div>
      <div className="flex gap-2">
        {tags.map((tag, i) => (
          <span key={i} className="text-xs font-mono py-1 px-3 rounded-full bg-slate-900/60 text-slate-300 border border-slate-700">
            {tag}
          </span>
        ))}
      </div>
    </div>
    <h3 className="text-2xl font-bold text-white mb-3 group-hover:text-cyan-400 transition-colors">{title}</h3>
    <p className="text-slate-300 leading-relaxed mb-6">
      {description}
    </p>
    <button className="text-sm font-bold text-white flex items-center gap-2 hover:gap-4 transition-all">
      Ver Repositorio <span>→</span>
    </button>
  </div>
);

export default Portfolio;
