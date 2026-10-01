<script setup lang="ts">
import { computed, ref, watch } from 'vue'

type Locale = 'en' | 'pt'

const locale = ref<Locale>('en')
const translations = {
  en: {
    title: 'Julia Boesing Ponticelli | Frontend Software Engineer',
    description: 'Portfolio of Julia Boesing Ponticelli, a software engineer focused on frontend, architecture, and web products.',
    languageSelector: 'Select language',
    navigationLabel: 'Main navigation',
    nav: { about: 'about', projects: 'projects', experience: 'experience', education: 'education', contact: "let's talk" },
    hero: { eyebrow: 'Software Engineer · Frontend', title: 'I build web products with', accent: 'intention.', intro: "I'm Julia Boesing Ponticelli, a software engineer with 8+ years of experience. I work across frontend architecture, accessible interfaces, and product delivery, building web products that can grow without losing quality.", journey: 'explore my experience', resume: 'download resume', portraitLabel: 'Portrait of Julia', portraitAlt: 'Julia Boesing Ponticelli', location: 'Porto Alegre · Brazil', caption: 'Frontend · Architecture · Product' },
    about: { label: '01 — about me', title: 'Great interfaces start with', accent: 'good questions.', paragraphs: ['I am a software engineer focused on frontend development, with experience in enterprise environments. I enjoy understanding the problem, organizing complex systems, and creating solutions that work for both the people who use them and the people who maintain them.', 'At Nelogica, I work on complex applications and take features from definition through production. Before that, I built financial products, joined innovation projects at SAP, and developed web, desktop, and virtual reality experiences.'], stats: [{ value: '8+', label: 'years in technology' }, { value: '4', label: 'companies and teams' }, { value: '01', label: 'global innovation award' }, { value: '3', label: 'languages' }] },
    projects: { label: '02 — selected projects', title: 'Built to solve', accent: 'real problems.', allLink: 'more projects on GitHub' },
    experience: { label: '03 — professional experience', title: 'A career shaped by', accent: 'product and engineering.', intro: 'From immersive experiences to financial platforms, every step has expanded my technical range and product perspective.' },
    education: { label: '04 — education', title: 'Always learning,', accent: 'always building.' },
    toolkit: { label: '05 — toolkit', title: 'Tools to build', accent: 'with care.', intro: 'I combine frontend fundamentals with software architecture, collaboration, and continuous product improvement.', languages: 'Languages', interests: 'Beyond the screen', interestsText: 'Software architecture, technology innovation, running, strength training, reading, and continuous learning.' },
    contact: { label: '06 — contact', title: "Let's", accent: 'talk.', intro: 'I enjoy exchanging ideas about frontend engineering, software architecture, and digital products.' },
    footer: { location: 'Porto Alegre, Brazil', backToTop: 'back to top ↑' },
  },
  pt: {
    title: 'Júlia Boesing Ponticelli | Engenharia Frontend',
    description: 'Portfólio de Júlia Boesing Ponticelli, engenheira de software com foco em frontend, arquitetura e produtos web.',
    languageSelector: 'Selecionar idioma',
    navigationLabel: 'Navegação principal',
    nav: { about: 'sobre', projects: 'projetos', experience: 'experiência', education: 'formação', contact: 'vamos conversar' },
    hero: { eyebrow: 'Engenheira de Software · Frontend', title: 'Construo produtos web com', accent: 'intenção.', intro: 'Sou Júlia Boesing Ponticelli, engenheira de software com mais de 8 anos de experiência. Trabalho com arquitetura frontend, interfaces acessíveis e produtos que crescem sem perder qualidade.', journey: 'minha trajetória', resume: 'baixar currículo', portraitLabel: 'Retrato de Júlia', portraitAlt: 'Júlia Boesing Ponticelli', location: 'Porto Alegre · Brasil', caption: 'Frontend · Arquitetura · Produto' },
    about: { label: '01 — sobre mim', title: 'Boas interfaces começam com', accent: 'boas perguntas.', paragraphs: ['Sou engenheira de software com foco em frontend e experiência em ambientes corporativos. Gosto de entender o problema, organizar sistemas complexos e criar soluções que façam sentido para quem usa e para quem mantém o produto.', 'Hoje, na Nelogica, trabalho em aplicações de alta complexidade e acompanho funcionalidades da definição à produção. No caminho, também construí produtos financeiros, participei de projetos de inovação na SAP e desenvolvi experiências web, desktop e de realidade virtual.'], stats: [{ value: '8+', label: 'anos em tecnologia' }, { value: '4', label: 'empresas e equipes' }, { value: '01', label: 'prêmio global de inovação' }, { value: '3', label: 'idiomas' }] },
    projects: { label: '02 — projetos selecionados', title: 'Feitos para resolver', accent: 'problemas reais.', allLink: 'mais projetos no GitHub' },
    experience: { label: '03 — experiência profissional', title: 'Uma trajetória entre', accent: 'produto e engenharia.', intro: 'De experiências imersivas a plataformas financeiras, cada etapa ampliou meu repertório técnico e minha visão de produto.' },
    education: { label: '04 — formação', title: 'Aprendizado em', accent: 'construção contínua.' },
    toolkit: { label: '05 — repertório', title: 'Ferramentas para', accent: 'construir com cuidado.', intro: 'Combino fundamentos de frontend com práticas de arquitetura, colaboração e evolução contínua de produto.', languages: 'Idiomas', interests: 'Fora do código', interestsText: 'Arquitetura de software, inovação, corrida, treinamento de força, leitura e aprendizado contínuo.' },
    contact: { label: '06 — contato', title: 'Vamos', accent: 'conversar?', intro: 'Gosto de trocar ideias sobre frontend, arquitetura de software e produtos digitais.' },
    footer: { location: 'Porto Alegre, Brasil', backToTop: 'voltar ao topo ↑' },
  },
} as const

const content = computed(() => translations[locale.value])

function setLocale(nextLocale: Locale) {
  locale.value = nextLocale
}

watch(locale, (currentLocale) => {
  document.documentElement.lang = currentLocale === 'en' ? 'en' : 'pt-BR'
  document.title = translations[currentLocale].title
  document.querySelector('meta[name="description"]')?.setAttribute('content', translations[currentLocale].description)
}, { immediate: true })

const projects = [
  {
    number: '01',
    title: 'Fintech Trading Dashboard',
    description: {
      en: 'A stock trading dashboard with market data visualization and Alpaca market data integration.',
      pt: 'Dashboard para operações de compra e venda de ações, com visualização de dados e integração com cotações da Alpaca.',
    },
    tags: ['React', 'Next.js', 'TypeScript', 'Alpaca'],
    link: 'https://github.com/JuliaBP2000/fintech-trading-dashboard',
    accent: 'blue',
  },
  {
    number: '02',
    title: 'Aurora Design System',
    description: {
      en: 'A custom design system for React, with reusable components and Storybook documentation.',
      pt: 'Design system próprio para React, com componentes reutilizáveis e documentação em Storybook.',
    },
    tags: ['React', 'JavaScript', 'Storybook'],
    link: 'https://github.com/JuliaBP2000/aurora-design-system-react',
    accent: 'coral',
  },
  {
    number: '03',
    title: 'Porfitolio',
    description: {
      en: 'This portfolio, built to bring together my work, projects, and interests in software engineering.',
      pt: 'Este portfólio, desenvolvido para reunir minha trajetória, projetos e interesses em engenharia de software.',
    },
    tags: ['Vue.js', 'TypeScript', 'Vite'],
    link: 'https://github.com/JuliaBP2000/porfitolio',
    accent: 'lime',
  },
]

const experience = [
  {
    period: { en: 'May 2025 — present', pt: 'Mai 2025 — atual' },
    role: 'Front-end Developer III',
    company: 'Nelogica',
    location: { en: 'Porto Alegre, Brazil', pt: 'Porto Alegre, RS' },
    highlights: {
      en: ['Promoted from Front-end Developer II in recognition of technical growth, autonomy, and impact on team deliveries.', 'Build and maintain applications with Vue.js 3, TypeScript, React, and PHP, contributing to frontend architecture, scalability, performance, and maintainability.', 'Own features end to end, from requirements through production, in partnership with Product, UX/UI, and Backend teams.'],
      pt: ['Promovida de Front-end Developer II em reconhecimento à evolução técnica, autonomia e impacto nas entregas.', 'Desenvolvimento de aplicações com Vue.js 3, TypeScript, React e PHP, contribuindo para arquitetura, escalabilidade, performance e manutenção.', 'Condução de funcionalidades de ponta a ponta, dos requisitos à produção, em parceria com Produto, UX/UI e Backend.'],
    },
    tags: { en: ['Vue.js 3', 'TypeScript', 'React', 'PHP'], pt: ['Vue.js 3', 'TypeScript', 'React', 'PHP'] },
  },
  {
    period: { en: 'Jun 2023 — Mar 2025', pt: 'Jun 2023 — mar 2025' },
    role: 'Front-end Developer / Systems Analyst III',
    company: 'MBOCHIP',
    location: { en: 'Porto Alegre, Brazil', pt: 'Porto Alegre, RS' },
    highlights: {
      en: ['Developed and maintained a financial dashboard for equity trading operations.', 'Built data visualization interfaces with real-time updates, focusing on performance and code quality.'],
      pt: ['Desenvolvimento e manutenção de um dashboard financeiro para operações de compra e venda de ações.', 'Criação de interfaces para visualização de dados e atualizações em tempo real, com foco em performance e qualidade de código.'],
    },
    tags: { en: ['Vue.js', 'TypeScript', 'Real-time data'], pt: ['Vue.js', 'TypeScript', 'Dados em tempo real'] },
  },
  {
    period: { en: 'May 2021 — May 2023', pt: 'Mai 2021 — mai 2023' },
    role: 'Developer — IXP Intern',
    company: 'SAP',
    location: { en: 'São Leopoldo, Brazil', pt: 'São Leopoldo, RS' },
    highlights: {
      en: ['Contributed to innovation, automation, and Design Thinking projects using SAP BTP, HANA, Analytics Cloud, CAI, and iRPA.', 'Developed frontend solutions with JavaScript, React, HTML, and CSS.', 'Won the SAP Global Hackathon D2B Champions’ League with an innovation business case.'],
      pt: ['Participação em projetos de inovação, automação e Design Thinking com SAP BTP, HANA, Analytics Cloud, CAI e iRPA.', 'Desenvolvimento de soluções frontend com JavaScript, React, HTML e CSS.', 'Vencedora do SAP Global Hackathon D2B Champions’ League com um business case de inovação.'],
    },
    tags: { en: ['React', 'JavaScript', 'SAP BTP', 'SAP HANA'], pt: ['React', 'JavaScript', 'SAP BTP', 'SAP HANA'] },
  },
  {
    period: { en: 'Apr 2018 — 2021', pt: 'Abr 2018 — 2021' },
    role: 'Developer',
    company: 'Unisinos — VizLab',
    location: { en: 'São Leopoldo, Brazil', pt: 'São Leopoldo, RS' },
    highlights: {
      en: ['Developed web and desktop applications, as well as virtual reality experiences.', 'Presented software solutions developed for Petrobras in Rio de Janeiro.'],
      pt: ['Desenvolvimento de aplicações web, desktop e experiências de realidade virtual.', 'Apresentação, no Rio de Janeiro, de soluções de software desenvolvidas para a Petrobras.'],
    },
    tags: { en: ['C#', 'Unity', 'Vue.js', 'JavaScript'], pt: ['C#', 'Unity', 'Vue.js', 'JavaScript'] },
  },
]

const education = [
  { period: { en: 'In progress', pt: 'Em andamento' }, degree: { en: 'Postgraduate Degree in Software Architecture', pt: 'Pós-graduação em Arquitetura de Software' }, school: { en: '', pt: '' } },
  { period: { en: '2024 — 2025', pt: '2024 — 2025' }, degree: { en: 'Postgraduate Degree in Full Stack Web Development', pt: 'Pós-graduação em Desenvolvimento Web Full Stack' }, school: { en: 'Anhanguera', pt: 'Anhanguera' } },
  { period: { en: '2018 — 2023', pt: '2018 — 2023' }, degree: { en: "Bachelor's Degree in Computer Science", pt: 'Bacharelado em Ciência da Computação' }, school: { en: 'Unisinos', pt: 'Unisinos' } },
  { period: { en: '2015 — 2018', pt: '2015 — 2018' }, degree: { en: 'Computer Technician', pt: 'Técnico em Informática' }, school: { en: 'Instituto Rio Branco', pt: 'Instituto Rio Branco' } },
]

const skillGroups = [
  { title: { en: 'Frontend', pt: 'Frontend' }, skills: { en: ['JavaScript', 'TypeScript', 'Vue.js 3', 'React', 'HTML', 'CSS'], pt: ['JavaScript', 'TypeScript', 'Vue.js 3', 'React', 'HTML', 'CSS'] } },
  { title: { en: 'Architecture', pt: 'Arquitetura' }, skills: { en: ['Modular applications', 'Reusable components', 'Design patterns', 'Scalability'], pt: ['Aplicações modulares', 'Componentes reutilizáveis', 'Padrões de projeto', 'Escalabilidade'] } },
  { title: { en: 'SAP ecosystem', pt: 'Ecossistema SAP' }, skills: { en: ['SAP BTP', 'SAP HANA', 'Analytics Cloud', 'SAP CAI', 'SAP iRPA'], pt: ['SAP BTP', 'SAP HANA', 'Analytics Cloud', 'SAP CAI', 'SAP iRPA'] } },
  { title: { en: 'Tools', pt: 'Ferramentas' }, skills: { en: ['Git', 'Figma', 'MURAL', 'Claude Code', 'Copilot'], pt: ['Git', 'Figma', 'MURAL', 'Claude Code', 'Copilot'] } },
]

const languages = [
  { name: { en: 'Portuguese', pt: 'Português' }, level: { en: 'Native', pt: 'Nativo' } },
  { name: { en: 'English', pt: 'Inglês' }, level: { en: 'Fluent', pt: 'Fluente' } },
  { name: { en: 'Spanish', pt: 'Espanhol' }, level: { en: 'Basic', pt: 'Básico' } },
  { name: { en: 'Korean', pt: 'Coreano' }, level: { en: 'Basic', pt: 'Básico' } },
]
</script>

<template>
  <header class="topbar">
    <a class="brand" href="#top" aria-label="Home">JB<span>.</span></a>
    <nav class="nav-links" :aria-label="content.navigationLabel">
      <a href="#sobre">{{ content.nav.about }}</a>
      <a href="#projetos">{{ content.nav.projects }}</a>
      <a href="#experiencia">{{ content.nav.experience }}</a>
      <a href="#formacao">{{ content.nav.education }}</a>
    </nav>
    <div class="header-actions">
    <a class="contact-link" href="mailto:juliabp2000@gmail.com">{{ content.nav.contact }} <span>↗</span></a>
    <div class="language-switch" role="group" :aria-label="content.languageSelector">
      <button type="button" :aria-pressed="locale === 'en'" @click="setLocale('en')">EN</button>
      <button type="button" :aria-pressed="locale === 'pt'" @click="setLocale('pt')">PT</button>
    </div>
    </div>
  </header>

  <main id="top">
    <section class="hero page-section">
      <div class="hero-copy reveal">
        <p class="eyebrow"><span class="status-dot"></span> {{ content.hero.eyebrow }}</p>
        <h1>{{ content.hero.title }} <em>{{ content.hero.accent }}</em></h1>
        <p class="hero-intro">{{ content.hero.intro }}</p>
        <div class="hero-actions">
          <a class="button button-dark" href="#experiencia">{{ content.hero.journey }} <span>↓</span></a>
          <a v-if="locale === 'pt'" class="text-link" href="/julia-boesing-ponticelli-cv-pt.pdf" download="Julia-Boesing-Ponticelli-CV.pdf">{{ content.hero.resume }} <span>↓</span></a>
          <a v-else class="text-link" href="/julia-boesing-ponticelli-cv-en.pdf" download="Julia-Boesing-Ponticelli-CV.pdf">{{ content.hero.resume }} <span>↓</span></a>
        </div>
      </div>
      <div class="hero-art reveal delay-one" role="group" :aria-label="content.hero.portraitLabel">
        <div class="art-frame">
          <img src="https://avatars.githubusercontent.com/u/43683346?v=4" :alt="content.hero.portraitAlt" />
          <div class="art-stamp">JB<br /><small>{{ content.hero.location }}</small></div>
        </div>
        <p class="art-note">{{ content.hero.caption }}</p>
      </div>
    </section>

    <section id="sobre" class="statement page-section">
      <p class="section-label">{{ content.about.label }}</p>
      <div>
        <h2>{{ content.about.title }} <span>{{ content.about.accent }}</span></h2>
        <p v-for="paragraph in content.about.paragraphs" :key="paragraph" class="statement-text">{{ paragraph }}</p>
        <div class="career-facts">
          <div v-for="stat in content.about.stats" :key="stat.label"><strong>{{ stat.value }}</strong><span>{{ stat.label }}</span></div>
        </div>
      </div>
    </section>

    <section id="projetos" class="projects page-section">
      <div class="section-heading">
        <div><p class="section-label">{{ content.projects.label }}</p><h2>{{ content.projects.title }} <span>{{ content.projects.accent }}</span></h2></div>
        <a class="text-link" href="https://github.com/JuliaBP2000" target="_blank" rel="noreferrer">{{ content.projects.allLink }} <span>↗</span></a>
      </div>
      <div class="project-list">
        <a v-for="project in projects" :key="project.number" class="project-card" :class="`accent-${project.accent}`" :href="project.link" target="_blank" rel="noreferrer">
          <div class="project-number">{{ project.number }}</div>
          <div class="project-content"><h3>{{ project.title }}</h3><p>{{ project.description[locale] }}</p><div class="tags"><span v-for="tag in project.tags" :key="tag">{{ tag }}</span></div></div>
          <span class="project-arrow">↗</span>
        </a>
      </div>
    </section>

    <section id="experiencia" class="experience page-section">
      <p class="section-label">{{ content.experience.label }}</p>
      <div class="experience-grid">
        <div class="experience-heading">
          <h2>{{ content.experience.title }} <span>{{ content.experience.accent }}</span></h2>
          <p>{{ content.experience.intro }}</p>
        </div>
        <div class="timeline">
          <article v-for="item in experience" :key="item.company" class="timeline-item">
            <div class="timeline-meta"><p class="period">{{ item.period[locale] }}</p><p class="location">{{ item.location[locale] }}</p></div>
            <div class="timeline-body">
              <h3>{{ item.role }}</h3>
              <p class="company">{{ item.company }}</p>
              <ul class="experience-highlights"><li v-for="highlight in item.highlights[locale]" :key="highlight">{{ highlight }}</li></ul>
              <div class="tags"><span v-for="tag in item.tags[locale]" :key="tag">{{ tag }}</span></div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section id="formacao" class="education page-section">
      <div class="section-heading">
        <div><p class="section-label">{{ content.education.label }}</p><h2>{{ content.education.title }} <span>{{ content.education.accent }}</span></h2></div>
      </div>
      <div class="education-list">
        <article v-for="item in education" :key="item.degree.en" class="education-item">
          <p class="period">{{ item.period[locale] }}</p>
          <div><h3>{{ item.degree[locale] }}</h3><p v-if="item.school[locale]">{{ item.school[locale] }}</p></div>
          <span class="education-mark" aria-hidden="true">↗</span>
        </article>
      </div>
    </section>

    <section class="toolkit page-section">
      <p class="section-label">{{ content.toolkit.label }}</p>
      <div class="toolkit-content">
        <div class="toolkit-heading"><h2>{{ content.toolkit.title }} <span>{{ content.toolkit.accent }}</span></h2><p>{{ content.toolkit.intro }}</p></div>
        <div class="skill-groups">
          <article v-for="group in skillGroups" :key="group.title.en" class="skill-group">
            <h3>{{ group.title[locale] }}</h3>
            <div class="skill-cloud"><span v-for="skill in group.skills[locale]" :key="skill">{{ skill }}</span></div>
          </article>
        </div>
      </div>
      <div class="profile-details">
        <div class="language-list"><h3>{{ content.toolkit.languages }}</h3><p v-for="language in languages" :key="language.name.en"><span>{{ language.name[locale] }}</span><span>{{ language.level[locale] }}</span></p></div>
        <div class="interests"><h3>{{ content.toolkit.interests }}</h3><p>{{ content.toolkit.interestsText }}</p></div>
      </div>
    </section>

    <section class="contact page-section"><p class="section-label">{{ content.contact.label }}</p><h2>{{ content.contact.title }}<br /><em>{{ content.contact.accent }}</em></h2><p class="contact-intro">{{ content.contact.intro }}</p><div class="contact-actions"><a class="button button-light" href="mailto:juliabp2000@gmail.com">juliabp2000@gmail.com <span>↗</span></a><a class="contact-social" href="https://www.linkedin.com/in/julia-boesing-ponticelli-9428b0101" target="_blank" rel="noreferrer">LinkedIn ↗</a><a class="contact-social" href="https://github.com/JuliaBP2000" target="_blank" rel="noreferrer">GitHub ↗</a></div></section>
  </main>

  <footer><span>© 2026 Júlia Boesing Ponticelli</span><span>{{ content.footer.location }}</span><a href="#top">{{ content.footer.backToTop }}</a></footer>
</template>
