# WANDER-LUST
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wanderlust - Explore the World</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Poppins', 'sans-serif'],
                        serif: ['Playfair Display', 'serif'],
                    },
                    colors: {
                        brand: {
                            50: '#f0f9ff',
                            100: '#e0f2fe',
                            500: '#0ea5e9',
                            600: '#0284c7',
                            900: '#0c4a6e',
                        }
                    }
                }
            }
        }
    </script>
    <style>
        .hero-bg {
            background-image: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), url('https://images.unsplash.com/photo-1469854523086-cc02fe5d8800?auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
        }
        .card-zoom:hover img {
            transform: scale(1.1);
        }
        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        ::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="font-sans text-gray-700 antialiased bg-gray-50">

    <!-- Navigation -->
    <nav class="fixed w-full z-50 transition-all duration-300 bg-white/90 backdrop-blur-md shadow-sm" id="navbar">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <!-- Logo -->
                <div class="flex-shrink-0 flex items-center gap-2 cursor-pointer" onclick="window.scrollTo(0,0)">
                    <i class="fa-solid fa-earth-americas text-brand-600 text-3xl"></i>
                    <span class="font-serif text-2xl font-bold text-gray-900">Wanderlust</span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden md:flex space-x-8 items-center">
                    <a href="#destinations" class="text-gray-600 hover:text-brand-600 font-medium transition">Destinations</a>
                    <a href="#experiences" class="text-gray-600 hover:text-brand-600 font-medium transition">Experiences</a>
                    <a href="#planner" class="text-gray-600 hover:text-brand-600 font-medium transition">Trip Planner</a>
                    <button onclick="document.getElementById('newsletter').scrollIntoView({behavior: 'smooth'})" class="bg-brand-600 text-white px-5 py-2.5 rounded-full hover:bg-brand-700 transition shadow-lg shadow-brand-500/30 font-medium">
                        Subscribe
                    </button>
                </div>

                <!-- Mobile menu button -->
                <div class="md:hidden flex items-center">
                    <button id="mobile-menu-btn" class="text-gray-600 hover:text-gray-900 focus:outline-none p-2">
                        <i class="fa-solid fa-bars text-2xl"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu Panel -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t border-gray-100 absolute w-full">
            <div class="px-4 pt-2 pb-6 space-y-2 shadow-lg">
                <a href="#destinations" class="block px-3 py-3 text-base font-medium text-gray-700 hover:bg-brand-50 hover:text-brand-600 rounded-md">Destinations</a>
                <a href="#experiences" class="block px-3 py-3 text-base font-medium text-gray-700 hover:bg-brand-50 hover:text-brand-600 rounded-md">Experiences</a>
                <a href="#planner" class="block px-3 py-3 text-base font-medium text-gray-700 hover:bg-brand-50 hover:text-brand-600 rounded-md">Trip Planner</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <header class="relative h-screen flex items-center justify-center hero-bg">
        <div class="relative z-10 text-center px-4 max-w-4xl mx-auto mt-16">
            <span class="inline-block py-1 px-3 rounded-full bg-white/20 backdrop-blur-sm text-white text-sm font-medium mb-6 border border-white/30 uppercase tracking-wider">
                Explore the unseen
            </span>
            <h1 class="text-5xl md:text-7xl font-serif font-bold text-white mb-6 leading-tight drop-shadow-lg">
                Discover Your Next <br/> <span class="text-brand-300 italic">Great Adventure</span>
            </h1>
            <p class="text-lg md:text-xl text-gray-200 mb-10 max-w-2xl mx-auto font-light">
                Curated guides for the modern explorer. From hidden mountain peaks to bustling city streets, find the journey that speaks to your soul.
            </p>
            
            <!-- Search/Filter Bar -->
            <div class="bg-white p-2 rounded-full shadow-2xl max-w-2xl mx-auto flex flex-col md:flex-row gap-2">
                <div class="flex-1 px-4 py-2 flex items-center border-b md:border-b-0 md:border-r border-gray-200">
                    <i class="fa-solid fa-location-dot text-gray-400 mr-3"></i>
                    <input type="text" id="search-input" placeholder="Where do you want to go?" class="w-full outline-none text-gray-700 placeholder-gray-400 bg-transparent">
                </div>
                <button onclick="filterDestinations('all')" class="bg-brand-600 hover:bg-brand-700 text-white px-8 py-3 rounded-full font-medium transition duration-300 flex items-center justify-center gap-2">
                    <i class="fa-solid fa-magnifying-glass"></i> Explore
                </button>
            </div>
        </div>
        
        <!-- Scroll Down Indicator -->
        <div class="absolute bottom-10 left-1/2 transform -translate-x-1/2 animate-bounce text-white/70">
            <i class="fa-solid fa-chevron-down text-2xl"></i>
        </div>
    </header>

    <!-- Stats Section -->
    <section class="py-10 bg-white border-b border-gray-100">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-8 text-center divide-x divide-gray-100">
                <div>
                    <div class="text-3xl font-bold text-brand-600 mb-1">150+</div>
                    <div class="text-sm text-gray-500 font-medium uppercase tracking-wide">Destinations</div>
                </div>
                <div>
                    <div class="text-3xl font-bold text-brand-600 mb-1">24/7</div>
                    <div class="text-sm text-gray-500 font-medium uppercase tracking-wide">Support</div>
                </div>
                <div>
                    <div class="text-3xl font-bold text-brand-600 mb-1">50k+</div>
                    <div class="text-sm text-gray-500 font-medium uppercase tracking-wide">Travelers</div>
                </div>
                <div>
                    <div class="text-3xl font-bold text-brand-600 mb-1">4.9</div>
                    <div class="text-sm text-gray-500 font-medium uppercase tracking-wide">Rating</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Destinations Section -->
    <section id="destinations" class="py-20 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-12">
            <h2 class="text-3xl md:text-4xl font-serif font-bold text-gray-900 mb-4">Popular Destinations</h2>
            <div class="w-20 h-1 bg-brand-500 mx-auto rounded-full mb-6"></div>
            <p class="text-gray-600 max-w-2xl mx-auto">Explore our hand-picked selection of the world's most breathtaking locations.</p>
        </div>

        <!-- Filters -->
        <div class="flex flex-wrap justify-center gap-3 mb-12">
            <button onclick="filterDestinations('all')" class="filter-btn active px-6 py-2 rounded-full border border-gray-200 bg-gray-900 text-white hover:bg-gray-800 transition shadow-md" data-filter="all">All</button>
            <button onclick="filterDestinations('nature')" class="filter-btn px-6 py-2 rounded-full border border-gray-200 bg-white text-gray-600 hover:bg-gray-50 hover:border-gray-300 transition" data-filter="nature">Nature</button>
            <button onclick="filterDestinations('city')" class="filter-btn px-6 py-2 rounded-full border border-gray-200 bg-white text-gray-600 hover:bg-gray-50 hover:border-gray-300 transition" data-filter="city">Cities</button>
            <button onclick="filterDestinations('beach')" class="filter-btn px-6 py-2 rounded-full border border-gray-200 bg-white text-gray-600 hover:bg-gray-50 hover:border-gray-300 transition" data-filter="beach">Beaches</button>
        </div>

        <!-- Grid -->
        <div id="destinations-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <!-- Cards will be injected by JS -->
        </div>
    </section>

    <!-- Travel Experiences / Features -->
    <section id="experiences" class="py-20 bg-brand-900 text-white relative overflow-hidden">
        <!-- Abstract Shapes -->
        <div class="absolute top-0 right-0 -mr-20 -mt-20 w-80 h-80 bg-brand-800 rounded-full opacity-50 blur-3xl"></div>
        <div class="absolute bottom-0 left-0 -ml-20 -mb-20 w-80 h-80 bg-brand-500 rounded-full opacity-20 blur-3xl"></div>

        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
            <div class="grid md:grid-cols-2 gap-16 items-center">
                <div>
                    <h2 class="text-3xl md:text-5xl font-serif font-bold mb-6">Travel the way you want</h2>
                    <p class="text-brand-100 text-lg mb-8 leading-relaxed">
                        We believe travel is personal. Whether you're seeking adrenaline-pumping adventures, serene retreats, or cultural immersions, our guides are tailored to your style.
                    </p>
                    
                    <div class="space-y-6">
                        <div class="flex gap-4">
                            <div class="w-12 h-12 rounded-xl bg-brand-800 flex items-center justify-center flex-shrink-0 text-brand-300">
                                <i class="fa-solid fa-compass text-xl"></i>
                            </div>
                            <div>
                                <h3 class="text-xl font-bold mb-1">Expert Guides</h3>
                                <p class="text-brand-200 text-sm">Curated itineraries by locals and travel experts.</p>
                            </div>
                        </div>
                        <div class="flex gap-4">
                            <div class="w-12 h-12 rounded-xl bg-brand-800 flex items-center justify-center flex-shrink-0 text-brand-300">
                                <i class="fa-solid fa-wallet text-xl"></i>
                            </div>
                            <div>
                                <h3 class="text-xl font-bold mb-1">Budget Friendly</h3>
                                <p class="text-brand-200 text-sm">Tips to save money without compromising experience.</p>
                            </div>
                        </div>
                        <div class="flex gap-4">
                            <div class="w-12 h-12 rounded-xl bg-brand-800 flex items-center justify-center flex-shrink-0 text-brand-300">
                                <i class="fa-solid fa-shield-heart text-xl"></i>
                            </div>
                            <div>
                                <h3 class="text-xl font-bold mb-1">Safe Travel</h3>
                                <p class="text-brand-200 text-sm">Verified safety information and emergency contacts.</p>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="relative">
                    <div class="grid grid-cols-2 gap-4">
                        <img src="https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=600&q=80" alt="Travel" class="rounded-2xl shadow-xl transform translate-y-8 object-cover h-64 w-full">
                        <img src="https://images.unsplash.com/photo-1506929562872-bb421503ef21?auto=format&fit=crop&w=600&q=80" alt="Beach" class="rounded-2xl shadow-xl transform -translate-y-8 object-cover h-64 w-full">
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Trip Planner Section -->
    <section id="planner" class="py-20 bg-gray-50">
        <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="bg-white rounded-3xl shadow-xl overflow-hidden">
                <div class="p-8 md:p-12">
                    <div class="text-center mb-10">
                        <span class="text-brand-600 font-bold tracking-wider uppercase text-sm">Start Planning</span>
                        <h2 class="text-3xl md:text-4xl font-serif font-bold text-gray-900 mt-2">Create Your Dream Trip</h2>
                    </div>

                    <form onsubmit="event.preventDefault(); showSuccessMessage();" class="space-y-6">
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">Destination</label>
                                <select class="w-full rounded-lg border-gray-300 bg-gray-50 border p-3 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 outline-none transition">
                                    <option>Select a region</option>
                                    <option>Europe</option>
                                    <option>Asia</option>
                                    <option>North America</option>
                                    <option>South America</option>
                                    <option>Oceania</option>
                                </select>
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">Travel Style</label>
                                <select class="w-full rounded-lg border-gray-300 bg-gray-50 border p-3 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 outline-none transition">
                                    <option>Relaxation</option>
                                    <option>Adventure</option>
                                    <option>Cultural</option>
                                    <option>Family</option>
                                    <option>Romantic</option>
                                </select>
                            </div>
                        </div>
                        
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                             <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">Check-in</label>
                                <input type="date" class="w-full rounded-lg border-gray-300 bg-gray-50 border p-3 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 outline-none transition text-gray-500">
                            </div>
                            <div>
                                <label class="block text-sm font-medium text-gray-700 mb-2">Duration</label>
                                <select class="w-full rounded-lg border-gray-300 bg-gray-50 border p-3 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 outline-none transition">
                                    <option>Weekend (2-3 days)</option>
                                    <option>Week (5-7 days)</option>
                                    <option>Fortnight (14 days)</option>
                                    <option>Month+</option>
                                </select>
                            </div>
                        </div>

                        <div>
                            <label class="block text-sm font-medium text-gray-700 mb-2">Your Email</label>
                            <input type="email" placeholder="john@example.com" class="w-full rounded-lg border-gray-300 bg-gray-50 border p-3 focus:ring-2 focus:ring-brand-500 focus:border-brand-500 outline-none transition">
                        </div>

                        <button type="submit" class="w-full bg-brand-600 hover:bg-brand-700 text-white font-bold py-4 rounded-lg transition duration-300 transform hover:-translate-y-1 shadow-lg shadow-brand-500/30">
                            Get My Free Itinerary
                        </button>
                    </form>
                    
                    <!-- Success Message (Hidden by default) -->
                    <div id="success-message" class="hidden mt-6 bg-green-50 border border-green-200 text-green-700 px-4 py-3 rounded relative text-center">
                        <strong class="font-bold">Success!</strong>
                        <span class="block sm:inline">We're crafting your itinerary. Check your inbox soon!</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Newsletter -->
    <section id="newsletter" class="py-20 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <i class="fa-regular fa-paper-plane text-4xl text-brand-500 mb-4"></i>
        <h2 class="text-3xl font-serif font-bold text-gray-900 mb-4">Join the Adventure</h2>
        <p class="text-gray-600 mb-8 max-w-lg mx-auto">Get exclusive travel tips, hidden gems, and special offers delivered directly to your inbox.</p>
        <div class="flex max-w-md mx-auto">
            <input type="email" placeholder="Enter your email" class="flex-1 appearance-none border border-gray-300 rounded-l-lg py-3 px-4 bg-white text-gray-700 placeholder-gray-400 shadow-sm focus:outline-none focus:ring-2 focus:ring-brand-500 focus:border-transparent">
            <button class="flex-shrink-0 bg-gray-900 hover:bg-gray-800 border-gray-900 hover:border-gray-800 text-sm border-4 text-white py-3 px-6 rounded-r-lg font-medium transition" onclick="alert('Thanks for subscribing! (Demo)')">
                Sign Up
            </button>
        </div>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-white pt-16 pb-8">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
                <div class="col-span-1 md:col-span-1">
                    <div class="flex items-center gap-2 mb-6">
                        <i class="fa-solid fa-earth-americas text-brand-500 text-2xl"></i>
                        <span class="font-serif text-2xl font-bold">Wanderlust</span>
                    </div>
                    <p class="text-gray-400 text-sm leading-relaxed">
                        Inspiring travelers to explore the world's most beautiful destinations since 2023.
                    </p>
                </div>
                <div>
                    <h4 class="text-lg font-bold mb-6">Quick Links</h4>
                    <ul class="space-y-3 text-gray-400 text-sm">
                        <li><a href="#" class="hover:text-brand-400 transition">About Us</a></li>
                        <li><a href="#" class="hover:text-brand-400 transition">Destinations</a></li>
                        <li><a href="#" class="hover:text-brand-400 transition">Travel Guides</a></li>
                        <li><a href="#" class="hover:text-brand-400 transition">Booking</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-lg font-bold mb-6">Support</h4>
                    <ul class="space-y-3 text-gray-400 text-sm">
                        <li><a href="#" class="hover:text-brand-400 transition">Contact Us</a></li>
                        <li><a href="#" class="hover:text-brand-400 transition">FAQ</a></li>
                        <li><a href="#" class="hover:text-brand-400 transition">Privacy Policy</a></li>
                        <li><a href="#" class="hover:text-brand-400 transition">Terms of Service</a></li>
                    </ul>
                </div>
                <div>
                    <h4 class="text-lg font-bold mb-6">Follow Us</h4>
                    <div class="flex space-x-4">
                        <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center hover:bg-brand-600 transition text-white">
                            <i class="fa-brands fa-instagram"></i>
                        </a>
                        <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center hover:bg-brand-600 transition text-white">
                            <i class="fa-brands fa-twitter"></i>
                        </a>
                        <a href="#" class="w-10 h-10 rounded-full bg-gray-800 flex items-center justify-center hover:bg-brand-600 transition text-white">
                            <i class="fa-brands fa-pinterest"></i>
                        </a>
                    </div>
                </div>
            </div>
            <div class="border-t border-gray-800 pt-8 flex flex-col md:flex-row justify-between items-center">
                <p class="text-gray-500 text-sm mb-4 md:mb-0">&copy; 2025 Wanderlust Travel. All rights reserved.</p>
                <div class="text-gray-500 text-sm">
                    Designed for travelers.
                </div>
            </div>
        </div>
    </footer>

    <!-- JavaScript for Logic -->
    <script>
        // Destination Data
        const destinations = [
            {
                id: 1,
                name: "Santorini, Greece",
                category: "beach",
                image: "https://images.unsplash.com/photo-1570077188670-e3a8d69ac5ff?auto=format&fit=crop&w=800&q=80",
                price: "$1,200",
                rating: 4.9,
                desc: "Iconic white buildings with blue domes overlooking the crystal clear Aegean Sea."
            },
            {
                id: 2,
                name: "Banff, Canada",
                category: "nature",
                image: "https://images.unsplash.com/photo-1532274402911-5a369e4c4bb5?auto=format&fit=crop&w=800&q=80",
                price: "$950",
                rating: 4.8,
                desc: "Stunning turquoise lakes and snow-capped peaks in the heart of the Rockies."
            },
            {
                id: 3,
                name: "Kyoto, Japan",
                category: "city",
                image: "https://images.unsplash.com/photo-1493976040374-85c8e12f0c0e?auto=format&fit=crop&w=800&q=80",
                price: "$1,500",
                rating: 5.0,
                desc: "Ancient temples, traditional tea houses, and sublime zen gardens."
            },
            {
                id: 4,
                name: "Machu Picchu, Peru",
                category: "nature",
                image: "https://images.unsplash.com/photo-1587595431973-160d0d94add1?auto=format&fit=crop&w=800&q=80",
                price: "$1,100",
                rating: 4.9,
                desc: "The mysterious Incan citadel set high in the Andes Mountains."
            },
            {
                id: 5,
                name: "New York City, USA",
                category: "city",
                image: "https://images.unsplash.com/photo-1496442226666-8d4d0e62e6e9?auto=format&fit=crop&w=800&q=80",
                price: "$1,300",
                rating: 4.7,
                desc: "The city that never sleeps, featuring Times Square and Central Park."
            },
            {
                id: 6,
                name: "Maldives",
                category: "beach",
                image: "https://images.unsplash.com/photo-1514282401047-d79a71a590e8?auto=format&fit=crop&w=800&q=80",
                price: "$2,200",
                rating: 5.0,
                desc: "Private overwater bungalows surrounded by turquoise lagoons."
            }
        ];

        // Mobile Menu Toggle
        const mobileMenuBtn = document.getElementById('mobile-menu-btn');
        const mobileMenu = document.getElementById('mobile-menu');

        mobileMenuBtn.addEventListener('click', () => {
            mobileMenu.classList.toggle('hidden');
            const icon = mobileMenuBtn.querySelector('i');
            if (mobileMenu.classList.contains('hidden')) {
                icon.classList.remove('fa-xmark');
                icon.classList.add('fa-bars');
            } else {
                icon.classList.remove('fa-bars');
                icon.classList.add('fa-xmark');
            }
        });

        // Navbar Scroll Effect
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('shadow-md');
                navbar.classList.remove('bg-white/90');
                navbar.classList.add('bg-white');
            } else {
                navbar.classList.remove('shadow-md');
                navbar.classList.add('bg-white/90');
                navbar.classList.remove('bg-white');
            }
        });

        // Render Destinations
        function renderDestinations(filter = 'all') {
            const grid = document.getElementById('destinations-grid');
            grid.innerHTML = '';
            
            const filteredData = filter === 'all' 
                ? destinations 
                : destinations.filter(dest => dest.category === filter);

            if(filteredData.length === 0) {
                grid.innerHTML = '<div class="col-span-full text-center text-gray-500 py-10">No destinations found matching your criteria.</div>';
                return;
            }

            filteredData.forEach(dest => {
                const card = document.createElement('div');
                card.className = 'group bg-white rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-300 overflow-hidden border border-gray-100 flex flex-col';
                card.innerHTML = `
                    <div class="relative overflow-hidden h-64 card-zoom cursor-pointer">
                        <img src="${dest.image}" alt="${dest.name}" class="w-full h-full object-cover transition duration-700">
                        <div class="absolute top-4 right-4 bg-white/90 backdrop-blur-sm px-3 py-1 rounded-full text-sm font-bold text-gray-800 shadow-sm">
                            <i class="fa-solid fa-star text-yellow-400 mr-1"></i> ${dest.rating}
                        </div>
                        <div class="absolute bottom-4 left-4">
                           <span class="inline-block px-3 py-1 bg-brand-600 text-white text-xs font-bold uppercase tracking-wider rounded-full">${dest.category}</span>
                        </div>
                    </div>
                    <div class="p-6 flex-1 flex flex-col">
                        <div class="flex justify-between items-start mb-2">
                            <h3 class="text-xl font-bold text-gray-900 group-hover:text-brand-600 transition">${dest.name}</h3>
                        </div>
                        <p class="text-gray-500 text-sm leading-relaxed mb-4 flex-1">${dest.desc}</p>
                        <div class="flex items-center justify-between pt-4 border-t border-gray-100">
                            <div>
                                <p class="text-xs text-gray-400 uppercase">Starting from</p>
                                <p class="text-lg font-bold text-brand-600">${dest.price}</p>
                            </div>
                            <button class="text-brand-600 font-semibold hover:text-brand-800 transition text-sm flex items-center gap-2 group-hover:translate-x-1 duration-300">
                                View Details <i class="fa-solid fa-arrow-right"></i>
                            </button>
                        </div>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        // Filter Function
        function filterDestinations(category) {
            renderDestinations(category);
            
            // Update active button state
            document.querySelectorAll('.filter-btn').forEach(btn => {
                if (btn.dataset.filter === category) {
                    btn.classList.add('bg-gray-900', 'text-white', 'shadow-md');
                    btn.classList.remove('bg-white', 'text-gray-600');
                } else {
                    btn.classList.remove('bg-gray-900', 'text-white', 'shadow-md');
                    btn.classList.add('bg-white', 'text-gray-600');
                }
            });
        }

        // Search Functionality
        const searchInput = document.getElementById('search-input');
        searchInput.addEventListener('input', (e) => {
            const searchTerm = e.target.value.toLowerCase();
            const grid = document.getElementById('destinations-grid');
            grid.innerHTML = '';

            const filteredData = destinations.filter(dest => 
                dest.name.toLowerCase().includes(searchTerm) || 
                dest.desc.toLowerCase().includes(searchTerm) ||
                dest.category.toLowerCase().includes(searchTerm)
            );

            // Reset buttons visual state if searching
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.classList.remove('bg-gray-900', 'text-white');
                btn.classList.add('bg-white', 'text-gray-600');
            });
            // highlight 'All' if search is empty
            if (searchTerm === '') {
                 document.querySelector('.filter-btn[data-filter="all"]').classList.add('bg-gray-900', 'text-white');
                 document.querySelector('.filter-btn[data-filter="all"]').classList.remove('bg-white', 'text-gray-600');
            }

            if(filteredData.length === 0) {
                 grid.innerHTML = '<div class="col-span-full text-center text-gray-500 py-10 flex flex-col items-center"><i class="fa-regular fa-face-frown text-4xl mb-3"></i><p>No destinations found matching "' + e.target.value + '"</p></div>';
            } else {
                filteredData.forEach(dest => {
                    // Logic duplicated for simplicity in this single file approach, 
                    // ideally renderCard() would be a separate helper
                     const card = document.createElement('div');
                    card.className = 'group bg-white rounded-2xl shadow-lg hover:shadow-2xl transition-all duration-300 overflow-hidden border border-gray-100 flex flex-col';
                    card.innerHTML = `
                        <div class="relative overflow-hidden h-64 card-zoom cursor-pointer">
                            <img src="${dest.image}" alt="${dest.name}" class="w-full h-full object-cover transition duration-700">
                            <div class="absolute top-4 right-4 bg-white/90 backdrop-blur-sm px-3 py-1 rounded-full text-sm font-bold text-gray-800 shadow-sm">
                                <i class="fa-solid fa-star text-yellow-400 mr-1"></i> ${dest.rating}
                            </div>
                            <div class="absolute bottom-4 left-4">
                            <span class="inline-block px-3 py-1 bg-brand-600 text-white text-xs font-bold uppercase tracking-wider rounded-full">${dest.category}</span>
                            </div>
                        </div>
                        <div class="p-6 flex-1 flex flex-col">
                            <div class="flex justify-between items-start mb-2">
                                <h3 class="text-xl font-bold text-gray-900 group-hover:text-brand-600 transition">${dest.name}</h3>
                            </div>
                            <p class="text-gray-500 text-sm leading-relaxed mb-4 flex-1">${dest.desc}</p>
                            <div class="flex items-center justify-between pt-4 border-t border-gray-100">
                                <div>
                                    <p class="text-xs text-gray-400 uppercase">Starting from</p>
                                    <p class="text-lg font-bold text-brand-600">${dest.price}</p>
                                </div>
                                <button class="text-brand-600 font-semibold hover:text-brand-800 transition text-sm flex items-center gap-2 group-hover:translate-x-1 duration-300">
                                    View Details <i class="fa-solid fa-arrow-right"></i>
                                </button>
                            </div>
                        </div>
                    `;
                    grid.appendChild(card);
                });
            }
        });

        // Form Success Logic
        function showSuccessMessage() {
            const successMsg = document.getElementById('success-message');
            successMsg.classList.remove('hidden');
            setTimeout(() => {
                successMsg.classList.add('hidden');
            }, 3000);
        }

        // Initialize
        renderDestinations();

    </script>
</body>
</html>
