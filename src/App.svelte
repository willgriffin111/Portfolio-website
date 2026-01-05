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
        <div class="content-shell">
          <div class="hero-grid">
            <div class="hero-copy">
              <h1 class="hero-title">Hi, I'm Will Griffin</h1>
              <p class="hero-lede">
                I’m a Computer Science graduate from UWE Bristol. I love working on ideas that blend hardware and software, and I’m excited by software engineering, systems programming, and the hardware that brings everything together.
              </p>
              <div class="hero-actions">
                <a class="pill primary" href="#projects">View projects</a>
                <a class="pill ghost" href="#contact">Get in touch</a>
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
              </div>
            </div>
            <div class="hero-image">
              <div class="portrait-shell">
                <img src="me.png" alt="Will Griffin" />
              </div>
            </div>
          </div>
        </div>
    {/if}
    
    {#if section === 'projects'}
      <div class="content-shell">
        <div class="section-header">
          <div>
            <p class="eyebrow">Selected work</p>
            <h2>Projects</h2>
          </div>
          <a class="pill ghost" href="https://github.com/willgriffin111" target="_blank" rel="noopener">View GitHub</a>
        </div>
        <div class="project-cards">
          <div class="project-card">
            <Slideshow slides={AutomotiveMonitoringSystemslides} />
            <h3>Automotive Monitoring System</h3>
            <p>Embedded system that collects real-time vehicle data from OBD-II, GPS, and IMU sensors. Logs to SD card and displays live and historical data via a UI built with Svelte and Tauri.</p>
            <a href="https://github.com/willgriffin111/Vehicle-Data-Logger-And-Analysis" target="_blank" class="pill link-pill">View on GitHub</a>
          </div>
        
          <div class="project-card">
            <Slideshow slides={UniHubslides} />
            <h3>UniHub Social Platform</h3>
            <p>A containerised full-stack student platform developed using Django and Django REST Framework, featuring JWT-based authentication, RESTful APIs, and core social features including posts, comments, events and admin management.</p>
            <a href="https://github.com/willgriffin111/Uni-Hub" target="_blank" class="pill link-pill">View on GitHub</a>
          </div>
        
          <div class="project-card">
            <video src="Projects/8-bitComputer.mp4" controls poster="Projects/8-bit.png" preload="none" width="100%">
              <track kind="captions" src="Projects/8-bitComputer.vtt" srclang="en" label="English captions" default />
            </video>
            <h3>8-bit Breadboard Computer</h3>
            <p>
            A low-level hardware computing project built using 7400-series TTL logic ICs, featuring a clock circuit, control unit, instruction and data registers, an arithmetic logic unit (ALU), and a simple instruction set architecture to demonstrate core CPU fundamentals.
            </p>

          </div>
        
          <div class="project-card">
            <Slideshow slides={RMslides} />
            <h3>Custom RM Command in C</h3>
            <p>
            Recreated the UNIX <code>rm</code> command in C, supporting recursive deletion, force flags, and interactive prompts, demonstrating low-level system programming and Linux fundamentals.
            </p>
            <a href="https://github.com/willgriffin111/" target="_blank" class="pill link-pill">View on GitHub</a>
          </div>
        
          <div class="project-card">
            <Slideshow slides={HorizonEPOSslides} />
            <h3>Horizon Restaurants EPOS</h3>
            <p>
            Developed a desktop point-of-sale application in Python using Tkinter, structured around using MVC architecture with role-based access control, supporting inventory, menu, and discount management and generating PDF reports for administrative use.
            </p>

            <a href="https://github.com/willgriffin111/Horizon-Restaurants-EPOS" target="_blank" class="pill link-pill">View on GitHub</a>
          </div>
        
          <div class="project-card">
            <Slideshow slides={HorizonTravelBookingWebsite} />
            <h3>Horizon Travel Booking Website</h3>
            <p>
            A travel booking system built with a Flask backend and dynamic frontend, supporting user registration, administrative dashboards, and real-time availability filtering by travel type and date.
            </p>

            <a href="https://github.com/willgriffin111/Horizon-Travels-Booking-Website" target="_blank" class="pill link-pill">View on GitHub</a>
          </div>
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
        <div class="content-shell">
          <div class="section-header">
            <div>
              <h2>Experience</h2>
            </div>
          </div>
          <div class="timeline-center">
            <div class="timeline-row right">
              <div class="timeline-icon"><i class="fas fa-briefcase"></i></div>
              <div class="timeline-item">
                <div class="arrow-right"></div>
                <h3>LOOP Project – Full Stack Developer Internship</h3>
                <span class="timeline-date">June – December 2025</span>
                <div class="timeline-media">
                  <img src="Experience/Loop.jpg" alt="LOOP project hardware" />
                </div>
                <p>
                 During my internship, I developed Loop, a system that transforms Fitbit fitness data or weather data into a physical servo-driven ring display, where each ring’s position reflects progress towards a fitness goal. 
                 I wrote embedded C++ firmware for a Raspberry Pi Pico to control an array of eight servo motors, built a Flask backend with JWT authentication and Fitbit OAuth to retrive fitness data, 
                 and deployed it on AWS EC2 with full HTTPS. I also developed a Svelte frontend hosted on S3/CloudFront to visualise data using Chart.js, configure Pico device settings, and allow a device to be converted into a shared group display with multiple users.
                </p>
              </div>
            </div>

            <div class="timeline-row left">
              <div class="timeline-icon"><i class="fas fa-briefcase"></i></div>
              <div class="timeline-item">
                <div class="arrow-left"></div>
                <h3>UCAS Work Experience</h3>
                <span class="timeline-date">July 2018</span>
                <p>Shadowed UCAS developers and observed the full software lifecycle.</p>
              </div>
            </div>
          </div>
        </div>

      {:else if section === 'education'}
        <div class="content-shell">
          <div class="section-header">
            <div>
              <h2>Education</h2>
            </div>
          </div>
          <div class="education-container">
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
                      <tr><td>3</td><td>Distributed & Enterprise Software Development</td><td>79%</td></tr>
                      <tr><td>3</td><td>Communications & Protocols</td><td>78%</td></tr>
                      <tr><td>3</td><td>Digital Systems Project</td><td>79%</td></tr>
                    </tbody>
                  </table>
                {/if}
              </div>
              <span class="grade-badge">First Class</span>
            </div>
          
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
        </div>
      
      

      {:else if section === 'contact'}
        <div class="content-shell contact-shell">
          <div class="section-header">
            <div>
              <p class="eyebrow">Say hello</p>
              <h2>Contact Me</h2>
            </div>
            <a class="pill ghost" href="mailto:willcfgriffin@gmail.com">Email</a>
          </div>
          <p class="contact-text">If you'd like to get in touch, email me at <a href="mailto:willcfgriffin@gmail.com">willcfgriffin@gmail.com</a> or use the form below.</p>
          <form action="https://formsubmit.co/willcfgriffin@gmail.com" method="POST" class="contact-form">
            <input type="text" name="name" placeholder="Your Name" required />
            <input type="email" name="email" placeholder="Your Email" required />
            <textarea name="message" placeholder="Your Message" rows="5" required></textarea>
            <button type="submit" style="margin-bottom: 100px;">Send Message</button>
          </form>
        </div>
      {/if}
    </section>

  {/each}
</main>
