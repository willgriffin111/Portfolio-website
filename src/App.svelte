<script>
  import { onMount } from 'svelte';

  let active = 'home';

  const sections = ['home', 'projects', 'techincal experience', 'industry experience', 'education', 'contact'];

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
  let currentSlideAutomotive = 0;
  let AutomotiveMonitoringSystemslides = [
    'Projects/AutomotiveMonitoringSystem1.JPG',
    'Projects/AutomotiveMonitoringSystem2.png',
  ];

  let currentSlideUniHub = 0;
  let UniHubslides = [
    'Projects/UniHub1.png',
    'Projects/UniHub2.png',
    'Projects/UniHub3.png',
    'Projects/UniHub4.png',
  ];

  let currentSlideRM = 0;
  let RMslides = [
    'Projects/RM1.png',
    'Projects/RM2.png',
    'Projects/RM3.png',
  ];

let currentSlideHorizonEPOS = 0;
  let HorizonEPOSslides = [
    'Projects/EPOS1.png',
    'Projects/EPOS2.png',
    'Projects/EPOS3.png',
    'Projects/EPOS4.png',

  ];

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
            <img src="me.png" alt="Will Griffin" />
          </div>
          <div class="home-bio">
            <h2>Hi, I'm Will Griffin</h2>
            <p>
              I'm a total nerd
            </p>
          </div>
        </div>

      {:else if section === 'projects'}
      <h1>Projects</h1>
      <div class="project-cards">
        <div class="project-card">
          <div class="slideshow">
            <button class="prev" on:click={() => currentSlideAutomotive = (currentSlideAutomotive - 1 + AutomotiveMonitoringSystemslides.length) % AutomotiveMonitoringSystemslides.length}>&#10094;</button>
            <img src={AutomotiveMonitoringSystemslides[currentSlideAutomotive]} alt="Automotive Monitoring System" />
            <button class="next" on:click={() => currentSlideAutomotive = (currentSlideAutomotive + 1) % AutomotiveMonitoringSystemslides.length}>&#10095;</button>
          </div>
          
          <h3>Automotive Monitoring System</h3>
          <p>A real-time embedded system that logs OBD, GPS, and IMU data to help improve driving behaviour and fuel efficiency.</p>
          <a href="https://github.com/willgriffin111/Vehicle-Data-Logger-And-Analysis" target="_blank" class="github-button">View on GitHub</a>
        </div>

        <div class="project-card">
          <div class="slideshow">
            <button class="prev" on:click={() => currentSlideUniHub = (currentSlideUniHub - 1 + UniHubslides.length) % UniHubslides.length}>&#10094;</button>
            <img src={UniHubslides[currentSlideUniHub]} alt="Automotive Monitoring System" />
            <button class="next" on:click={() => currentSlideUniHub = (currentSlideUniHub + 1) % UniHubslides.length}>&#10095;</button>
          </div>
          <h3>UniHub Social Platform</h3>
          <p>A Django-based student social platform with communities, posts, authentication, and live events — built using REST and Docker.</p>
          <a href="https://github.com/willgriffin111/Uni-Hub" target="_blank" class="github-button">View on GitHub</a>
        </div>
        <div class="project-card">
          <video src="Projects/8-bitComputer.mp4" controls poster="/8-bit.png" width="100%"> </video>
          <h3>8-bit Breadboard Computer</h3>
          <p>Built a fully functional 8-bit computer on breadboards using 7400-series logic ICs. It features a custom clock, instruction set, and microcoded control unit.</p>
        </div>
        <div class="project-card">
          <div class="slideshow">
            <button class="prev" on:click={() => currentSlideRM = (currentSlideRM - 1 + RMslides.length) % RMslides.length}>&#10094;</button>
            <img src={RMslides[currentSlideRM]} alt="Automotive Monitoring System" />
            <button class="next" on:click={() => currentSlideRM = (currentSlideRM + 1) % RMslides.length}>&#10095;</button>
          </div>
          <h3>Implementation of RM Command on Linux | C</h3>
          <p>Developed a custom <code>rm</code> command in C, enabling file and directory deletions with support for recursive, force, and interactive deletions.</p>
          <a href="https://github.com/willgriffin111/" target="_blank" class="github-button">View on GitHub</a>
        </div>
        <div class="project-card">
          <div class="slideshow">
            <button class="prev" on:click={() => currentSlideHorizonEPOS = (currentSlideHorizonEPOS - 1 + HorizonEPOSslides.length) % HorizonEPOSslides.length}>&#10094;</button>
            <img src={HorizonEPOSslides[currentSlideHorizonEPOS]} alt="Automotive Monitoring System" />
            <button class="next" on:click={() => currentSlideHorizonEPOS = (currentSlideHorizonEPOS + 1) % HorizonEPOSslides.length}>&#10095;</button>
          </div>
          <h3>Horizon Restaurants EPOS</h3>
          <p>
            A EPOS system built in Python using Tkinter with MVC architecture. It supports multi-role access, live inventory control, reservation management across branches, discount systems, and sales/staff reporting with PDF exports.
          </p>
          <a href="https://github.com/willgriffin111/Horizon-Restaurants-EPOS" target="_blank" class="github-button">View on GitHub</a>
        </div>
        <div class="project-card">
          <img src="/horizon-travel.png" alt="Horizon Travel Booking Website" />
          <h3>Dynamic Horizon Travel Booking Website</h3>
          <p>
            A travel booking platform for air, train, and coach transport. Built with secure user authentication, role-based access, and booking functionality. Offers both regular user features and admin controls.
          </p>
          <a href="https://github.com/willgriffin111/Horizon-Travels-Booking-Website" target="_blank" class="github-button">View on GitHub</a>
        </div>
        
        
        
      </div>
      

      {:else if section === 'techincal experience'}
      <h1>Techincal Experience</h1>
      <div class="skills-grid">
        <div class="skill-item">
          <img src="Skills/python.png" alt="Python" />
          <p>Python</p>
        </div>

      </div>
      

      {:else if section === 'industry experience'}
      <h1>Industry Experience</h1>
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
      <h1>Education</h1>
      <div class="education-container">
        <div class="education-card">
          <img src="Education/uwe.png" alt="UWE Bristol Logo" />
          <div class="education-content">
            <h3>University of the West of England</h3>
            <p>
              <strong>BSc (Hons) Computer Science</strong> — Graduate July 2025
              <span class="grade-badge ">First Class</span>
            </p>

          </div>
        </div>
      
        <div class="education-card">
          <img src="Education/gloscol.png" alt="Gloucestershire College Logo" />
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
      <h1>Contact Me</h1>
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

