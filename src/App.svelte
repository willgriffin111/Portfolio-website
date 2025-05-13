<script>
  import { onMount } from 'svelte';
  import Slideshow from './lib/Slideshow.svelte';

  let active = 'home';

  const sections = ['home', 'projects','experience', 'education', 'contact'];

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

  let AutomotiveMonitoringSystemslides = [
    'Projects/AutomotiveMonitoringSystem1.JPG',
    'Projects/AutomotiveMonitoringSystem2.png',
  ];

  let UniHubslides = [
    'Projects/UniHub1.png',
    'Projects/UniHub2.png',
    'Projects/UniHub3.png',
    'Projects/UniHub4.png',
  ];

  let RMslides = [
    'Projects/RM1.png',
    'Projects/RM2.png',
    'Projects/RM3.png',
  ];

  let HorizonEPOSslides = [
    'Projects/EPOS1.png',
    'Projects/EPOS2.png',
    'Projects/EPOS3.png',
    'Projects/EPOS4.png',
  ];

  let HorizonTravelBookingWebsite = [
    'Projects/HorizonTravels1.png',
    'Projects/HorizonTravels2.png',
    'Projects/HorizonTravels3.png',
  ];

  let uweExpanded = false;
  let glosExpanded = false;
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

  {#each sections as section}
    <section id={section} class="page-section {section === 'home' ? 'home-section' : ''}">
      {#if section === 'home'}


      <section id="home" class="page-section home-section">
        
        <div class="home-content">
          <div class="home-image">
            <img src="me.png" alt="Will Griffin" />
          </div>
          <div class="home-bio">
            <h2>Hi, I'm Will Griffin</h2>
            <p style="font-size: 20px;">   I'm a Computer Science graduate from UWE Bristol with a strong interest 
              in embedded systems and full-stack development. I enjoy designing systems 
              that interact with real-world data - from building an 8-bit computer on breadboards
               to creating real-time Automotive Monitoring system.
            </p>
          </div>
        </div>
    
        <div class="social-buttons">
          <a href="https://github.com/willgriffin111" target="_blank" rel="noopener" class="social-btn">
            <div class="icon-circle"><i class="fab fa-github"></i></div>
            <span>GitHub</span>
          </a>
          <a href="https://www.linkedin.com/in/willcfgriffin/" target="_blank" rel="noopener" class="social-btn">
            <div class="icon-circle"><i class="fab fa-linkedin"></i></div>
            <span>LinkedIn</span>
          </a>
          <!-- <a href="https://leetcode.com/u/willgriffin111/" target="_blank" rel="noopener" class="social-btn">
            <div class="icon-circle" ><i class="fas fa-code"></i></div>
            <span>LeetCode</span>
          </a> -->
         
        </div>
      </section>
    {/if}
    
    {#if section === 'projects'}
    <h1>Projects</h1>
    <div class="project-cards">
      <div class="project-card">
        <Slideshow slides={AutomotiveMonitoringSystemslides} />
        <h3>Automotive Monitoring System</h3>
        <p>Embedded system that collects real-time vehicle data from OBD-II, GPS, and IMU sensors. Logs to SD card and displays live and historical data via a custom UI built with Svelte and Tauri.</p>
        <a href="https://github.com/willgriffin111/Vehicle-Data-Logger-And-Analysis" target="_blank" class="github-button">View on GitHub</a>
      </div>
    
      <div class="project-card">
        <Slideshow slides={UniHubslides} />
        <h3>UniHub Social Platform</h3>
        <p>Full-stack student platform built with Django, REST, and Docker. Features user auth, posts, comments, events, and Redis caching for high-performance data handling.</p>
        <a href="https://github.com/willgriffin111/Uni-Hub" target="_blank" class="github-button">View on GitHub</a>
      </div>
    
      <div class="project-card">
        <video src="Projects/8-bitComputer.mp4" controls poster="Projects/8-bit.png" preload="none" width="100%"> </video>

        <h3>8-bit Breadboard Computer</h3>
        <p>Hardware project built entirely with 7400-series logic ICs. Features a custom clock, microcoded control unit, and instruction set architecture.</p>
      </div>
    
      <div class="project-card">
        <Slideshow slides={RMslides} />
        <h3>Custom RM Command in C</h3>
        <p>Recreated the UNIX <code>rm</code> command in C, supporting recursive deletion, force flags, and interactive prompts. Demonstrates low-level system programming.</p>
        <a href="https://github.com/willgriffin111/" target="_blank" class="github-button">View on GitHub</a>
      </div>
    
      <div class="project-card">
        <Slideshow slides={HorizonEPOSslides} />
        <h3>Horizon Restaurants EPOS</h3>
        <p>Desktop point-of-sale system using Python and Tkinter. Implements MVC architecture, role-based access (admin, chef, director), inventory tracking, and PDF reporting.</p>
        <a href="https://github.com/willgriffin111/Horizon-Restaurants-EPOS" target="_blank" class="github-button">View on GitHub</a>
      </div>
    
      <div class="project-card">
        <Slideshow slides={HorizonTravelBookingWebsite} />
        <h3>Horizon Travel Booking Website</h3>
        <p>Travel booking system with Flask backend and dynamic frontend. Supports user registration, admin dashboards, and real-time availability by travel type and date.</p>
        <a href="https://github.com/willgriffin111/Horizon-Travels-Booking-Website" target="_blank" class="github-button">View on GitHub</a>
      </div>
    </div>
    

      <!-- {:else if section === 'techincal experience'}
        <h1>Technical Experience</h1>
        <div class="skills-grid">
          <div class="skill-item">
            <img src="Skills/python.png" alt="Python" />
            <p>Python</p>
          </div>
        </div> -->

      {:else if section === 'experience'}
        <h1>Experience</h1>
        <div class="timeline-center">
          <div class="timeline-row right">
            <div class="timeline-icon"><i class="fas fa-briefcase"></i></div>
            <div class="timeline-item">
              <div class="arrow-left"></div>
              <h3>LOOP Project</h3>
              <span class="timeline-date">July 2025</span>
              <p>TBD</p>
            </div>
          </div>

          <div class="timeline-row left">
            <div class="timeline-icon"><i class="fas fa-briefcase"></i></div>
            <div class="timeline-item">
              <div class="arrow-right"></div>
              <h3>UCAS Work Experience</h3>
              <span class="timeline-date">July 2018</span>
              <p>Shadowed UCAS developers and observed the full software lifecycle.</p>
            </div>
          </div>
        </div>

      {:else if section === 'education'}
      <script>
        let uweExpanded = false;
        let glosExpanded = false;
      </script>
      
      <h1>Education</h1>
      <div class="education-container">
      
        <!-- UWE Bristol -->
        <div class="education-card">
          <img src="Education/uwe.png" alt="UWE Bristol Logo" />
          <div class="education-content">
            <h3>University of the West of England (UWE Bristol)</h3>
            <p><strong>BSc (Hons) Computer Science</strong> </p>
            <p>September 2022 - July 2025</p>
            <button on:click={() => uweExpanded = !uweExpanded} class="toggle-button">
              {uweExpanded ? 'Hide Modules' : 'Show Modules'}
            </button>
      
            {#if uweExpanded}
              <table class="grades-table">
                <thead><tr><th>Year</th><th>Module</th><th>Grade</th></tr></thead>
                <tbody>
                  <tr><td>1</td><td>Principles of Programming</td><td>89%</td></tr>
                  <tr><td>1</td><td>Foundations of Computing</td><td>85%</td></tr>
                  <tr><td>1</td><td>Computer Systems Architecture</td><td>91%</td></tr>
                  <tr><td>1</td><td>Web Development & Databases</td><td>94%</td></tr>
                  <tr><td>1</td><td>Artificial Intelligence 1</td><td>67%</td></tr>
      
                  <tr><td>2</td><td>Advanced Algorithms</td><td>73%</td></tr>
                  <tr><td>2</td><td>Internet of Things</td><td>75%</td></tr>
                  <tr><td>2</td><td>Systems Development</td><td>73%</td></tr>
                  <tr><td>2</td><td>Advanced Software Development</td><td>79%</td></tr>
                  <tr><td>2</td><td>Artificial Intelligence 2</td><td>87%</td></tr>
                  <tr><td>2</td><td>Operating Systems</td><td>70%</td></tr>
      
                  <tr><td>3</td><td>Advanced Systems Programming</td><td>89%</td></tr>
                  <tr><td>3</td><td>Autonomous Agents & Multi-Agent Systems</td><td>73%</td></tr>
                  <tr><td>3</td><td>Distributed & Enterprise Software Development</td><td>TBD</td></tr>
                  <tr><td>3</td><td>Communications & Protocols</td><td>TBD</td></tr>
                  <tr><td>3</td><td>Digital Systems Project</td><td>TBD</td></tr>
                </tbody>
              </table>
            {/if}
          </div>
          <span class="grade-badge">First Class</span>
        </div>
      
        <!-- Gloucestershire College -->
        <div class="education-card">
          <img src="Education/gloscol.png" alt="Gloucestershire College Logo" />
          <div class="education-content">
            <h3>Gloucestershire College</h3>
            <p><strong>EAL Level 3 Diploma in Advanced Manufacturing Engineering </strong></p>
            <p>September 2020 - August 2022</p>
            <button on:click={() => glosExpanded = !glosExpanded}>
              {glosExpanded ? 'Hide Modules' : 'Show Modules'}
            </button>
      
            {#if glosExpanded}
              <table class="grades-table">
                <thead><tr><th>Unit</th><th>Module</th><th>Grade</th></tr></thead>
                <tbody>
                  <tr><td>001</td><td>Health and Safety in the Engineering Workplace</td><td>Distinction</td></tr>
                  <tr><td>002</td><td>Communications for Engineering Technicians</td><td>Distinction</td></tr>
                  <tr><td>003</td><td>Mathematics for Engineering Technicians</td><td>Distinction</td></tr>
                  <tr><td>004</td><td>Engineering Project</td><td>Distinction</td></tr>
                  <tr><td>006</td><td>Electrical and Electronic Principles</td><td>Merit</td></tr>
                  <tr><td>013</td><td>Programmable Logic Controllers (PLCs)</td><td>Distinction</td></tr>
                  <tr><td>014</td><td>Further Mathematics</td><td>Merit</td></tr>
                  <tr><td>018</td><td>Electrical Machines</td><td>Distinction</td></tr>
                  <tr><td>020</td><td>Further Electrical and Electronic Principles</td><td>Merit</td></tr>
                  <tr><td>024</td><td>Fault Diagnosis of Engineering Systems</td><td>Distinction</td></tr>
                  <tr><td>064</td><td>Microelectronics</td><td>Distinction</td></tr>
                </tbody>
              </table>
            {/if}
          </div>
          <span class="grade-badge">Distinction</span>
        </div>
      </div>
      
      

      {:else if section === 'contact'}
        <h1>Contact Me</h1>
        <h4 class="contact-text">If you'd like to get in touch, feel free to email me directly at <a href="mailto:willcfgriffin@gmail.com" style="color: black;" >willcfgriffin@gmail.com</a> or use the form below.</h4>
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
