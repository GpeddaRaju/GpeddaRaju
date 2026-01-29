<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gadige Peddaraju - Resume</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 30px;
            overflow: hidden;
            box-shadow: 0 30px 80px rgba(0,0,0,0.3);
            animation: slideIn 0.8s ease;
        }

        @keyframes slideIn {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Header Section */
        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 60px 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.1) 1px, transparent 1px);
            background-size: 50px 50px;
            animation: backgroundMove 20s linear infinite;
        }

        @keyframes backgroundMove {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 5px solid white;
            margin: 0 auto 20px;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 60px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            animation: pulse 2s infinite;
            position: relative;
            z-index: 1;
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
        }

        .header h1 {
            font-size: 3em;
            margin-bottom: 10px;
            animation: fadeInDown 1s ease;
            position: relative;
            z-index: 1;
        }

        .header .tagline {
            font-size: 1.3em;
            opacity: 0.95;
            animation: fadeInUp 1.2s ease;
            position: relative;
            z-index: 1;
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
            flex-wrap: wrap;
            position: relative;
            z-index: 1;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 10px;
            background: rgba(255,255,255,0.2);
            padding: 10px 20px;
            border-radius: 25px;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
            animation: fadeInUp 1.4s ease;
        }

        .contact-item:hover {
            background: rgba(255,255,255,0.3);
            transform: translateY(-5px);
        }

        /* Section Styles */
        .section {
            padding: 50px 40px;
            animation: fadeInUp 0.8s ease;
        }

        .section:nth-child(even) {
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
        }

        .section-title {
            font-size: 2.2em;
            margin-bottom: 30px;
            color: #2d3748;
            position: relative;
            padding-bottom: 15px;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, #667eea, #764ba2);
            border-radius: 2px;
            animation: expand 1s ease;
        }

        @keyframes expand {
            from { width: 0; }
            to { width: 80px; }
        }

        .section-title i {
            margin-right: 15px;
            color: #667eea;
        }

        /* Objective */
        .objective {
            font-size: 1.1em;
            line-height: 1.8;
            color: #4a5568;
            padding: 25px;
            background: white;
            border-radius: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            border-left: 5px solid #667eea;
            animation: slideInLeft 1s ease;
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        /* Education Cards */
        .education-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }

        .education-card {
            background: white;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            animation: fadeInUp 1s ease;
        }

        .education-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, #667eea, #764ba2);
        }

        .education-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
        }

        .education-card h3 {
            color: #667eea;
            font-size: 1.5em;
            margin-bottom: 10px;
        }

        .education-card .institution {
            color: #718096;
            font-size: 1.1em;
            margin-bottom: 15px;
        }

        .education-card .details {
            display: flex;
            justify-content: space-between;
            margin-top: 15px;
            padding-top: 15px;
            border-top: 2px solid #e2e8f0;
        }

        .percentage-badge {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 8px 20px;
            border-radius: 20px;
            font-weight: bold;
            animation: bounce 1s infinite alternate;
        }

        @keyframes bounce {
            from { transform: translateY(0); }
            to { transform: translateY(-5px); }
        }

        /* Skills Section */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .skill-card {
            background: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            cursor: pointer;
            animation: scaleIn 0.6s ease;
        }

        @keyframes scaleIn {
            from {
                opacity: 0;
                transform: scale(0.5);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        .skill-card:hover {
            transform: translateY(-10px) rotate(3deg);
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
        }

        .skill-icon {
            font-size: 3em;
            margin-bottom: 15px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: rotate 3s linear infinite;
        }

        @keyframes rotate {
            0%, 100% { transform: rotateY(0deg); }
            50% { transform: rotateY(180deg); }
        }

        .skill-name {
            font-weight: bold;
            color: #2d3748;
            font-size: 1.1em;
        }

        /* Strengths */
        .strengths-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-top: 30px;
        }

        .strength-item {
            background: white;
            padding: 20px;
            border-radius: 15px;
            display: flex;
            align-items: center;
            gap: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .strength-item:hover {
            transform: translateX(10px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }

        .strength-icon {
            font-size: 2em;
            color: #667eea;
            min-width: 50px;
        }

        /* Languages */
        .languages-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 25px;
            margin-top: 30px;
        }

        .language-card {
            background: white;
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }

        .language-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1), rgba(118, 75, 162, 0.1));
            transform: translateY(100%);
            transition: transform 0.3s ease;
        }

        .language-card:hover::before {
            transform: translateY(0);
        }

        .language-flag {
            font-size: 3em;
            margin-bottom: 10px;
        }

        .language-name {
            font-size: 1.2em;
            font-weight: bold;
            color: #2d3748;
            margin-bottom: 10px;
        }

        .language-level {
            color: #718096;
            font-style: italic;
        }

        /* Project Section */
        .project-card {
            background: white;
            padding: 40px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            margin-top: 30px;
            border-left: 8px solid #667eea;
            animation: slideInRight 1s ease;
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        .project-card h3 {
            color: #667eea;
            font-size: 1.8em;
            margin-bottom: 20px;
        }

        .project-card p {
            color: #4a5568;
            line-height: 1.8;
            font-size: 1.1em;
        }

        .project-tags {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-top: 20px;
        }

        .tag {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            animation: fadeIn 1.5s ease;
        }

        /* Footer */
        .footer {
            background: linear-gradient(135deg, #2d3748 0%, #1a202c 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }

        .footer p {
            margin: 10px 0;
            opacity: 0.9;
        }

        /* Animations */
        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2em;
            }
            .section {
                padding: 30px 20px;
            }
            .contact-info {
                flex-direction: column;
                align-items: center;
            }
        }

        /* Scroll Animation */
        .fade-in-section {
            opacity: 0;
            transform: translateY(50px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }

        .fade-in-section.is-visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Header -->
        <div class="header">
            <div class="profile-img">
                <i class="fas fa-user-tie"></i>
            </div>
            <h1>GADIGE PEDDARAJU</h1>
            <p class="tagline">🚀 Full Stack Java Developer | Spring Boot Specialist | Database Expert</p>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <span>gadigeraju2003@gmail.com</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>+91 9390891145</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>Kurnool, Andhra Pradesh</span>
                </div>
            </div>
        </div>

        <!-- Career Objective -->
        <div class="section fade-in-section">
            <h2 class="section-title"><i class="fas fa-bullseye"></i>Career Objective</h2>
            <div class="objective">
                I aspire to work with innovative organizations where I can leverage my technical expertise in Java development to create impactful solutions. My goal is to continuously enhance my knowledge and skills while contributing to organizational growth through efficient, scalable, and high-quality software solutions. I am passionate about learning new technologies and delivering excellence in every project.
            </div>
        </div>

        <!-- Education -->
        <div class="section fade-in-section">
            <h2 class="section-title"><i class="fas fa-graduation-cap"></i>Educational Qualifications</h2>
            <div class="education-grid">
                <div class="education-card">
                    <h3><i class="fas fa-university"></i> B.TECH (EEE)</h3>
                    <p class="institution">Jawaharlal Nehru Technological University</p>
                    <p class="institution">Anantapur, Andhra Pradesh</p>
                    <div class="details">
                        <span><i class="fas fa-calendar"></i> 2025</span>
                        <span class="percentage-badge">75%</span>
                    </div>
                </div>
                <div class="education-card">
                    <h3><i class="fas fa-school"></i> DIPLOMA (EEE)</h3>
                    <p class="institution">State Board of Technical Education</p>
                    <p class="institution">Andhra Pradesh</p>
                    <div class="details">
                        <span><i class="fas fa-calendar"></i> 2022</span>
                        <span class="percentage-badge">71%</span>
                    </div>
                </div>
                <div class="education-card">
                    <h3><i class="fas fa-book"></i> SSC</h3>
                    <p class="institution">Board of Secondary Education</p>
                    <p class="institution">Andhra Pradesh</p>
                    <div class="details">
                        <span><i class="fas fa-calendar"></i> 2018</span>
                        <span class="percentage-badge">65%</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Technical Skills -->
        <div class="section fade-in-section">
            <h2 class="section-title"><i class="fas fa-code"></i>Technical Skills</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <div class="skill-icon"><i class="fab fa-java"></i></div>
                    <div class="skill-name">Java</div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon"><i class="fas fa-code-branch"></i></div>
                    <div class="skill-name">Advanced Java</div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon"><i class="fas fa-database"></i></div>
                    <div class="skill-name">Oracle</div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon"><i class="fab fa-html5"></i></div>
                    <div class="skill-name">HTML</div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon"><i class="fab fa-css3-alt"></i></div>
                    <div class="skill-name">CSS</div>
                </div>
                <div class="skill-card">
                    <div class="skill-icon"><i class="fab fa-js"></i></div>
                    <div class="skill-name">JavaScript</div>
                </div>
            </div>
        </div>

        <!-- Personal Skills & Strengths -->
        <div class="section fade-in-section">
            <h2 class="section-title"><i class="fas fa-star"></i>Core Strengths</h2>
            <div class="strengths-container">
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-users"></i></div>
                    <div>
                        <strong>Team Work</strong>
                        <p>Collaborate effectively with team members</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-comments"></i></div>
                    <div>
                        <strong>Communication</strong>
                        <p>Excellent verbal and written skills</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-dumbbell"></i></div>
                    <div>
                        <strong>Hard Working</strong>
                        <p>Dedicated and committed to excellence</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-clock"></i></div>
                    <div>
                        <strong>Time Management</strong>
                        <p>Efficient task prioritization</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-brain"></i></div>
                    <div>
                        <strong>Fast Learner</strong>
                        <p>Quick adaptation to new technologies</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-chart-line"></i></div>
                    <div>
                        <strong>Analytical Skills</strong>
                        <p>Strong problem-solving abilities</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-sync-alt"></i></div>
                    <div>
                        <strong>Adaptable</strong>
                        <p>Adjust to any environment quickly</p>
                    </div>
                </div>
                <div class="strength-item">
                    <div class="strength-icon"><i class="fas fa-medal"></i></div>
                    <div>
                        <strong>Confident</strong>
                        <p>Self-assured professional approach</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Languages -->
        <div class="section fade-in-section">
            <h2 class="section-title"><i class="fas fa-language"></i>Languages Known</h2>
            <div class="languages-grid">
                <div class="language-card">
                    <div class="language-flag">🇮🇳</div>
                    <div class="language-name">Telugu</div>
                    <div class="language-level">Native</div>
                </div>
                <div class="language-card">
                    <div class="language-flag">🇮🇳</div>
                    <div class="language-name">Kannada</div>
                    <div class="language-level">Fluent</div>
                </div>
                <div class="language-card">
                    <div class="language-flag">🇬🇧</div>
                    <div class="language-name">English</div>
                    <div class="language-level">Professional</div>
                </div>
                <div class="language-card">
                    <div class="language-flag">🇮🇳</div>
                    <div class="language-name">Hindi</div>
                    <div class="language-level">Conversational</div>
                </div>
            </div>
        </div>

        <!-- Projects -->
        <div class="section fade-in-section">
            <h2 class="section-title"><i class="fas fa-project-diagram"></i>Featured Project</h2>
            <div class="project-card">
                <h3>⚡ Railway Electric Fault Detection and Predictive Maintenance System</h3>
                <p>
                    Developed an innovative IoT-enabled system to detect electrical faults in railway infrastructure and predict maintenance requirements using advanced analytics. The system monitors real-time electrical parameters, identifies potential issues before they escalate, and generates alerts for preventive maintenance. This project enhances railway safety, reduces downtime, and optimizes maintenance schedules.
                </p>
                <div class="project-tags">
                    <span class="tag"><i class="fab fa-java"></i> Java</span>
                    <span class="tag"><i class="fas fa-database"></i> Oracle</span>
                    <span class="tag"><i class="fas fa-microchip"></i> IoT</span>
                    <span class="tag"><i class="fas fa-chart-line"></i> Predictive Analytics</span>
                    <span class="tag"><i class="fab fa-html5"></i> Web Interface</span>
                </div>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <h3>📄 Declaration</h3>
            <p>I hereby declare that all the information provided above is true to the best of my knowledge and belief.</p>
            <br>
            <p><strong>Date:</strong> January 2025</p>
            <p><strong>Place:</strong> Kurnool, Andhra Pradesh</p>
            <br>
            <p><strong>GADIGE PEDDARAJU</strong></p>
            <br>
            <p style="opacity: 0.7;">Made with ❤️ and ☕</p>
        </div>
    </div>

    <script>
        // Intersection Observer for fade-in animations
        const faders = document.querySelectorAll('.fade-in-section');

        const appearOptions = {
            threshold: 0.2,
            rootMargin: "0px 0px -100px 0px"
        };

        const appearOnScroll = new IntersectionObserver(function(entries, appearOnScroll) {
            entries.forEach(entry => {
                if (!entry.isIntersecting) {
                    return;
                } else {
                    entry.target.classList.add('is-visible');
                    appearOnScroll.unobserve(entry.target);
                }
            });
        }, appearOptions);

        faders.forEach(fader => {
            appearOnScroll.observe(fader);
        });

        // Skill card animation delays
        const skillCards = document.querySelectorAll('.skill-card');
        skillCards.forEach((card, index) => {
            card.style.animationDelay = `${index * 0.1}s`;
        });

        // Smooth scroll
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });
    </script>
</body>
</html>
