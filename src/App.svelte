<script>
  import { onMount } from 'svelte';

  let active = 'home';

  const sections = ['home', 'projects', 'skills', 'experience', 'education', 'contact'];

  onMount(() => {
    const handleScroll = () => {
      for (const section of sections) {
        const el = document.getElementById(section);
        const rect = el?.getBoundingClientRect();
        if (rect && rect.top <= 150 && rect.bottom >= 150) {
          active = section;
          break;
        }
      }
    };

    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  });
</script>

<nav class="navbar">
  <ul>
    {#each sections as section}
      <li class:selected={active === section}>
        <a href={"#" + section}>{section.charAt(0).toUpperCase() + section.slice(1)}</a>
      </li>
    {/each}
  </ul>
</nav>

<main>
  <link
  rel="stylesheet"
  href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css"
/>
  {#each sections as section}
    <section id={section} class="page-section {section === 'home' ? 'home-section' : ''}">
      {#if section === 'home'}
        <div class="home-content">
          <div class="home-image">
            <img src="/ID.png" alt="Will Griffin" />
          </div>
          <div class="home-bio">
            <h2>Hi, I'm Will Griffin</h2>
            <p>
              I'm a total nerd
            </p>
          </div>
        </div>

      {:else if section === 'projects'}
      <h2>Projects</h2>
      <div class="project-cards">
        <div class="project-card">
          <img src="/vehicle-project.png" alt="Smart Vehicle Monitoring System" />
          <h3>Smart Vehicle Monitoring System</h3>
          <p>A real-time embedded system that logs OBD, GPS, and IMU data to help improve driving behaviour and fuel efficiency.</p>
          <a href="https://github.com/willgriffin111/Vehicle-Data-Logger-And-Analysis" target="_blank" class="github-button">View on GitHub</a>
        </div>
      
        <div class="project-card">
          <img src="/unihub.png" alt="UniHub Platform" />
          <h3>UniHub Social Platform</h3>
          <p>A Django-based student social platform with communities, posts, authentication, and live events — built using REST and Docker.</p>
          <a href="https://github.com/willgriffin111/Uni-Hub" target="_blank" class="github-button">View on GitHub</a>
        </div>
      
      </div>
      

      {:else if section === 'skills'}
      <h2>Skills</h2>
      <div class="skills-grid">
        <div class="skill-item">
          <img src="/Skills/python.png" alt="Python" />
          <p>Python</p>
        </div>

      </div>
      

      {:else if section === 'experience'}
      <h2>Industry Experience</h2>
      <div class="timeline-center">
      
        <div class="timeline-row right">
          <div class="timeline-icon"><i class="fas fa-briefcase"></i></div>
          <div class="timeline-item">
            <div class="arrow-left"></div>
            <h3>LOOP Research Project</h3>
            <span class="timeline-date">July 2025</span>
            <p>Working on LOOP</p>
          </div>
        </div>
      
        <div class="timeline-row left">
          <div class="timeline-icon"><i class="fas fa-briefcase"></i></div>
          <div class="timeline-item">
            <div class="arrow-right"></div>
            <h3>UCAS Work Experience</h3>
            <span class="timeline-date">July 2018</span>
            <p>Shadowed UCAS developers and observed the full software lifecycle: planning, coding, testing, maintenance.</p>
          </div>
        </div>
      
      </div>
      
      {:else if section === 'education'}
      <h2>Education</h2>
      <div class="education-container">
        <div class="education-card">
          <img src="/uwe.png" alt="UWE Bristol Logo" />
          <div class="education-content">
            <h3>University of the West of England</h3>
            <p>
              <strong>BSc (Hons) Computer Science</strong> — Graduate July 2025
              <span class="grade-badge ">First Class</span>
            </p>

          </div>
        </div>
      
        <div class="education-card">
          <img src="/gloscollege.png" alt="Gloucestershire College Logo" />
          <div class="education-content">
            <h3>Gloucestershire College</h3>
            <p>
              <strong>EAL Level 3 Diploma in Advanced Manufacturing Engineering</strong><br />
              (Electrical & Electronic) — Sept 2020 – July 2022
              <span class="grade-badge ">Distinction</span>
            </p>

          </div>
        </div>
      </div>
      
      
      {:else if section === 'contact'}
      <h2>Contact Me</h2>
      <form action="https://formsubmit.co/willcfgriffin@gmail.com" method="POST" class="contact-form">
        <input type="text" name="name" placeholder="Your Name" required />
        <input type="email" name="email" placeholder="Your Email" required />
        <textarea name="message" placeholder="Your Message" rows="5" required></textarea>
        <button type="submit">Send Message</button>
      

      </form>
      
      {/if}
    </section>
  {/each}
</main>

