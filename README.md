 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Seller Portal | The Beauty Bond</title>
    
    <!-- Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">
    <!-- Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">

    <style>
        :root {
            --primary: #B76E79; /* Rose Gold */
            --primary-hover: #9c5d67;
            --bg-pastel: #FAF6F5;
            --white: #FFFFFF;
            --text-dark: #333333;
            --text-light: #777777;
            --glass-bg: rgba(255, 255, 255, 0.7);
            --glass-border: rgba(255, 255, 255, 0.3);
            --shadow: 0 8px 32px 0 rgba(183, 110, 121, 0.15);
            --transition: all 0.3s ease;
            --sidebar-width: 260px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background-color: var(--bg-pastel);
            color: var(--text-dark);
            display: flex;
            min-height: 100vh;
            overflow-x: hidden;
        }

        h1, h2, h3, .brand-font {
            font-family: 'Playfair Display', serif;
        }

        /* Glassmorphism Classes */
        .glass {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            box-shadow: var(--shadow);
            border-radius: 15px;
        }

        /* Sidebar */
        .sidebar {
            width: var(--sidebar-width);
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            border-right: 1px solid var(--glass-border);
            padding: 2rem 1.5rem;
            display: flex;
            flex-direction: column;
            position: fixed;
            height: 100vh;
            z-index: 100;
            transition: var(--transition);
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 3rem;
        }

        .nav-menu {
            list-style: none;
            flex: 1;
        }

        .nav-item {
            margin-bottom: 10px;
        }

        .nav-link {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 12px 15px;
            color: var(--text-dark);
            text-decoration: none;
            border-radius: 10px;
            transition: var(--transition);
            font-weight: 500;
            cursor: pointer;
        }

        .nav-link:hover, .nav-link.active {
            background: var(--primary);
            color: var(--white);
            box-shadow: 0 4px 15px rgba(183, 110, 121, 0.3);
        }

        /* Main Content */
        .main-content {
            margin-left: var(--sidebar-width);
            flex: 1;
            padding: 2rem 3rem;
            width: calc(100% - var(--sidebar-width));
        }

        .topbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .user-profile {
            display: flex;
            align-items: center;
            gap: 15px;
            background: var(--white);
            padding: 8px 20px;
            border-radius: 30px;
            box-shadow: var(--shadow);
        }

        .user-profile img {
            width: 35px;
            height: 35px;
            border-radius: 50%;
            object-fit: cover;
        }

        /* Views */
        .view-section {
            display: none;
            animation: fadeIn 0.5s ease-in-out;
        }
        .view-section.active { display: block; }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Dashboard Cards */
        .dashboard-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 2rem;
        }

        .stat-card {
            padding: 1.5rem;
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .stat-icon {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: rgba(183, 110, 121, 0.1);
            color: var(--primary);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.5rem;
        }

        .stat-details h3 { font-size: 1.8rem; color: var(--text-dark); }
        .stat-details p { color: var(--text-light); font-size: 0.9rem; }

        /* Forms & Tables */
        .form-container { padding: 2rem; max-width: 800px; margin: 0 auto; }
        
        .form-group { margin-bottom: 1.5rem; }
        .form-group label { display: block; margin-bottom: 8px; font-weight: 500; font-size: 0.9rem; }
        .form-control {
            width: 100%; padding: 12px 15px;
            border: 1px solid var(--glass-border);
            border-radius: 8px; outline: none;
            background: rgba(255, 255, 255, 0.5);
            transition: var(--transition);
            font-family: inherit;
        }
        .form-control:focus { border-color: var(--primary); background: var(--white); box-shadow: 0 0 0 3px rgba(183,110,121,0.1); }
        
        .btn {
            padding: 12px 25px; border: none; border-radius: 30px;
            cursor: pointer; font-weight: 500; transition: var(--transition);
        }
        .btn-primary { background: var(--primary); color: white; }
        .btn-primary:hover { background: var(--primary-hover); transform: translateY(-2px); box-shadow: var(--shadow); }
        .btn-sm { padding: 6px 15px; font-size: 0.8rem; }
        .btn-success { background: #4CAF50; color: white; }

        .table-wrapper { overflow-x: auto; padding: 1rem; }
        table { width: 100%; border-collapse: collapse; text-align: left; }
        th, td { padding: 15px; border-bottom: 1px solid rgba(0,0,0,0.05); }
        th { color: var(--text-light); font-weight: 500; }
        .status-badge {
            padding: 5px 12px; border-radius: 20px; font-size: 0.8rem; font-weight: 500;
        }
        .status-pending { background: #FFF3E0; color: #FF9800; }
        .status-ready { background: #E3F2FD; color: #2196F3; }
        .status-delivered { background: #E8F5E9; color: #4CAF50; }

        /* Auth Modal */
        .modal {
            display: flex; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(250, 246, 245, 0.9); backdrop-filter: blur(5px);
            z-index: 2000; justify-content: center; align-items: center;
        }
        .modal.hidden { display: none; }
        .modal-content { padding: 2.5rem; max-width: 400px; width: 90%; text-align: center; }

        /* Toast */
        .toast {
            position: fixed; bottom: 20px; right: 20px;
            background: var(--text-dark); color: white; padding: 12px 25px;
            border-radius: 8px; z-index: 3000; display: none; box-shadow: var(--shadow);
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        @media (max-width: 768px) {
            .sidebar { transform: translateX(-100%); }
            .sidebar.open { transform: translateX(0); box-shadow: var(--shadow); }
            .main-content { margin-left: 0; width: 100%; padding: 1rem; }
            .mobile-toggle { display: block; font-size: 1.5rem; color: var(--primary); }
        }
        .mobile-toggle { display: none; cursor: pointer; }
    </style>
</head>
<body>

    <!-- Auth Modal Overlay -->
    <div class="modal" id="auth-modal">
        <div class="modal-content glass">
            <h2 class="brand-font" style="color:var(--primary); margin-bottom: 10px;">Seller Portal</h2>
            <p style="margin-bottom: 20px; color:var(--text-light); font-size:0.9rem;">Sign in to manage your beauty empire.</p>
            
            <div class="form-group">
                <input type="email" id="auth-email" class="form-control" placeholder="Email Address">
            </div>
            <div class="form-group">
                <input type="password" id="auth-password" class="form-control" placeholder="Password">
            </div>
            <button class="btn btn-primary" style="width:100%; margin-bottom: 15px;" onclick="sellerApp.login()">Access Dashboard</button>
            <p style="font-size:0.85rem; color:var(--text-light);">Authorized Sellers Only.</p>
        </div>
    </div>

    <!-- Sidebar -->
    <aside class="sidebar" id="sidebar">
        <a href="#" class="logo brand-font">
            <i class="fa-solid fa-gem"></i> Beauty Bond
        </a>
        <ul class="nav-menu">
            <li class="nav-item">
                <a class="nav-link active" onclick="sellerApp.switchTab('dashboard')">
                    <i class="fa-solid fa-chart-pie"></i> Dashboard
                </a>
            </li>
            <li class="nav-item">
                <a class="nav-link" onclick="sellerApp.switchTab('add-product')">
                    <i class="fa-solid fa-plus-circle"></i> Add Product
                </a>
            </li>
            <li class="nav-item">
                <a class="nav-link" onclick="sellerApp.switchTab('orders')">
                    <i class="fa-solid fa-box-open"></i> Order Management
                </a>
            </li>
        </ul>
        <div style="margin-top: auto;">
            <a class="nav-link" style="color: #ff4d4d;" onclick="sellerApp.logout()">
                <i class="fa-solid fa-sign-out-alt"></i> Logout
            </a>
        </div>
    </aside>

    <!-- Main Content -->
    <main class="main-content">
        <div class="topbar">
            <i class="fa-solid fa-bars mobile-toggle" onclick="document.getElementById('sidebar').classList.toggle('open')"></i>
            <h2 class="brand-font" id="page-title">Dashboard</h2>
            <div class="user-profile">
                <span id="seller-email" style="font-size: 0.9rem; font-weight:500;">Seller</span>
                <img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?q=80&w=150&auto=format&fit=crop" alt="Profile">
            </div>
        </div>

        <!-- Dashboard View -->
        <div id="dashboard-view" class="view-section active">
            <div class="dashboard-grid">
                <div class="stat-card glass">
                    <div class="stat-icon"><i class="fa-solid fa-wallet"></i></div>
                    <div class="stat-details">
                        <p>Total Earnings</p>
                        <h3 class="brand-font" id="stat-earnings">$0.00</h3>
                    </div>
                </div>
                <div class="stat-card glass">
                    <div class="stat-icon"><i class="fa-solid fa-box"></i></div>
                    <div class="stat-details">
                        <p>Pending Orders</p>
                        <h3 class="brand-font" id="stat-pending">0</h3>
                    </div>
                </div>
                <div class="stat-card glass">
                    <div class="stat-icon"><i class="fa-solid fa-check-circle"></i></div>
                    <div class="stat-details">
                        <p>Ready/Shipped</p>
                        <h3 class="brand-font" id="stat-ready">0</h3>
                    </div>
                </div>
            </div>

            <h3 class="brand-font" style="margin: 2rem 0 1rem;">Recent Activity</h3>
            <div class="glass table-wrapper">
                <table>
                    <thead>
                        <tr>
                            <th>Order ID</th>
                            <th>Amount</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody id="recent-activity-list">
                        <tr><td colspan="3" style="text-align:center;">Loading...</td></tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- Add Product View -->
        <div id="add-product-view" class="view-section">
            <div class="glass form-container">
                <h3 class="brand-font" style="margin-bottom: 1.5rem; text-align:center;">Create New Product listing</h3>
                
                <div class="form-group">
                    <label>Product Name</label>
                    <input type="text" id="prod-name" class="form-control" placeholder="e.g. Luminous Silk Foundation">
                </div>
                
                <div style="display:flex; gap:20px;">
                    <div class="form-group" style="flex:1;">
                        <label>Price ($)</label>
                        <input type="number" id="prod-price" class="form-control" placeholder="0.00" step="0.01">
                    </div>
                    <div class="form-group" style="flex:1;">
                        <label>Category</label>
                        <select id="prod-cat" class="form-control">
                            <option value="Makeup">Makeup</option>
                            <option value="Skincare">Skincare</option>
                            <option value="Fragrance">Fragrance</option>
                            <option value="Accessories">Accessories</option>
                        </select>
                    </div>
                </div>

                <div class="form-group">
                    <label>Image URL (High-Quality)</label>
                    <input type="url" id="prod-img" class="form-control" placeholder="https://images.unsplash.com/photo-...">
                </div>

                <div class="form-group">
                    <label>Product Description</label>
                    <textarea id="prod-desc" class="form-control" rows="4" placeholder="Describe the premium qualities of this product..."></textarea>
                </div>

                <button class="btn btn-primary" style="width:100%;" onclick="sellerApp.addProduct()">List Product</button>
            </div>
        </div>

        <!-- Orders Management View -->
        <div id="orders-view" class="view-section">
            <div class="glass table-wrapper">
                <h3 class="brand-font" style="margin-bottom: 1rem;">Customer Orders</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Order ID</th>
                            <th>Customer Address</th>
                            <th>Items</th>
                            <th>Total</th>
                            <th>Status</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody id="orders-table-body">
                        <tr><td colspan="6" style="text-align:center;">Loading orders...</td></tr>
                    </tbody>
                </table>
            </div>
        </div>
    </main>

    <!-- Toast Notification -->
    <div class="toast" id="toast">Notification</div>

    <!-- FIREBASE & LOGIC SCRIPT -->
    <script type="module">
        // Import Firebase V9 Modular SDK
        import { initializeApp } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-app.js";
        import { getAuth, signInWithEmailAndPassword, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-auth.js";
        import { getFirestore, collection, addDoc, getDocs, updateDoc, doc, query, orderBy, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.8.1/firebase-firestore.js";

        // EXACT Configuration provided
        const firebaseConfig = {
            apiKey: "AIzaSyDXpODNoKhq2f_7_5e7W35Ozmq9fzJ9_0E",
            authDomain: "the-beauty-bond-shop.firebaseapp.com",
            databaseURL: "https://the-beauty-bond-shop-default-rtdb.firebaseio.com",
            projectId: "the-beauty-bond-shop",
            storageBucket: "the-beauty-bond-shop.firebasestorage.app",
            messagingSenderId: "524828448767",
            appId: "1:524828448767:web:4eda37ff961d762830b9ca",
            measurementId: "G-6FQWPCC786"
        };

        // Initialize Firebase
        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);

        const AppState = {
            user: null,
            orders: []
        };

        window.sellerApp = {
            showToast: (msg) => {
                const t = document.getElementById('toast');
                t.innerText = msg;
                t.style.display = 'block';
                setTimeout(() => t.style.display = 'none', 3000);
            },

            switchTab: (tabId) => {
                // Update UI Views
                document.querySelectorAll('.view-section').forEach(el => el.classList.remove('active'));
                document.getElementById(`${tabId}-view`).classList.add('active');
                
                // Update Nav Active State
                document.querySelectorAll('.nav-link').forEach(el => el.classList.remove('active'));
                event.currentTarget.classList.add('active');

                // Update Title
                const titles = {
                    'dashboard': 'Dashboard Overview',
                    'add-product': 'Add New Product',
                    'orders': 'Order Management'
                };
                document.getElementById('page-title').innerText = titles[tabId];

                // Close mobile sidebar if open
                document.getElementById('sidebar').classList.remove('open');

                if(tabId === 'dashboard' || tabId === 'orders') {
                    sellerApp.fetchOrders();
                }
            },

            // --- Authentication ---
            login: async () => {
                const email = document.getElementById('auth-email').value;
                const pass = document.getElementById('auth-password').value;
                if(!email || !pass) return sellerApp.showToast("Enter email and password");

                try {
                    await signInWithEmailAndPassword(auth, email, pass);
                    sellerApp.showToast("Welcome to the Seller Portal");
                } catch (error) {
                    sellerApp.showToast("Login Failed: " + error.message);
                }
            },

            logout: async () => {
                await signOut(auth);
                sellerApp.showToast("Logged out successfully");
            },

            // --- Product Management ---
            addProduct: async () => {
                const name = document.getElementById('prod-name').value;
                const price = parseFloat(document.getElementById('prod-price').value);
                const category = document.getElementById('prod-cat').value;
                const img = document.getElementById('prod-img').value;
                const desc = document.getElementById('prod-desc').value;

                if(!name || !price || !img) return sellerApp.showToast("Please fill required fields (Name, Price, Image)");

                try {
                    await addDoc(collection(db, "products"), {
                        name,
                        price,
                        category,
                        img,
                        description: desc,
                        sellerId: AppState.user.uid,
                        rating: 5.0, // Default premium rating
                        createdAt: serverTimestamp()
                    });
                    
                    sellerApp.showToast("Product added successfully!");
                    // Clear form
                    document.getElementById('prod-name').value = '';
                    document.getElementById('prod-price').value = '';
                    document.getElementById('prod-img').value = '';
                    document.getElementById('prod-desc').value = '';
                    
                } catch (error) {
                    sellerApp.showToast("Error adding product: " + error.message);
                }
            },

            // --- Order Management ---
            fetchOrders: async () => {
                try {
                    // Fetching all orders. In a complex app, we would query `where("sellerId", "==", uid)`
                    const q = query(collection(db, "orders"), orderBy("createdAt", "desc"));
                    const snapshot = await getDocs(q);
                    
                    AppState.orders = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));
                    
                    sellerApp.updateDashboardStats();
                    sellerApp.renderOrdersTable();
                } catch (error) {
                    console.error("Error fetching orders:", error);
                }
            },

            updateDashboardStats: () => {
                let earnings = 0;
                let pending = 0;
                let ready = 0;

                AppState.orders.forEach(order => {
                    if(order.status === 'Delivered' || order.status === 'Ready') earnings += order.total;
                    if(order.status === 'Pending') pending++;
                    if(order.status === 'Ready' || order.status === 'Delivered') ready++;
                });

                document.getElementById('stat-earnings').innerText = `$${earnings.toFixed(2)}`;
                document.getElementById('stat-pending').innerText = pending;
                document.getElementById('stat-ready').innerText = ready;

                // Update Recent Activity (Dashboard)
                const activityTbody = document.getElementById('recent-activity-list');
                activityTbody.innerHTML = '';
                
                const recent = AppState.orders.slice(0, 5); // top 5
                if(recent.length === 0) {
                    activityTbody.innerHTML = '<tr><td colspan="3" style="text-align:center;">No recent activity</td></tr>';
                    return;
                }

                recent.forEach(order => {
                    const statusClass = order.status === 'Pending' ? 'status-pending' : (order.status === 'Ready' ? 'status-ready' : 'status-delivered');
                    activityTbody.innerHTML += `
                        <tr>
                            <td>#${order.id.substring(0,8)}</td>
                            <td style="font-weight:600; color:var(--primary);">$${order.total.toFixed(2)}</td>
                            <td><span class="status-badge ${statusClass}">${order.status}</span></td>
                        </tr>
                    `;
                });
            },

            renderOrdersTable: () => {
                const tbody = document.getElementById('orders-table-body');
                tbody.innerHTML = '';

                if(AppState.orders.length === 0) {
                    tbody.innerHTML = '<tr><td colspan="6" style="text-align:center;">No orders found.</td></tr>';
                    return;
                }

                AppState.orders.forEach(order => {
                    const itemsStr = order.items ? order.items.map(i => `${i.qty}x ${i.name}`).join(', ') : 'N/A';
                    const statusClass = order.status === 'Pending' ? 'status-pending' : (order.status === 'Ready' ? 'status-ready' : 'status-delivered');
                    
                    // Button logic: Only show "Mark Ready" if it's Pending. 
                    const actionBtn = order.status === 'Pending' 
                        ? `<button class="btn btn-sm btn-success" onclick="sellerApp.markOrderReady('${order.id}')">Mark Ready</button>`
                        : `<span style="color:var(--text-light); font-size:0.85rem;">Processed</span>`;

                    tbody.innerHTML += `
                        <tr>
                            <td style="font-weight:500;">#${order.id.substring(0,8)}</td>
                            <td style="font-size:0.85rem; max-width:200px;">${order.address || 'N/A'}</td>
                            <td style="font-size:0.85rem; max-width:250px;">${itemsStr}</td>
                            <td style="font-weight:600; color:var(--primary);">$${order.total.toFixed(2)}</td>
                            <td><span class="status-badge ${statusClass}">${order.status}</span></td>
                            <td>${actionBtn}</td>
                        </tr>
                    `;
                });
            },

            markOrderReady: async (orderId) => {
                try {
                    const orderRef = doc(db, "orders", orderId);
                    // Update status to Ready (which Delivery Panel will pick up)
                    await updateDoc(orderRef, { status: 'Ready' });
                    
                    sellerApp.showToast("Order marked as Ready to Ship!");
                    sellerApp.fetchOrders(); // Refresh lists
                } catch (error) {
                    sellerApp.showToast("Failed to update order: " + error.message);
                }
            }
        };

        // Auth State Observer
        onAuthStateChanged(auth, (user) => {
            const modal = document.getElementById('auth-modal');
            if (user) {
                AppState.user = user;
                modal.classList.add('hidden');
                document.getElementById('seller-email').innerText = user.email.split('@')[0];
                sellerApp.fetchOrders(); // Load data once logged in
            } else {
                AppState.user = null;
                modal.classList.remove('hidden');
            }
        });

    </script>
</body>
</html>
