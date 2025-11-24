<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eklavya - Intelligent Exam Prep</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

    <style>
        body { font-family: 'Inter', sans-serif; }
        .fade-in { animation: fadeIn 0.3s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
        .spin { animation: spin 1s linear infinite; }
        @keyframes spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }
        
        /* Custom Scrollbar */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #c7c7c7; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: #a0a0a0; }
    </style>
</head>
<body class="bg-gray-50 text-gray-900 overflow-x-hidden">

    <!-- Toast Notification Container -->
    <div id="toast-container" class="fixed bottom-6 right-6 z-50 flex flex-col gap-2 pointer-events-none"></div>

    <!-- Main App Container -->
    <div id="app">
        <!-- Content will be injected here by JavaScript -->
        <div class="min-h-screen flex items-center justify-center bg-gray-50">
            <div class="flex flex-col items-center gap-4">
                <div class="w-10 h-10 border-4 border-indigo-600 border-t-transparent rounded-full spin"></div>
                <p class="text-gray-500 font-medium">Initializing AI Environment...</p>
            </div>
        </div>
    </div>

    <!-- Firebase & Application Logic -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInWithCustomToken, signInAnonymously, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, collection, doc, getDoc, setDoc, updateDoc, increment, onSnapshot, addDoc, serverTimestamp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // --- 1. CONFIGURATION ---
        // In a real deployment, these values are injected by the server
        const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';

        let app, auth, db;
        
        // Initialize Firebase safely
        try {
            app = initializeApp(firebaseConfig);
            auth = getAuth(app);
            db = getFirestore(app);
        } catch (e) {
            console.error("Firebase Init Error:", e);
        }

        // --- 2. STATE MANAGEMENT ---
        const state = {
            user: null,
            userData: null,
            view: 'landing', // landing, dashboard, test, processing, result, pricing, library, notes, mentor, howitworks
            activeTest: null,
            testResult: null,
            isAdminMode: false,
            dbQuestions: [],
            chatHistory: [
                { sender: 'ai', text: "Hello Eklavya! I'm your AI UPSC Mentor. I noticed you struggled with 'Economics' in your last test. Shall we review 'Inflation targeting' concepts?" }
            ],
            chatInput: "",
            newQ: { text: '', subject: 'Polity', difficulty: 'Medium', explanation: '', options: ['', '', '', ''], correct: 0 }
        };

        // --- 3. MOCK DATA ---
        const INITIAL_QUESTIONS = [
            { id: 'q1', text: "Which Schedule of the Indian Constitution distributes powers between the Union and the States?", options: ["First Schedule", "Seventh Schedule", "Ninth Schedule", "Tenth Schedule"], correct: 1, subject: "Polity", difficulty: "Medium", explanation: "The Seventh Schedule contains the Union List, State List, and Concurrent List.", source: "Laxmikant Ch. 3" },
            { id: 'q2', text: "Consider the following statements regarding the 'Monetary Policy Committee': 1. It is headed by the Finance Minister. 2. It decides the benchmark interest rates. Which is correct?", options: ["1 only", "2 only", "Both 1 and 2", "Neither 1 nor 2"], correct: 1, subject: "Economics", difficulty: "Hard", explanation: "MPC is headed by the RBI Governor, not the Finance Minister.", source: "The Hindu" },
            { id: 'q3', text: "The term 'West Texas Intermediate' is frequently used in the context of:", options: ["Rare Earth elements", "Crude Oil", "Bullion Market", "Semiconductors"], correct: 1, subject: "Current Affairs", difficulty: "Easy", explanation: "WTI is a grade of crude oil used as a benchmark in oil pricing.", source: "Economic Times" }
        ];
        
        state.dbQuestions = [...INITIAL_QUESTIONS];

        const TESTIMONIALS = [
            { name: "Priya Sharma", rank: "AIR 42", text: "The AI analysis spotted my weakness in Economics immediately.", role: "IAS 2023 Batch" },
            { name: "Rahul Verma", rank: "AIR 105", text: "Finally, a test series that tells you WHY you are wrong.", role: "IPS 2023 Batch" }
        ];

        const PRICING_PLANS = [
            { name: "Starter", price: "$3", period: "/month", features: ["10 Full Mock Tests", "Basic Stats", "Past 3 Years Papers"], color: "blue", recommended: false },
            { name: "Pro aspirant", price: "$9", period: "/month", features: ["Unlimited Tests", "Deep AI Analysis", "Daily Schedule", "Priority Support"], color: "indigo", recommended: true },
            { name: "Elite", price: "$13", period: "/month", features: ["Everything in Pro", "1-on-1 AI Mentor", "Live Doubt Sessions"], color: "purple", recommended: false }
        ];

        const MOCK_NOTES = [
            { id: 1, title: "Anti-Defection Law", date: "2 days ago", tags: ["Polity"], content: "Added by 52nd Amendment, 1985. Decisions made by Speaker/Chairman." },
            { id: 2, title: "Monetary Policy", date: "5 days ago", tags: ["Economy"], content: "Monetary: RBI (Repo, CRR). Fiscal: Govt (Tax, Budget)." }
        ];

        // --- 4. UTILITY FUNCTIONS ---
        
        // Show Toast Notification
        window.showToast = (msg, type = 'info') => {
            const container = document.getElementById('toast-container');
            const toast = document.createElement('div');
            const bgClass = type === 'success' ? 'bg-emerald-600' : type === 'error' ? 'bg-red-600' : 'bg-gray-900';
            toast.className = `pointer-events-auto px-6 py-4 rounded-xl shadow-2xl flex items-center gap-3 text-white ${bgClass} fade-in`;
            toast.innerHTML = `<span class="font-medium">${msg}</span>`;
            container.appendChild(toast);
            setTimeout(() => toast.remove(), 3000);
        };

        // Render Icons
        const refreshIcons = () => {
            if (window.lucide) window.lucide.createIcons();
        };

        // --- 5. RENDER LOGIC (THE ROUTER) ---

        const render = () => {
            const appDiv = document.getElementById('app');
            appDiv.innerHTML = ''; // Clear current view

            switch (state.view) {
                case 'landing':
                    appDiv.innerHTML = renderLandingPage();
                    break;
                case 'dashboard':
                    appDiv.innerHTML = renderDashboard();
                    break;
                case 'test':
                    appDiv.innerHTML = renderTestEngine();
                    break;
                case 'processing':
                    appDiv.innerHTML = renderProcessing();
                    break;
                case 'result':
                    appDiv.innerHTML = renderResultPage();
                    break;
                case 'pricing':
                    appDiv.innerHTML = renderPricingPage();
                    break;
                case 'library':
                    appDiv.innerHTML = renderLibraryPage();
                    break;
                case 'notes':
                    appDiv.innerHTML = renderNotesPage();
                    break;
                case 'mentor':
                    appDiv.innerHTML = renderMentorPage();
                    break;
                case 'howitworks':
                    appDiv.innerHTML = renderHowItWorksPage();
                    break;
                default:
                    appDiv.innerHTML = renderLandingPage();
            }
            refreshIcons();
            attachEventHandlers();
        };

        // --- 6. VIEW GENERATORS (HTML Strings) ---

        const renderLandingPage = () => `
            <div class="min-h-screen bg-white font-sans text-gray-900 flex flex-col">
                <nav class="border-b bg-white/80 backdrop-blur-md sticky top-0 z-50">
                    <div class="flex items-center justify-between px-6 py-4 max-w-7xl mx-auto">
                        <div class="flex items-center gap-2 font-bold text-2xl text-indigo-900 tracking-tight">
                            <div class="bg-indigo-600 text-white p-1.5 rounded-lg"><i data-lucide="brain"></i></div>
                            <span>Eklavya<span class="text-indigo-600">.AI</span></span>
                        </div>
                        <div class="hidden md:flex gap-8 items-center">
                            <button onclick="window.navigate('library')" class="text-gray-600 hover:text-indigo-600 font-medium text-sm">Test Series</button>
                            <button onclick="window.navigate('mentor')" class="text-gray-600 hover:text-indigo-600 font-medium text-sm">AI Mentor</button>
                            <button onclick="window.navigate('pricing')" class="text-gray-600 hover:text-indigo-600 font-medium text-sm">Pricing</button>
                            <button onclick="window.navigate('dashboard')" class="bg-indigo-600 text-white px-4 py-2 rounded-lg font-medium hover:bg-indigo-700 shadow-md transition-all">
                                ${state.user ? "Go to Dashboard" : "Start Free Trial"}
                            </button>
                        </div>
                    </div>
                </nav>

                <main class="flex-1">
                    <section class="pt-20 pb-32 px-6 max-w-7xl mx-auto">
                        <div class="grid lg:grid-cols-2 gap-16 items-center">
                            <div class="space-y-8 fade-in">
                                <span class="bg-blue-100 text-blue-800 border-blue-200 px-4 py-1.5 text-sm font-semibold rounded-full border">Trusted by 10,000+ Aspirants</span>
                                <h1 class="text-5xl md:text-6xl font-extrabold leading-[1.1] tracking-tight text-gray-900">
                                    The Only Test Series That <span class="text-transparent bg-clip-text bg-gradient-to-r from-indigo-600 to-blue-500">Adapts To You.</span>
                                </h1>
                                <p class="text-xl text-gray-600 leading-relaxed max-w-lg">
                                    Don't just take tests. Let our AI analyze your conceptual gaps and build a personalized daily schedule to fix them.
                                </p>
                                <div class="flex flex-col sm:flex-row gap-4">
                                    <button onclick="window.navigate('dashboard')" class="h-14 px-8 text-lg bg-indigo-600 text-white rounded-lg font-medium hover:bg-indigo-700 shadow-lg flex items-center justify-center gap-2 w-full sm:w-auto">
                                        Attempt 3 Free Tests <i data-lucide="arrow-right" size="20"></i>
                                    </button>
                                    <button onclick="window.navigate('howitworks')" class="h-14 px-8 text-lg bg-white text-indigo-700 border border-indigo-200 rounded-lg font-medium hover:bg-indigo-50 flex items-center justify-center gap-2 w-full sm:w-auto">
                                        <i data-lucide="play" size="20"></i> How it Works
                                    </button>
                                </div>
                            </div>
                            <!-- Hero Image Placeholder -->
                            <div class="relative fade-in">
                                <div class="absolute -inset-1 bg-gradient-to-r from-indigo-500 to-purple-500 rounded-2xl blur opacity-20"></div>
                                <div class="relative bg-white rounded-2xl shadow-2xl overflow-hidden border border-gray-100 p-6">
                                     <div class="flex justify-between items-center mb-6">
                                        <h3 class="font-bold text-gray-900">Live Analysis</h3>
                                        <span class="px-2 py-1 bg-green-100 text-green-800 text-xs font-bold rounded">Excellent</span>
                                     </div>
                                     <div class="grid grid-cols-2 gap-4">
                                        <div class="bg-gray-50 p-4 rounded-xl text-center">
                                            <p class="text-xs text-gray-500 uppercase">Score</p>
                                            <p class="text-2xl font-bold text-gray-900">112.5</p>
                                        </div>
                                        <div class="bg-gray-50 p-4 rounded-xl text-center">
                                            <p class="text-xs text-gray-500 uppercase">Accuracy</p>
                                            <p class="text-2xl font-bold text-gray-900">88%</p>
                                        </div>
                                     </div>
                                </div>
                            </div>
                        </div>
                    </section>

                    <section class="py-20 max-w-7xl mx-auto px-6 bg-gray-50 rounded-3xl">
                        <h2 class="text-3xl font-bold text-center mb-16">Results Speak Louder</h2>
                        <div class="grid md:grid-cols-2 gap-8">
                            ${TESTIMONIALS.map(t => `
                                <div class="bg-white p-8 rounded-2xl shadow-lg border border-gray-100 relative">
                                    <p class="text-gray-600 text-lg mb-6 italic">"${t.text}"</p>
                                    <div>
                                        <p class="font-bold text-gray-900">${t.name}</p>
                                        <p class="text-sm text-indigo-600 font-medium">${t.role} • ${t.rank}</p>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                    </section>
                </main>
                
                 <footer class="bg-gray-900 text-gray-400 py-12 px-6 mt-12">
                    <div class="max-w-7xl mx-auto text-center">
                        <div class="text-white font-bold text-xl mb-4">Eklavya</div>
                        <p class="text-sm">Empowering aspirants with data-driven preparation strategies.</p>
                        <div class="border-t border-gray-800 pt-8 mt-8 text-xs">
                            © 2025 Eklavya Technologies. All rights reserved.
                        </div>
                    </div>
                </footer>
            </div>
        `;

        const renderDashboard = () => `
            <div class="min-h-screen bg-gray-50 flex flex-col md:flex-row font-sans">
                <!-- Sidebar -->
                <aside class="w-full md:w-72 bg-white border-r border-gray-200 flex-shrink-0 z-20">
                    <div class="p-6 border-b border-gray-100 flex items-center gap-2 font-bold text-xl text-indigo-900">
                        <div class="bg-indigo-600 text-white p-1 rounded"><i data-lucide="brain"></i></div> Eklavya
                    </div>
                    <nav class="p-4 space-y-1">
                        <button onclick="window.navigate('dashboard')" class="w-full flex items-center gap-3 px-4 py-3 bg-indigo-50 text-indigo-700 rounded-lg font-medium shadow-sm ring-1 ring-indigo-200">
                            <i data-lucide="bar-chart-2" size="20"></i> Dashboard
                        </button>
                        <button onclick="window.navigate('library')" class="w-full flex items-center gap-3 px-4 py-3 text-gray-600 hover:bg-gray-50 rounded-lg font-medium transition-colors">
                            <i data-lucide="layers" size="20"></i> Tests Library
                        </button>
                        <button onclick="window.navigate('notes')" class="w-full flex items-center gap-3 px-4 py-3 text-gray-600 hover:bg-gray-50 rounded-lg font-medium transition-colors">
                            <i data-lucide="book-open" size="20"></i> Saved Notes
                        </button>
                        <div class="pt-4 mt-4 border-t border-gray-100">
                            <button onclick="window.handleLogout()" class="w-full flex items-center gap-3 px-4 py-3 text-red-600 hover:bg-red-50 rounded-lg font-medium transition-colors">
                                <i data-lucide="log-out" size="20"></i> Logout
                            </button>
                        </div>
                        
                        <div class="mt-8 mx-2 bg-indigo-900 text-white rounded-xl p-5 relative overflow-hidden shadow-lg">
                            <div class="relative z-10">
                                <p class="text-indigo-200 text-xs font-bold uppercase tracking-wider mb-2">Free Plan</p>
                                <p class="text-3xl font-bold">${state.userData?.freeTestsRemaining || 0}</p>
                                <p class="text-sm text-indigo-200 mb-3">tests left</p>
                                <button onclick="window.navigate('pricing')" class="w-full text-xs font-bold bg-white text-indigo-900 py-2 rounded-lg hover:bg-indigo-50 transition-colors shadow">Upgrade to Unlimited</button>
                            </div>
                        </div>
                    </nav>
                </aside>

                <!-- Main Content -->
                <main class="flex-1 overflow-y-auto">
                    <header class="bg-white border-b px-8 py-4 flex flex-col md:flex-row justify-between items-center gap-4 sticky top-0 z-10 shadow-sm">
                        <div>
                            <h1 class="text-xl font-bold text-gray-900 flex items-center gap-2">Welcome, ${state.userData?.name || "Aspirant"} 👋</h1>
                        </div>
                        <div class="flex items-center gap-4">
                            <button onclick="window.toggleAdminMode()" class="px-3 py-1.5 border rounded-lg text-sm font-medium hover:bg-gray-50 flex items-center gap-2">
                                <i data-lucide="settings" size="16"></i> ${state.isAdminMode ? "Close Admin" : "Admin Cockpit"}
                            </button>
                            <div class="h-10 w-10 bg-indigo-100 rounded-full flex items-center justify-center text-indigo-700 font-bold border border-indigo-200">
                                ${state.userData?.name?.[0] || "A"}
                            </div>
                        </div>
                    </header>

                    <div class="p-8 max-w-7xl mx-auto space-y-8">
                        
                        <!-- Admin Panel -->
                        ${state.isAdminMode ? `
                            <div class="bg-gray-900 text-white rounded-2xl p-6 shadow-2xl border border-gray-700 fade-in">
                                <div class="flex items-center justify-between mb-6 border-b border-gray-700 pb-4">
                                    <h2 class="text-lg font-bold flex items-center gap-2"><i data-lucide="shield" class="text-red-500"></i> Admin Cockpit</h2>
                                    <span class="px-2 py-0.5 bg-red-100 text-red-800 rounded-full text-xs font-bold">Live Production</span>
                                </div>
                                <div class="grid lg:grid-cols-2 gap-8">
                                    <div class="space-y-4">
                                        <h3 class="font-bold text-gray-300">Add New Question</h3>
                                        <div class="space-y-3">
                                            <textarea id="admin-q-text" class="w-full bg-gray-800 border border-gray-700 rounded-lg p-3 text-sm" placeholder="Enter question text here..."></textarea>
                                            <div class="grid grid-cols-2 gap-3">
                                                <select id="admin-q-sub" class="bg-gray-800 border border-gray-700 rounded-lg p-2 text-sm">
                                                    <option>Polity</option><option>History</option><option>Economics</option>
                                                </select>
                                                <select id="admin-q-diff" class="bg-gray-800 border border-gray-700 rounded-lg p-2 text-sm">
                                                    <option>Medium</option><option>Hard</option><option>Easy</option>
                                                </select>
                                            </div>
                                            <textarea id="admin-q-exp" class="w-full bg-gray-800 border border-gray-700 rounded-lg p-3 text-sm" placeholder="Explanation..."></textarea>
                                            <button onclick="window.handleAddQuestion()" class="w-full bg-indigo-600 hover:bg-indigo-500 py-2 rounded-lg font-medium">Publish Question</button>
                                        </div>
                                    </div>
                                    <div class="bg-gray-800 rounded-xl p-4">
                                        <h3 class="font-bold text-gray-300 mb-4">Stats</h3>
                                        <p class="text-gray-400">Total Questions: ${state.dbQuestions.length}</p>
                                    </div>
                                </div>
                            </div>
                        ` : ''}

                        <!-- Stats Grid -->
                        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                            <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex items-center gap-4">
                                <div class="h-12 w-12 bg-blue-100 text-blue-600 rounded-full flex items-center justify-center"><i data-lucide="check-circle"></i></div>
                                <div><p class="text-sm text-gray-500 font-medium">Tests Attempted</p><p class="text-3xl font-bold text-gray-900">${state.userData?.testsTaken || 0}</p></div>
                            </div>
                            <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100 flex items-center gap-4">
                                <div class="h-12 w-12 bg-purple-100 text-purple-600 rounded-full flex items-center justify-center"><i data-lucide="activity"></i></div>
                                <div><p class="text-sm text-gray-500 font-medium">Avg Accuracy</p><p class="text-3xl font-bold text-gray-900">68%</p></div>
                            </div>
                             <div class="p-6 rounded-xl shadow-lg border-none relative overflow-hidden bg-gradient-to-r from-indigo-600 to-blue-600 text-white flex items-center gap-4">
                                <div class="relative z-10">
                                    <p class="text-indigo-100 font-medium text-sm">Next Milestone</p>
                                    <p class="text-2xl font-bold mt-1">Unlock Pro</p>
                                    <div class="mt-2 text-xs bg-white/20 inline-block px-2 py-1 rounded">Score 95% +</div>
                                </div>
                                <i data-lucide="award" class="absolute -right-4 -bottom-4 text-white/10 w-32 h-32"></i>
                            </div>
                        </div>

                        <!-- Recommendations -->
                        <div class="grid lg:grid-cols-3 gap-8">
                            <div class="lg:col-span-2 space-y-6">
                                <h2 class="text-lg font-bold text-gray-900">Recommended Tests</h2>
                                <div class="grid md:grid-cols-2 gap-5">
                                    <div onclick="window.startTest('GS Full Mock', 120)" class="bg-white rounded-xl border border-gray-200 p-5 hover:border-indigo-300 hover:shadow-lg transition-all cursor-pointer group">
                                        <div class="flex justify-between items-start mb-4">
                                            <span class="px-2.5 py-0.5 rounded-full text-xs font-semibold bg-blue-100 text-blue-800">Full Syllabus</span>
                                            <span class="text-xs text-gray-500 font-mono bg-gray-100 px-2 py-1 rounded">120 MIN</span>
                                        </div>
                                        <h3 class="font-bold text-lg text-gray-900 group-hover:text-indigo-600">UPSC Prelims Simulator I</h3>
                                        <p class="text-sm text-gray-500 mt-2 mb-6">Strict UPSC pattern: 100 Qs, -0.66 Neg Marking.</p>
                                        <span class="text-indigo-600 font-bold text-sm flex items-center gap-1 group-hover:translate-x-1 transition-transform">Start <i data-lucide="chevron-right" size="16"></i></span>
                                    </div>
                                    
                                     <div onclick="window.startTest('2023 PYQ', 120)" class="bg-white rounded-xl border border-gray-200 p-5 hover:border-green-300 hover:shadow-lg transition-all cursor-pointer group">
                                        <div class="flex justify-between items-start mb-4">
                                            <span class="px-2.5 py-0.5 rounded-full text-xs font-semibold bg-green-100 text-green-800">PYQ</span>
                                            <span class="text-xs text-gray-500 font-mono bg-gray-100 px-2 py-1 rounded">2023</span>
                                        </div>
                                        <h3 class="font-bold text-lg text-gray-900 group-hover:text-green-600">CSE Prelims 2023 (GS)</h3>
                                        <p class="text-sm text-gray-500 mt-2 mb-6">Attempt the actual 2023 paper in simulated mode.</p>
                                        <span class="text-green-600 font-bold text-sm flex items-center gap-1 group-hover:translate-x-1 transition-transform">Simulate <i data-lucide="chevron-right" size="16"></i></span>
                                    </div>
                                </div>

                                <div class="bg-gradient-to-br from-gray-900 to-gray-800 text-white rounded-xl p-6 shadow-xl">
                                    <div class="flex items-center gap-3 mb-6">
                                        <div class="bg-indigo-500 p-2 rounded-lg"><i data-lucide="brain" class="text-white"></i></div>
                                        <div><h3 class="font-bold text-lg">AI Tutor Recommendations</h3><p class="text-xs text-indigo-300">Generated based on your last 3 attempts</p></div>
                                    </div>
                                    <div class="space-y-3">
                                        <div class="flex items-center gap-4 bg-white/10 p-3 rounded-lg border border-white/5">
                                            <div class="w-1 h-8 rounded-full bg-indigo-400"></div>
                                            <div class="flex-1"><p class="font-medium text-sm">Revise: Directive Principles (Polity)</p></div>
                                            <div class="text-xs font-mono bg-black/30 px-2 py-1 rounded">30m</div>
                                        </div>
                                    </div>
                                </div>
                            </div>

                            <div class="space-y-6">
                                <div class="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                                    <h3 class="font-bold text-gray-900 mb-4">Topic Strength</h3>
                                    <div class="space-y-4">
                                        <div>
                                            <div class="flex justify-between text-xs mb-1 font-medium text-gray-600"><span>Polity</span><span>75%</span></div>
                                            <div class="w-full bg-gray-100 rounded-full h-2"><div class="h-2 rounded-full bg-green-500" style="width: 75%"></div></div>
                                        </div>
                                        <div>
                                            <div class="flex justify-between text-xs mb-1 font-medium text-gray-600"><span>Economics</span><span>45%</span></div>
                                            <div class="w-full bg-gray-100 rounded-full h-2"><div class="h-2 rounded-full bg-red-500" style="width: 45%"></div></div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </main>
            </div>
        `;

        const renderTestEngine = () => {
            if (!state.activeTest) return '<div>Error: No active test</div>';
            const q = state.activeTest.questions[state.activeTest.currentQ];
            const isSelected = (idx) => state.activeTest.answers[state.activeTest.currentQ] === idx;
            
            return `
            <div class="min-h-screen bg-gray-50 flex flex-col h-screen font-sans">
                <header class="bg-white border-b px-6 py-3 flex items-center justify-between shadow-sm z-10 select-none">
                    <div>
                        <h2 class="font-bold text-lg text-gray-900">${state.activeTest.name}</h2>
                        <div class="flex items-center gap-2 text-xs text-gray-500"><i data-lucide="shield" size="12"></i> Proctoring Active</div>
                    </div>
                    <div class="flex items-center gap-4">
                         <div class="flex items-center gap-2 bg-gray-900 px-4 py-2 rounded-lg text-white font-mono font-bold shadow-lg">
                           <i data-lucide="clock" class="text-red-400" size="18"></i>
                           ${Math.floor(state.activeTest.timeLeft / 60)}:${(state.activeTest.timeLeft % 60).toString().padStart(2, '0')}
                         </div>
                         <button onclick="window.submitTest()" class="bg-red-500 text-white px-4 py-2 rounded-lg font-medium hover:bg-red-600">Submit Test</button>
                    </div>
                </header>
                <div class="flex-1 flex overflow-hidden">
                    <main class="flex-1 overflow-y-auto p-4 md:p-8 bg-gray-50/50">
                        <div class="max-w-4xl mx-auto">
                             <div class="flex items-center justify-between mb-6">
                                <span class="text-sm font-bold text-gray-500 uppercase tracking-wide">Question ${state.activeTest.currentQ + 1} of ${state.activeTest.questions.length}</span>
                                <div class="flex gap-2">
                                  <span class="px-2 py-0.5 rounded text-xs font-semibold bg-green-100 text-green-800">+2.0 Marks</span>
                                  <span class="px-2 py-0.5 rounded text-xs font-semibold bg-red-100 text-red-800">-0.66 Marks</span>
                                </div>
                             </div>
                             <div class="bg-white rounded-2xl shadow-sm border border-gray-200 p-8 mb-6 fade-in">
                                <p class="text-xl font-medium text-gray-900 leading-loose mb-8 font-serif">${q.text}</p>
                                <div class="space-y-3">
                                    ${q.options.map((opt, idx) => `
                                        <button onclick="window.handleAnswer(${idx})" class="w-full text-left p-4 rounded-xl border-2 transition-all flex items-center gap-4 group relative overflow-hidden ${isSelected(idx) ? 'border-indigo-600 bg-indigo-50 shadow-inner' : 'border-gray-200 hover:border-gray-300 hover:bg-gray-50'}">
                                            <div class="w-6 h-6 rounded-full border-2 flex items-center justify-center flex-shrink-0 transition-colors ${isSelected(idx) ? 'border-indigo-600 bg-indigo-600 text-white' : 'border-gray-300 text-gray-400'}">
                                                ${isSelected(idx) ? '<div class="w-2 h-2 bg-white rounded-full"></div>' : ''}
                                            </div>
                                            <span class="${isSelected(idx) ? 'text-indigo-900 font-semibold' : 'text-gray-700'}">${opt}</span>
                                        </button>
                                    `).join('')}
                                </div>
                             </div>
                             <div class="flex items-center justify-between">
                                <button onclick="window.handleAnswer(null)" class="bg-white text-indigo-700 border border-indigo-200 px-4 py-2 rounded-lg font-medium hover:bg-indigo-50">Clear</button>
                                <div class="flex gap-3">
                                    <button onclick="window.navigateTest(-1)" ${state.activeTest.currentQ === 0 ? 'disabled class="opacity-50 cursor-not-allowed border px-4 py-2 rounded-lg"' : 'class="border px-4 py-2 rounded-lg bg-white hover:bg-gray-50"'}>Previous</button>
                                    <button onclick="window.navigateTest(1)" ${state.activeTest.currentQ === state.activeTest.questions.length - 1 ? 'disabled class="opacity-50 cursor-not-allowed bg-indigo-600 text-white px-4 py-2 rounded-lg"' : 'class="bg-indigo-600 text-white px-4 py-2 rounded-lg hover:bg-indigo-700"'}>Save & Next</button>
                                </div>
                             </div>
                        </div>
                    </main>
                    <aside class="w-72 bg-white border-l p-6 hidden lg:flex flex-col">
                        <div class="flex-1 overflow-y-auto">
                            <h3 class="font-bold text-gray-900 mb-4 text-sm uppercase tracking-wider">Question Palette</h3>
                            <div class="grid grid-cols-4 gap-3">
                                ${state.activeTest.questions.map((_, i) => {
                                    const isAnswered = state.activeTest.answers[i] !== undefined && state.activeTest.answers[i] !== null;
                                    const isCurrent = state.activeTest.currentQ === i;
                                    let cls = "bg-white border-gray-200 text-gray-600 hover:border-gray-400";
                                    if(isCurrent) cls = "ring-2 ring-indigo-600 border-indigo-600 text-indigo-700 font-bold";
                                    else if(isAnswered) cls = "bg-green-500 border-green-600 text-white font-bold shadow-sm";
                                    return `<button onclick="window.jumpToQuestion(${i})" class="w-10 h-10 rounded-lg text-sm border flex items-center justify-center transition-all ${cls}">${i+1}</button>`;
                                }).join('')}
                            </div>
                        </div>
                    </aside>
                </div>
            </div>`;
        };

        const renderProcessing = () => `
            <div class="min-h-screen bg-gray-50 flex flex-col items-center justify-center p-6 fade-in">
                <div class="w-full max-w-md bg-white p-8 rounded-2xl shadow-xl border border-indigo-100 text-center">
                    <div class="mx-auto w-20 h-20 bg-indigo-50 rounded-full flex items-center justify-center mb-6 relative">
                        <i data-lucide="brain" class="text-indigo-600 w-10 h-10 animate-pulse"></i>
                        <div class="absolute inset-0 border-4 border-indigo-100 rounded-full border-t-indigo-600 spin"></div>
                    </div>
                    <h2 class="text-xl font-bold text-gray-900 mb-2">Analyzing Performance</h2>
                    <p class="text-gray-500 mb-8 text-sm">Our AI is checking for conceptual gaps...</p>
                </div>
            </div>
        `;

        const renderResultPage = () => {
            if (!state.testResult) return 'Error loading result';
            const res = state.testResult;
            return `
            <div class="min-h-screen bg-gray-50 pb-20">
                <nav class="bg-gray-900 text-white p-4 sticky top-0 z-50 shadow-lg">
                    <div class="max-w-6xl mx-auto flex justify-between items-center">
                        <div class="flex items-center gap-2 font-bold"><i data-lucide="award" class="text-yellow-400"></i> Test Report</div>
                        <button onclick="window.navigate('dashboard')" class="text-sm hover:text-gray-300">Close Report</button>
                    </div>
                </nav>
                <div class="max-w-6xl mx-auto p-6 mt-6 space-y-8 fade-in">
                    <div class="bg-white rounded-xl shadow-sm p-8 text-center md:text-left flex flex-col md:flex-row items-center gap-8">
                         <div class="relative w-40 h-40 flex-shrink-0">
                             <!-- Simple circle rep -->
                             <div class="w-40 h-40 rounded-full border-8 border-indigo-100 flex items-center justify-center border-t-indigo-600 transform -rotate-45">
                                 <div class="text-center transform rotate-45">
                                     <span class="text-4xl font-extrabold text-gray-900 block">${res.score}</span>
                                     <span class="text-sm text-gray-400">/ ${res.maxScore}</span>
                                 </div>
                             </div>
                         </div>
                         <div class="flex-1">
                             <span class="inline-block bg-indigo-50 text-indigo-700 px-3 py-1 rounded-full text-xs font-bold mb-3 uppercase">AI Insight</span>
                             <h2 class="text-2xl font-bold text-gray-900 mb-2">${res.score > 90 ? "Excellent Performance!" : "Good Attempt, Keep Improving"}</h2>
                             <p class="text-gray-600 max-w-xl">${res.aiAdvice}</p>
                         </div>
                    </div>
                    <div class="bg-indigo-900 rounded-2xl p-8 text-white shadow-xl relative overflow-hidden">
                        <h3 class="text-xl font-bold mb-6 flex items-center gap-2"><i data-lucide="brain" class="text-yellow-400"></i> AI Recommended Plan</h3>
                        <div class="grid md:grid-cols-3 gap-6 relative z-10">
                            ${res.studyPlan.map(step => `
                                <div class="bg-white/10 p-5 rounded-xl border border-white/10">
                                    <div class="text-indigo-300 text-xs font-bold uppercase mb-2">${step.day} • ${step.type}</div>
                                    <p class="font-medium">${step.task}</p>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                </div>
            </div>`;
        };

        const renderLibraryPage = () => {
            return `
            <div class="min-h-screen bg-gray-50 font-sans">
                <nav class="bg-white border-b px-6 py-4 flex items-center justify-between sticky top-0 z-50">
                    <div class="flex items-center gap-3">
                        <button onclick="window.navigate('dashboard')" class="p-2 hover:bg-gray-100 rounded-lg text-gray-600"><i data-lucide="chevron-left"></i></button>
                        <h1 class="text-xl font-bold text-gray-900">Test Library</h1>
                    </div>
                </nav>
                <div class="max-w-7xl mx-auto p-8 grid md:grid-cols-3 gap-6">
                    ${[1,2,3,4,5,6].map(i => `
                         <div onclick="window.startTest('Mock Test ${i}', 60)" class="bg-white rounded-xl border border-gray-200 p-5 hover:shadow-lg transition-shadow cursor-pointer">
                            <div class="flex justify-between items-start mb-4">
                                <span class="bg-blue-100 text-blue-800 px-2 py-0.5 rounded text-xs font-bold">Mock</span>
                                <span class="text-xs text-gray-500 bg-gray-100 px-2 py-1 rounded">60 MIN</span>
                            </div>
                            <h3 class="font-bold text-lg text-gray-900">UPSC GS Mock #${i}</h3>
                            <p class="text-sm text-gray-500 mt-2 mb-4">Focus areas: Polity, Governance.</p>
                            <span class="text-indigo-600 font-bold text-sm">Start Test</span>
                        </div>
                    `).join('')}
                </div>
            </div>`;
        };
        
        const renderPricingPage = () => `
             <div class="min-h-screen bg-gray-50 font-sans">
                <nav class="bg-white border-b px-6 py-4 flex items-center justify-between sticky top-0 z-50">
                    <div class="flex items-center gap-3">
                        <button onclick="window.navigate('dashboard')" class="p-2 hover:bg-gray-100 rounded-lg text-gray-600"><i data-lucide="chevron-left"></i></button>
                        <h1 class="text-xl font-bold text-gray-900">Plans</h1>
                    </div>
                </nav>
                <div class="max-w-7xl mx-auto p-8 text-center">
                    <div class="grid md:grid-cols-3 gap-8 max-w-6xl mx-auto">
                        ${PRICING_PLANS.map(p => `
                            <div class="bg-white rounded-2xl shadow-xl p-8 border-2 ${p.recommended ? 'border-indigo-600' : 'border-transparent'}">
                                ${p.recommended ? '<div class="text-indigo-600 font-bold uppercase text-xs mb-2">Most Popular</div>' : ''}
                                <h3 class="text-xl font-bold text-gray-900 mb-2">${p.name}</h3>
                                <div class="flex items-center justify-center mb-6"><span class="text-4xl font-extrabold">${p.price}</span><span class="text-gray-500 ml-2">${p.period}</span></div>
                                <button class="w-full mb-8 bg-indigo-600 text-white py-2 rounded-lg font-bold">Choose Plan</button>
                                <ul class="space-y-4 text-left">
                                    ${p.features.map(f => `<li class="flex items-center gap-3 text-sm text-gray-700"><i data-lucide="check-circle" class="text-green-500" size="16"></i> ${f}</li>`).join('')}
                                </ul>
                            </div>
                        `).join('')}
                    </div>
                </div>
             </div>
        `;

        const renderMentorPage = () => `
            <div class="min-h-screen bg-gray-50 font-sans flex flex-col h-screen">
                <nav class="bg-white border-b px-6 py-4 flex items-center justify-between flex-shrink-0">
                    <div class="flex items-center gap-3">
                        <button onclick="window.navigate('dashboard')" class="p-2 hover:bg-gray-100 rounded-lg text-gray-600"><i data-lucide="chevron-left"></i></button>
                        <h1 class="text-xl font-bold text-gray-900">AI Personal Mentor</h1>
                    </div>
                </nav>
                <div class="flex-1 max-w-4xl w-full mx-auto p-4 flex flex-col overflow-hidden">
                    <div class="flex-1 bg-white rounded-2xl shadow-sm border border-gray-200 overflow-hidden flex flex-col">
                        <div id="chat-box" class="flex-1 p-6 overflow-y-auto space-y-6 bg-gray-50/50">
                            ${state.chatHistory.map(msg => `
                                <div class="flex ${msg.sender === 'user' ? 'justify-end' : 'justify-start'}">
                                    <div class="max-w-[80%] p-4 rounded-2xl shadow-sm ${msg.sender === 'user' ? 'bg-indigo-600 text-white rounded-tr-none' : 'bg-white border border-gray-200 text-gray-800 rounded-tl-none'}">
                                        ${msg.sender === 'ai' ? '<div class="flex items-center gap-2 mb-2 text-xs font-bold text-indigo-600"><i data-lucide="brain" size="12"></i> AI MENTOR</div>' : ''}
                                        <p class="leading-relaxed">${msg.text}</p>
                                    </div>
                                </div>
                            `).join('')}
                        </div>
                        <div class="p-4 bg-white border-t">
                            <form onsubmit="window.handleChatSubmit(event)" class="flex gap-2">
                                <input id="chat-input" type="text" placeholder="Ask doubt..." class="flex-1 bg-gray-100 border-0 rounded-xl px-4 py-3 focus:ring-2 focus:ring-indigo-500 focus:bg-white outline-none">
                                <button type="submit" class="bg-indigo-600 text-white px-4 rounded-xl hover:bg-indigo-700"><i data-lucide="arrow-right"></i></button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        `;

        const renderNotesPage = () => `
             <div class="min-h-screen bg-gray-50 font-sans">
                <nav class="bg-white border-b px-6 py-4 flex items-center justify-between sticky top-0 z-50">
                    <div class="flex items-center gap-3">
                        <button onclick="window.navigate('dashboard')" class="p-2 hover:bg-gray-100 rounded-lg text-gray-600"><i data-lucide="chevron-left"></i></button>
                        <h1 class="text-xl font-bold text-gray-900">Saved Notes</h1>
                    </div>
                </nav>
                <div class="max-w-5xl mx-auto p-8 grid gap-6">
                    ${MOCK_NOTES.map(n => `
                        <div class="bg-white p-6 rounded-xl border border-gray-200 shadow-sm">
                            <h3 class="font-bold text-lg text-gray-900 mb-2">${n.title}</h3>
                            <p class="text-gray-700 bg-yellow-50 p-4 rounded-lg border border-yellow-100 font-serif">${n.content}</p>
                        </div>
                    `).join('')}
                </div>
             </div>
        `;

        const renderHowItWorksPage = () => `
            <div class="min-h-screen bg-white font-sans">
                 <nav class="bg-white border-b px-6 py-4 flex items-center justify-between sticky top-0 z-50">
                    <div class="flex items-center gap-3">
                        <button onclick="window.navigate('landing')" class="p-2 hover:bg-gray-100 rounded-lg text-gray-600"><i data-lucide="chevron-left"></i></button>
                        <h1 class="text-xl font-bold text-gray-900">How It Works</h1>
                    </div>
                </nav>
                <div class="max-w-4xl mx-auto p-12 text-center">
                    <h2 class="text-4xl font-extrabold text-gray-900 mb-6">Master UPSC in 4 Steps</h2>
                    <div class="space-y-12 text-left">
                        <div class="flex gap-4">
                            <div class="w-12 h-12 rounded-full bg-indigo-600 text-white flex items-center justify-center font-bold text-xl flex-shrink-0">1</div>
                            <div><h3 class="text-xl font-bold">Diagnostic Test</h3><p>Take a test so AI can learn your patterns.</p></div>
                        </div>
                        <div class="flex gap-4">
                             <div class="w-12 h-12 rounded-full bg-indigo-600 text-white flex items-center justify-center font-bold text-xl flex-shrink-0">2</div>
                            <div><h3 class="text-xl font-bold">AI Analysis</h3><p>We find conceptual gaps down to micro-topics.</p></div>
                        </div>
                         <div class="flex gap-4">
                             <div class="w-12 h-12 rounded-full bg-indigo-600 text-white flex items-center justify-center font-bold text-xl flex-shrink-0">3</div>
                            <div><h3 class="text-xl font-bold">Daily Plan</h3><p>Get a custom schedule every morning.</p></div>
                        </div>
                    </div>
                     <button onclick="window.navigate('dashboard')" class="mt-12 px-8 py-3 bg-indigo-600 text-white rounded-lg font-bold text-lg">Start Now</button>
                </div>
            </div>
        `;

        // --- 7. GLOBAL ACTIONS (Attached to Window) ---

        window.navigate = (viewName) => {
            state.view = viewName;
            render();
        };

        window.toggleAdminMode = () => {
            state.isAdminMode = !state.isAdminMode;
            render();
        };

        window.handleLogout = async () => {
            await signOut(auth);
            state.user = null;
            state.userData = null;
            window.navigate('landing');
            window.showToast("Logged out successfully");
        };

        window.startTest = (name, duration) => {
            if (!state.userData) {
                if(!state.user) {
                     window.showToast("Please login first", "error");
                     return;
                }
                // wait for profile
                return;
            }
            if (state.userData.freeTestsRemaining <= 0 && state.userData.role !== 'admin') {
                window.showToast("No free tests left! Upgrade to continue.", "error");
                return;
            }

            state.activeTest = {
                name,
                duration,
                questions: [...state.dbQuestions], // clone
                answers: {},
                currentQ: 0,
                timeLeft: duration * 60
            };

            // Deduct test
            if (state.userData.role !== 'admin') {
                const userRef = doc(db, 'artifacts', appId, 'users', state.user.uid, 'profile', 'main');
                updateDoc(userRef, { freeTestsRemaining: increment(-1) });
                state.userData.freeTestsRemaining--; // Optimistic update
            }

            window.navigate('test');
            // Start Timer
            if (window.testTimer) clearInterval(window.testTimer);
            window.testTimer = setInterval(() => {
                if (state.activeTest && state.activeTest.timeLeft > 0) {
                    state.activeTest.timeLeft--;
                    // Update timer DOM directly for performance instead of full re-render
                    const timerEl = document.querySelector('header .font-mono');
                    if(timerEl) {
                        const m = Math.floor(state.activeTest.timeLeft / 60);
                        const s = (state.activeTest.timeLeft % 60).toString().padStart(2, '0');
                        timerEl.innerHTML = `<i data-lucide="clock" class="text-red-400 inline mr-1" size="18"></i> ${m}:${s}`;
                        refreshIcons();
                    }
                } else if (state.activeTest && state.activeTest.timeLeft === 0) {
                    window.submitTest();
                }
            }, 1000);
        };

        window.handleAnswer = (idx) => {
            if (!state.activeTest) return;
            state.activeTest.answers[state.activeTest.currentQ] = idx;
            render(); // Re-render to update UI selection
        };

        window.navigateTest = (dir) => {
            if (!state.activeTest) return;
            state.activeTest.currentQ += dir;
            render();
        };

        window.jumpToQuestion = (idx) => {
             if (!state.activeTest) return;
             state.activeTest.currentQ = idx;
             render();
        };

        window.submitTest = async () => {
            if (window.testTimer) clearInterval(window.testTimer);
            window.navigate('processing');

            // Simulate AI Delay
            await new Promise(r => setTimeout(r, 2000));

            // Logic from React version
            const answers = state.activeTest.answers;
            let correct = 0, incorrect = 0;
            state.activeTest.questions.forEach((q, i) => {
                const a = answers[i];
                if (a === q.correct) correct++;
                else if (a !== undefined && a !== null) incorrect++;
            });
            
            const score = Math.max(0, (correct * 2) - (incorrect * 0.66)).toFixed(2);
            const percentage = (score / (state.activeTest.questions.length * 2)) * 100;

            // AI Advice
            let advice = "Needs Improvement.";
            if (percentage > 90) advice = "Exceptional! Ready for Prelims.";
            else if (percentage > 50) advice = "Good effort. Focus on weak areas.";

            // Study Plan
            const plan = [
                { day: "Tomorrow", type: "Concept", task: "Revise Fundamental Rights" },
                { day: "Day 2", type: "Practice", task: "Attempt 20 Polity MCQs" }
            ];

            state.testResult = {
                score,
                maxScore: state.activeTest.questions.length * 2,
                accuracy: ((correct / (correct + incorrect || 1)) * 100).toFixed(0),
                aiAdvice: advice,
                studyPlan: plan,
                incorrectCount: incorrect
            };

            // 95% Rule
            if (percentage >= 95) {
                 const userRef = doc(db, 'artifacts', appId, 'users', state.user.uid, 'profile', 'main');
                 updateDoc(userRef, { freeTestsRemaining: increment(3) });
                 window.showToast("🎉 95% Score! 3 FREE Tests Unlocked!", "success");
            }

            // Save Attempt
            try {
                 await addDoc(collection(db, 'artifacts', appId, 'users', state.user.uid, 'attempts'), {
                     score, date: serverTimestamp()
                 });
                 // Update local stats
                 state.userData.testsTaken = (state.userData.testsTaken || 0) + 1;
            } catch(e) { console.error(e); }

            state.activeTest = null;
            window.navigate('result');
        };

        window.handleChatSubmit = (e) => {
            e.preventDefault();
            const input = document.getElementById('chat-input');
            const text = input.value;
            if(!text) return;
            
            state.chatHistory.push({ sender: 'user', text });
            input.value = '';
            render(); // Update chat UI

            // AI Response
            setTimeout(() => {
                state.chatHistory.push({ sender: 'ai', text: "That's an interesting point. Let's break down the concept of 'Judicial Review' further..." });
                render();
                const box = document.getElementById('chat-box');
                if(box) box.scrollTop = box.scrollHeight;
            }, 1000);
        };

        window.handleAddQuestion = () => {
             const text = document.getElementById('admin-q-text').value;
             if(!text) return alert("Text required");
             state.dbQuestions.push({
                 id: Date.now(),
                 text,
                 options: ["Opt 1", "Opt 2", "Opt 3", "Opt 4"], // Simplified for HTML demo
                 correct: 0,
                 subject: document.getElementById('admin-q-sub').value,
                 difficulty: document.getElementById('admin-q-diff').value
             });
             window.showToast("Question Added");
             render();
        };

        const attachEventHandlers = () => {
            // Re-run icons
            refreshIcons();
        };

        // --- 8. INITIALIZATION ---
        const init = async () => {
            if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                 await signInWithCustomToken(auth, __initial_auth_token);
            } else {
                 await signInAnonymously(auth);
            }
            
            onAuthStateChanged(auth, (u) => {
                state.user = u;
                if (u) {
                    const userRef = doc(db, 'artifacts', appId, 'users', u.uid, 'profile', 'main');
                    onSnapshot(userRef, (snap) => {
                        if (snap.exists()) {
                            state.userData = snap.data();
                        } else {
                            // Create profile
                            const profile = { name: "Eklavya", freeTestsRemaining: 3, testsTaken: 0, role: 'student' };
                            setDoc(userRef, profile);
                            state.userData = profile;
                        }
                        // Only render if still on landing or initial load to avoid disrupting user
                        if(!document.getElementById('app').innerHTML.includes('Welcome')) {
                           render();
                        }
                    });
                } else {
                    render();
                }
            });
        };

        init();

    </script>
</body>
</html>
