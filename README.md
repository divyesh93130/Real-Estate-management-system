<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>LuxeEstate | Management System</title>
    <style>
        /* CSS Variables for both views */
        :root {
            --primary: #4f46e5;    /* Indigo */
            --secondary: #10b981;  /* Emerald */
            --sidebar: #0f172a;    /* Dark Slate */
            --bg-dark: #0f172a;    /* Login Background */
            --bg-light: #f8fafc;   /* Dashboard Background */
            --text-main: #1e293b;
            --text-muted: #64748b;
        }

        * { box-sizing: border-box; }

        body, html {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--bg-dark); /* Default to dark for login */
            overflow: hidden;
        }

        /* --- 1. LOGIN CENTERING STYLES --- */
        #login-view {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100vh;
           
        }

        .login-card {
            background: white;
            padding: 2.5rem;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            width: 100%;
            max-width: 400px;
            text-align: center;
           
             
        }
        .logo { font-size: 1.8rem; font-weight: bold; margin-bottom: 1rem; color: var(--sidebar); }
        .logo span { color: var(--primary); }

        .input-group { text-align: left; margin-bottom: 1.2rem; }
        .input-group label { display: block; font-size: 0.9rem; font-weight: 600; margin-bottom: 0.5rem; }
        
        .input-group input {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #cbd5e1;
            border-radius: 8px;
            outline: none;
        }

        .btn-login {
            width: 100%;
            padding: 0.8rem;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-login:hover { background: #4338ca; }

        /* --- 2. DASHBOARD STYLES --- */
        #dashboard-view {
            display: none; /* Hidden until login */
            height: 100vh;
            width: 100%;
            background: var(--bg-light);
            grid-template-columns: 260px 1fr;
        }

        .sidebar {
            background: var(--sidebar);
            color: white;
            padding: 2rem 1rem;
            display: flex;
            flex-direction: column;
        }

        .nav-item {
            color: #94a3b8;
            padding: 0.8rem 1rem;
            text-decoration: none;
            border-radius: 8px;
            margin-bottom: 0.5rem;
            display: block;
        }

        .nav-item.active, .nav-item:hover { background: #1e293b; color: white; }

        .main-content {
            padding: 2rem 3rem;
            overflow-y: auto;
            color: var(--text-main);
        }

        /* Filter Bar (.in) */
        .filter-bar {
            display: flex;
            background: white;
            padding: 1.5rem;
            border-radius: 16px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            gap: 1rem;
            margin-bottom: 2rem;
            align-items: flex-end;
        }

        /* Common button style */
.btn {
    padding: 8px 18px;
    font-size: 14px;
    font-weight: 500;
    border-radius: 6px;
    border: none;
    cursor: pointer;
    transition: all 0.3s ease;
    margin-left: 5px;
}

/* Search button style */
.btn-search {
    background-color: #007bff;
    color: white;
}

.btn-search:hover {
    background-color: #0056b3;
}

/* Filter button style */
.btn-filter {
    background-color: #f1f1f1;
    color: #333;
    border: 1px solid #ccc;
}

.btn-filter:hover {
    background-color: #ddd;
}

/* Optional: align buttons properly */
.btn-container {
    display: inline-flex;
    align-items: center;
}
.btn {
    padding: 10px 20px;
    border-radius: 8px;
    background: linear-gradient(135deg, #4CAF50, #2e7d32);
    color: white;
    border: none;
}

.btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
        .filter-group { display: flex; flex-direction: column; flex: 1; }
        .filter-group label { font-size: 0.75rem; font-weight: 700; color: var(--text-muted); text-transform: uppercase; margin-bottom: 5px;}
        .filter-group input, .filter-group select { padding: 0.6rem; border: 1px solid #e2e8f0; border-radius: 8px; }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
        }

        .card {
            background: white;
            padding: 1rem;
            border-radius: 16px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.02);
            border: 1px solid #f1f5f9;
        }

        .card img { width: 100%; height: 180px; object-fit: cover; border-radius: 12px; }
        .price-tag { color: var(--secondary); font-weight: 800; font-size: 1.2rem; margin: 10px 0; }

        .logout { margin-top: auto; color: #fb7185 !important; font-weight: bold; }

    </style>
</head>
<body>

    <div id="login-view">
      
        <div class="login-card">
            
            <div class="logo">Real<span>Estate</span></div>
            <p style="color: var(--text-muted)">Management Portal Login</p>
            <form id="loginForm">
                 
                <div class="input-group">
                    <label>Username / Email</label>
                    <input type="text" id="username" required placeholder="admin@Realestate.com">
                </div>
                <div class="input-group">
                    <label>Password</label>
                    <input type="password" id="password" required placeholder="••••••••">
                </div>
                <button type="submit" class="btn-login">Sign In</button>
            </form>
        </div>
    </div>

    <div id="dashboard-view">
        <aside class="sidebar">
            <div class="logo" style="color: white; margin-bottom: 2rem;">Luxe<span>Estate</span></div>
            <a href="#" class="nav-item active">🏠 Dashboard</a>
            <a href="#" class="nav-item">🏙️ My Properties</a>
            <a href="#" class="nav-item">🔑 Tenants</a>
            <a href="#" class="nav-item logout" onclick="location.reload()">🚪 Logout</a>
        </aside>

        <main class="main-content">
            <div class="filter-bar">
                <div class="filter-group">
                    <label>Location</label>
                    <input type="text" placeholder="City or area">
                </div>
                <div class="filter-group">
                <label>Property Type</label>
                <select id="type">
                    <option value="all">All Types</option>
                    <option value="house">House</option>
                    <option value="apartment">Apartment</option>
                    <option value="studio">Studio</option>
                </select>
            </div>
            <div class="filter-group">
                <label>Status</label>
                <select id="r-o">
                    <option value="rent">For Rent</option>
                    <option value="own">For Sale</option>
                </select>
            </div>
            <div class="filter-group">
                <label>Max Price</label>
                <input type="text" placeholder="₹ Amount">
            </div>
            <div class="filter-group">
                <label>BHK</label>
                <select id="rooms">
                    <option>1</option><option>2</option><option>3</option><option>4+</option>
                </select>
            </div>
            <div>
           <button class="btn btn-search">Search</button>
           <button class="btn btn-filter">Filters</button>
            </div>

            
        </div>
        <div class="grid" id="propertyGrid">
        </main>
    </div>

    <script>
        // HANDLE LOGIN LOGIC
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Swap views
            document.getElementById('login-view').style.display = 'none';
            document.getElementById('dashboard-view').style.display = 'grid';
            
            // Set body background to dashboard color
            document.body.style.background = "var(--bg-light)";
            document.body.style.overflow = "auto";
        });

        // PROPERTY DATA
        const properties = [
            { name: "Skyline Residency", price: "₹45,000", loc: "Mumbai", img: "https://images.unsplash.com/photo-1570129477492-45c003edd2be?w=400" },
            { name: "Emerald Gardens", price: "₹28,500", loc: "Bangalore", img: "https://images.unsplash.com/photo-1568605114967-8130f3a36994?w=400" },
            { name: "Royal Oak Villa", price: "₹1,15,000", loc: "Gurgaon", img: "https://images.unsplash.com/photo-1560448204-e02f11c3d0e2?w=400" }
        ];

        // RENDER PROPERTIES
        const grid = document.getElementById('propertyGrid');
        grid.innerHTML = properties.map(p => `
            <div class="card">
                <img src="${p.img}">
                <p style="color: var(--text-muted); font-size: 0.8rem; margin: 10px 0 0 0;">${p.loc}</p>
                <h3 style="margin: 5px 0;">${p.name}</h3>
                <p class="price-tag">${p.price}<span style="font-size: 0.8rem; color: #94a3b8"> /mo</span></p>
                <button style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 6px; cursor: pointer; background: white;">Manage</button>
            </div>
        `).join('');
        
    </script>
</body>
</html>
