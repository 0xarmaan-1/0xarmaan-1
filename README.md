<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Armaan — Offensive Security Researcher</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#10141c;
    --bg-raise:#161b26;
    --line:#262c3a;
    --ink:#e7e4dc;
    --ink-dim:#8a91a3;
    --amber:#e8a33d;
    --teal:#4fb3a9;
    --font-display:'Space Grotesk', system-ui, 'Segoe UI', sans-serif;
    --font-body:'IBM Plex Sans', system-ui, 'Segoe UI', sans-serif;
    --font-mono:'IBM Plex Mono', 'SFMono-Regular', Consolas, monospace;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:var(--font-body);
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }
  a{color:inherit;}
  .wrap{max-width:860px; margin:0 auto; padding:0 28px;}

  /* ---------- hero ---------- */
  .hero{
    position:relative;
    padding:88px 0 72px;
    border-bottom:1px solid var(--line);
    overflow:hidden;
  }
  .hero::before{
    content:"";
    position:absolute; inset:0 0 auto 0;
    height:3px;
    background:linear-gradient(90deg, var(--amber), var(--teal) 55%, transparent);
  }
  .prompt{
    font-family:var(--font-mono);
    font-size:13px;
    color:var(--teal);
    margin:0 0 20px;
    opacity:0;
    animation:rise .5s ease-out forwards;
  }
  .prompt::after{
    content:"";
    display:inline-block;
    width:7px; height:14px;
    margin-left:6px;
    background:var(--teal);
    vertical-align:-2px;
    animation:blink 1.1s steps(1) infinite;
  }
  h1{
    font-family:var(--font-display);
    font-weight:700;
    font-size:clamp(48px, 9vw, 84px);
    line-height:0.95;
    margin:0 0 14px;
    letter-spacing:-0.02em;
    opacity:0;
    animation:rise .6s ease-out .12s forwards;
  }
  .role{
    font-family:var(--font-display);
    font-weight:500;
    font-size:19px;
    color:var(--ink-dim);
    margin:0 0 22px;
    opacity:0;
    animation:rise .6s ease-out .22s forwards;
  }
  .statement{
    max-width:58ch;
    font-size:16px;
    color:#c7c3b9;
    margin:0 0 28px;
    opacity:0;
    animation:rise .6s ease-out .32s forwards;
  }
  .status-row{
    display:flex; flex-wrap:wrap; gap:10px;
    opacity:0;
    animation:rise .6s ease-out .42s forwards;
  }
  .badge{
    font-family:var(--font-mono);
    font-size:12.5px;
    padding:7px 12px;
    border:1px solid var(--line);
    border-radius:3px;
    background:var(--bg-raise);
  }
  .badge-amber{color:var(--amber); border-color:#4a3a22;}
  .badge-teal{color:var(--teal); border-color:#204440;}

  @keyframes rise{ from{opacity:0; transform:translateY(10px);} to{opacity:1; transform:translateY(0);} }
  @keyframes blink{ 50%{opacity:0;} }

  /* ---------- sections ---------- */
  main{padding:64px 0 24px;}
  section{padding:48px 0; border-bottom:1px solid var(--line);}
  section:last-of-type{border-bottom:none;}

  .section-head{
    display:flex; align-items:baseline; gap:14px;
    margin-bottom:28px;
  }
  .log-id{
    font-family:var(--font-mono);
    font-size:12.5px;
    color:var(--ink-dim);
    opacity:0.65;
  }
  h2{
    font-family:var(--font-display);
    font-weight:600;
    font-size:26px;
    margin:0;
    letter-spacing:-0.01em;
  }
  .section-note{
    font-size:14px;
    color:var(--ink-dim);
    margin:-18px 0 26px;
  }

  /* capabilities */
  .cap-grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:0;
    border:1px solid var(--line);
    border-radius:4px;
    overflow:hidden;
  }
  .cap{
    padding:22px 24px;
    border-bottom:1px solid var(--line);
  }
  .cap:nth-child(odd){border-right:1px solid var(--line);}
  .cap:nth-last-child(-n+2){border-bottom:none;}
  .cap h3{
    font-family:var(--font-display);
    font-size:15px;
    font-weight:600;
    margin:0 0 12px;
  }
  .tag-row{display:flex; flex-wrap:wrap; gap:7px;}
  .tag{
    font-family:var(--font-mono);
    font-size:12px;
    color:#b7b3a8;
    background:var(--bg-raise);
    border:1px solid var(--line);
    padding:4px 9px;
    border-radius:3px;
  }

  /* findings table */
  table{width:100%; border-collapse:collapse; font-size:14.5px;}
  th{
    text-align:left;
    font-family:var(--font-body);
    font-weight:600;
    font-size:12.5px;
    color:var(--ink-dim);
    padding:0 14px 10px 0;
    border-bottom:1px solid var(--line);
  }
  td{
    padding:14px 14px 14px 0;
    border-bottom:1px solid var(--line);
    vertical-align:top;
  }
  tr:last-child td{border-bottom:none;}
  .impact{color:var(--amber); font-family:var(--font-mono); font-size:13px;}
  .platform{color:var(--teal); font-family:var(--font-mono); font-size:13px;}

  /* toolkit */
  .toolkit-grid{display:grid; grid-template-columns:1fr 1fr; gap:36px;}
  .toolkit-grid h3{
    font-family:var(--font-display);
    font-size:15px;
    font-weight:600;
    margin:0 0 12px;
  }

  /* certifications */
  .cert-list{display:flex; flex-direction:column;}
  .cert-row{
    display:flex; justify-content:space-between; gap:16px;
    padding:12px 0;
    border-bottom:1px solid var(--line);
    font-size:14.5px;
  }
  .cert-row:last-child{border-bottom:none;}
  .cert-name{color:var(--ink);}
  .cert-issuer{
    font-family:var(--font-mono);
    font-size:12.5px;
    color:var(--ink-dim);
    white-space:nowrap;
  }

  footer{
    padding:40px 0 60px;
    text-align:left;
  }
  .closing-line{
    font-family:var(--font-display);
    font-style:italic;
    font-size:15px;
    color:var(--ink-dim);
    margin:0;
  }

  @media (max-width:640px){
    .cap-grid{grid-template-columns:1fr;}
    .cap:nth-child(odd){border-right:none;}
    .cap:nth-last-child(-n+2){border-bottom:1px solid var(--line);}
    .cap:last-child{border-bottom:none;}
    .toolkit-grid{grid-template-columns:1fr;}
    table, thead, tbody, th, td, tr{display:block;}
    thead{display:none;}
    td{border-bottom:none; padding:3px 0;}
    tr{padding:14px 0; border-bottom:1px solid var(--line);}
    td:first-child{font-family:var(--font-display); font-weight:600; padding-top:0;}
  }
</style>
</head>
<body>

<header class="hero">
  <div class="wrap">
    <p class="prompt">armaan@offsec:~$ whoami</p>
    <h1>Armaan</h1>
    <p class="role">Red Teamer — Web, Mobile &amp; Infrastructure Security</p>
    <p class="statement">I focus on offensive security research — red teaming, web and Android application testing, and OSINT — combining hands-on testing with modern AI-assisted tooling.</p>
    <div class="status-row">
      <span class="badge badge-amber">Active bug bounty researcher</span>
      <span class="badge badge-teal">CRTP — in preparation</span>
    </div>
  </div>
</header>

<main>
  <div class="wrap">

    <section id="capabilities">
      <div class="section-head">
        <span class="log-id">4af21c</span>
        <h2>Capabilities</h2>
      </div>
      <div class="cap-grid">
        <div class="cap">
          <h3>Offensive Security</h3>
          <div class="tag-row">
            <span class="tag">Red Teaming</span>
            <span class="tag">Web App Pentesting</span>
            <span class="tag">Privilege Escalation</span>
            <span class="tag">Post-Exploitation</span>
          </div>
        </div>
        <div class="cap">
          <h3>Vulnerability Classes</h3>
          <div class="tag-row">
            <span class="tag">SSRF</span>
            <span class="tag">SQL Injection</span>
            <span class="tag">XSS</span>
            <span class="tag">IDOR</span>
            <span class="tag">XXE</span>
            <span class="tag">CSRF</span>
            <span class="tag">Auth Bypass</span>
            <span class="tag">HTTP Smuggling</span>
          </div>
        </div>
        <div class="cap">
          <h3>Mobile &amp; Android Security</h3>
          <div class="tag-row">
            <span class="tag">APK Reverse Engineering</span>
            <span class="tag">Static &amp; Dynamic Analysis</span>
            <span class="tag">Insecure Storage</span>
            <span class="tag">Intent Hijacking</span>
            <span class="tag">Frida Instrumentation</span>
          </div>
        </div>
        <div class="cap">
          <h3>OSINT &amp; Recon</h3>
          <div class="tag-row">
            <span class="tag">Attack Surface Mapping</span>
            <span class="tag">Digital Footprint Analysis</span>
            <span class="tag">Passive Recon</span>
            <span class="tag">Google Dorking</span>
          </div>
        </div>
      </div>
    </section>

    <section id="findings">
      <div class="section-head">
        <span class="log-id">9e02f7</span>
        <h2>Verified Findings</h2>
      </div>
      <p class="section-note">Real targets, responsibly disclosed.</p>
      <table>
        <thead>
          <tr><th>Target</th><th>Vulnerability</th><th>Impact</th><th>Platform</th></tr>
        </thead>
        <tbody>
          <tr>
            <td>Major Social Platform</td>
            <td>OTP Bypass / Auth Flaw</td>
            <td class="impact">Account Takeover Risk</td>
            <td class="platform">HackerOne</td>
          </tr>
          <tr>
            <td>Private Program</td>
            <td>SSRF → Internal Server Access</td>
            <td class="impact">Server-Level Access</td>
            <td class="platform">Private Disclosure</td>
          </tr>
          <tr>
            <td>Institutional Web Portal</td>
            <td>SQL Injection</td>
            <td class="impact">Full Database Extraction</td>
            <td class="platform">Responsibly Reported</td>
          </tr>
        </tbody>
      </table>
    </section>

    <section id="toolkit">
      <div class="section-head">
        <span class="log-id">c71db4</span>
        <h2>Toolkit &amp; Platforms</h2>
      </div>
      <div class="toolkit-grid">
        <div>
          <h3>Tools</h3>
          <div class="tag-row">
            <span class="tag">Burp Suite</span>
            <span class="tag">Nmap</span>
            <span class="tag">Metasploit</span>
            <span class="tag">SQLMap</span>
            <span class="tag">Gobuster</span>
            <span class="tag">Nikto</span>
            <span class="tag">Wireshark</span>
            <span class="tag">Dalfox</span>
            <span class="tag">MobSF</span>
            <span class="tag">Frida</span>
            <span class="tag">Jadx</span>
            <span class="tag">ADB</span>
          </div>
        </div>
        <div>
          <h3>Platforms</h3>
          <div class="tag-row">
            <span class="tag">Kali Linux</span>
            <span class="tag">Parrot OS</span>
            <span class="tag">TryHackMe — 100+ Rooms</span>
            <span class="tag">PortSwigger Academy</span>
          </div>
        </div>
      </div>
    </section>

    <section id="certifications">
      <div class="section-head">
        <span class="log-id">2b86a0</span>
        <h2>Certifications</h2>
      </div>
      <div class="cert-list">
        <div class="cert-row"><span class="cert-name">SQL Injection Attacks</span><span class="cert-issuer">EC-Council</span></div>
        <div class="cert-row"><span class="cert-name">Advent of Cyber 2025</span><span class="cert-issuer">TryHackMe</span></div>
        <div class="cert-row"><span class="cert-name">Cyber Security Fundamentals</span><span class="cert-issuer">TryHackMe</span></div>
        <div class="cert-row"><span class="cert-name">Advanced OSINT</span><span class="cert-issuer">Udemy</span></div>
        <div class="cert-row"><span class="cert-name">Ethical Hacking Course</span><span class="cert-issuer">Coding Junction</span></div>
        <div class="cert-row"><span class="cert-name">Web Application Pentesting</span><span class="cert-issuer">Coding Junction</span></div>
        <div class="cert-row"><span class="cert-name">Dark Web, Anonymity, and Cryptocurrency</span><span class="cert-issuer">EC-Council</span></div>
        <div class="cert-row"><span class="cert-name">Claude 101</span><span class="cert-issuer">Anthropic</span></div>
        <div class="cert-row"><span class="cert-name">AI Fluency for Students</span><span class="cert-issuer">Anthropic</span></div>
      </div>
    </section>

  </div>
</main>

<footer>
  <div class="wrap">
    <p class="closing-line">"The quieter you become, the more you can hear."</p>
  </div>
</footer>

</body>
</html>
