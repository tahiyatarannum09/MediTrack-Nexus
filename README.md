# MediTrack-Nexus
Smart Medical Drug Inventory System
<!doctype html>
<html lang="en">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MediTrack Nexus - Smart Medical Supply Chain</title>
  <script src="/_sdk/data_sdk.js"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    }
    
    .fade-in {
      animation: fadeIn 0.4s ease-in;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    @keyframes pulse {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.6; }
    }
    
    .pulse {
      animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
    }
    
    /* 3D Model Animations */
    @keyframes rotate3d {
      0% { transform: rotateY(0deg) rotateX(10deg); }
      100% { transform: rotateY(360deg) rotateX(10deg); }
    }
    
    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-20px); }
    }
    
    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-10px); }
    }
    
    @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }
    
    @keyframes moleculeOrbit {
      0% { transform: rotate(0deg) translateX(40px) rotate(0deg); }
      100% { transform: rotate(360deg) translateX(40px) rotate(-360deg); }
    }
    
    .model-3d {
      animation: rotate3d 20s linear infinite;
      transform-style: preserve-3d;
    }
    
    .float-animation {
      animation: float 3s ease-in-out infinite;
    }
    
    .bounce-animation {
      animation: bounce 2s ease-in-out infinite;
    }
    
    .spin-animation {
      animation: spin 4s linear infinite;
    }
    
    .scene-3d {
      perspective: 1000px;
      transform-style: preserve-3d;
    }
    
    .cube-3d {
      width: 100px;
      height: 100px;
      position: relative;
      transform-style: preserve-3d;
      animation: rotate3d 8s linear infinite;
    }
    
    .cube-face {
      position: absolute;
      width: 100px;
      height: 100px;
      opacity: 0.9;
      border: 2px solid rgba(255, 255, 255, 0.3);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 24px;
    }
    
    .pill-3d {
      width: 120px;
      height: 50px;
      background: linear-gradient(135deg, #ef4444 0%, #dc2626 50%, #fef3c7 50%, #fde047 100%);
      border-radius: 25px;
      position: relative;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
      animation: float 3s ease-in-out infinite;
    }
    
    .pill-3d::before {
      content: '';
      position: absolute;
      top: 10px;
      left: 20px;
      width: 30px;
      height: 10px;
      background: rgba(255, 255, 255, 0.3);
      border-radius: 50%;
    }
    
    .dna-strand {
      position: relative;
      width: 150px;
      height: 200px;
      animation: rotate3d 10s linear infinite;
    }
    
    .dna-ball {
      position: absolute;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      animation: moleculeOrbit 4s linear infinite;
    }
    
    .syringe-3d {
      width: 40px;
      height: 120px;
      position: relative;
      animation: bounce 2s ease-in-out infinite;
    }
    
    .heart-3d {
      width: 80px;
      height: 80px;
      position: relative;
      animation: pulse 1.5s ease-in-out infinite;
    }
    
    .molecule-structure {
      position: relative;
      width: 150px;
      height: 150px;
      animation: rotate3d 15s linear infinite;
    }
    
    .atom {
      position: absolute;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      box-shadow: 0 0 20px currentColor;
    }
    
    .scan-line {
      position: absolute;
      width: 100%;
      height: 2px;
      background: linear-gradient(90deg, transparent, #3b82f6, transparent);
      animation: scanEffect 2s linear infinite;
    }
    
    @keyframes scanEffect {
      0% { top: 0; }
      100% { top: 100%; }
    }
    
    .hologram-effect {
      position: relative;
      background: linear-gradient(180deg, 
        rgba(59, 130, 246, 0.1) 0%, 
        rgba(6, 182, 212, 0.2) 50%, 
        rgba(59, 130, 246, 0.1) 100%);
      animation: hologramGlow 2s ease-in-out infinite;
    }
    
    @keyframes hologramGlow {
      0%, 100% { opacity: 0.7; }
      50% { opacity: 1; }
    }
    
    .particle {
      position: absolute;
      width: 4px;
      height: 4px;
      border-radius: 50%;
      background: currentColor;
      animation: particleFloat 3s ease-in-out infinite;
    }
    
    @keyframes particleFloat {
      0%, 100% { transform: translateY(0) translateX(0); opacity: 0; }
      50% { opacity: 1; }
      100% { transform: translateY(-100px) translateX(20px); opacity: 0; }
    }
    
    .status-badge {
      display: inline-block;
      padding: 0.25rem 0.75rem;
      border-radius: 9999px;
      font-size: 0.75rem;
      font-weight: 600;
    }
    
    .card-hover {
      transition: transform 0.2s, box-shadow 0.2s;
    }
    
    .card-hover:hover {
      transform: translateY(-2px);
      box-shadow: 0 10px 25px -5px rgba(59, 130, 246, 0.3);
    }
    
    .gradient-bg {
      background: linear-gradient(135deg, #3b82f6 0%, #06b6d4 100%);
    }
    
    .hexagon {
      width: 60px;
      height: 52px;
      position: relative;
      margin: 30px auto;
    }
    
    .hexagon:before,
    .hexagon:after {
      content: "";
      position: absolute;
      width: 0;
      border-left: 30px solid transparent;
      border-right: 30px solid transparent;
    }
    
    .hexagon:before {
      bottom: 100%;
      border-bottom: 17.32px solid currentColor;
    }
    
    .hexagon:after {
      top: 100%;
      border-top: 17.32px solid currentColor;
    }
    
    .hexagon span {
      position: absolute;
      top: 0;
      left: 0;
      width: 60px;
      height: 52px;
      background: currentColor;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    
    .ai-badge {
      background: linear-gradient(135deg, #8b5cf6, #ec4899);
      color: white;
      padding: 0.25rem 0.5rem;
      border-radius: 0.375rem;
      font-size: 0.625rem;
      font-weight: 700;
      letter-spacing: 0.05em;
    }
    
    .gps-tracking {
      position: relative;
      overflow: hidden;
    }
    
    .gps-tracking::before {
      content: '';
      position: absolute;
      top: 50%;
      left: 50%;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle, rgba(59, 130, 246, 0.2) 0%, transparent 70%);
      animation: radar 3s linear infinite;
      transform: translate(-50%, -50%);
    }
    
    @keyframes radar {
      0% { transform: translate(-50%, -50%) scale(0); opacity: 1; }
      100% { transform: translate(-50%, -50%) scale(2); opacity: 0; }
    }
  </style>
  <style>@view-transition { navigation: auto; }</style>
 </head>
 <body>
  <div id="app" class="w-full min-h-full"></div>
  <script>
    // Reference data
    const FACILITIES = [
      { id: 'fac1', name: 'Central Hospital', type: 'Hospital', location: 'Nairobi', lat: '-1.2921', lng: '36.8219' },
      { id: 'fac2', name: 'District Clinic A', type: 'Clinic', location: 'Mombasa', lat: '-4.0435', lng: '39.6682' },
      { id: 'fac3', name: 'Regional Warehouse', type: 'Warehouse', location: 'Kisumu', lat: '-0.0917', lng: '34.7680' },
      { id: 'fac4', name: 'Community Health Center', type: 'Health Center', location: 'Eldoret', lat: '0.5143', lng: '35.2698' }
    ];

    const DRUGS = [
      { id: 'drug1', name: 'Paracetamol 500mg', code: 'PAR500', unit: 'Tablets', min_stock: 1000, category: 'Analgesic' },
      { id: 'drug2', name: 'Amoxicillin 250mg', code: 'AMX250', unit: 'Capsules', min_stock: 500, category: 'Antibiotic' },
      { id: 'drug3', name: 'Artemether-Lumefantrine', code: 'ALU', unit: 'Tablets', min_stock: 800, category: 'Antimalarial' },
      { id: 'drug4', name: 'ORS Sachets', code: 'ORS', unit: 'Sachets', min_stock: 2000, category: 'Rehydration' },
      { id: 'drug5', name: 'Metformin 500mg', code: 'MET500', unit: 'Tablets', min_stock: 600, category: 'Antidiabetic' },
      { id: 'drug6', name: 'Insulin Glargine', code: 'INS100', unit: 'Vials', min_stock: 100, category: 'Hormone' }
    ];

    // Default configuration
    const defaultConfig = {
      app_title: 'MediTrack Nexus',
      tagline: 'Smart Medical Drug Inventory System',
      login_title: 'MediTrack Nexus',
      footer_text: '© 2024 MediTrack Nexus - Healthcare Innovation',
      background_color: '#f0f4f8',
      primary_color: '#2563eb',
      secondary_color: '#ffffff',
      text_color: '#1e293b',
      accent_color: '#8b5cf6',
      font_family: 'Inter',
      font_size: 16
    };

    // State
    let currentScreen = 'login';
    let currentUser = null;
    let allRecords = [];
    let offlineMode = false;
    let voiceAssistantActive = false;
    let darkMode = false;
    let chatMessages = [];

    // Initialize SDKs
    const dataHandler = {
      onDataChanged(data) {
        allRecords = data;
        if (currentScreen !== 'login') {
          renderCurrentScreen();
        }
      }
    };

    async function onConfigChange(config) {
      const customFont = config.font_family || defaultConfig.font_family;
      const baseSize = config.font_size || defaultConfig.font_size;
      const baseFontStack = '-apple-system, BlinkMacSystemFont, sans-serif';

      document.body.style.fontFamily = `${customFont}, ${baseFontStack}`;
      document.body.style.backgroundColor = config.background_color || defaultConfig.background_color;
      document.body.style.color = config.text_color || defaultConfig.text_color;

      // Update all text elements
      const elements = {
        '.app-title': { text: config.app_title || defaultConfig.app_title, size: baseSize * 1.5 },
        '.tagline': { text: config.tagline || defaultConfig.tagline, size: baseSize * 0.875 },
        '.login-title': { text: config.login_title || defaultConfig.login_title, size: baseSize * 2 },
        '.footer-text': { text: config.footer_text || defaultConfig.footer_text, size: baseSize * 0.875 }
      };

      Object.entries(elements).forEach(([selector, data]) => {
        document.querySelectorAll(selector).forEach(el => {
          el.textContent = data.text;
          el.style.fontSize = `${data.size}px`;
        });
      });

      // Update colors
      document.querySelectorAll('.btn-primary').forEach(btn => {
        btn.style.backgroundColor = config.primary_color || defaultConfig.primary_color;
      });

      document.querySelectorAll('.card-bg').forEach(card => {
        card.style.backgroundColor = config.secondary_color || defaultConfig.secondary_color;
      });

      document.querySelectorAll('.accent-color').forEach(el => {
        el.style.color = config.accent_color || defaultConfig.accent_color;
      });
    }

    function renderLogin() {
      const config = window.elementSdk?.config || defaultConfig;
      const app = document.getElementById('app');
      
      app.innerHTML = `
        <div class="w-full min-h-full flex items-center justify-center p-6 overflow-hidden" style="background: linear-gradient(135deg, #e0f2fe 0%, #ddd6fe 100%); position: relative;">
          <!-- Animated particles background -->
          <div style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; overflow: hidden; pointer-events: none;">
            ${Array.from({length: 20}, (_, i) => `
              <div class="particle" style="left: ${Math.random() * 100}%; top: ${Math.random() * 100}%; color: ${config.primary_color || defaultConfig.primary_color}; animation-delay: ${Math.random() * 3}s;"></div>
            `).join('')}
          </div>
          
          <!-- 3D Medical Models floating around -->
          <div style="position: absolute; top: 10%; left: 10%; transform-style: preserve-3d;">
            <div class="pill-3d" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%);"></div>
          </div>
          
          <div style="position: absolute; top: 20%; right: 15%; transform-style: preserve-3d;">
            <div class="molecule-structure">
              <div class="atom" style="top: 50%; left: 50%; background: ${config.primary_color || defaultConfig.primary_color}; transform: translate(-50%, -50%);"></div>
              <div class="atom" style="top: 20%; left: 50%; background: ${config.accent_color || defaultConfig.accent_color}; animation: moleculeOrbit 3s linear infinite;"></div>
              <div class="atom" style="top: 80%; left: 50%; background: ${config.accent_color || defaultConfig.accent_color}; animation: moleculeOrbit 3s linear infinite; animation-delay: 1s;"></div>
              <div class="atom" style="top: 50%; left: 20%; background: ${config.accent_color || defaultConfig.accent_color}; animation: moleculeOrbit 3s linear infinite; animation-delay: 2s;"></div>
              <div class="atom" style="top: 50%; right: 20%; background: ${config.accent_color || defaultConfig.accent_color}; animation: moleculeOrbit 3s linear infinite; animation-delay: 1.5s;"></div>
            </div>
          </div>
          
          <div style="position: absolute; bottom: 20%; left: 15%;">
            <div class="syringe-3d">
              <svg width="40" height="120" viewBox="0 0 40 120" style="filter: drop-shadow(0 10px 20px rgba(0,0,0,0.3));">
                <rect x="15" y="10" width="10" height="15" fill="${config.primary_color || defaultConfig.primary_color}" rx="2"/>
                <rect x="12" y="25" width="16" height="60" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" rx="3"/>
                <rect x="14" y="30" width="12" height="40" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.3"/>
                <rect x="17" y="85" width="6" height="30" fill="${config.primary_color || defaultConfig.primary_color}"/>
                <path d="M17 115 L20 120 L23 115" fill="${config.primary_color || defaultConfig.primary_color}"/>
              </svg>
            </div>
          </div>
          
          <div style="position: absolute; bottom: 15%; right: 10%;">
            <div class="heart-3d">
              <svg width="80" height="80" viewBox="0 0 80 80" style="filter: drop-shadow(0 5px 15px rgba(239,68,68,0.5));">
                <path d="M40,70 C40,70 10,50 10,30 C10,15 20,10 27,10 C34,10 40,15 40,15 C40,15 46,10 53,10 C60,10 70,15 70,30 C70,50 40,70 40,70 Z" fill="#ef4444" opacity="0.8"/>
                <ellipse cx="30" cy="25" rx="8" ry="6" fill="#fca5a5" opacity="0.6"/>
              </svg>
            </div>
          </div>
          
          <!-- Main login card with 3D effect -->
          <div class="card-bg w-full max-w-md rounded-2xl shadow-2xl fade-in" style="background: white; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; position: relative; z-index: 10; box-shadow: 0 20px 60px rgba(37, 99, 235, 0.15);">
            <!-- Advanced 3D Medical Logo -->
            <div class="flex justify-center pt-8 pb-4">
              <div class="scene-3d" style="perspective: 1000px; height: 160px;">
                <div class="model-3d" style="width: 140px; height: 140px; position: relative; transform-style: preserve-3d; animation-duration: 20s;">
                  <!-- 3D Hexagonal container -->
                  <svg width="140" height="140" viewBox="0 0 200 200" style="filter: drop-shadow(0 25px 70px ${config.primary_color || defaultConfig.primary_color}99);">
                    <!-- Outer glow rings -->
                    <circle cx="100" cy="100" r="90" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.2" class="pulse"/>
                    <circle cx="100" cy="100" r="80" fill="none" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="2" opacity="0.3" class="pulse" style="animation-delay: 0.5s;"/>
                    
                    <!-- 3D Hexagon base -->
                    <polygon points="100,20 160,50 160,110 100,140 40,110 40,50" 
                             fill="url(#hexGradient)" 
                             stroke="white" 
                             stroke-width="3"
                             opacity="0.95"/>
                    
                    <!-- Inner hexagon for depth -->
                    <polygon points="100,35 145,57 145,103 100,125 55,103 55,57" 
                             fill="${config.primary_color || defaultConfig.primary_color}" 
                             opacity="0.4"/>
                    
                    <!-- 3D Medical Cross with depth -->
                    <g style="transform: translateZ(20px);">
                      <!-- Vertical bar with 3D effect -->
                      <rect x="85" y="55" width="30" height="90" fill="white" rx="5"/>
                      <rect x="88" y="58" width="24" height="84" fill="${config.secondary_color || defaultConfig.secondary_color}" opacity="0.3" rx="4"/>
                      
                      <!-- Horizontal bar with 3D effect -->
                      <rect x="55" y="85" width="90" height="30" fill="white" rx="5"/>
                      <rect x="58" y="88" width="84" height="24" fill="${config.secondary_color || defaultConfig.secondary_color}" opacity="0.3" rx="4"/>
                      
                      <!-- Central glowing orb -->
                      <circle cx="100" cy="100" r="18" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9">
                        <animate attributeName="r" values="18;22;18" dur="2s" repeatCount="indefinite"/>
                      </circle>
                      <circle cx="100" cy="100" r="12" fill="white"/>
                      <circle cx="95" cy="95" r="5" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.6"/>
                      
                      <!-- Plus sign details -->
                      <circle cx="100" cy="65" r="4" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.8"/>
                      <circle cx="100" cy="135" r="4" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.8"/>
                      <circle cx="65" cy="100" r="4" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.8"/>
                      <circle cx="135" cy="100" r="4" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.8"/>
                    </g>
                    
                    <!-- Corner accent circles for medical theme -->
                    <circle cx="100" cy="25" r="5" fill="white" opacity="0.9"/>
                    <circle cx="155" cy="55" r="5" fill="white" opacity="0.9"/>
                    <circle cx="155" cy="105" r="5" fill="white" opacity="0.9"/>
                    <circle cx="100" cy="135" r="5" fill="white" opacity="0.9"/>
                    <circle cx="45" cy="105" r="5" fill="white" opacity="0.9"/>
                    <circle cx="45" cy="55" r="5" fill="white" opacity="0.9"/>
                    
                    <!-- DNA helix pattern around -->
                    <g opacity="0.4">
                      <circle cx="70" cy="50" r="3" fill="${config.accent_color || defaultConfig.accent_color}" class="float-animation"/>
                      <circle cx="130" cy="70" r="3" fill="${config.accent_color || defaultConfig.accent_color}" class="float-animation" style="animation-delay: 0.5s;"/>
                      <circle cx="130" cy="130" r="3" fill="${config.accent_color || defaultConfig.accent_color}" class="float-animation" style="animation-delay: 1s;"/>
                      <circle cx="70" cy="150" r="3" fill="${config.accent_color || defaultConfig.accent_color}" class="float-animation" style="animation-delay: 1.5s;"/>
                    </g>
                    
                    <!-- Gradient definitions -->
                    <defs>
                      <linearGradient id="hexGradient" x1="0%" y1="0%" x2="100%" y2="100%">
                        <stop offset="0%" style="stop-color:${config.primary_color || defaultConfig.primary_color};stop-opacity:1" />
                        <stop offset="50%" style="stop-color:${config.accent_color || defaultConfig.accent_color};stop-opacity:1" />
                        <stop offset="100%" style="stop-color:${config.primary_color || defaultConfig.primary_color};stop-opacity:0.8" />
                      </linearGradient>
                    </defs>
                  </svg>
                </div>
              </div>
            </div>
            
            <div class="px-8 pb-8">
              <div class="text-center mb-8">
                <h1 class="login-title font-bold mb-2" style="color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 2}px; text-shadow: 0 2px 10px ${config.primary_color || defaultConfig.primary_color}33">${config.login_title || defaultConfig.login_title}</h1>
                <p class="tagline mb-1" style="color: #64748b; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${config.tagline || defaultConfig.tagline}</p>
                <div class="flex items-center justify-center gap-2 mt-3">
                  <div class="ai-badge">🏆 AVISHKAAR S3</div>
                  <div class="ai-badge" style="background: linear-gradient(135deg, #f59e0b, #d97706);">AI-POWERED</div>
                </div>
              </div>
              
              <div class="space-y-4">
                <button onclick="login('admin')" class="btn-primary w-full py-3 px-4 rounded-lg font-semibold hover:opacity-90 transition flex items-center justify-center gap-2 relative overflow-hidden" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; font-size: ${config.font_size || defaultConfig.font_size}px; box-shadow: 0 5px 20px ${config.primary_color || defaultConfig.primary_color}44;">
                  <span>👨‍💼</span> Admin Dashboard
                </button>
                <button onclick="login('pharmacist')" class="btn-primary w-full py-3 px-4 rounded-lg font-semibold hover:opacity-90 transition flex items-center justify-center gap-2" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; font-size: ${config.font_size || defaultConfig.font_size}px; box-shadow: 0 5px 20px ${config.primary_color || defaultConfig.primary_color}44;">
                  <span>💊</span> Pharmacist Portal
                </button>
                <button onclick="login('nurse')" class="btn-primary w-full py-3 px-4 rounded-lg font-semibold hover:opacity-90 transition flex items-center justify-center gap-2" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; font-size: ${config.font_size || defaultConfig.font_size}px; box-shadow: 0 5px 20px ${config.primary_color || defaultConfig.primary_color}44;">
                  <span>👩‍⚕️</span> Nurse Access
                </button>
              </div>
              
              <p class="footer-text text-center mt-8" style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${config.footer_text || defaultConfig.footer_text}</p>
            </div>
          </div>
        </div>
      `;
    }

    function renderDashboard() {
      const config = window.elementSdk?.config || defaultConfig;
      const app = document.getElementById('app');
      
      // Calculate statistics
      const alerts = allRecords.filter(r => r.type === 'alert');
      const inventory = allRecords.filter(r => r.type === 'inventory');
      const shipments = allRecords.filter(r => r.type === 'shipment');
      const expiringItems = allRecords.filter(r => r.type === 'expiry_alert');
      
      app.innerHTML = `
        <div class="w-full min-h-full" style="background-color: ${config.background_color || defaultConfig.background_color}">
          <!-- Header -->
          <header class="card-bg shadow-sm" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <div class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">
              <div class="flex items-center gap-4">
                <div class="scene-3d" style="width: 52px; height: 52px; perspective: 500px;">
                  <div class="model-3d" style="width: 52px; height: 52px; animation-duration: 15s;">
                    <svg width="52" height="52" viewBox="0 0 100 100" style="filter: drop-shadow(0 4px 15px ${config.primary_color || defaultConfig.primary_color}88);">
                      <!-- 3D Hexagon -->
                      <polygon points="50,10 80,25 80,60 50,75 20,60 20,25" 
                               fill="url(#headerGradient)" 
                               stroke="white" 
                               stroke-width="2"/>
                      <polygon points="50,18 73,30 73,57 50,68 27,57 27,30" 
                               fill="${config.primary_color || defaultConfig.primary_color}" 
                               opacity="0.4"/>
                      
                      <!-- 3D Cross -->
                      <rect x="43" y="30" width="14" height="40" fill="white" rx="2"/>
                      <rect x="30" y="43" width="40" height="14" fill="white" rx="2"/>
                      <circle cx="50" cy="50" r="8" fill="${config.accent_color || defaultConfig.accent_color}">
                        <animate attributeName="r" values="8;10;8" dur="2s" repeatCount="indefinite"/>
                      </circle>
                      <circle cx="50" cy="50" r="5" fill="white"/>
                      
                      <defs>
                        <linearGradient id="headerGradient" x1="0%" y1="0%" x2="100%" y2="100%">
                          <stop offset="0%" style="stop-color:${config.primary_color || defaultConfig.primary_color};stop-opacity:1" />
                          <stop offset="100%" style="stop-color:${config.accent_color || defaultConfig.accent_color};stop-opacity:1" />
                        </linearGradient>
                      </defs>
                    </svg>
                  </div>
                </div>
                <div>
                  <h1 class="app-title font-bold" style="color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">${config.app_title || defaultConfig.app_title}</h1>
                  <p class="tagline text-gray-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px">${config.tagline || defaultConfig.tagline}</p>
                </div>
              </div>
              <div class="flex items-center gap-3">
                <button onclick="toggleTheme()" class="w-10 h-10 rounded-lg border border-gray-300 hover:bg-gray-50 transition flex items-center justify-center" title="Toggle Day/Night Mode" id="theme-toggle">
                  <span style="font-size: 20px;">☀️</span>
                </button>
                <button onclick="toggleVoiceAssistant()" class="w-10 h-10 rounded-lg border transition flex items-center justify-center" style="border-color: ${config.primary_color || defaultConfig.primary_color}44;" title="AI Voice Assistant" id="voice-toggle">
                  <span style="font-size: 20px;" id="voice-icon">🎤</span>
                </button>
                <button onclick="toggleChatbot()" class="w-10 h-10 rounded-lg transition flex items-center justify-center relative" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; box-shadow: 0 4px 12px ${config.primary_color || defaultConfig.primary_color}44;" title="AI Chatbot">
                  <span style="font-size: 20px;">💬</span>
                  <span class="pulse absolute -top-1 -right-1 w-3 h-3 rounded-full" style="background: #ef4444;"></span>
                </button>
                <button onclick="toggleOfflineMode()" class="px-3 py-1 rounded-lg border ${offlineMode ? 'bg-yellow-100 border-yellow-500 text-yellow-700' : 'border-gray-300 text-gray-600'}" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">
                  ${offlineMode ? '📵 Offline' : '🌐 Online'}
                </button>
                <span class="text-gray-600" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${currentUser.role}</span>
                <button onclick="logout()" class="px-4 py-2 text-gray-700 hover:bg-gray-100 rounded-lg transition" style="font-size: ${config.font_size || defaultConfig.font_size}px">Logout</button>
              </div>
            </div>
          </header>

          <!-- Navigation -->
          <nav class="card-bg border-b" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <div class="max-w-7xl mx-auto px-6">
              <div class="flex gap-8 overflow-x-auto">
                ${['overview', 'inventory', 'expiry', 'shipments', 'ai-insights', 'qr-scan', 'alerts'].map(screen => {
                  const icons = {
                    overview: '📊',
                    inventory: '💊',
                    expiry: '⏰',
                    shipments: '🚚',
                    'ai-insights': '🤖',
                    'qr-scan': '📱',
                    alerts: '⚠️'
                  };
                  const labels = {
                    overview: 'Overview',
                    inventory: 'Inventory',
                    expiry: 'Expiry',
                    shipments: 'Shipments',
                    'ai-insights': 'AI Insights',
                    'qr-scan': 'QR Scan',
                    alerts: 'Alerts'
                  };
                  const count = screen === 'alerts' ? alerts.length : screen === 'expiry' ? expiringItems.length : 0;
                  return `
                    <button onclick="navigateTo('${screen}')" class="nav-link py-4 px-2 border-b-2 whitespace-nowrap ${currentScreen === screen ? 'border-blue-500' : 'border-transparent'} hover:border-blue-300 transition font-semibold" style="font-size: ${config.font_size || defaultConfig.font_size}px; color: ${currentScreen === screen ? (config.primary_color || defaultConfig.primary_color) : '#64748b'}">
                      ${icons[screen]} ${labels[screen]} ${count > 0 ? `<span class="ml-2 px-2 py-1 bg-red-500 text-white rounded-full text-xs">${count}</span>` : ''}
                    </button>
                  `;
                }).join('')}
              </div>
            </div>
          </nav>

          <!-- Content -->
          <main class="max-w-7xl mx-auto px-6 py-8">
            <div id="content" class="fade-in"></div>
          </main>
        </div>

        <!-- AI Chatbot -->
        <div id="chatbot-container" class="fixed bottom-6 right-6 w-96 max-w-full shadow-2xl rounded-2xl overflow-hidden fade-in" style="display: none; z-index: 1001; background: white; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; max-height: 600px;">
          <!-- Chatbot Header -->
          <div class="p-4 flex items-center justify-between" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%);">
            <div class="flex items-center gap-3">
              <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background: rgba(255, 255, 255, 0.2);">
                <span style="font-size: 24px;">🤖</span>
              </div>
              <div>
                <h3 class="text-white font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">AI Assistant</h3>
                <p class="text-white text-xs opacity-80">Always here to help</p>
              </div>
            </div>
            <button onclick="toggleChatbot()" class="text-white hover:bg-white hover:bg-opacity-20 rounded-lg p-2 transition">
              <span style="font-size: 20px;">✕</span>
            </button>
          </div>

          <!-- Chat Messages -->
          <div id="chat-messages" class="p-4 space-y-3 overflow-y-auto" style="height: 400px; background: #f8fafc;">
            <div class="flex gap-3">
              <div class="w-8 h-8 rounded-full flex items-center justify-center flex-shrink-0" style="background: ${config.primary_color || defaultConfig.primary_color}22;">
                <span>🤖</span>
              </div>
              <div class="flex-1 p-3 rounded-lg" style="background: white; border: 1px solid ${config.primary_color || defaultConfig.primary_color}22;">
                <p style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Hi! I'm your AI assistant. I can help you with inventory management, alert you about low stock, expiring drugs, and optimize your supply chain. What would you like to know?</p>
              </div>
            </div>
          </div>

          <!-- Chat Input -->
          <div class="p-4 border-t" style="background: white;">
            <form id="chat-form" class="flex gap-2">
              <input type="text" id="chat-input" placeholder="Ask me anything..." class="flex-1 px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:border-blue-400" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">
              <button type="submit" class="px-4 py-2 rounded-lg text-white font-semibold hover:opacity-90 transition" style="background: ${config.primary_color || defaultConfig.primary_color};">
                <span style="font-size: 20px;">📤</span>
              </button>
            </form>
            <div class="mt-2 flex gap-2 overflow-x-auto">
              <button onclick="quickChat('Show low stock items')" class="px-3 py-1 rounded-full text-xs whitespace-nowrap" style="background: ${config.primary_color || defaultConfig.primary_color}22; color: ${config.primary_color || defaultConfig.primary_color};">📊 Low Stock</button>
              <button onclick="quickChat('What drugs are expiring soon?')" class="px-3 py-1 rounded-full text-xs whitespace-nowrap" style="background: ${config.accent_color || defaultConfig.accent_color}22; color: ${config.accent_color || defaultConfig.accent_color};">⏰ Expiring</button>
              <button onclick="quickChat('Active shipments status')" class="px-3 py-1 rounded-full text-xs whitespace-nowrap" style="background: ${config.primary_color || defaultConfig.primary_color}22; color: ${config.primary_color || defaultConfig.primary_color};">🚚 Shipments</button>
            </div>
          </div>
        </div>

        <!-- Voice Assistant Indicator with 3D Demo -->
        <div id="voice-indicator" class="fixed bottom-6 left-6 rounded-2xl shadow-2xl fade-in" style="display: none; z-index: 1001; background: white; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; max-width: 420px;">
          <div class="p-4">
            <div class="flex items-center gap-3 mb-3">
              <div class="relative">
                <div class="w-12 h-12 rounded-full flex items-center justify-center" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%);">
                  <span style="font-size: 24px;">🎤</span>
                </div>
                <div class="pulse absolute inset-0 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color}; opacity: 0.3;"></div>
              </div>
              <div>
                <p class="font-bold" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">AI Voice Active 🔴</p>
                <p class="text-xs" style="color: ${config.text_color || defaultConfig.text_color}88;">Speak your command</p>
              </div>
            </div>
            
            <!-- Voice Commands Demo -->
            <div class="border-t pt-3" style="border-color: ${config.primary_color || defaultConfig.primary_color}22;">
              <p class="text-xs font-semibold mb-2" style="color: ${config.text_color || defaultConfig.text_color}88;">TRY SAYING:</p>
              <div class="space-y-1">
                <div class="flex items-center gap-2 text-xs" style="color: ${config.text_color || defaultConfig.text_color};">
                  <span style="color: ${config.primary_color || defaultConfig.primary_color};">▸</span>
                  <span>"Open inventory"</span>
                </div>
                <div class="flex items-center gap-2 text-xs" style="color: ${config.text_color || defaultConfig.text_color};">
                  <span style="color: ${config.primary_color || defaultConfig.primary_color};">▸</span>
                  <span>"Show expiry"</span>
                </div>
                <div class="flex items-center gap-2 text-xs" style="color: ${config.text_color || defaultConfig.text_color};">
                  <span style="color: ${config.primary_color || defaultConfig.primary_color};">▸</span>
                  <span>"Open shipments"</span>
                </div>
                <div class="flex items-center gap-2 text-xs" style="color: ${config.text_color || defaultConfig.text_color};">
                  <span style="color: ${config.primary_color || defaultConfig.primary_color};">▸</span>
                  <span>"Show alerts"</span>
                </div>
                <div class="flex items-center gap-2 text-xs" style="color: ${config.text_color || defaultConfig.text_color};">
                  <span style="color: ${config.primary_color || defaultConfig.primary_color};">▸</span>
                  <span>"Open AI insights"</span>
                </div>
              </div>
            </div>
            
            <!-- 3D Sound Wave Visualization -->
            <div class="mt-3 pt-3 border-t" style="border-color: ${config.primary_color || defaultConfig.primary_color}22;">
              <div class="flex items-center justify-center gap-1" style="height: 40px;">
                ${Array.from({length: 20}, (_, i) => `
                  <div class="bounce-animation" style="width: 3px; background: ${config.primary_color || defaultConfig.primary_color}; border-radius: 2px; animation-delay: ${i * 0.1}s; height: ${20 + Math.random() * 20}px; opacity: 0.7;"></div>
                `).join('')}
              </div>
            </div>
          </div>
        </div>
      `;

      renderContent();
      
      // Initialize chat form
      setTimeout(() => {
        initChatForm();
      }, 100);
    }

    function renderContent() {
      const config = window.elementSdk?.config || defaultConfig;
      const content = document.getElementById('content');
      
      const screens = {
        overview: renderOverview,
        inventory: renderInventory,
        expiry: renderExpiry,
        shipments: renderShipments,
        'ai-insights': renderAIInsights,
        'qr-scan': renderQRScan,
        alerts: renderAlerts
      };
      
      if (screens[currentScreen]) {
        screens[currentScreen](content, config);
      }
    }

    function renderOverview(content, config) {
      const alerts = allRecords.filter(r => r.type === 'alert');
      const inventory = allRecords.filter(r => r.type === 'inventory');
      const shipments = allRecords.filter(r => r.type === 'shipment');
      const expiringItems = allRecords.filter(r => r.type === 'expiry_alert');
      
      const lowStockCount = alerts.filter(a => a.status === 'low_stock').length;
      const totalDrugs = inventory.length;
      const activeShipments = shipments.filter(s => s.status === 'in_transit').length;
      const expiringCount = expiringItems.length;
      
      content.innerHTML = `
        <!-- 3D Holographic Command Center Header -->
        <div class="card-bg p-8 rounded-2xl shadow-2xl mb-8" style="background: linear-gradient(135deg, white 0%, #f8fafc 100%); border: 2px solid ${config.primary_color || defaultConfig.primary_color}33; position: relative; overflow: hidden; box-shadow: 0 10px 40px rgba(37, 99, 235, 0.1);">
          <div style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; opacity: 0.1; pointer-events: none;">
            ${Array.from({length: 30}, (_, i) => `
              <div class="particle" style="left: ${Math.random() * 100}%; top: ${Math.random() * 100}%; color: ${config.primary_color || defaultConfig.primary_color}; animation-delay: ${Math.random() * 3}s;"></div>
            `).join('')}
          </div>
          
          <div class="grid grid-cols-1 lg:grid-cols-3 gap-6 items-center relative z-10">
            <!-- 3D DNA Helix Logo -->
            <div class="text-center">
              <div class="scene-3d flex justify-center" style="height: 200px;">
                <div class="model-3d" style="width: 150px; height: 200px; animation-duration: 20s;">
                  <svg width="150" height="200" viewBox="0 0 150 200" style="filter: drop-shadow(0 0 25px ${config.primary_color || defaultConfig.primary_color}99);">
                    <!-- Central double helix strands -->
                    <path d="M 75 10 Q 95 40, 75 70 Q 55 100, 75 130 Q 95 160, 75 190" 
                          stroke="${config.primary_color || defaultConfig.primary_color}" 
                          stroke-width="4" 
                          fill="none" 
                          opacity="0.9"/>
                    <path d="M 75 10 Q 55 40, 75 70 Q 95 100, 75 130 Q 55 160, 75 190" 
                          stroke="${config.accent_color || defaultConfig.accent_color}" 
                          stroke-width="4" 
                          fill="none" 
                          opacity="0.9"/>
                    
                    <!-- Connecting base pairs with glow -->
                    <g opacity="0.8">
                      <line x1="60" y1="20" x2="90" y2="20" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                      <line x1="55" y1="40" x2="95" y2="40" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                      <line x1="60" y1="60" x2="90" y2="60" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                      <line x1="55" y1="80" x2="95" y2="80" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                      <line x1="60" y1="100" x2="90" y2="100" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                      <line x1="55" y1="120" x2="95" y2="120" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                      <line x1="60" y1="140" x2="90" y2="140" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                      <line x1="55" y1="160" x2="95" y2="160" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                      <line x1="60" y1="180" x2="90" y2="180" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                    </g>
                    
                    <!-- Nucleotide spheres with 3D effect -->
                    <g class="float-animation" style="animation-delay: 0s;">
                      <circle cx="60" cy="20" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="60" cy="20" r="4" fill="white" opacity="0.6"/>
                      <circle cx="90" cy="20" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="90" cy="20" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 0.5s;">
                      <circle cx="55" cy="40" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="55" cy="40" r="4" fill="white" opacity="0.6"/>
                      <circle cx="95" cy="40" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="95" cy="40" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 1s;">
                      <circle cx="60" cy="60" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="60" cy="60" r="4" fill="white" opacity="0.6"/>
                      <circle cx="90" cy="60" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="90" cy="60" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 1.5s;">
                      <circle cx="55" cy="80" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="55" cy="80" r="4" fill="white" opacity="0.6"/>
                      <circle cx="95" cy="80" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="95" cy="80" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 2s;">
                      <circle cx="60" cy="100" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="60" cy="100" r="4" fill="white" opacity="0.6"/>
                      <circle cx="90" cy="100" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="90" cy="100" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 2.5s;">
                      <circle cx="55" cy="120" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="55" cy="120" r="4" fill="white" opacity="0.6"/>
                      <circle cx="95" cy="120" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="95" cy="120" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 3s;">
                      <circle cx="60" cy="140" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="60" cy="140" r="4" fill="white" opacity="0.6"/>
                      <circle cx="90" cy="140" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="90" cy="140" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 3.5s;">
                      <circle cx="55" cy="160" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="55" cy="160" r="4" fill="white" opacity="0.6"/>
                      <circle cx="95" cy="160" r="8" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                      <circle cx="95" cy="160" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <g class="float-animation" style="animation-delay: 4s;">
                      <circle cx="60" cy="180" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="60" cy="180" r="4" fill="white" opacity="0.6"/>
                      <circle cx="90" cy="180" r="8" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                      <circle cx="90" cy="180" r="4" fill="white" opacity="0.6"/>
                    </g>
                    
                    <!-- Outer glow rings -->
                    <ellipse cx="75" cy="100" rx="70" ry="95" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.2" class="pulse"/>
                    <ellipse cx="75" cy="100" rx="60" ry="85" fill="none" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="1.5" opacity="0.3" class="pulse" style="animation-delay: 0.5s;"/>
                    
                    <!-- Center medical cross overlay -->
                    <g opacity="0.6">
                      <rect x="72" y="85" width="6" height="30" fill="white" rx="2"/>
                      <rect x="60" y="97" width="30" height="6" fill="white" rx="2"/>
                      <circle cx="75" cy="100" r="5" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    </g>
                  </svg>
                </div>
              </div>
              <p class="text-sm font-semibold" style="color: ${config.primary_color || defaultConfig.primary_color};">DNA-LEVEL TRACKING</p>
            </div>
            
            <!-- Center Title -->
            <div class="text-center">
              <h2 class="text-4xl font-bold mb-2" style="color: ${config.text_color || defaultConfig.text_color}; text-shadow: 0 0 20px ${config.primary_color || defaultConfig.primary_color}66;">COMMAND CENTER</h2>
              <div class="ai-badge text-lg px-6 py-2 mb-4">QUANTUM AI ACTIVE</div>
              <div class="flex justify-center gap-2">
                <div class="pulse w-3 h-3 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color};"></div>
                <span style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">All Systems Operational</span>
              </div>
            </div>
            
            <!-- 3D Rotating Medical Cross -->
            <div class="text-center">
              <div class="scene-3d flex justify-center" style="height: 200px;">
                <div class="model-3d" style="width: 150px; height: 150px;">
                  <svg width="150" height="150" viewBox="0 0 100 100" style="filter: drop-shadow(0 0 30px ${config.primary_color || defaultConfig.primary_color});">
                    <rect x="40" y="10" width="20" height="80" fill="${config.primary_color || defaultConfig.primary_color}" rx="3"/>
                    <rect x="10" y="40" width="80" height="20" fill="${config.accent_color || defaultConfig.accent_color}" rx="3"/>
                    <circle cx="50" cy="50" r="12" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="white" stroke-width="2"/>
                    <circle cx="50" cy="50" r="6" fill="white"/>
                  </svg>
                </div>
              </div>
              <p class="text-sm font-semibold" style="color: ${config.accent_color || defaultConfig.accent_color};">MEDICAL GRADE AI</p>
            </div>
          </div>
        </div>

        <h2 class="text-2xl font-bold mb-6" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">Real-Time Analytics</h2>
        
        <!-- Stats Grid with 3D Icons -->
        <div class="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
          <div class="card-bg card-hover p-6 rounded-lg" style="background: white; border: 2px solid ${config.primary_color || defaultConfig.primary_color}22; box-shadow: 0 4px 20px rgba(37, 99, 235, 0.08);">
            <div class="flex items-center justify-between">
              <div>
                <p class="text-gray-600 mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Total Inventory</p>
                <p class="text-3xl font-bold" style="color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 2}px">${totalDrugs}</p>
              </div>
              <div class="scene-3d" style="width: 60px; height: 60px;">
                <div class="pill-3d float-animation" style="width: 60px; height: 25px; background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 50%, #fde047 50%, #fef3c7 100%);"></div>
              </div>
            </div>
          </div>
          
          <div class="card-bg card-hover p-6 rounded-lg shadow hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid #ef444433;">
            <div class="flex items-center justify-between">
              <div>
                <p class="text-gray-600 mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Low Stock Alerts</p>
                <p class="text-3xl font-bold text-red-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 2}px">${lowStockCount}</p>
              </div>
              <div class="scene-3d" style="width: 60px; height: 60px;">
                <svg width="60" height="60" viewBox="0 0 100 100" class="spin-animation" style="animation-duration: 3s;">
                  <polygon points="50,10 90,90 10,90" fill="#ef4444" opacity="0.8" stroke="white" stroke-width="4"/>
                  <text x="50" y="70" text-anchor="middle" fill="white" font-size="40" font-weight="bold">!</text>
                </svg>
              </div>
            </div>
          </div>
          
          <div class="card-bg card-hover p-6 rounded-lg shadow hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid ${config.accent_color || defaultConfig.accent_color}33;">
            <div class="flex items-center justify-between">
              <div>
                <p class="text-gray-600 mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Active Shipments</p>
                <p class="text-3xl font-bold accent-color" style="color: ${config.accent_color || defaultConfig.accent_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 2}px">${activeShipments}</p>
              </div>
              <div class="scene-3d" style="width: 60px; height: 60px;">
                <svg width="60" height="40" viewBox="0 0 200 120" class="float-animation">
                  <rect x="40" y="30" width="80" height="40" fill="${config.accent_color || defaultConfig.accent_color}" rx="4"/>
                  <rect x="120" y="35" width="30" height="35" fill="${config.primary_color || defaultConfig.primary_color}" rx="2"/>
                  <circle cx="60" cy="75" r="8" fill="#1f2937"/>
                  <circle cx="100" cy="75" r="8" fill="#1f2937"/>
                  <circle cx="135" cy="75" r="8" fill="#1f2937"/>
                </svg>
              </div>
            </div>
          </div>
          
          <div class="card-bg card-hover p-6 rounded-lg shadow hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid #f9731633;">
            <div class="flex items-center justify-between">
              <div>
                <p class="text-gray-600 mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Expiring Soon</p>
                <p class="text-3xl font-bold text-orange-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 2}px">${expiringCount}</p>
              </div>
              <div class="scene-3d" style="width: 60px; height: 60px;">
                <svg width="60" height="60" viewBox="0 0 100 100" class="pulse">
                  <circle cx="50" cy="50" r="45" fill="none" stroke="#f97316" stroke-width="4"/>
                  <circle cx="50" cy="50" r="30" fill="none" stroke="#f97316" stroke-width="3" opacity="0.6"/>
                  <rect x="48" y="20" width="4" height="25" fill="#f97316" rx="2"/>
                  <rect x="48" y="55" width="4" height="8" fill="#f97316" rx="2"/>
                </svg>
              </div>
            </div>
          </div>
        </div>

        <!-- Features Grid with 3D Temperature Monitoring -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
          <div class="card-bg p-6 rounded-lg shadow hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 1px solid ${config.primary_color || defaultConfig.primary_color}22;">
            <div class="flex items-center gap-3 mb-3">
              <div class="text-3xl">🤖</div>
              <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">AI Forecasting</h3>
            </div>
            <p class="text-gray-600 mb-3" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Predictive analytics for demand forecasting</p>
            <div class="flex items-center gap-2">
              <div class="pulse w-2 h-2 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color};"></div>
              <span style="color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px; font-weight: 600;">94.2% ACCURACY</span>
            </div>
          </div>
          
          <div class="card-bg p-6 rounded-lg shadow hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 1px solid ${config.primary_color || defaultConfig.primary_color}22;">
            <div class="flex items-center gap-3 mb-3">
              <div class="text-3xl">📍</div>
              <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">GPS Tracking</h3>
            </div>
            <p class="text-gray-600 mb-3" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Real-time location tracking for shipments</p>
            <div class="flex items-center gap-2">
              <div class="pulse w-2 h-2 rounded-full bg-green-500"></div>
              <span style="color: #10b981; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px; font-weight: 600;">LIVE TRACKING</span>
            </div>
          </div>
          
          <div class="card-bg p-6 rounded-lg shadow hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 1px solid ${config.primary_color || defaultConfig.primary_color}22;">
            <div class="flex items-center gap-3 mb-3">
              <div class="text-3xl">⏰</div>
              <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">Expiry Management</h3>
            </div>
            <p class="text-gray-600 mb-3" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Smart FEFO batch tracking system</p>
            <div class="flex items-center gap-2">
              <div class="pulse w-2 h-2 rounded-full bg-blue-500"></div>
              <span style="color: #3b82f6; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px; font-weight: 600;">AUTO ALERTS</span>
            </div>
          </div>
          
          <div class="card-bg p-6 rounded-lg shadow hologram-effect relative overflow-hidden" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 1px solid ${config.accent_color || defaultConfig.accent_color}22;">
            <div class="flex items-center gap-3 mb-3">
              <div class="scene-3d" style="width: 40px; height: 40px;">
                <svg width="40" height="40" viewBox="0 0 100 100" class="float-animation">
                  <rect x="30" y="10" width="40" height="70" fill="${config.accent_color || defaultConfig.accent_color}" rx="8" stroke="white" stroke-width="2"/>
                  <rect x="35" y="60" width="30" height="15" fill="#ef4444" rx="3"/>
                  <circle cx="50" cy="67" r="3" fill="white"/>
                  <rect x="42" y="25" width="16" height="3" fill="white" opacity="0.7"/>
                  <rect x="42" y="35" width="16" height="3" fill="white" opacity="0.7"/>
                  <rect x="42" y="45" width="16" height="3" fill="white" opacity="0.7"/>
                </svg>
              </div>
              <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">Cold Chain</h3>
            </div>
            <p class="text-gray-600 mb-3" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Temperature monitoring 24/7</p>
            <div class="flex items-center gap-2">
              <div class="pulse w-2 h-2 rounded-full" style="background: ${config.accent_color || defaultConfig.accent_color};"></div>
              <span style="color: ${config.accent_color || defaultConfig.accent_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px; font-weight: 600;">2-8°C OPTIMAL</span>
            </div>
          </div>
        </div>

        <!-- 3D Blockchain Security Section -->
        <div class="card-bg p-8 rounded-2xl shadow-2xl mb-8 hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; position: relative;">
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
            <div>
              <div class="flex items-center gap-3 mb-4">
                <div class="ai-badge">🔐 BLOCKCHAIN</div>
                <h3 class="text-2xl font-bold" style="color: ${config.text_color || defaultConfig.text_color};">Tamper-Proof Security</h3>
              </div>
              <p class="text-gray-600 mb-6" style="font-size: ${config.font_size || defaultConfig.font_size}px;">Every transaction is cryptographically secured and permanently recorded on our distributed ledger.</p>
              <div class="space-y-3">
                <div class="flex items-center gap-3">
                  <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background: ${config.primary_color || defaultConfig.primary_color}22;">
                    <span>🔗</span>
                  </div>
                  <div>
                    <p class="font-semibold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Chain Verification</p>
                    <p class="text-gray-500 text-sm">256-bit encryption</p>
                  </div>
                </div>
                <div class="flex items-center gap-3">
                  <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background: ${config.accent_color || defaultConfig.accent_color}22;">
                    <span>✓</span>
                  </div>
                  <div>
                    <p class="font-semibold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Audit Trail</p>
                    <p class="text-gray-500 text-sm">Immutable records</p>
                  </div>
                </div>
                <div class="flex items-center gap-3">
                  <div class="w-10 h-10 rounded-full flex items-center justify-center" style="background: ${config.primary_color || defaultConfig.primary_color}22;">
                    <span>🛡️</span>
                  </div>
                  <div>
                    <p class="font-semibold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Anti-Counterfeit</p>
                    <p class="text-gray-500 text-sm">Drug authenticity</p>
                  </div>
                </div>
              </div>
            </div>
            <div class="scene-3d flex justify-center" style="height: 250px;">
              <div class="model-3d">
                <svg width="280" height="250" viewBox="0 0 280 250" style="filter: drop-shadow(0 0 30px ${config.primary_color || defaultConfig.primary_color}66);">
                  <!-- Chain blocks -->
                  <g class="float-animation" style="animation-delay: 0s;">
                    <rect x="20" y="40" width="60" height="60" fill="${config.primary_color || defaultConfig.primary_color}" rx="8" opacity="0.9"/>
                    <text x="50" y="75" text-anchor="middle" fill="white" font-size="12" font-weight="bold">BLOCK</text>
                    <text x="50" y="90" text-anchor="middle" fill="white" font-size="10">#1</text>
                  </g>
                  
                  <line x1="80" y1="70" x2="110" y2="70" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3" opacity="0.6"/>
                  
                  <g class="float-animation" style="animation-delay: 0.5s;">
                    <rect x="110" y="40" width="60" height="60" fill="${config.accent_color || defaultConfig.accent_color}" rx="8" opacity="0.9"/>
                    <text x="140" y="75" text-anchor="middle" fill="white" font-size="12" font-weight="bold">BLOCK</text>
                    <text x="140" y="90" text-anchor="middle" fill="white" font-size="10">#2</text>
                  </g>
                  
                  <line x1="170" y1="70" x2="200" y2="70" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3" opacity="0.6"/>
                  
                  <g class="float-animation" style="animation-delay: 1s;">
                    <rect x="200" y="40" width="60" height="60" fill="${config.primary_color || defaultConfig.primary_color}" rx="8" opacity="0.9"/>
                    <text x="230" y="75" text-anchor="middle" fill="white" font-size="12" font-weight="bold">BLOCK</text>
                    <text x="230" y="90" text-anchor="middle" fill="white" font-size="10">#3</text>
                  </g>
                  
                  <!-- Verification nodes -->
                  <g class="bounce-animation">
                    <circle cx="50" cy="150" r="25" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                    <text x="50" y="157" text-anchor="middle" fill="${config.primary_color || defaultConfig.primary_color}" font-size="24">✓</text>
                  </g>
                  
                  <g class="bounce-animation" style="animation-delay: 0.5s;">
                    <circle cx="140" cy="150" r="25" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                    <text x="140" y="157" text-anchor="middle" fill="${config.accent_color || defaultConfig.accent_color}" font-size="24">��</text>
                  </g>
                  
                  <g class="bounce-animation" style="animation-delay: 1s;">
                    <circle cx="230" cy="150" r="25" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                    <text x="230" y="157" text-anchor="middle" fill="${config.primary_color || defaultConfig.primary_color}" font-size="24">✓</text>
                  </g>
                  
                  <!-- Connection lines -->
                  <line x1="50" y1="100" x2="50" y2="125" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.4" stroke-dasharray="5,5"/>
                  <line x1="140" y1="100" x2="140" y2="125" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="2" opacity="0.4" stroke-dasharray="5,5"/>
                  <line x1="230" y1="100" x2="230" y2="125" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.4" stroke-dasharray="5,5"/>
                </svg>
              </div>
            </div>
          </div>
        </div>

        <!-- Facilities -->
        <div class="card-bg p-6 rounded-lg shadow mb-8" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
          <h3 class="text-xl font-bold mb-4" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.25}px">Connected Facilities</h3>
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
            ${FACILITIES.map(f => `
              <div class="border border-gray-200 rounded-lg p-4 hover:border-blue-300 transition">
                <div class="flex justify-between items-start mb-2">
                  <div>
                    <p class="font-semibold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">${f.name}</p>
                    <p class="text-gray-600" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${f.type}</p>
                  </div>
                  <span class="status-badge" style="background-color: ${config.accent_color || defaultConfig.accent_color}33; color: ${config.accent_color || defaultConfig.accent_color}">
                    <span class="pulse inline-block w-2 h-2 bg-green-500 rounded-full mr-1"></span>
                    Active
                  </span>
                </div>
                <p class="text-gray-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">📍 ${f.location}</p>
              </div>
            `).join('')}
          </div>
        </div>
      `;
    }

    function renderInventory(content, config) {
      const inventory = allRecords.filter(r => r.type === 'inventory');
      
      content.innerHTML = `
        <div class="flex justify-between items-center mb-6">
          <div>
            <h2 class="text-2xl font-bold mb-2" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">Drug Inventory Management</h2>
            <div class="flex items-center gap-4">
              <div class="flex items-center gap-2">
                <div class="pulse w-2 h-2 rounded-full bg-green-500"></div>
                <span style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">IoT Sensors Active</span>
              </div>
              <div class="ai-badge text-xs">REAL-TIME MONITORING</div>
            </div>
          </div>
          <button onclick="showAddInventory()" class="px-6 py-2 rounded-lg font-semibold hover:opacity-90 transition" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; font-size: ${config.font_size || defaultConfig.font_size}px; box-shadow: 0 5px 20px ${config.primary_color || defaultConfig.primary_color}44;">+ Add Stock</button>
        </div>
        
        <!-- 3D IoT Sensor Network Visualization -->
        <div class="card-bg p-6 rounded-2xl shadow-2xl mb-6 hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; position: relative; overflow: hidden;">
          <div class="grid grid-cols-1 lg:grid-cols-4 gap-4">
            <div class="text-center">
              <div class="scene-3d flex justify-center mb-2" style="height: 80px;">
                <div class="model-3d" style="width: 60px; height: 60px;">
                  <svg width="60" height="60" viewBox="0 0 100 100" style="filter: drop-shadow(0 0 15px ${config.primary_color || defaultConfig.primary_color});">
                    <circle cx="50" cy="50" r="20" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                    <circle cx="50" cy="50" r="30" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.5"/>
                    <circle cx="50" cy="50" r="40" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="1" opacity="0.3"/>
                    <rect x="45" y="10" width="10" height="15" fill="${config.primary_color || defaultConfig.primary_color}"/>
                  </svg>
                </div>
              </div>
              <p class="font-bold" style="color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px;">24</p>
              <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Temperature Sensors</p>
            </div>
            
            <div class="text-center">
              <div class="scene-3d flex justify-center mb-2" style="height: 80px;">
                <div class="model-3d" style="width: 60px; height: 60px; animation-delay: 0.5s;">
                  <svg width="60" height="60" viewBox="0 0 100 100" style="filter: drop-shadow(0 0 15px ${config.accent_color || defaultConfig.accent_color});">
                    <rect x="30" y="30" width="40" height="40" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9" rx="5"/>
                    <circle cx="50" cy="50" r="8" fill="white"/>
                    <line x1="50" y1="50" x2="65" y2="35" stroke="white" stroke-width="2"/>
                  </svg>
                </div>
              </div>
              <p class="font-bold" style="color: ${config.accent_color || defaultConfig.accent_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px;">18</p>
              <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Humidity Monitors</p>
            </div>
            
            <div class="text-center">
              <div class="scene-3d flex justify-center mb-2" style="height: 80px;">
                <div class="model-3d" style="width: 60px; height: 60px; animation-delay: 1s;">
                  <svg width="60" height="60" viewBox="0 0 100 100" style="filter: drop-shadow(0 0 15px ${config.primary_color || defaultConfig.primary_color});">
                    <rect x="20" y="30" width="60" height="40" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9" rx="3"/>
                    <circle cx="40" cy="50" r="5" fill="white"/>
                    <circle cx="60" cy="50" r="5" fill="white"/>
                    <path d="M 35 60 Q 50 70 65 60" stroke="white" stroke-width="2" fill="none"/>
                  </svg>
                </div>
              </div>
              <p class="font-bold text-green-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px;">32</p>
              <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Motion Detectors</p>
            </div>
            
            <div class="text-center">
              <div class="scene-3d flex justify-center mb-2" style="height: 80px;">
                <div class="model-3d" style="width: 60px; height: 60px; animation-delay: 1.5s;">
                  <svg width="60" height="60" viewBox="0 0 100 100" style="filter: drop-shadow(0 0 15px ${config.accent_color || defaultConfig.accent_color});">
                    <polygon points="50,20 80,35 80,65 50,80 20,65 20,35" fill="${config.accent_color || defaultConfig.accent_color}" opacity="0.9"/>
                    <circle cx="50" cy="50" r="10" fill="white"/>
                  </svg>
                </div>
              </div>
              <p class="font-bold text-yellow-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px;">16</p>
              <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Light Sensors</p>
            </div>
          </div>
        </div>

        <div class="card-bg rounded-lg shadow overflow-hidden" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
          <table class="w-full">
            <thead class="bg-gray-50">
              <tr>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Facility</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Drug</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Batch</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Stock</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Min Level</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Expiry</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Status</th>
                <th class="px-6 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Actions</th>
              </tr>
            </thead>
            <tbody class="divide-y divide-gray-200">
              ${inventory.length === 0 ? `
                <tr>
                  <td colspan="8" class="px-6 py-8 text-center text-gray-500" style="font-size: ${config.font_size || defaultConfig.font_size}px">
                    No inventory records yet. Click "Add Stock" to get started.
                  </td>
                </tr>
              ` : inventory.map(item => {
                const isLowStock = item.quantity < item.min_level;
                const expiryDate = item.expiry_date ? new Date(item.expiry_date) : null;
                const daysToExpiry = expiryDate ? Math.ceil((expiryDate - new Date()) / (1000 * 60 * 60 * 24)) : null;
                const isExpiringSoon = daysToExpiry && daysToExpiry <= 90;
                
                return `
                  <tr class="hover:bg-gray-50">
                    <td class="px-6 py-4 whitespace-nowrap" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${item.facility_name}</td>
                    <td class="px-6 py-4 whitespace-nowrap font-medium" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${item.drug_name}</td>
                    <td class="px-6 py-4 whitespace-nowrap text-gray-500" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px">${item.batch_number || 'N/A'}</td>
                    <td class="px-6 py-4 whitespace-nowrap" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${item.quantity}</td>
                    <td class="px-6 py-4 whitespace-nowrap" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${item.min_level}</td>
                    <td class="px-6 py-4 whitespace-nowrap" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">
                      ${expiryDate ? `<span class="${isExpiringSoon ? 'text-orange-600 font-semibold' : 'text-gray-600'}">${expiryDate.toLocaleDateString()}</span>` : 'N/A'}
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap">
                      <span class="status-badge" style="background-color: ${isLowStock ? '#fef2f2' : '#f0fdf4'}; color: ${isLowStock ? '#dc2626' : '#16a34a'}">
                        ${isLowStock ? '⚠️ Low' : '✓ OK'}
                      </span>
                    </td>
                    <td class="px-6 py-4 whitespace-nowrap">
                      <button onclick="adjustStock('${item.id}')" class="text-blue-600 hover:text-blue-800 mr-2" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Adjust</button>
                      <button onclick="deleteRecord('${item.id}')" class="text-red-600 hover:text-red-800" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Delete</button>
                    </td>
                  </tr>
                `;
              }).join('')}
            </tbody>
          </table>
        </div>

        <div id="inventory-modal"></div>
      `;
    }

    function renderExpiry(content, config) {
      const inventory = allRecords.filter(r => r.type === 'inventory' && r.expiry_date);
      const now = new Date();
      
      const expiringItems = inventory.map(item => {
        const expiryDate = new Date(item.expiry_date);
        const daysToExpiry = Math.ceil((expiryDate - now) / (1000 * 60 * 60 * 24));
        return { ...item, daysToExpiry, expiryDate };
      }).filter(item => item.daysToExpiry <= 180).sort((a, b) => a.daysToExpiry - b.daysToExpiry);
      
      content.innerHTML = `
        <div class="flex justify-between items-center mb-6">
          <h2 class="text-2xl font-bold" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">Expiry Management (FEFO)</h2>
          <div class="ai-badge">AI OPTIMIZED</div>
        </div>

        <div class="card-bg p-6 rounded-lg shadow mb-6" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
          <h3 class="font-bold mb-3" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">📊 Expiry Analytics</h3>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
            <div class="border border-red-200 rounded-lg p-4 bg-red-50">
              <p class="text-red-600 font-bold text-2xl">${expiringItems.filter(i => i.daysToExpiry <= 30).length}</p>
              <p class="text-red-700 text-sm">Expiring in 30 days</p>
            </div>
            <div class="border border-orange-200 rounded-lg p-4 bg-orange-50">
              <p class="text-orange-600 font-bold text-2xl">${expiringItems.filter(i => i.daysToExpiry > 30 && i.daysToExpiry <= 90).length}</p>
              <p class="text-orange-700 text-sm">Expiring in 90 days</p>
            </div>
            <div class="border border-yellow-200 rounded-lg p-4 bg-yellow-50">
              <p class="text-yellow-600 font-bold text-2xl">${expiringItems.filter(i => i.daysToExpiry > 90).length}</p>
              <p class="text-yellow-700 text-sm">Expiring in 180 days</p>
            </div>
          </div>
        </div>

        <div class="space-y-4">
          ${expiringItems.length === 0 ? `
            <div class="card-bg p-8 rounded-lg shadow text-center" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
              <div class="text-6xl mb-4">✅</div>
              <p class="text-xl font-semibold mb-2" style="color: ${config.accent_color || defaultConfig.accent_color}">No Expiring Items</p>
              <p class="text-gray-500" style="font-size: ${config.font_size || defaultConfig.font_size}px">All inventory is within safe expiry dates</p>
            </div>
          ` : expiringItems.map(item => {
            const urgency = item.daysToExpiry <= 30 ? 'critical' : item.daysToExpiry <= 90 ? 'warning' : 'notice';
            const colors = {
              critical: { border: 'border-red-500', bg: 'bg-red-50', text: 'text-red-700' },
              warning: { border: 'border-orange-500', bg: 'bg-orange-50', text: 'text-orange-700' },
              notice: { border: 'border-yellow-500', bg: 'bg-yellow-50', text: 'text-yellow-700' }
            };
            
            return `
              <div class="card-bg card-hover p-6 rounded-lg shadow border-l-4 ${colors[urgency].border}" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
                <div class="flex justify-between items-start">
                  <div class="flex-1">
                    <div class="flex items-center gap-3 mb-2">
                      <span class="text-2xl">⏰</span>
                      <div>
                        <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">${item.drug_name}</h3>
                        <p class="text-gray-600" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${item.facility_name} • Batch: ${item.batch_number}</p>
                      </div>
                    </div>
                    <div class="ml-11 grid grid-cols-3 gap-4">
                      <div>
                        <p class="text-gray-500 text-xs">Expiry Date</p>
                        <p class="${colors[urgency].text} font-semibold">${item.expiryDate.toLocaleDateString()}</p>
                      </div>
                      <div>
                        <p class="text-gray-500 text-xs">Days Remaining</p>
                        <p class="${colors[urgency].text} font-semibold">${item.daysToExpiry} days</p>
                      </div>
                      <div>
                        <p class="text-gray-500 text-xs">Quantity</p>
                        <p class="font-semibold">${item.quantity} units</p>
                      </div>
                    </div>
                    ${item.ai_recommendation ? `
                      <div class="ml-11 mt-3 p-3 ${colors[urgency].bg} rounded">
                        <p class="text-sm font-semibold ${colors[urgency].text}">🤖 AI Recommendation:</p>
                        <p class="text-sm ${colors[urgency].text}">${item.ai_recommendation}</p>
                      </div>
                    ` : ''}
                  </div>
                </div>
              </div>
            `;
          }).join('')}
        </div>
      `;
    }

    function renderShipments(content, config) {
      const shipments = allRecords.filter(r => r.type === 'shipment');
      
      content.innerHTML = `
        <div class="flex justify-between items-center mb-6">
          <div>
            <h2 class="text-2xl font-bold mb-2" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">🚚 3D GPS Tracking</h2>
            <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Real-time shipment monitoring with live coordinates</p>
          </div>
          <button onclick="showAddShipment()" class="px-6 py-2 rounded-lg font-semibold hover:opacity-90 transition" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; font-size: ${config.font_size || defaultConfig.font_size}px; box-shadow: 0 5px 20px ${config.primary_color || defaultConfig.primary_color}44;">+ New Shipment</button>
        </div>
        
        <!-- 3D Truck Model for active shipments -->
        ${shipments.some(s => s.status === 'in_transit') ? `
          <div class="card-bg p-6 rounded-lg shadow mb-6 text-center hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44;">
            <div class="scene-3d flex justify-center mb-4" style="height: 150px;">
              <div class="model-3d" style="animation-duration: 15s;">
                <svg width="200" height="120" viewBox="0 0 200 120" style="filter: drop-shadow(0 10px 30px ${config.primary_color || defaultConfig.primary_color}88);">
                  <!-- Truck body -->
                  <rect x="40" y="40" width="100" height="50" fill="${config.primary_color || defaultConfig.primary_color}" rx="5"/>
                  <rect x="140" y="45" width="40" height="45" fill="${config.accent_color || defaultConfig.accent_color}" rx="3"/>
                  
                  <!-- Cargo container with medical cross -->
                  <rect x="45" y="35" width="90" height="5" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.8"/>
                  <line x1="90" y1="50" x2="90" y2="75" stroke="white" stroke-width="4"/>
                  <line x1="77.5" y1="62.5" x2="102.5" y2="62.5" stroke="white" stroke-width="4"/>
                  
                  <!-- Windows -->
                  <rect x="145" y="52" width="15" height="12" fill="${config.secondary_color || defaultConfig.secondary_color}" opacity="0.6" rx="2"/>
                  <rect x="162" y="52" width="13" height="12" fill="${config.secondary_color || defaultConfig.secondary_color}" opacity="0.6" rx="2"/>
                  
                  <!-- Wheels -->
                  <circle cx="65" cy="95" r="12" fill="#1f2937" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2"/>
                  <circle cx="65" cy="95" r="6" fill="${config.primary_color || defaultConfig.primary_color}"/>
                  <circle cx="115" cy="95" r="12" fill="#1f2937" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2"/>
                  <circle cx="115" cy="95" r="6" fill="${config.primary_color || defaultConfig.primary_color}"/>
                  <circle cx="160" cy="95" r="12" fill="#1f2937" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="2"/>
                  <circle cx="160" cy="95" r="6" fill="${config.accent_color || defaultConfig.accent_color}"/>
                  
                  <!-- GPS signal -->
                  <circle cx="90" cy="30" r="3" fill="${config.primary_color || defaultConfig.primary_color}"/>
                  <circle cx="90" cy="30" r="8" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.6"/>
                  <circle cx="90" cy="30" r="13" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="1.5" opacity="0.3"/>
                </svg>
              </div>
            </div>
            <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color}22; color: ${config.primary_color || defaultConfig.primary_color};">
              <div class="pulse w-2 h-2 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color};"></div>
              <span style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px; font-weight: 600;">${shipments.filter(s => s.status === 'in_transit').length} ACTIVE SHIPMENT(S)</span>
            </div>
          </div>
        ` : ''}

        <div class="grid gap-4">
          ${shipments.length === 0 ? `
            <div class="card-bg p-8 rounded-lg shadow text-center" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
              <p class="text-gray-500" style="font-size: ${config.font_size || defaultConfig.font_size}px">No shipments yet. Click "New Shipment" to create one.</p>
            </div>
          ` : shipments.map(shipment => {
            const statusColors = {
              'pending': { bg: '#fef3c7', text: '#92400e', icon: '⏳' },
              'in_transit': { bg: '#dbeafe', text: '#1e40af', icon: '🚚' },
              'delivered': { bg: '#d1fae5', text: '#065f46', icon: '✅' },
              'delayed': { bg: '#fee2e2', text: '#991b1b', icon: '⚠️' }
            };
            const colors = statusColors[shipment.status] || statusColors.pending;
            
            return `
              <div class="card-bg card-hover p-6 rounded-lg shadow ${shipment.status === 'in_transit' ? 'gps-tracking' : ''}" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
                <div class="flex justify-between items-start mb-4">
                  <div class="flex-1">
                    <div class="flex items-center gap-2 mb-2">
                      <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">${shipment.drug_name}</h3>
                      ${shipment.status === 'in_transit' ? '<span class="ai-badge">LIVE GPS</span>' : ''}
                    </div>
                    <p class="text-gray-600" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">📦 ${shipment.quantity} units • Batch: ${shipment.batch_number || 'N/A'}</p>
                  </div>
                  <span class="status-badge" style="background-color: ${colors.bg}; color: ${colors.text}">
                    ${colors.icon} ${shipment.status.replace('_', ' ')}
                  </span>
                </div>
                <div class="grid grid-cols-2 gap-4 mb-4 text-sm">
                  <div>
                    <p class="text-gray-500 mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">From</p>
                    <p class="font-medium" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${shipment.facility_name}</p>
                    ${shipment.location_lat && shipment.status === 'in_transit' ? `
                      <p class="text-xs text-gray-400">📍 ${shipment.location_lat}, ${shipment.location_lng}</p>
                    ` : ''}
                  </div>
                  <div>
                    <p class="text-gray-500 mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">To</p>
                    <p class="font-medium" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${shipment.message}</p>
                  </div>
                </div>
                ${shipment.status !== 'delivered' ? `
                  <div class="flex gap-2">
                    <button onclick="updateShipmentStatus('${shipment.id}', '${shipment.status === 'pending' ? 'in_transit' : 'delivered'}')" class="flex-1 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">
                      ${shipment.status === 'pending' ? '🚀 Start Transit' : '��� Mark Delivered'}
                    </button>
                    ${shipment.status === 'in_transit' ? `
                      <button onclick="updateShipmentStatus('${shipment.id}', 'delayed')" class="flex-1 py-2 border border-orange-300 text-orange-700 rounded-lg hover:bg-orange-50 transition" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">
                        ⚠️ Mark Delayed
                      </button>
                    ` : ''}
                  </div>
                ` : ''}
              </div>
            `;
          }).join('')}
        </div>

        <div id="shipment-modal"></div>
      `;
    }

    function renderAIInsights(content, config) {
      const inventory = allRecords.filter(r => r.type === 'inventory');
      const shipments = allRecords.filter(r => r.type === 'shipment');
      
      // AI-generated insights
      const insights = [
        {
          type: 'forecast',
          title: 'Demand Forecast',
          message: 'Paracetamol 500mg demand predicted to increase by 25% next month based on seasonal patterns.',
          recommendation: 'Consider increasing stock levels by 300 units at Central Hospital.',
          confidence: 87
        },
        {
          type: 'optimization',
          title: 'Stock Balancing Opportunity',
          message: 'District Clinic A has excess Amoxicillin while Community Health Center is running low.',
          recommendation: 'Transfer 150 units from District Clinic A to Community Health Center.',
          confidence: 92
        },
        {
          type: 'safety',
          title: 'Safety Stock Alert',
          message: 'Insulin Glargine inventory below calculated safety stock level.',
          recommendation: 'Reorder 50 vials immediately. Current lead time: 5 days.',
          confidence: 95
        },
        {
          type: 'efficiency',
          title: 'Route Optimization',
          message: 'Shipment routing inefficiency detected between Regional Warehouse and clinics.',
          recommendation: 'Consolidate deliveries to reduce trips by 30% and save costs.',
          confidence: 78
        },
        {
          type: 'drone',
          title: 'Drone Delivery Available',
          message: 'Emergency medical supplies can be delivered via autonomous drone to remote locations.',
          recommendation: 'Deploy drone fleet for critical deliveries within 30-minute radius.',
          confidence: 89
        }
      ];
      
      content.innerHTML = `
        <div class="flex justify-between items-center mb-6">
          <div>
            <h2 class="text-2xl font-bold mb-2" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">AI-Powered Insights</h2>
            <p class="text-gray-600" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Machine learning recommendations for optimal inventory management</p>
          </div>
          <div class="ai-badge text-lg px-4 py-2">QUANTUM AI ACTIVE</div>
        </div>
        
        <!-- 3D Drone Delivery System -->
        <div class="card-bg p-8 rounded-2xl shadow-2xl mb-8 hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; position: relative; overflow: hidden;">
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
            <div class="scene-3d flex justify-center" style="height: 250px;">
              <div class="model-3d" style="animation-duration: 12s;">
                <svg width="300" height="250" viewBox="0 0 300 250" style="filter: drop-shadow(0 0 30px ${config.primary_color || defaultConfig.primary_color}66);">
                  <!-- Drone body -->
                  <ellipse cx="150" cy="120" rx="40" ry="15" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3"/>
                  <rect x="130" y="105" width="40" height="30" fill="${config.primary_color || defaultConfig.primary_color}" rx="5"/>
                  <circle cx="150" cy="120" r="8" fill="white"/>
                  
                  <!-- Propeller arms -->
                  <line x1="150" y1="120" x2="80" y2="80" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="4"/>
                  <line x1="150" y1="120" x2="220" y2="80" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="4"/>
                  <line x1="150" y1="120" x2="80" y2="160" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="4"/>
                  <line x1="150" y1="120" x2="220" y2="160" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="4"/>
                  
                  <!-- Propellers with spin animation -->
                  <g class="spin-animation" style="transform-origin: 80px 80px;">
                    <ellipse cx="80" cy="80" rx="25" ry="5" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                    <ellipse cx="80" cy="80" rx="5" ry="25" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                  </g>
                  
                  <g class="spin-animation" style="transform-origin: 220px 80px; animation-delay: 0.1s;">
                    <ellipse cx="220" cy="80" rx="25" ry="5" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                    <ellipse cx="220" cy="80" rx="5" ry="25" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                  </g>
                  
                  <g class="spin-animation" style="transform-origin: 80px 160px; animation-delay: 0.2s;">
                    <ellipse cx="80" cy="160" rx="25" ry="5" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                    <ellipse cx="80" cy="160" rx="5" ry="25" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                  </g>
                  
                  <g class="spin-animation" style="transform-origin: 220px 160px; animation-delay: 0.3s;">
                    <ellipse cx="220" cy="160" rx="25" ry="5" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                    <ellipse cx="220" cy="160" rx="5" ry="25" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.7"/>
                  </g>
                  
                  <!-- Medical package -->
                  <rect x="135" y="135" width="30" height="25" fill="white" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="2" rx="3"/>
                  <line x1="150" y1="140" x2="150" y2="155" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                  <line x1="142.5" y1="147.5" x2="157.5" y2="147.5" stroke="${config.accent_color || defaultConfig.accent_color}" stroke-width="3"/>
                  
                  <!-- GPS signals -->
                  <circle cx="150" cy="90" r="3" fill="${config.primary_color || defaultConfig.primary_color}"/>
                  <circle cx="150" cy="90" r="10" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" opacity="0.5" class="pulse"/>
                  <circle cx="150" cy="90" r="17" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="1" opacity="0.3" class="pulse" style="animation-delay: 0.5s;"/>
                </svg>
              </div>
            </div>
            
            <div>
              <div class="flex items-center gap-3 mb-4">
                <div class="ai-badge">🚁 AUTONOMOUS</div>
                <h3 class="text-2xl font-bold" style="color: ${config.text_color || defaultConfig.text_color};">Drone Delivery Fleet</h3>
              </div>
              <p class="text-gray-600 mb-6" style="font-size: ${config.font_size || defaultConfig.font_size}px;">AI-powered autonomous drones deliver critical medical supplies to remote locations in under 30 minutes.</p>
              
              <div class="grid grid-cols-2 gap-4 mb-6">
                <div class="border rounded-lg p-4" style="border-color: ${config.primary_color || defaultConfig.primary_color}44;">
                  <p class="text-3xl font-bold" style="color: ${config.primary_color || defaultConfig.primary_color};">8</p>
                  <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Active Drones</p>
                </div>
                <div class="border rounded-lg p-4" style="border-color: ${config.accent_color || defaultConfig.accent_color}44;">
                  <p class="text-3xl font-bold" style="color: ${config.accent_color || defaultConfig.accent_color};">142</p>
                  <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Deliveries Today</p>
                </div>
              </div>
              
              <div class="space-y-2">
                <div class="flex items-center gap-3">
                  <div class="pulse w-2 h-2 rounded-full bg-green-500"></div>
                  <span style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Real-time obstacle avoidance</span>
                </div>
                <div class="flex items-center gap-3">
                  <div class="pulse w-2 h-2 rounded-full bg-green-500"></div>
                  <span style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">Temperature-controlled cargo bay</span>
                </div>
                <div class="flex items-center gap-3">
                  <div class="pulse w-2 h-2 rounded-full bg-green-500"></div>
                  <span style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">30km operational radius</span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
          <div class="card-bg p-6 rounded-lg shadow" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <div class="flex items-center gap-3 mb-3">
              <div class="text-3xl">🎯</div>
              <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">Prediction Accuracy</h3>
            </div>
            <p class="text-4xl font-bold" style="color: ${config.primary_color || defaultConfig.primary_color}">94.2%</p>
            <p class="text-gray-600 text-sm mt-2">30-day rolling average</p>
          </div>
          
          <div class="card-bg p-6 rounded-lg shadow" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <div class="flex items-center gap-3 mb-3">
              <div class="text-3xl">💰</div>
              <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">Cost Savings</h3>
            </div>
            <p class="text-4xl font-bold" style="color: ${config.accent_color || defaultConfig.accent_color}">$12,450</p>
            <p class="text-gray-600 text-sm mt-2">Optimizations this month</p>
          </div>
        </div>

        <div class="space-y-4">
          ${insights.map(insight => {
            const typeColors = {
              forecast: { icon: '📈', bg: '#eff6ff', border: '#3b82f6' },
              optimization: { icon: '⚡', bg: '#f0fdfa', border: '#06b6d4' },
              safety: { icon: '🛡️', bg: '#fef2f2', border: '#ef4444' },
              efficiency: { icon: '🎯', bg: '#f0fdf4', border: '#10b981' }
            };
            const colors = typeColors[insight.type] || typeColors.forecast;
            
            return `
              <div class="card-bg card-hover p-6 rounded-lg shadow border-l-4" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border-color: ${colors.border}">
                <div class="flex items-start gap-4">
                  <div class="text-4xl">${colors.icon}</div>
                  <div class="flex-1">
                    <div class="flex items-center justify-between mb-2">
                      <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">${insight.title}</h3>
                      <span class="status-badge" style="background-color: ${colors.bg}; color: ${colors.border}">
                        ${insight.confidence}% confidence
                      </span>
                    </div>
                    <p class="text-gray-700 mb-3" style="font-size: ${config.font_size || defaultConfig.font_size}px">${insight.message}</p>
                    <div class="p-3 rounded" style="background-color: ${colors.bg}">
                      <p class="font-semibold text-sm mb-1" style="color: ${colors.border}">🤖 AI Recommendation:</p>
                      <p class="text-sm" style="color: ${colors.border}">${insight.recommendation}</p>
                    </div>
                  </div>
                </div>
              </div>
            `;
          }).join('')}
        </div>
      `;
    }

    function renderQRScan(content, config) {
      content.innerHTML = `
        <div class="text-center mb-8">
          <h2 class="text-2xl font-bold mb-2" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">🔬 Advanced 3D Scanner</h2>
          <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${config.font_size || defaultConfig.font_size}px">AI-powered QR/RFID recognition system</p>
        </div>

        <div class="max-w-4xl mx-auto">
          <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
            <!-- 3D Scanner Display -->
            <div class="card-bg p-8 rounded-lg shadow text-center hologram-effect" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 2px solid ${config.primary_color || defaultConfig.primary_color}44; position: relative;">
              <div class="scan-line"></div>
              
              <!-- 3D Rotating QR Code -->
              <div class="scene-3d mb-6 flex justify-center" style="height: 280px;">
                <div class="model-3d" style="width: 220px; height: 220px; position: relative; transform-style: preserve-3d;">
                  <svg width="220" height="220" viewBox="0 0 200 200" class="mx-auto" style="filter: drop-shadow(0 0 30px ${config.primary_color || defaultConfig.primary_color}88);">
                    <!-- Outer glow -->
                    <rect x="10" y="10" width="180" height="180" fill="none" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="3" rx="8" opacity="0.3"/>
                    
                    <!-- QR Code pattern with glow -->
                    <rect x="20" y="20" width="40" height="40" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                    <rect x="70" y="20" width="10" height="10" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    <rect x="90" y="20" width="10" height="10" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    <rect x="110" y="20" width="10" height="10" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    <rect x="140" y="20" width="40" height="40" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                    
                    <rect x="20" y="70" width="10" height="10" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    <rect x="40" y="70" width="10" height="10" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    <rect x="70" y="70" width="20" height="20" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    <rect x="110" y="70" width="20" height="20" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    <rect x="150" y="70" width="10" height="10" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    
                    <rect x="20" y="110" width="10" height="10" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    <rect x="50" y="110" width="30" height="30" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    <rect x="110" y="110" width="30" height="30" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    <rect x="170" y="110" width="10" height="10" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    
                    <rect x="20" y="140" width="40" height="40" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                    <rect x="70" y="150" width="10" height="10" fill="${config.accent_color || defaultConfig.accent_color}"/>
                    <rect x="90" y="150" width="10" height="10" fill="${config.primary_color || defaultConfig.primary_color}"/>
                    <rect x="140" y="140" width="40" height="40" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.9"/>
                    
                    <!-- Corner markers -->
                    <circle cx="30" cy="30" r="3" fill="white"/>
                    <circle cx="170" cy="30" r="3" fill="white"/>
                    <circle cx="30" cy="170" r="3" fill="white"/>
                  </svg>
                </div>
              </div>
              
              <div class="mb-4">
                <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color}22; color: ${config.primary_color || defaultConfig.primary_color};">
                  <div class="pulse w-2 h-2 rounded-full" style="background: ${config.primary_color || defaultConfig.primary_color};"></div>
                  <span style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px; font-weight: 600;">SCANNER READY</span>
                </div>
              </div>
              
              <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${config.font_size || defaultConfig.font_size}px; margin-bottom: 1.5rem;">Position item within scanning area</p>
              
              <button onclick="simulateScan()" class="w-full py-3 px-4 rounded-lg font-semibold hover:opacity-90 transition" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white; font-size: ${config.font_size || defaultConfig.font_size}px; box-shadow: 0 5px 20px ${config.primary_color || defaultConfig.primary_color}44;">
                📱 Activate 3D Scan
              </button>
            </div>

            <!-- Features & 3D Models -->
            <div class="space-y-4">
              <!-- Scanner Features -->
              <div class="card-bg p-6 rounded-lg shadow" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 1px solid ${config.primary_color || defaultConfig.primary_color}22;">
                <div class="flex items-center gap-3 mb-4">
                  <div class="text-3xl">✨</div>
                  <h3 class="font-bold" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">Scanner Capabilities</h3>
                </div>
                <ul class="space-y-2" style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">
                  <li class="flex items-center gap-2">
                    <span style="color: ${config.primary_color || defaultConfig.primary_color};">●</span>
                    QR Code & RFID support
                  </li>
                  <li class="flex items-center gap-2">
                    <span style="color: ${config.primary_color || defaultConfig.primary_color};">●</span>
                    Instant batch identification
                  </li>
                  <li class="flex items-center gap-2">
                    <span style="color: ${config.primary_color || defaultConfig.primary_color};">●</span>
                    Automatic expiry date capture
                  </li>
                  <li class="flex items-center gap-2">
                    <span style="color: ${config.primary_color || defaultConfig.primary_color};">●</span>
                    Real-time stock updates
                  </li>
                  <li class="flex items-center gap-2">
                    <span style="color: ${config.primary_color || defaultConfig.primary_color};">●</span>
                    Drug recall verification
                  </li>
                  <li class="flex items-center gap-2">
                    <span style="color: ${config.primary_color || defaultConfig.primary_color};">●</span>
                    Theft prevention tracking
                  </li>
                </ul>
              </div>

              <!-- 3D Medical Models Display -->
              <div class="card-bg p-6 rounded-lg shadow" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}; border: 1px solid ${config.accent_color || defaultConfig.accent_color}22;">
                <div class="flex items-center gap-3 mb-4">
                  <div class="text-3xl">🔬</div>
                  <h3 class="font-bold" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">Recognized Items</h3>
                </div>
                <div class="grid grid-cols-3 gap-4">
                  <div class="text-center">
                    <div class="flex justify-center mb-2">
                      <div class="pill-3d" style="width: 60px; height: 25px; background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 50%, #fde047 50%, #fef3c7 100%);"></div>
                    </div>
                    <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Pills</p>
                  </div>
                  <div class="text-center">
                    <div class="flex justify-center mb-2" style="height: 40px;">
                      <svg width="30" height="40" viewBox="0 0 40 120" class="bounce-animation">
                        <rect x="15" y="5" width="10" height="8" fill="${config.primary_color || defaultConfig.primary_color}" rx="2"/>
                        <rect x="12" y="13" width="16" height="20" fill="${config.secondary_color || defaultConfig.secondary_color}" stroke="${config.primary_color || defaultConfig.primary_color}" stroke-width="2" rx="3"/>
                        <rect x="14" y="15" width="12" height="12" fill="${config.primary_color || defaultConfig.primary_color}" opacity="0.3"/>
                        <rect x="17" y="33" width="6" height="7" fill="${config.primary_color || defaultConfig.primary_color}"/>
                      </svg>
                    </div>
                    <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Injections</p>
                  </div>
                  <div class="text-center">
                    <div class="flex justify-center mb-2" style="height: 40px;">
                      <svg width="30" height="30" viewBox="0 0 80 80" class="float-animation">
                        <rect x="20" y="10" width="40" height="50" fill="${config.accent_color || defaultConfig.accent_color}" rx="5"/>
                        <rect x="20" y="10" width="40" height="15" fill="${config.primary_color || defaultConfig.primary_color}" rx="5"/>
                        <text x="40" y="40" text-anchor="middle" fill="white" font-size="20" font-weight="bold">Rx</text>
                      </svg>
                    </div>
                    <p style="color: ${config.text_color || defaultConfig.text_color}88; font-size: ${(config.font_size || defaultConfig.font_size) * 0.75}px;">Bottles</p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      `;
    }

    function renderAlerts(content, config) {
      const alerts = allRecords.filter(r => r.type === 'alert');
      
      content.innerHTML = `
        <div class="flex justify-between items-center mb-6">
          <h2 class="text-2xl font-bold" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.5}px">Active Alerts & Notifications</h2>
          ${alerts.length > 0 ? `
            <button onclick="clearAllAlerts()" class="px-6 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition" style="font-size: ${config.font_size || defaultConfig.font_size}px">Clear All</button>
          ` : ''}
        </div>

        <div class="space-y-4">
          ${alerts.length === 0 ? `
            <div class="card-bg p-8 rounded-lg shadow text-center" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
              <div class="text-6xl mb-4">✓</div>
              <p class="text-xl font-semibold mb-2" style="color: ${config.accent_color || defaultConfig.accent_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.25}px">All Clear!</p>
              <p class="text-gray-500" style="font-size: ${config.font_size || defaultConfig.font_size}px">No active alerts at this time</p>
            </div>
          ` : alerts.map(alert => {
            const isLowStock = alert.status === 'low_stock';
            const isCritical = alert.status === 'critical';
            return `
              <div class="card-bg card-hover p-6 rounded-lg shadow border-l-4 ${isCritical ? 'border-red-600' : isLowStock ? 'border-orange-500' : 'border-yellow-500'}" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
                <div class="flex justify-between items-start">
                  <div class="flex-1">
                    <div class="flex items-center gap-3 mb-2">
                      <span class="text-2xl">${isCritical ? '������' : isLowStock ? '⚠️' : '��'}</span>
                      <div>
                        <h3 class="font-bold" style="font-size: ${(config.font_size || defaultConfig.font_size) * 1.125}px">${alert.facility_name}</h3>
                        <p class="text-gray-600" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">${alert.drug_name}</p>
                      </div>
                      ${isCritical ? '<span class="ai-badge ml-2">URGENT</span>' : ''}
                    </div>
                    <p class="text-gray-700 ml-11" style="font-size: ${config.font_size || defaultConfig.font_size}px">${alert.message}</p>
                    <p class="text-gray-400 text-xs ml-11 mt-2">${new Date(alert.timestamp).toLocaleString()}</p>
                  </div>
                  <button onclick="dismissAlert('${alert.id}')" class="text-gray-400 hover:text-gray-600 ml-4">✕</button>
                </div>
              </div>
            `;
          }).join('')}
        </div>
      `;
    }

    // Global functions
    window.login = function(role) {
      currentUser = { role };
      currentScreen = 'overview';
      renderDashboard();
    };

    window.logout = function() {
      currentUser = null;
      currentScreen = 'login';
      renderLogin();
    };

    window.navigateTo = function(screen) {
      currentScreen = screen;
      renderDashboard();
    };

    window.toggleOfflineMode = function() {
      offlineMode = !offlineMode;
      showToast(offlineMode ? 'Offline mode enabled' : 'Back online', 'info');
      renderDashboard();
    };

    window.renderCurrentScreen = function() {
      if (currentScreen === 'login') {
        renderLogin();
      } else {
        renderDashboard();
      }
    };

    window.showAddInventory = async function() {
      if (allRecords.length >= 999) {
        showToast('Maximum limit of 999 records reached. Please delete some records first.', 'error');
        return;
      }

      const config = window.elementSdk?.config || defaultConfig;
      const modal = document.getElementById('inventory-modal');
      
      modal.innerHTML = `
        <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4" style="z-index: 1000">
          <div class="card-bg max-w-md w-full p-6 rounded-lg shadow-xl" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <h3 class="text-xl font-bold mb-4" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.25}px">Add Inventory Record</h3>
            <form id="add-inventory-form" class="space-y-4">
              <div>
                <label for="facility" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Facility</label>
                <select id="facility" required class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
                  ${FACILITIES.map(f => `<option value="${f.id}">${f.name}</option>`).join('')}
                </select>
              </div>
              <div>
                <label for="drug" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Drug</label>
                <select id="drug" required class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
                  ${DRUGS.map(d => `<option value="${d.id}">${d.name}</option>`).join('')}
                </select>
              </div>
              <div>
                <label for="batch" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Batch Number</label>
                <input type="text" id="batch" required placeholder="e.g., BTH${Math.floor(Math.random() * 10000)}" class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
              </div>
              <div>
                <label for="quantity" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Quantity</label>
                <input type="number" id="quantity" required min="0" class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
              </div>
              <div>
                <label for="expiry" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Expiry Date</label>
                <input type="date" id="expiry" required class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
              </div>
              <div class="flex gap-3 pt-4">
                <button type="submit" class="btn-primary flex-1 py-2 rounded-lg text-white font-semibold hover:opacity-90 transition" style="background-color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${config.font_size || defaultConfig.font_size}px">Add</button>
                <button type="button" onclick="closeModal()" class="flex-1 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition" style="font-size: ${config.font_size || defaultConfig.font_size}px">Cancel</button>
              </div>
            </form>
          </div>
        </div>
      `;

      document.getElementById('add-inventory-form').addEventListener('submit', async (e) => {
        e.preventDefault();
        
        const submitBtn = e.target.querySelector('button[type="submit"]');
        submitBtn.disabled = true;
        submitBtn.textContent = 'Adding...';

        const facilityId = document.getElementById('facility').value;
        const drugId = document.getElementById('drug').value;
        const batch = document.getElementById('batch').value;
        const quantity = parseInt(document.getElementById('quantity').value);
        const expiry = document.getElementById('expiry').value;

        const facility = FACILITIES.find(f => f.id === facilityId);
        const drug = DRUGS.find(d => d.id === drugId);

        const result = await window.dataSdk.create({
          id: 'inv_' + Date.now(),
          type: 'inventory',
          facility_name: facility.name,
          drug_name: drug.name,
          batch_number: batch,
          expiry_date: new Date(expiry).toISOString(),
          quantity: quantity,
          min_level: drug.min_stock,
          status: 'active',
          timestamp: new Date().toISOString(),
          message: '',
          location_lat: facility.lat,
          location_lng: facility.lng,
          ai_recommendation: quantity < drug.min_stock ? `Reorder ${drug.min_stock - quantity} units to reach minimum stock level` : ''
        });

        if (result.isOk) {
          // Check if low stock alert needed
          if (quantity < drug.min_stock) {
            await window.dataSdk.create({
              id: 'alert_' + Date.now(),
              type: 'alert',
              facility_name: facility.name,
              drug_name: drug.name,
              batch_number: batch,
              expiry_date: '',
              quantity: quantity,
              min_level: drug.min_stock,
              status: 'low_stock',
              timestamp: new Date().toISOString(),
              message: `Stock below minimum level. Current: ${quantity}, Required: ${drug.min_stock}`,
              location_lat: '',
              location_lng: '',
              ai_recommendation: ''
            });
          }
          
          closeModal();
          showToast('Inventory record added successfully', 'success');
        } else {
          showToast('Failed to add inventory record', 'error');
          submitBtn.disabled = false;
          submitBtn.textContent = 'Add';
        }
      });
    };

    window.showAddShipment = async function() {
      if (allRecords.length >= 999) {
        showToast('Maximum limit of 999 records reached. Please delete some records first.', 'error');
        return;
      }

      const config = window.elementSdk?.config || defaultConfig;
      const modal = document.getElementById('shipment-modal');
      
      modal.innerHTML = `
        <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4" style="z-index: 1000">
          <div class="card-bg max-w-md w-full p-6 rounded-lg shadow-xl" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <h3 class="text-xl font-bold mb-4" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.25}px">Create Shipment</h3>
            <form id="add-shipment-form" class="space-y-4">
              <div>
                <label for="from-facility" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">From Facility</label>
                <select id="from-facility" required class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
                  ${FACILITIES.map(f => `<option value="${f.id}">${f.name}</option>`).join('')}
                </select>
              </div>
              <div>
                <label for="to-facility" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">To Facility</label>
                <select id="to-facility" required class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
                  ${FACILITIES.map(f => `<option value="${f.id}">${f.name}</option>`).join('')}
                </select>
              </div>
              <div>
                <label for="shipment-drug" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Drug</label>
                <select id="shipment-drug" required class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
                  ${DRUGS.map(d => `<option value="${d.id}">${d.name}</option>`).join('')}
                </select>
              </div>
              <div>
                <label for="shipment-batch" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Batch Number</label>
                <input type="text" id="shipment-batch" required placeholder="e.g., BTH${Math.floor(Math.random() * 10000)}" class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
              </div>
              <div>
                <label for="shipment-quantity" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Quantity</label>
                <input type="number" id="shipment-quantity" required min="1" class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
              </div>
              <div class="flex gap-3 pt-4">
                <button type="submit" class="btn-primary flex-1 py-2 rounded-lg text-white font-semibold hover:opacity-90 transition" style="background-color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${config.font_size || defaultConfig.font_size}px">Create</button>
                <button type="button" onclick="closeShipmentModal()" class="flex-1 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition" style="font-size: ${config.font_size || defaultConfig.font_size}px">Cancel</button>
              </div>
            </form>
          </div>
        </div>
      `;

      document.getElementById('add-shipment-form').addEventListener('submit', async (e) => {
        e.preventDefault();
        
        const submitBtn = e.target.querySelector('button[type="submit"]');
        submitBtn.disabled = true;
        submitBtn.textContent = 'Creating...';

        const fromId = document.getElementById('from-facility').value;
        const toId = document.getElementById('to-facility').value;
        const drugId = document.getElementById('shipment-drug').value;
        const batch = document.getElementById('shipment-batch').value;
        const quantity = parseInt(document.getElementById('shipment-quantity').value);

        const fromFacility = FACILITIES.find(f => f.id === fromId);
        const toFacility = FACILITIES.find(f => f.id === toId);
        const drug = DRUGS.find(d => d.id === drugId);

        const result = await window.dataSdk.create({
          id: 'ship_' + Date.now(),
          type: 'shipment',
          facility_name: fromFacility.name,
          drug_name: drug.name,
          batch_number: batch,
          expiry_date: '',
          quantity: quantity,
          min_level: 0,
          status: 'pending',
          timestamp: new Date().toISOString(),
          message: toFacility.name,
          location_lat: fromFacility.lat,
          location_lng: fromFacility.lng,
          ai_recommendation: ''
        });

        if (result.isOk) {
          closeShipmentModal();
          showToast('Shipment created successfully', 'success');
        } else {
          showToast('Failed to create shipment', 'error');
          submitBtn.disabled = false;
          submitBtn.textContent = 'Create';
        }
      });
    };

    window.closeModal = function() {
      document.getElementById('inventory-modal').innerHTML = '';
    };

    window.closeShipmentModal = function() {
      document.getElementById('shipment-modal').innerHTML = '';
    };

    window.adjustStock = async function(recordId) {
      const record = allRecords.find(r => r.id === recordId);
      if (!record) return;

      const config = window.elementSdk?.config || defaultConfig;
      const modal = document.getElementById('inventory-modal');
      
      modal.innerHTML = `
        <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4" style="z-index: 1000">
          <div class="card-bg max-w-md w-full p-6 rounded-lg shadow-xl" style="background-color: ${config.secondary_color || defaultConfig.secondary_color}">
            <h3 class="text-xl font-bold mb-4" style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 1.25}px">Adjust Stock</h3>
            <div class="mb-4">
              <p class="text-gray-600 mb-2" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">Current stock: <span class="font-bold">${record.quantity}</span></p>
            </div>
            <form id="adjust-stock-form" class="space-y-4">
              <div>
                <label for="new-quantity" class="block text-sm font-medium mb-1" style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px">New Quantity</label>
                <input type="number" id="new-quantity" required min="0" value="${record.quantity}" class="w-full px-3 py-2 border border-gray-300 rounded-lg" style="font-size: ${config.font_size || defaultConfig.font_size}px">
              </div>
              <div class="flex gap-3 pt-4">
                <button type="submit" class="btn-primary flex-1 py-2 rounded-lg text-white font-semibold hover:opacity-90 transition" style="background-color: ${config.primary_color || defaultConfig.primary_color}; font-size: ${config.font_size || defaultConfig.font_size}px">Update</button>
                <button type="button" onclick="closeModal()" class="flex-1 py-2 border border-gray-300 rounded-lg hover:bg-gray-50 transition" style="font-size: ${config.font_size || defaultConfig.font_size}px">Cancel</button>
              </div>
            </form>
          </div>
        </div>
      `;

      document.getElementById('adjust-stock-form').addEventListener('submit', async (e) => {
        e.preventDefault();
        
        const submitBtn = e.target.querySelector('button[type="submit"]');
        submitBtn.disabled = true;
        submitBtn.textContent = 'Updating...';

        const newQuantity = parseInt(document.getElementById('new-quantity').value);
        
        const result = await window.dataSdk.update({
          ...record,
          quantity: newQuantity,
          timestamp: new Date().toISOString()
        });

        if (result.isOk) {
          closeModal();
          showToast('Stock updated successfully', 'success');
        } else {
          showToast('Failed to update stock', 'error');
          submitBtn.disabled = false;
          submitBtn.textContent = 'Update';
        }
      });
    };

    window.deleteRecord = async function(recordId) {
      const record = allRecords.find(r => r.id === recordId);
      if (!record) return;

      const result = await window.dataSdk.delete(record);

      if (result.isOk) {
        showToast('Record deleted successfully', 'success');
      } else {
        showToast('Failed to delete record', 'error');
      }
    };

    window.updateShipmentStatus = async function(recordId, newStatus) {
      const record = allRecords.find(r => r.id === recordId);
      if (!record) return;

      const result = await window.dataSdk.update({
        ...record,
        status: newStatus,
        timestamp: new Date().toISOString()
      });

      if (result.isOk) {
        showToast('Shipment status updated', 'success');
      } else {
        showToast('Failed to update shipment', 'error');
      }
    };

    window.dismissAlert = async function(recordId) {
      const record = allRecords.find(r => r.id === recordId);
      if (!record) return;

      const result = await window.dataSdk.delete(record);

      if (result.isOk) {
        showToast('Alert dismissed', 'success');
      } else {
        showToast('Failed to dismiss alert', 'error');
      }
    };

    window.clearAllAlerts = async function() {
      const alerts = allRecords.filter(r => r.type === 'alert');
      
      for (const alert of alerts) {
        await window.dataSdk.delete(alert);
      }
      
      showToast('All alerts cleared', 'success');
    };

    window.simulateScan = function() {
      const randomDrug = DRUGS[Math.floor(Math.random() * DRUGS.length)];
      const randomBatch = 'BTH' + Math.floor(Math.random() * 10000);
      
      showToast(`Scanned: ${randomDrug.name} - Batch ${randomBatch}`, 'success');
      
      setTimeout(() => {
        navigateTo('inventory');
      }, 1500);
    };

    function showToast(message, type = 'info') {
      const config = window.elementSdk?.config || defaultConfig;
      const toast = document.createElement('div');
      const bgColor = type === 'error' ? '#fee2e2' : type === 'success' ? '#d1fae5' : '#e0e7ff';
      const textColor = type === 'error' ? '#991b1b' : type === 'success' ? '#065f46' : '#3730a3';
      
      toast.className = 'fixed bottom-4 right-4 px-6 py-3 rounded-lg shadow-lg fade-in';
      toast.style.backgroundColor = bgColor;
      toast.style.color = textColor;
      toast.style.fontSize = `${(config.font_size || defaultConfig.font_size) * 0.875}px`;
      toast.style.zIndex = '2000';
      toast.textContent = message;
      
      document.body.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    // AI Voice Assistant Functions
    window.toggleVoiceAssistant = function() {
      voiceAssistantActive = !voiceAssistantActive;
      const indicator = document.getElementById('voice-indicator');
      const voiceIcon = document.getElementById('voice-icon');
      const voiceToggle = document.getElementById('voice-toggle');
      
      if (voiceAssistantActive) {
        indicator.style.display = 'block';
        voiceIcon.textContent = '🔴';
        voiceToggle.style.background = 'linear-gradient(135deg, #ef4444 0%, #dc2626 100%)';
        voiceToggle.style.color = 'white';
        speak('Voice assistant activated. Say open inventory, open expiry, or open shipments to navigate.');
        startVoiceRecognition();
      } else {
        indicator.style.display = 'none';
        voiceIcon.textContent = '🎤';
        const config = window.elementSdk?.config || defaultConfig;
        voiceToggle.style.background = 'white';
        voiceToggle.style.color = config.text_color || defaultConfig.text_color;
        speak('Voice assistant deactivated.');
        stopVoiceRecognition();
      }
    };

    function speak(text) {
      const utterance = new SpeechSynthesisUtterance(text);
      utterance.rate = 1;
      utterance.pitch = 1;
      utterance.volume = 1;
      window.speechSynthesis.speak(utterance);
    }

    // AI Chatbot Functions
    window.toggleChatbot = function() {
      const chatbot = document.getElementById('chatbot-container');
      if (chatbot.style.display === 'none') {
        chatbot.style.display = 'block';
        setTimeout(() => {
          const messagesDiv = document.getElementById('chat-messages');
          messagesDiv.scrollTop = messagesDiv.scrollHeight;
        }, 100);
      } else {
        chatbot.style.display = 'none';
      }
    };

    window.quickChat = function(message) {
      const input = document.getElementById('chat-input');
      input.value = message;
      document.getElementById('chat-form').dispatchEvent(new Event('submit'));
    };

    function addChatMessage(message, isUser = false) {
      const config = window.elementSdk?.config || defaultConfig;
      const messagesDiv = document.getElementById('chat-messages');
      
      const messageDiv = document.createElement('div');
      messageDiv.className = 'flex gap-3 fade-in';
      
      if (isUser) {
        messageDiv.innerHTML = `
          <div class="flex-1"></div>
          <div class="flex-1 p-3 rounded-lg" style="background: linear-gradient(135deg, ${config.primary_color || defaultConfig.primary_color} 0%, ${config.accent_color || defaultConfig.accent_color} 100%); color: white;">
            <p style="font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">${message}</p>
          </div>
          <div class="w-8 h-8 rounded-full flex items-center justify-center flex-shrink-0" style="background: ${config.primary_color || defaultConfig.primary_color}22;">
            <span>👤</span>
          </div>
        `;
      } else {
        messageDiv.innerHTML = `
          <div class="w-8 h-8 rounded-full flex items-center justify-center flex-shrink-0" style="background: ${config.primary_color || defaultConfig.primary_color}22;">
            <span>🤖</span>
          </div>
          <div class="flex-1 p-3 rounded-lg" style="background: white; border: 1px solid ${config.primary_color || defaultConfig.primary_color}22;">
            <p style="color: ${config.text_color || defaultConfig.text_color}; font-size: ${(config.font_size || defaultConfig.font_size) * 0.875}px;">${message}</p>
          </div>
        `;
      }
      
      messagesDiv.appendChild(messageDiv);
      messagesDiv.scrollTop = messagesDiv.scrollHeight;
    }

    function getAIResponse(userMessage) {
      const lowerMessage = userMessage.toLowerCase();
      
      // Analyze data
      const inventory = allRecords.filter(r => r.type === 'inventory');
      const alerts = allRecords.filter(r => r.type === 'alert');
      const shipments = allRecords.filter(r => r.type === 'shipment');
      const lowStock = alerts.filter(a => a.status === 'low_stock');
      const expiringItems = inventory.filter(item => {
        if (!item.expiry_date) return false;
        const daysToExpiry = Math.ceil((new Date(item.expiry_date) - new Date()) / (1000 * 60 * 60 * 24));
        return daysToExpiry <= 90;
      });
      
      // Generate responses
      if (lowerMessage.includes('low stock') || lowerMessage.includes('stock level')) {
        if (lowStock.length === 0) {
          return "Great news! All inventory levels are above minimum thresholds. No low stock alerts at this time. 📊";
        }
        const items = lowStock.slice(0, 3).map(item => `• ${item.drug_name} at ${item.facility_name} (${item.quantity}/${item.min_level})`).join('\n');
        return `I found ${lowStock.length} low stock alert${lowStock.length > 1 ? 's' : ''}:\n\n${items}\n\nWould you like me to suggest reorder quantities?`;
      }
      
      if (lowerMessage.includes('expir')) {
        if (expiringItems.length === 0) {
          return "All inventory items are within safe expiry dates. No items expiring in the next 90 days. ✅";
        }
        const items = expiringItems.slice(0, 3).map(item => {
          const days = Math.ceil((new Date(item.expiry_date) - new Date()) / (1000 * 60 * 60 * 24));
          return `• ${item.drug_name} expires in ${days} days (${item.quantity} units)`;
        }).join('\n');
        return `⏰ I found ${expiringItems.length} item${expiringItems.length > 1 ? 's' : ''} expiring soon:\n\n${items}\n\nRecommendation: Use FEFO (First Expiry First Out) method.`;
      }
      
      if (lowerMessage.includes('shipment')) {
        const active = shipments.filter(s => s.status === 'in_transit');
        if (active.length === 0) {
          return `No active shipments at the moment. Total shipments: ${shipments.length} (${shipments.filter(s => s.status === 'delivered').length} delivered). 🚚`;
        }
        const items = active.slice(0, 3).map(s => `• ${s.drug_name} to ${s.message} (${s.status})`).join('\n');
        return `🚚 ${active.length} active shipment${active.length > 1 ? 's' : ''}:\n\n${items}\n\nAll shipments are being tracked in real-time with GPS.`;
      }
      
      if (lowerMessage.includes('recommend') || lowerMessage.includes('suggest')) {
        return "Based on current data:\n\n1. 📈 Increase Paracetamol stock by 25% (high demand predicted)\n2. 🔄 Transfer excess Amoxicillin between facilities\n3. ⚡ Enable drone delivery for urgent orders\n4. 🌡️ Monitor cold chain for temperature-sensitive items\n\nWould you like details on any of these?";
      }
      
      if (lowerMessage.includes('drone')) {
        return "🚁 Drone Delivery System Status:\n\n• 8 drones active\n• 142 deliveries today\n• 30km operational radius\n• Average delivery time: 18 minutes\n• Temperature-controlled cargo bay\n\nDrones are perfect for emergency medical supplies to remote locations!";
      }
      
      if (lowerMessage.includes('blockchain') || lowerMessage.includes('security')) {
        return "🔐 Blockchain Security Features:\n\n• 256-bit encryption on all transactions\n• Immutable audit trail\n• Anti-counterfeit drug verification\n• Real-time tamper detection\n• 99.99% uptime\n\nYour medical supply chain is completely secure and transparent!";
      }
      
      if (lowerMessage.includes('ai') || lowerMessage.includes('artificial intelligence')) {
        return "🤖 AI Capabilities:\n\n• 94.2% demand forecast accuracy\n• Automatic stock reorder suggestions\n• Predictive expiry management (FEFO)\n• Route optimization for deliveries\n• Anomaly detection in supply chain\n• Voice command recognition\n\nI'm constantly learning from your data to improve efficiency!";
      }
      
      if (lowerMessage.includes('help') || lowerMessage.includes('what can you do')) {
        return "I can help you with:\n\n📊 Inventory management\n⏰ Expiry tracking & alerts\n🚚 Shipment monitoring\n🤖 AI-powered recommendations\n🚁 Drone delivery coordination\n🔐 Blockchain security insights\n📈 Demand forecasting\n💰 Cost optimization\n\nJust ask me anything about your medical supply chain!";
      }
      
      // Default response
      return `I understand you're asking about "${userMessage}". I can provide information about inventory levels, expiring drugs, active shipments, AI recommendations, drone deliveries, and blockchain security. What specific aspect would you like to know more about?`;
    }

    // Theme Toggle
    window.toggleTheme = function() {
      darkMode = !darkMode;
      const themeToggle = document.getElementById('theme-toggle');
      
      if (darkMode) {
        document.body.style.filter = 'brightness(0.8) contrast(1.1)';
        themeToggle.innerHTML = '<span style="font-size: 20px;">🌙</span>';
        showToast('Night mode activated', 'info');
        if (voiceAssistantActive) speak('Night mode activated. Screen brightness reduced.');
      } else {
        document.body.style.filter = 'brightness(1) contrast(1)';
        themeToggle.innerHTML = '<span style="font-size: 20px;">☀���</span>';
        showToast('Day mode activated', 'info');
        if (voiceAssistantActive) speak('Day mode activated. Full brightness restored.');
      }
    };

    // Initialize chat form listener
    function initChatForm() {
      const form = document.getElementById('chat-form');
      if (form) {
        form.addEventListener('submit', (e) => {
          e.preventDefault();
          const input = document.getElementById('chat-input');
          const message = input.value.trim();
          
          if (message) {
            addChatMessage(message, true);
            input.value = '';
            
            // Simulate AI thinking
            setTimeout(() => {
              const response = getAIResponse(message);
              addChatMessage(response, false);
              
              // Voice response if enabled
              if (voiceAssistantActive) {
                speak(response);
              }
            }, 500);
          }
        });
      }
    }

    // Voice Command Recognition
    let recognition;
    
    function startVoiceRecognition() {
      if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
        console.log('Speech recognition not supported');
        return;
      }
      
      const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
      recognition = new SpeechRecognition();
      recognition.continuous = true;
      recognition.interimResults = false;
      recognition.lang = 'en-US';
      
      recognition.onresult = (event) => {
        const transcript = event.results[event.results.length - 1][0].transcript.toLowerCase().trim();
        console.log('Voice command:', transcript);
        processVoiceCommand(transcript);
      };
      
      recognition.onerror = (event) => {
        console.error('Speech recognition error:', event.error);
      };
      
      recognition.start();
    }
    
    function stopVoiceRecognition() {
      if (recognition) {
        recognition.stop();
      }
    }
    
    function processVoiceCommand(command) {
      if (!voiceAssistantActive) return;
      
      // Navigation commands
      if (command.includes('open') || command.includes('show') || command.includes('go to') || command.includes('navigate')) {
        if (command.includes('overview') || command.includes('dashboard') || command.includes('home')) {
          navigateTo('overview');
          speak('Opening overview dashboard');
          return;
        }
        if (command.includes('inventory') || command.includes('stock')) {
          navigateTo('inventory');
          speak('Opening inventory management');
          return;
        }
        if (command.includes('expiry') || command.includes('expiring') || command.includes('expiration')) {
          navigateTo('expiry');
          speak('Opening expiry management');
          return;
        }
        if (command.includes('shipment') || command.includes('delivery') || command.includes('shipping')) {
          navigateTo('shipments');
          speak('Opening shipment tracking');
          return;
        }
        if (command.includes('ai') || command.includes('insight') || command.includes('analytics')) {
          navigateTo('ai-insights');
          speak('Opening AI insights');
          return;
        }
        if (command.includes('scan') || command.includes('qr') || command.includes('scanner')) {
          navigateTo('qr-scan');
          speak('Opening QR scanner');
          return;
        }
        if (command.includes('alert') || command.includes('notification')) {
          navigateTo('alerts');
          speak('Opening alerts');
          return;
        }
      }
      
      // Action commands
      if (command.includes('add stock') || command.includes('new inventory')) {
        showAddInventory();
        speak('Opening add inventory form');
        return;
      }
      
      if (command.includes('new shipment') || command.includes('create shipment')) {
        showAddShipment();
        speak('Opening new shipment form');
        return;
      }
      
      if (command.includes('scan item') || command.includes('start scan')) {
        simulateScan();
        speak('Starting scanner');
        return;
      }
      
      // Chat commands
      if (command.includes('open chat') || command.includes('show chat') || command.includes('chatbot')) {
        toggleChatbot();
        speak('Opening AI chatbot');
        return;
      }
      
      // Theme commands
      if (command.includes('night mode') || command.includes('dark mode')) {
        if (!darkMode) toggleTheme();
        return;
      }
      
      if (command.includes('day mode') || command.includes('light mode')) {
        if (darkMode) toggleTheme();
        return;
      }
      
      // Status commands
      if (command.includes('status') || command.includes('summary')) {
        const inventory = allRecords.filter(r => r.type === 'inventory');
        const alerts = allRecords.filter(r => r.type === 'alert');
        speak(`System status: ${inventory.length} inventory items, ${alerts.length} active alerts`);
        return;
      }
      
      // Default - didn't understand
      speak('Command not recognized. Say open inventory, open expiry, open shipments, or open alerts to navigate.');
    }
    
    // Auto-alerts via voice
    function checkAndAnnounceAlerts() {
      if (!voiceAssistantActive || currentScreen === 'login') return;
      
      const alerts = allRecords.filter(r => r.type === 'alert');
      const newAlerts = alerts.filter(a => {
        const timestamp = new Date(a.timestamp);
        const now = new Date();
        return (now - timestamp) < 5000; // Last 5 seconds
      });
      
      if (newAlerts.length > 0) {
        const alert = newAlerts[0];
        speak(`Alert: ${alert.message} at ${alert.facility_name}`);
      }
    }

    // Monitor alerts every 10 seconds
    setInterval(checkAndAnnounceAlerts, 10000);

    // Initialize
    async function init() {
      const dataResult = await window.dataSdk.init(dataHandler);
      if (!dataResult.isOk) {
        console.error('Failed to initialize data SDK');
        return;
      }

      if (window.elementSdk) {
        window.elementSdk.init({
          defaultConfig,
          onConfigChange,
          mapToCapabilities: (config) => ({
            recolorables: [
              {
                get: () => config.background_color || defaultConfig.background_color,
                set: (value) => {
                  window.elementSdk.config.background_color = value;
                  window.elementSdk.setConfig({ background_color: value });
                }
              },
              {
                get: () => config.primary_color || defaultConfig.primary_color,
                set: (value) => {
                  window.elementSdk.config.primary_color = value;
                  window.elementSdk.setConfig({ primary_color: value });
                }
              },
              {
                get: () => config.secondary_color || defaultConfig.secondary_color,
                set: (value) => {
                  window.elementSdk.config.secondary_color = value;
                  window.elementSdk.setConfig({ secondary_color: value });
                }
              },
              {
                get: () => config.text_color || defaultConfig.text_color,
                set: (value) => {
                  window.elementSdk.config.text_color = value;
                  window.elementSdk.setConfig({ text_color: value });
                }
              },
              {
                get: () => config.accent_color || defaultConfig.accent_color,
                set: (value) => {
                  window.elementSdk.config.accent_color = value;
                  window.elementSdk.setConfig({ accent_color: value });
                }
              }
            ],
            borderables: [],
            fontEditable: {
              get: () => config.font_family || defaultConfig.font_family,
              set: (value) => {
                window.elementSdk.config.font_family = value;
                window.elementSdk.setConfig({ font_family: value });
              }
            },
            fontSizeable: {
              get: () => config.font_size || defaultConfig.font_size,
              set: (value) => {
                window.elementSdk.config.font_size = value;
                window.elementSdk.setConfig({ font_size: value });
              }
            }
          }),
          mapToEditPanelValues: (config) => new Map([
            ['app_title', config.app_title || defaultConfig.app_title],
            ['tagline', config.tagline || defaultConfig.tagline],
            ['login_title', config.login_title || defaultConfig.login_title],
            ['footer_text', config.footer_text || defaultConfig.footer_text]
          ])
        });
      }

      renderLogin();
    }

    init();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9a4198d085af8875',t:'MTc2NDA3ODQzNi4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
