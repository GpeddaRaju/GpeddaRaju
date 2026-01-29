<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Microservices Architecture - Java Developer Portfolio</title>
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
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }

        h1 {
            text-align: center;
            color: #2d3748;
            margin-bottom: 10px;
            font-size: 2.5em;
            animation: fadeInDown 0.8s ease;
        }

        .subtitle {
            text-align: center;
            color: #718096;
            margin-bottom: 40px;
            font-size: 1.2em;
            animation: fadeInDown 1s ease;
        }

        .architecture-diagram {
            position: relative;
            padding: 40px 20px;
            min-height: 800px;
        }

        .layer {
            margin-bottom: 60px;
            animation: fadeInUp 1s ease;
        }

        .layer-title {
            text-align: center;
            font-size: 1.3em;
            color: #4a5568;
            margin-bottom: 30px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .services-row {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
            position: relative;
        }

        .service-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            border-radius: 15px;
            padding: 25px;
            width: 220px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            cursor: pointer;
            transition: all 0.3s ease;
            animation: bounceIn 0.8s ease;
            position: relative;
            overflow: hidden;
        }

        .service-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.3) 0%, transparent 70%);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .service-card:hover::before {
            opacity: 1;
            animation: ripple 1.5s ease;
        }

        .service-card:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .service-icon {
            font-size: 2.5em;
            text-align: center;
            margin-bottom: 15px;
            animation: pulse 2s infinite;
        }

        .service-name {
            color: white;
            font-size: 1.2em;
            font-weight: 600;
            text-align: center;
            margin-bottom: 10px;
        }

        .service-tech {
            color: rgba(255,255,255,0.9);
            font-size: 0.85em;
            text-align: center;
            line-height: 1.5;
        }

        .api-gateway {
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            width: 300px;
            margin: 0 auto 40px;
        }

        .database {
            background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
        }

        .infrastructure {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
        }

        .connection-line {
            position: absolute;
            height: 2px;
            background: linear-gradient(90deg, #667eea, #764ba2);
            transform-origin: left center;
            animation: drawLine 1.5s ease;
            opacity: 0.6;
        }

        .tech-stack {
            margin-top: 50px;
            padding: 30px;
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            border-radius: 15px;
            animation: fadeInUp 1.2s ease;
        }

        .tech-stack h2 {
            color: #2d3748;
            margin-bottom: 20px;
            text-align: center;
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .tech-item {
            background: white;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
        }

        .tech-item:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        .tech-item strong {
            color: #667eea;
            display: block;
            margin-bottom: 5px;
        }

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

        @keyframes bounceIn {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.1);
            }
        }

        @keyframes drawLine {
            from {
                width: 0;
            }
            to {
                width: 100%;
            }
        }

        @keyframes ripple {
            0% {
                transform: translate(-50%, -50%) scale(0);
            }
            100% {
                transform: translate(-50%, -50%) scale(1);
            }
        }

        .info-panel {
            position: fixed;
            right: -400px;
            top: 50%;
            transform: translateY(-50%);
            width: 350px;
            background: white;
            padding: 30px;
            border-radius: 15px 0 0 15px;
            box-shadow: -5px 0 30px rgba(0,0,0,0.3);
            transition: right 0.4s ease;
            z-index: 1000;
        }

        .info-panel.active {
            right: 0;
        }

        .info-panel h3 {
            color: #667eea;
            margin-bottom: 15px;
        }

        .info-panel p {
            color: #4a5568;
            line-height: 1.6;
            margin-bottom: 10px;
        }

        .close-btn {
            position: absolute;
            top: 15px;
            right: 15px;
            background: #667eea;
            color: white;
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2em;
            transition: all 0.3s ease;
        }

        .close-btn:hover {
            background: #764ba2;
            transform: rotate(90deg);
        }

        .legend {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 40px;
            flex-wrap: wrap;
        }

        .legend-item {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .legend-color {
            width: 30px;
            height: 30px;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🚀 Microservices Architecture Design</h1>
        <p class="subtitle">Enterprise Java-Based System | Designed by Gadige Peddaraju</p>

        <div class="architecture-diagram">
            <!-- API Gateway Layer -->
            <div class="layer">
                <div class="layer-title">⚡ API Gateway Layer</div>
                <div class="services-row">
                    <div class="service-card api-gateway" onclick="showInfo('gateway')">
                        <div class="service-icon">🌐</div>
                        <div class="service-name">API Gateway</div>
                        <div class="service-tech">Spring Cloud Gateway<br>Netflix Zuul<br>Authentication & Routing</div>
                    </div>
                </div>
            </div>

            <!-- Microservices Layer -->
            <div class="layer">
                <div class="layer-title">🔧 Core Microservices</div>
                <div class="services-row">
                    <div class="service-card" onclick="showInfo('user')">
                        <div class="service-icon">👤</div>
                        <div class="service-name">User Service</div>
                        <div class="service-tech">Spring Boot<br>JWT Authentication<br>User Management</div>
                    </div>
                    <div class="service-card" onclick="showInfo('product')">
                        <div class="service-icon">📦</div>
                        <div class="service-name">Product Service</div>
                        <div class="service-tech">Spring Boot<br>REST APIs<br>Catalog Management</div>
                    </div>
                    <div class="service-card" onclick="showInfo('order')">
                        <div class="service-icon">🛒</div>
                        <div class="service-name">Order Service</div>
                        <div class="service-tech">Spring Boot<br>Transaction Management<br>Order Processing</div>
                    </div>
                    <div class="service-card" onclick="showInfo('payment')">
                        <div class="service-icon">💳</div>
                        <div class="service-name">Payment Service</div>
                        <div class="service-tech">Spring Boot<br>Payment Gateway Integration<br>Secure Transactions</div>
                    </div>
                    <div class="service-card" onclick="showInfo('notification')">
                        <div class="service-icon">📧</div>
                        <div class="service-name">Notification Service</div>
                        <div class="service-tech">Spring Boot<br>Email/SMS APIs<br>Event-Driven</div>
                    </div>
                </div>
            </div>

            <!-- Database Layer -->
            <div class="layer">
                <div class="layer-title">💾 Data Layer</div>
                <div class="services-row">
                    <div class="service-card database" onclick="showInfo('userdb')">
                        <div class="service-icon">🗄️</div>
                        <div class="service-name">User DB</div>
                        <div class="service-tech">Oracle / PostgreSQL<br>User Data</div>
                    </div>
                    <div class="service-card database" onclick="showInfo('productdb')">
                        <div class="service-icon">🗄️</div>
                        <div class="service-name">Product DB</div>
                        <div class="service-tech">Oracle / MySQL<br>Product Catalog</div>
                    </div>
                    <div class="service-card database" onclick="showInfo('orderdb')">
                        <div class="service-icon">🗄️</div>
                        <div class="service-name">Order DB</div>
                        <div class="service-tech">Oracle / PostgreSQL<br>Order History</div>
                    </div>
                    <div class="service-card database" onclick="showInfo('cache')">
                        <div class="service-icon">⚡</div>
                        <div class="service-name">Redis Cache</div>
                        <div class="service-tech">In-Memory Cache<br>Session Management</div>
                    </div>
                </div>
            </div>

            <!-- Infrastructure Layer -->
            <div class="layer">
                <div class="layer-title">🏗️ Infrastructure & DevOps</div>
                <div class="services-row">
                    <div class="service-card infrastructure" onclick="showInfo('eureka')">
                        <div class="service-icon">🔍</div>
                        <div class="service-name">Service Discovery</div>
                        <div class="service-tech">Eureka Server<br>Service Registry</div>
                    </div>
                    <div class="service-card infrastructure" onclick="showInfo('config')">
                        <div class="service-icon">⚙️</div>
                        <div class="service-name">Config Server</div>
                        <div class="service-tech">Spring Cloud Config<br>Centralized Configuration</div>
                    </div>
                    <div class="service-card infrastructure" onclick="showInfo('monitor')">
                        <div class="service-icon">📊</div>
                        <div class="service-name">Monitoring</div>
                        <div class="service-tech">Prometheus<br>Grafana<br>ELK Stack</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Tech Stack Section -->
        <div class="tech-stack">
            <h2>🛠️ Technology Stack</h2>
            <div class="tech-grid">
                <div class="tech-item">
                    <strong>Backend</strong>
                    Java 17+, Spring Boot, Spring Cloud
                </div>
                <div class="tech-item">
                    <strong>Database</strong>
                    Oracle, PostgreSQL, MySQL, MongoDB
                </div>
                <div class="tech-item">
                    <strong>Frontend</strong>
                    HTML5, CSS3, JavaScript, React
                </div>
                <div class="tech-item">
                    <strong>Messaging</strong>
                    Apache Kafka, RabbitMQ
                </div>
                <div class="tech-item">
                    <strong>Containerization</strong>
                    Docker, Kubernetes
                </div>
                <div class="tech-item">
                    <strong>CI/CD</strong>
                    Jenkins, GitLab CI, GitHub Actions
                </div>
            </div>
        </div>

        <!-- Legend -->
        <div class="legend">
            <div class="legend-item">
                <div class="legend-color" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"></div>
                <span>Microservices</span>
            </div>
            <div class="legend-item">
                <div class="legend-color" style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);"></div>
                <span>Databases</span>
            </div>
            <div class="legend-item">
                <div class="legend-color" style="background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);"></div>
                <span>Infrastructure</span>
            </div>
        </div>
    </div>

    <!-- Info Panel -->
    <div class="info-panel" id="infoPanel">
        <button class="close-btn" onclick="closeInfo()">×</button>
        <h3 id="infoTitle">Service Details</h3>
        <p id="infoContent"></p>
    </div>

    <script>
        const serviceInfo = {
            gateway: {
                title: '🌐 API Gateway',
                content: 'Central entry point for all client requests. Handles authentication, rate limiting, load balancing, and routes requests to appropriate microservices. Built with Spring Cloud Gateway or Netflix Zuul.'
            },
            user: {
                title: '👤 User Service',
                content: 'Manages user registration, authentication, profile management, and authorization. Implements JWT-based security, password encryption, and role-based access control (RBAC).'
            },
            product: {
                title: '📦 Product Service',
                content: 'Handles product catalog, inventory management, product search, and filtering. Provides REST APIs for product CRUD operations with caching for performance optimization.'
            },
            order: {
                title: '🛒 Order Service',
                content: 'Manages order lifecycle from creation to fulfillment. Handles order validation, inventory checks, order status updates, and integrates with payment and notification services.'
            },
            payment: {
                title: '💳 Payment Service',
                content: 'Processes payments securely through integrated payment gateways. Handles payment validation, transaction history, refunds, and complies with PCI-DSS standards.'
            },
            notification: {
                title: '📧 Notification Service',
                content: 'Sends notifications via email, SMS, and push notifications. Event-driven architecture using message queues (Kafka/RabbitMQ) for asynchronous communication.'
            },
            userdb: {
                title: '🗄️ User Database',
                content: 'Stores user credentials, profiles, preferences, and authentication tokens. Uses Oracle or PostgreSQL with encryption for sensitive data.'
            },
            productdb: {
                title: '🗄️ Product Database',
                content: 'Maintains product catalog, inventory levels, pricing, and product attributes. Optimized for read-heavy operations with proper indexing.'
            },
            orderdb: {
                title: '🗄️ Order Database',
                content: 'Stores order details, transaction history, and order status. Ensures ACID properties for transactional consistency.'
            },
            cache: {
                title: '⚡ Redis Cache',
                content: 'In-memory data store for caching frequently accessed data, session management, and real-time analytics. Improves response time significantly.'
            },
            eureka: {
                title: '🔍 Service Discovery',
                content: 'Netflix Eureka server for service registration and discovery. Enables dynamic service location and load balancing without hard-coded URLs.'
            },
            config: {
                title: '⚙️ Config Server',
                content: 'Centralized configuration management using Spring Cloud Config. Supports environment-specific configs and hot-reloading without service restart.'
            },
            monitor: {
                title: '📊 Monitoring & Logging',
                content: 'Comprehensive monitoring using Prometheus for metrics, Grafana for visualization, and ELK Stack (Elasticsearch, Logstash, Kibana) for centralized logging and analysis.'
            }
        };

        function showInfo(service) {
            const panel = document.getElementById('infoPanel');
            const title = document.getElementById('infoTitle');
            const content = document.getElementById('infoContent');
            
            if (serviceInfo[service]) {
                title.textContent = serviceInfo[service].title;
                content.textContent = serviceInfo[service].content;
                panel.classList.add('active');
            }
        }

        function closeInfo() {
            document.getElementById('infoPanel').classList.remove('active');
        }

        // Add stagger animation to service cards
        document.addEventListener('DOMContentLoaded', () => {
            const cards = document.querySelectorAll('.service-card');
            cards.forEach((card, index) => {
                card.style.animationDelay = `${index * 0.1}s`;
            });
        });
    </script>
</body>
</html>
