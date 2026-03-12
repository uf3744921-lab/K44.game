<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>K44 Game - Online Gaming Platform</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');
        
        body {
            font-family: 'Inter', sans-serif;
            background-color: #0a0e1a;
            color: #ffffff;
        }
        
        .neon-green {
            color: #00ff88;
        }
        
        .bg-neon-green {
            background-color: #00ff88;
        }
        
        .border-neon-green {
            border-color: #00ff88;
        }
        
        .hover-neon:hover {
            color: #00ff88;
            transition: all 0.3s ease;
        }
        
        .game-card {
            background: linear-gradient(145deg, #1a1f2e 0%, #151922 100%);
            border: 1px solid #2a3142;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }
        
        .game-card:hover {
            transform: translateY(-5px);
            border-color: #00ff88;
            box-shadow: 0 10px 30px rgba(0, 255, 136, 0.2);
        }
        
        .game-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.1), transparent);
            transition: left 0.5s;
        }
        
        .game-card:hover::before {
            left: 100%;
        }
        
        .sidebar-item {
            transition: all 0.3s ease;
            border-left: 3px solid transparent;
        }
        
        .sidebar-item:hover, .sidebar-item.active {
            background: linear-gradient(90deg, rgba(0, 255, 136, 0.1) 0%, transparent 100%);
            border-left-color: #00ff88;
            color: #00ff88;
        }
        
        .gradient-text {
            background: linear-gradient(135deg, #00ff88 0%, #00cc6a 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        
        .pulse-animation {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }
        
        .float-animation {
            animation: float 3s ease-in-out infinite;
        }
        
        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }
        
        .marquee-container {
            overflow: hidden;
            white-space: nowrap;
        }
        
        .marquee-content {
            display: inline-block;
            animation: marquee 20s linear infinite;
        }
        
        @keyframes marquee {
            0% { transform: translateX(0); }
            100% { transform: translateX(-50%); }
        }
        
        .glass-effect {
            background: rgba(26, 31, 46, 0.8);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .category-pill {
            transition: all 0.3s ease;
        }
        
        .category-pill.active {
            background-color: #00ff88;
            color: #0a0e1a;
            font-weight: 600;
        }
        
        .category-pill:hover:not(.active) {
            background-color: rgba(0, 255, 136, 0.2);
            color: #00ff88;
        }
        
        .jackpot-counter {
            font-variant-numeric: tabular-nums;
            letter-spacing: 2px;
        }
        
        .live-badge {
            background: linear-gradient(45deg, #ff0044, #ff8800);
            animation: livePulse 1.5s infinite;
        }
        
        @keyframes livePulse {
            0%, 100% { box-shadow: 0 0 5px rgba(255, 0, 68, 0.5); }
            50% { box-shadow: 0 0 20px rgba(255, 0, 68, 0.8); }
        }
        
        .scroll-hidden::-webkit-scrollbar {
            display: none;
        }
        .scroll-hidden {
            -ms-overflow-style: none;
            scrollbar-width: none;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            backdrop-filter: blur(5px);
        }
        
        .modal.active {
            display: flex;
            animation: fadeIn 0.3s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .loader {
            border: 3px solid rgba(0, 255, 136, 0.3);
            border-top: 3px solid #00ff88;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="bg-[#0a0e1a] min-h-screen overflow-x-hidden">

    <!-- Top Navigation -->
    <nav class="fixed top-0 w-full z-50 glass-effect border-b border-gray-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <!-- Logo -->
                <div class="flex items-center space-x-2 cursor-pointer" onclick="window.location.reload()">
                    <div class="w-10 h-10 bg-gradient-to-br from-green-400 to-green-600 rounded-lg flex items-center justify-center text-black font-bold text-xl">K44</div>
                    <span class="text-2xl font-bold gradient-text tracking-tighter">GAME</span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden md:flex items-center space-x-8">
                    <a href="#" class="text-gray-300 hover-neon font-medium">Lobby</a>
                    <a href="#" class="text-gray-300 hover-neon font-medium">Promotions</a>
                    <a href="#" class="text-gray-300 hover-neon font-medium">VIP</a>
                    <a href="#" class="text-gray-300 hover-neon font-medium">Support</a>
                </div>

                <!-- Right Side -->
                <div class="flex items-center space-x-4">
                    <!-- Balance -->
                    <div class="hidden sm:flex items-center bg-[#151922] rounded-full px-4 py-2 border border-gray-700">
                        <i class="fas fa-wallet text-[#00ff88] mr-2"></i>
                        <span class="font-bold text-[#00ff88]">₹</span>
                        <span id="balance" class="font-bold text-white ml-1">50,000.00</span>
                    </div>

                    <!-- Notifications -->
                    <button class="relative p-2 text-gray-400 hover:text-white transition" onclick="toggleNotifications()">
                        <i class="fas fa-bell text-xl"></i>
                        <span class="absolute top-1 right-1 w-2 h-2 bg-red-500 rounded-full animate-pulse"></span>
                    </button>

                    <!-- Profile -->
                    <div class="flex items-center space-x-2 cursor-pointer" onclick="toggleProfile()">
                        <div class="w-10 h-10 rounded-full bg-gradient-to-r from-purple-500 to-pink-500 flex items-center justify-center font-bold">
                            U
                        </div>
                        <i class="fas fa-chevron-down text-gray-400 text-sm hidden sm:block"></i>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- Notification Dropdown -->
    <div id="notificationPanel" class="fixed top-16 right-4 w-80 bg-[#151922] border border-gray-700 rounded-xl shadow-2xl z-40 hidden transform transition-all duration-300 origin-top-right">
        <div class="p-4 border-b border-gray-700 flex justify-between items-center">
            <h3 class="font-bold text-lg">Notifications</h3>
            <button class="text-xs text-[#00ff88] hover:underline">Mark all read</button>
        </div>
        <div class="max-h-64 overflow-y-auto">
            <div class="p-4 border-b border-gray-800 hover:bg-[#1a1f2e] cursor-pointer">
                <div class="flex items-start space-x-3">
                    <div class="w-2 h-2 bg-[#00ff88] rounded-full mt-2"></div>
                    <div>
                        <p class="text-sm font-medium">Welcome Bonus Credited!</p>
                        <p class="text-xs text-gray-400 mt-1">You received ₹5,000 welcome bonus</p>
                        <p class="text-xs text-gray-500 mt-1">2 mins ago</p>
                    </div>
                </div>
            </div>
            <div class="p-4 border-b border-gray-800 hover:bg-[#1a1f2e] cursor-pointer">
                <div class="flex items-start space-x-3">
                    <div class="w-2 h-2 bg-blue-500 rounded-full mt-2"></div>
                    <div>
                        <p class="text-sm font-medium">New Tournament Available</p>
                        <p class="text-xs text-gray-400 mt-1">Join the Poker Championship now!</p>
                        <p class="text-xs text-gray-500 mt-1">1 hour ago</p>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Main Layout -->
    <div class="pt-16 flex min-h-screen">
        
        <!-- Sidebar -->
        <aside class="fixed left-0 top-16 w-64 h-[calc(100vh-4rem)] bg-[#0f1419] border-r border-gray-800 hidden lg:block overflow-y-auto z-30">
            <div class="p-4">
                <!-- Search -->
                <div class="relative mb-6">
                    <input type="text" placeholder="Search games..." class="w-full bg-[#1a1f2e] border border-gray-700 rounded-lg py-2 pl-10 pr-4 text-sm focus:outline-none focus:border-[#00ff88] transition">
                    <i class="fas fa-search absolute left-3 top-2.5 text-gray-500"></i>
                </div>

                <!-- Categories -->
                <div class="space-y-1">
                    <div class="sidebar-item active flex items-center space-x-3 p-3 rounded-lg cursor-pointer" onclick="filterGames('all')">
                        <i class="fas fa-th-large w-5"></i>
                        <span class="font-medium">All Games</span>
                    </div>
                    <div class="sidebar-item flex items-center space-x-3 p-3 rounded-lg cursor-pointer text-gray-400" onclick="filterGames('hot')">
                        <i class="fas fa-fire w-5 text-orange-500"></i>
                        <span class="font-medium">Hot Games</span>
                        <span class="ml-auto bg-red-500 text-white text-xs px-2 py-0.5 rounded-full">HOT</span>
                    </div>
                    <div class="sidebar-item flex items-center space-x-3 p-3 rounded-lg cursor-pointer text-gray-400" onclick="filterGames('live')">
                        <i class="fas fa-video w-5 text-red-500"></i>
                        <span class="font-medium">Live Casino</span>
                        <span class="ml-auto live-badge text-white text-xs px-2 py-0.5 rounded-full">LIVE</span>
                    </div>
                    <div class="sidebar-item flex items-center space-x-3 p-3 rounded-lg cursor-pointer text-gray-400" onclick="filterGames('slots')">
                        <i class="fas fa-slot-machine w-5 text-purple-500"></i>
                        <span class="font-medium">Slots</span>
                    </div>
                    <div class="sidebar-item flex items-center space-x-3 p-3 rounded-lg cursor-pointer text-gray-400" onclick="filterGames('fish')">
                        <i class="fas fa-fish w-5 text-blue-500"></i>
                        <span class="font-medium">Fishing</span>
                    </div>
                    <div class="sidebar-item flex items-center space-x-3 p-3 rounded-lg cursor-pointer text-gray-400" onclick="filterGames('poker')">
                        <i class="fas fa-cards w-5 text-yellow-500"></i>
                        <span class="font-medium">Poker</span>
                    </div>
                    <div class="sidebar-item flex items-center space-x-3 p-3 rounded-lg cursor-pointer text-gray-400" onclick="filterGames('sports')">
                        <i class="fas fa-futbol w-5 text-green-500"></i>
                        <span class="font-medium">Sports</span>
                    </div>
                </div>

                <!-- Jackpot -->
                <div class="mt-8 p-4 bg-gradient-to-br from-[#1a1f2e] to-[#0f1419] rounded-xl border border-gray-800">
                    <div class="text-center">
                        <i class="fas fa-trophy text-yellow-400 text-2xl mb-2"></i>
                        <p class="text-xs text-gray-400 mb-1">Progressive Jackpot</p>
                        <p class="text-2xl font-bold gradient-text jackpot-counter" id="jackpot">₹1,245,890</p>
                    </div>
                </div>

                <!-- Recent Winners -->
                <div class="mt-6">
                    <h4 class="text-sm font-bold text-gray-400 mb-3 uppercase tracking-wider">Recent Winners</h4>
                    <div class="space-y-3">
                        <div class="flex items-center space-x-3 text-sm">
                            <div class="w-8 h-8 rounded-full bg-blue-500 flex items-center justify-center text-xs font-bold">A</div>
                            <div class="flex-1 min-w-0">
                                <p class="truncate font-medium">Ali_Khan</p>
                                <p class="text-xs text-gray-500">Aviator</p>
                            </div>
                            <span class="text-[#00ff88] font-bold">₹45K</span>
                        </div>
                        <div class="flex items-center space-x-3 text-sm">
                            <div class="w-8 h-8 rounded-full bg-pink-500 flex items-center justify-center text-xs font-bold">S</div>
                            <div class="flex-1 min-w-0">
                                <p class="truncate font-medium">Sara_22</p>
                                <p class="text-xs text-gray-500">Dragon Tiger</p>
                            </div>
                            <span class="text-[#00ff88] font-bold">₹128K</span>
                        </div>
                        <div class="flex items-center space-x-3 text-sm">
                            <div class="w-8 h-8 rounded-full bg-purple-500 flex items-center justify-center text-xs font-bold">M</div>
                            <div class="flex-1 min-w-0">
                                <p class="truncate font-medium">Mohammad_1</p>
                                <p class="text-xs text-gray-500">Teen Patti</p>
                            </div>
                            <span class="text-[#00ff88] font-bold">₹89K</span>
                        </div>
                    </div>
                </div>
            </div>
        </aside>

        <!-- Main Content -->
        <main class="flex-1 lg:ml-64 p-4 lg:p-8">
            
            <!-- Mobile Category Scroll -->
            <div class="lg:hidden mb-6 overflow-x-auto scroll-hidden">
                <div class="flex space-x-3 min-w-max">
                    <button class="category-pill active px-6 py-2 rounded-full bg-[#1a1f2e] border border-gray-700 text-sm font-medium" onclick="filterGames('all')">All</button>
                    <button class="category-pill px-6 py-2 rounded-full bg-[#1a1f2e] border border-gray-700 text-sm font-medium text-gray-400" onclick="filterGames('hot')">Hot</button>
                    <button class="category-pill px-6 py-2 rounded-full bg-[#1a1f2e] border border-gray-700 text-sm font-medium text-gray-400" onclick="filterGames('live')">Live</button>
                    <button class="category-pill px-6 py-2 rounded-full bg-[#1a1f2e] border border-gray-700 text-sm font-medium text-gray-400" onclick="filterGames('slots')">Slots</button>
                    <button class="category-pill px-6 py-2 rounded-full bg-[#1a1f2e] border border-gray-700 text-sm font-medium text-gray-400" onclick="filterGames('fish')">Fish</button>
                    <button class="category-pill px-6 py-2 rounded-full bg-[#1a1f2e] border border-gray-700 text-sm font-medium text-gray-400" onclick="filterGames('poker')">Poker</button>
                </div>
            </div>

            <!-- Hero Banner -->
            <div class="relative rounded-2xl overflow-hidden mb-8 group cursor-pointer" onclick="showPromo()">
                <div class="absolute inset-0 bg-gradient-to-r from-purple-900/90 to-blue-900/90 z-10"></div>
                <img src="https://images.unsplash.com/photo-1596838333650-72b563cf6315?w=1200&h=400&fit=crop" alt="Casino" class="w-full h-64 lg:h-80 object-cover transform group-hover:scale-105 transition duration-700">
                
                <div class="absolute inset-0 z-20 flex items-center justify-between p-8 lg:p-12">
                    <div class="max-w-lg">
                        <div class="flex items-center space-x-2 mb-4">
                            <span class="bg-[#00ff88] text-black text-xs font-bold px-3 py-1 rounded-full">NEW</span>
                            <span class="text-[#00ff88] font-semibold">Welcome Offer</span>
                        </div>
                        <h1 class="text-4xl lg:text-6xl font-bold mb-4 leading-tight">
                            Get <span class="gradient-text">100% Bonus</span><br>
                            Up to ₹50,000
                        </h1>
                        <p class="text-gray-300 mb-6 text-lg">Join Pakistan's #1 gaming platform. Instant withdrawals, 24/7 support.</p>
                        <button class="bg-[#00ff88] text-black font-bold py-3 px-8 rounded-full hover:bg-[#00cc6a] transition transform hover:scale-105 flex items-center space-x-2">
                            <span>Claim Now</span>
                            <i class="fas fa-arrow-right"></i>
                        </button>
                    </div>
                    <div class="hidden lg:block float-animation">
                        <div class="w-48 h-48 bg-gradient-to-br from-[#00ff88] to-[#00cc6a] rounded-full flex items-center justify-center shadow-2xl shadow-green-500/50">
                            <div class="text-center text-black">
                                <p class="text-sm font-bold">BONUS</p>
                                <p class="text-4xl font-black">100%</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Marquee -->
            <div class="bg-[#151922] border border-gray-800 rounded-lg mb-8 overflow-hidden">
                <div class="marquee-container py-3">
                    <div class="marquee-content text-sm">
                        <span class="text-[#00ff88] mx-4">🔥 Hot Streak:</span>
                        <span class="text-gray-300 mx-4">Player Ahmad just won ₹245,000 on Aviator!</span>
                        <span class="text-gray-600 mx-4">|</span>
                        <span class="text-[#00ff88] mx-4">💰 Jackpot Alert:</span>
                        <span class="text-gray-300 mx-4">Progressive jackpot now at ₹1.2M and growing!</span>
                        <span class="text-gray-600 mx-4">|</span>
                        <span class="text-[#00ff88] mx-4">🎮 Tournament:</span>
                        <span class="text-gray-300 mx-4">Daily Poker Championship starts in 2 hours!</span>
                        <span class="text-gray-600 mx-4">|</span>
                        <span class="text-[#00ff88] mx-4">🔥 Hot Streak:</span>
                        <span class="text-gray-300 mx-4">Player Ahmad just won ₹245,000 on Aviator!</span>
                        <span class="text-gray-600 mx-4">|</span>
                        <span class="text-[#00ff88] mx-4">💰 Jackpot Alert:</span>
                        <span class="text-gray-300 mx-4">Progressive jackpot now at ₹1.2M and growing!</span>
                    </div>
                </div>
            </div>

            <!-- Section Header -->
            <div class="flex items-center justify-between mb-6">
                <div class="flex items-center space-x-3">
                    <h2 class="text-2xl font-bold" id="sectionTitle">All Games</h2>
                    <span class="bg-gray-800 text-gray-400 text-xs px-3 py-1 rounded-full" id="gameCount">24 games</span>
                </div>
                <div class="flex items-center space-x-2">
                    <button class="p-2 text-gray-400 hover:text-white transition" onclick="changeView('grid')">
                        <i class="fas fa-th-large text-lg"></i>
                    </button>
                    <button class="p-2 text-gray-400 hover:text-white transition" onclick="changeView('list')">
                        <i class="fas fa-list text-lg"></i>
                    </button>
                </div>
            </div>

            <!-- Games Grid -->
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-4 lg:gap-6" id="gamesGrid">
                <!-- Games will be populated by JavaScript -->
            </div>

            <!-- Load More -->
            <div class="mt-12 text-center">
                <button class="bg-transparent border-2 border-[#00ff88] text-[#00ff88] font-bold py-3 px-12 rounded-full hover:bg-[#00ff88] hover:text-black transition transform hover:scale-105" onclick="loadMore()">
                    Load More Games
                </button>
            </div>

            <!-- Footer -->
            <footer class="mt-16 pt-8 border-t border-gray-800">
                <div class="grid grid-cols-2 md:grid-cols-4 gap-8 mb-8">
                    <div>
                        <h4 class="font-bold mb-4 text-[#00ff88]">Games</h4>
                        <ul class="space-y-2 text-sm text-gray-400">
                            <li><a href="#" class="hover:text-white transition">Slots</a></li>
                            <li><a href="#" class="hover:text-white transition">Live Casino</a></li>
                            <li><a href="#" class="hover:text-white transition">Poker</a></li>
                            <li><a href="#" class="hover:text-white transition">Sports</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4 text-[#00ff88]">Support</h4>
                        <ul class="space-y-2 text-sm text-gray-400">
                            <li><a href="#" class="hover:text-white transition">Help Center</a></li>
                            <li><a href="#" class="hover:text-white transition">Live Chat</a></li>
                            <li><a href="#" class="hover:text-white transition">Contact Us</a></li>
                            <li><a href="#" class="hover:text-white transition">FAQ</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4 text-[#00ff88]">Legal</h4>
                        <ul class="space-y-2 text-sm text-gray-400">
                            <li><a href="#" class="hover:text-white transition">Privacy Policy</a></li>
                            <li><a href="#" class="hover:text-white transition">Terms of Service</a></li>
                            <li><a href="#" class="hover:text-white transition">Responsible Gaming</a></li>
                            <li><a href="#" class="hover:text-white transition">Licenses</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4 text-[#00ff88]">Payment Methods</h4>
                        <div class="flex space-x-3 text-2xl text-gray-400">
                            <i class="fab fa-cc-visa hover:text-white transition"></i>
                            <i class="fab fa-cc-mastercard hover:text-white transition"></i>
                            <i class="fas fa-wallet hover:text-white transition"></i>
                            <i class="fab fa-bitcoin hover:text-white transition"></i>
                        </div>
                    </div>
                </div>
                <div class="text-center text-gray-600 text-sm pb-8">
                    <p>&copy; 2026 K44 Game. All rights reserved. 18+ Only. Gamble Responsibly.</p>
                </div>
            </footer>
        </main>
    </div>

    <!-- Floating Action Button -->
    <div class="fixed bottom-6 right-6 z-40">
        <button class="w-14 h-14 bg-[#00ff88] rounded-full shadow-lg shadow-green-500/30 flex items-center justify-center text-black text-2xl hover:scale-110 transition transform" onclick="toggleChat()">
            <i class="fas fa-comments"></i>
        </button>
    </div>

    <!-- Chat Modal -->
    <div id="chatModal" class="fixed bottom-24 right-6 w-80 bg-[#151922] border border-gray-700 rounded-2xl shadow-2xl z-40 hidden transform transition-all duration-300 origin-bottom-right">
        <div class="p-4 border-b border-gray-700 flex justify-between items-center bg-gradient-to-r from-[#1a1f2e] to-[#151922] rounded-t-2xl">
            <div class="flex items-center space-x-2">
                <div class="w-2 h-2 bg-[#00ff88] rounded-full animate-pulse"></div>
                <h3 class="font-bold">Live Support</h3>
            </div>
            <button onclick="toggleChat()" class="text-gray-400 hover:text-white"><i class="fas fa-times"></i></button>
        </div>
        <div class="h-64 overflow-y-auto p-4 space-y-3" id="chatMessages">
            <div class="flex items-start space-x-2">
                <div class="w-8 h-8 rounded-full bg-[#00ff88] flex items-center justify-center text-black text-xs font-bold">S</div>
                <div class="bg-[#1a1f2e] rounded-lg p-3 text-sm max-w-[80%]">
                    <p>Hello! Welcome to K44 Game. How can I help you today?</p>
                </div>
            </div>
        </div>
        <div class="p-4 border-t border-gray-700">
            <div class="flex space-x-2">
                <input type="text" placeholder="Type a message..." class="flex-1 bg-[#1a1f2e] border border-gray-700 rounded-lg px-3 py-2 text-sm focus:outline-none focus:border-[#00ff88]" id="chatInput">
                <button class="bg-[#00ff88] text-black px-4 py-2 rounded-lg font-bold hover:bg-[#00cc6a] transition" onclick="sendMessage()">
                    <i class="fas fa-paper-plane"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- Game Launch Modal -->
    <div id="gameModal" class="modal items-center justify-center p-4">
        <div class="bg-[#151922] border border-gray-700 rounded-2xl max-w-2xl w-full max-h-[90vh] overflow-y-auto transform transition-all duration-300 scale-95" id="gameModalContent">
            <div class="relative">
                <img id="modalImage" src="" alt="Game" class="w-full h-64 object-cover rounded-t-2xl">
                <button onclick="closeGameModal()" class="absolute top-4 right-4 w-10 h-10 bg-black/50 rounded-full flex items-center justify-center text-white hover:bg-black/70 transition">
                    <i class="fas fa-times"></i>
                </button>
                <div class="absolute bottom-0 left-0 right-0 bg-gradient-to-t from-[#151922] to-transparent h-32"></div>
                <div class="absolute bottom-4 left-6">
                    <span class="bg-[#00ff88] text-black text-xs font-bold px-3 py-1 rounded-full mb-2 inline-block" id="modalCategory">SLOTS</span>
                    <h2 class="text-3xl font-bold" id="modalTitle">Game Title</h2>
                </div>
            </div>
            <div class="p-6">
                <div class="flex items-center justify-between mb-6">
                    <div>
                        <p class="text-gray-400 text-sm mb-1">Current Jackpot</p>
                        <p class="text-2xl font-bold gradient-text">₹<span id="modalJackpot">125,000</span></p>
                    </div>
                    <div class="text-right">
                        <p class="text-gray-400 text-sm mb-1">RTP</p>
                        <p class="text-2xl font-bold text-white">96.5%</p>
                    </div>
                </div>
                <p class="text-gray-300 mb-6 leading-relaxed">Experience the thrill of this exciting game with stunning graphics and massive winning potential. Join thousands of players winning big every day!</p>
                
                <div class="grid grid-cols-2 gap-4 mb-6">
                    <button class="bg-[#1a1f2e] border border-gray-700 py-3 rounded-xl font-bold text-gray-300 hover:border-[#00ff88] hover:text-[#00ff88] transition">
                        Demo Play
                    </button>
                    <button class="bg-[#00ff88] text-black py-3 rounded-xl font-bold hover:bg-[#00cc6a] transition transform hover:scale-105" onclick="startGame()">
                        Play Now
                    </button>
                </div>

                <div class="border-t border-gray-800 pt-4">
                    <h4 class="font-bold mb-3 text-sm text-gray-400 uppercase">Recent Big Wins</h4>
                    <div class="space-y-2">
                        <div class="flex justify-between text-sm">
                            <span class="text-gray-400">Player786</span>
                            <span class="text-[#00ff88] font-bold">₹45,200</span>
                        </div>
                        <div class="flex justify-between text-sm">
                            <span class="text-gray-400">LuckyStar</span>
                            <span class="text-[#00ff88] font-bold">₹128,500</span>
                        </div>
                        <div class="flex justify-between text-sm">
                            <span class="text-gray-400">KingKhan</span>
                            <span class="text-[#00ff88] font-bold">₹89,000</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Loading Overlay -->
    <div id="loadingOverlay" class="fixed inset-0 bg-black/90 z-[60] hidden items-center justify-center flex-col">
        <div class="loader mb-4"></div>
        <p class="text-[#00ff88] font-bold animate-pulse">Loading Game...</p>
    </div>

    <script>
        // Game Data
        const games = [
            { id: 1, title: "Aviator", category: "hot", image: "https://images.unsplash.com/photo-1550745165-9bc0b252726f?w=400&h=300&fit=crop", rtp: "97%", badge: "HOT" },
            { id: 2, title: "Dragon Tiger", category: "live", image: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?w=400&h=300&fit=crop", rtp: "96.5%", badge: "LIVE" },
            { id: 3, title: "Teen Patti", category: "poker", image: "https://images.unsplash.com/photo-1596838333650-72b563cf6315?w=400&h=300&fit=crop", rtp: "95%", badge: "POPULAR" },
            { id: 4, title: "Fortune Tiger", category: "slots", image: "https://images.unsplash.com/photo-1606167668584-78701c57f13d?w=400&h=300&fit=crop", rtp: "96%", badge: "NEW" },
            { id: 5, title: "Fishing War", category: "fish", image: "https://images.unsplash.com/photo-1544551763-46a013bb70d5?w=400&h=300&fit=crop", rtp: "94%", badge: "HOT" },
            { id: 6, title: "Andar Bahar", category: "live", image: "https://images.unsplash.com/photo-1511193311914-0346f16efe90?w=400&h=300&fit=crop", rtp: "95.5%", badge: "LIVE" },
            { id: 7, title: "Roulette", category: "live", image: "https://images.unsplash.com/photo-1601645191163-3fc0d5d64e35?w=400&h=300&fit=crop", rtp: "97.3%", badge: "VIP" },
            { id: 8, title: "Blackjack", category: "live", image: "https://images.unsplash.com/photo-1595327816687-227cb5b2763c?w=400&h=300&fit=crop", rtp: "99.5%", badge: "LIVE" },
            { id: 9, title: "Sweet Bonanza", category: "slots", image: "https://images.unsplash.com/photo-1560167164-616078ea2824?w=400&h=300&fit=crop", rtp: "96.5%", badge: "HOT" },
            { id: 10, title: "Gates of Olympus", category: "slots", image: "https://images.unsplash.com/photo-1570303345338-e1f0eddf4946?w=400&h=300&fit=crop", rtp: "96%", badge: "NEW" },
            { id: 11, title: "Cricket Live", category: "sports", image: "https://images.unsplash.com/photo-1531415074968-036ba1b575da?w=400&h=300&fit=crop", rtp: "-", badge: "LIVE" },
            { id: 12, title: "Football Pro", category: "sports", image: "https://images.unsplash.com/photo-1579952363873-27f3bade9f55?w=400&h=300&fit=crop", rtp: "-", badge: "HOT" },
            { id: 13, title: "Money Coming", category: "slots", image: "https://images.unsplash.com/photo-1518546305927-5a555bb7020d?w=400&h=300&fit=crop", rtp: "95%", badge: "HOT" },
            { id: 14, title: "Color Game", category: "hot", image: "https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=400&h=300&fit=crop", rtp: "94%", badge: "TRENDING" },
            { id: 15, title: "Pirate Flip", category: "fish", image: "https://images.unsplash.com/photo-1516690561799-46d8f74f9abf?w=400&h=300&fit=crop", rtp: "93%", badge: "NEW" },
            { id: 16, title: "Rocket Crash", category: "hot", image: "https://images.unsplash.com/photo-1517976487492-5750f3195933?w=400&h=300&fit=crop", rtp: "98%", badge: "HOT" },
            { id: 17, title: "Ludo Quick", category: "hot", image: "https://images.unsplash.com/photo-1610890716171-6b1c9f2bd40c?w=400&h=300&fit=crop", rtp: "90%", badge: "POPULAR" },
            { id: 18, title: "Mine Sweeper", category: "hot", image: "https://images.unsplash.com/photo-1595590424283-b8f17842773f?w=400&h=300&fit=crop", rtp: "95%", badge: "NEW" },
            { id: 19, title: "Baccarat", category: "live", image: "https://images.unsplash.com/photo-1601645191163-3fc0d5d64e35?w=400&h=300&fit=crop", rtp: "98.9%", badge: "VIP" },
            { id: 20, title: "Dinosaur Tycoon", category: "fish", image: "https://images.unsplash.com/photo-1518709268805-4e9042af9f23?w=400&h=300&fit=crop", rtp: "92%", badge: "NEW" }
        ];

        let currentFilter = 'all';
        let displayedGames = 12;

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            renderGames();
            startJackpotCounter();
            startBalanceUpdate();
        });

        // Render Games
        function renderGames() {
            const grid = document.getElementById('gamesGrid');
            const filtered = currentFilter === 'all' ? games : games.filter(g => g.category === currentFilter);
            const toShow = filtered.slice(0, displayedGames);
            
            document.getElementById('gameCount').textContent = `${filtered.length} games`;
            
            grid.innerHTML = toShow.map(game => `
                <div class="game-card rounded-xl cursor-pointer group" onclick="openGame(${game.id})">
                    <div class="relative overflow-hidden rounded-t-xl">
                        <img src="${game.image}" alt="${game.title}" class="w-full h-40 object-cover transform group-hover:scale-110 transition duration-500">
                        <div class="absolute top-2 right-2">
                            ${game.badge === 'LIVE' ? '<span class="live-badge text-white text-xs font-bold px-2 py-1 rounded">LIVE</span>' : 
                              game.badge === 'HOT' ? '<span class="bg-red-500 text-white text-xs font-bold px-2 py-1 rounded">HOT</span>' :
                              game.badge === 'NEW' ? '<span class="bg-blue-500 text-white text-xs font-bold px-2 py-1 rounded">NEW</span>' :
                              '<span class="bg-purple-500 text-white text-xs font-bold px-2 py-1 rounded">VIP</span>'}
                        </div>
                        <div class="absolute inset-0 bg-black/50 opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center">
                            <button class="bg-[#00ff88] text-black font-bold py-2 px-6 rounded-full transform scale-0 group-hover:scale-100 transition duration-300">
                                Play Now
                            </button>
                        </div>
                    </div>
                    <div class="p-4">
                        <h3 class="font-bold text-lg mb-1 group-hover:text-[#00ff88] transition">${game.title}</h3>
                        <div class="flex items-center justify-between text-xs text-gray-400">
                            <span>RTP: ${game.rtp}</span>
                            <span class="flex items-center"><i class="fas fa-user mr-1"></i> ${Math.floor(Math.random() * 5000) + 1000}</span>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        // Filter Games
        function filterGames(category) {
            currentFilter = category;
            displayedGames = 12;
            
            // Update active states
            document.querySelectorAll('.sidebar-item').forEach(item => {
                item.classList.remove('active');
                item.classList.add('text-gray-400');
            });
            event.target.closest('.sidebar-item').classList.add('active');
            event.target.closest('.sidebar-item').classList.remove('text-gray-400');
            
            // Update mobile pills
            document.querySelectorAll('.category-pill').forEach(pill => {
                pill.classList.remove('active');
                if(pill.textContent.toLowerCase().includes(category) || (category === 'all' && pill.textContent === 'All')) {
                    pill.classList.add('active');
                    pill.classList.remove('text-gray-400');
                } else {
                    pill.classList.add('text-gray-400');
                }
            });
            
            // Update title
            const titles = {
                'all': 'All Games',
                'hot': 'Hot Games',
                'live': 'Live Casino',
                'slots': 'Slot Games',
                'fish': 'Fishing Games',
                'poker': 'Poker Games',
                'sports': 'Sports Betting'
            };
            document.getElementById('sectionTitle').textContent = titles[category] || 'Games';
            
            renderGames();
        }

        // Load More
        function loadMore() {
            displayedGames += 8;
            renderGames();
        }

        // Game Modal
        function openGame(id) {
            const game = games.find(g => g.id === id);
            if (!game) return;
            
            document.getElementById('modalImage').src = game.image;
            document.getElementById('modalTitle').textContent = game.title;
            document.getElementById('modalCategory').textContent = game.category.toUpperCase();
            document.getElementById('modalJackpot').textContent = Math.floor(Math.random() * 200000 + 50000).toLocaleString();
            
            document.getElementById('gameModal').classList.add('active');
            document.getElementById('gameModalContent').classList.remove('scale-95');
            document.getElementById('gameModalContent').classList.add('scale-100');
        }

        function closeGameModal() {
            document.getElementById('gameModal').classList.remove('active');
            document.getElementById('gameModalContent').classList.add('scale-95');
            document.getElementById('gameModalContent').classList.remove('scale-100');
        }

        function startGame() {
            closeGameModal();
            document.getElementById('loadingOverlay').classList.remove('hidden');
            document.getElementById('loadingOverlay').classList.add('flex');
            
            setTimeout(() => {
                document.getElementById('loadingOverlay').classList.add('hidden');
                document.getElementById('loadingOverlay').classList.remove('flex');
                alert('Game would launch here! This is a demo interface.');
            }, 2000);
        }

        // Jackpot Counter Animation
        function startJackpotCounter() {
            let jackpot = 1245890;
            setInterval(() => {
                jackpot += Math.floor(Math.random() * 100);
                document.getElementById('jackpot').textContent = '₹' + jackpot.toLocaleString();
            }, 3000);
        }

        // Balance Update Simulation
        function startBalanceUpdate() {
            setInterval(() => {
                // Randomly update balance slightly to simulate live feel
                if(Math.random() > 0.7) {
                    const balanceEl = document.getElementById('balance');
                    let current = parseFloat(balanceEl.textContent.replace(/,/g, ''));
                    current += Math.random() * 10 - 5;
                    balanceEl.textContent = current.toLocaleString('en-IN', {minimumFractionDigits: 2, maximumFractionDigits: 2});
                }
            }, 5000);
        }

        // UI Toggles
        function toggleNotifications() {
            const panel = document.getElementById('notificationPanel');
            panel.classList.toggle('hidden');
        }

        function toggleProfile() {
            alert('Profile menu would open here');
        }

        function toggleChat() {
            const chat = document.getElementById('chatModal');
            chat.classList.toggle('hidden');
        }

        function sendMessage() {
            const input = document.getElementById('chatInput');
            const message = input.value.trim();
            if (!message) return;
            
            const container = document.getElementById('chatMessages');
            container.innerHTML += `
                <div class="flex items-start space-x-2 justify-end">
                    <div class="bg-[#00ff88] text-black rounded-lg p-3 text-sm max-w-[80%]">
                        <p>${message}</p>
                    </div>
                </div>
            `;
            input.value = '';
            container.scrollTop = container.scrollHeight;
            
            // Simulate response
            setTimeout(() => {
                container.innerHTML += `
                    <div class="flex items-start space-x-2">
                        <div class="w-8 h-8 rounded-full bg-[#00ff88] flex items-center justify-center text-black text-xs font-bold">S</div>
                        <div class="bg-[#1a1f2e] rounded-lg p-3 text-sm max-w-[80%]">
                            <p>Thanks for your message! Our team will assist you shortly.</p>
                        </div>
                    </div>
                `;
                container.scrollTop = container.scrollHeight;
            }, 1000);
        }

        function showPromo() {
            alert('Welcome Bonus: 100% up to ₹50,000! Deposit now to claim.');
        }

        function changeView(type) {
            const grid = document.getElementById('gamesGrid');
            if (type === 'list') {
                grid.classList.remove('grid-cols-2', 'md:grid-cols-3', 'lg:grid-cols-4', 'xl:grid-cols-5');
                grid.classList.add('grid-cols-1');
            } else {
                grid.classList.add('grid-cols-2', 'md:grid-cols-3', 'lg:grid-cols-4', 'xl:grid-cols-5');
                grid.classList.remove('grid-cols-1');
            }
        }

        // Close modals on outside click
        window.onclick = function(event) {
            const modal = document.getElementById('gameModal');
            if (event.target === modal) {
                closeGameModal();
            }
        }

        // Enter key for chat
        document.getElementById('chatInput')?.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') sendMessage();
        });
    </script>
</body>
</html>
