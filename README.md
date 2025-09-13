<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Challenges Page - Prop Firm Brokers 2025 Demo</title>
    <style>
        body { 
            font-family: Arial, sans-serif; 
            background-color: #f4f4f4; 
            padding: 20px; 
            margin: 0;
        }
        h2 { text-align: center; color: #333; }
        .section { margin: 40px 0; padding: 20px; background: white; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
        /* Navigation Menu */
        .nav-menu {
            display: flex;
            justify-content: center;
            gap: 10px;
            background: #fff;
            padding: 10px 0;
            border-bottom: 1px solid #ddd;
            margin-bottom: 20px;
        }
        .nav-menu a {
            padding: 10px 20px;
            border-radius: 20px;
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: background 0.3s, color 0.3s;
        }
        .nav-menu a:hover {
            background: #e7f3ff;
            color: #007bff;
        }
        .nav-menu a.active {
            background: #007bff;
            color: white;
        }
        /* Filter Bar */
        .filter-bar {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            align-items: center;
            margin-bottom: 20px;
        }
        .filter-bar button, .filter-bar select {
            padding: 8px 16px;
            border-radius: 20px;
            border: 1px solid #ddd;
            background: #fff;
            cursor: pointer;
            font-size: 0.9em;
        }
        .filter-bar button:hover, .filter-bar select:hover {
            background: #e7f3ff;
        }
        .filter-bar .filter-btn::before {
            content: '🔍 '; /* Placeholder filter icon */
        }
        .filter-bar .bookmarks-btn::before {
            content: '🔖 '; /* Placeholder bookmark icon */
        }
        .filter-bar .all-btn {
            background: #007bff;
            color: white;
            border: none;
        }
        .filter-bar .all-btn:hover {
            background: #0056b3;
        }
        /* Toggle Switch */
        .toggle-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 40px;
            height: 20px;
        }
        .toggle-switch input {
            opacity: 0;
            width: 0;
            height: 0;
        }
        .slider {
            position: absolute;
            cursor: pointer;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: #ccc;
            border-radius: 20px;
            transition: 0.3s;
        }
        .slider:before {
            position: absolute;
            content: "";
            height: 16px;
            width: 16px;
            left: 2px;
            bottom: 2px;
            background: white;
            border-radius: 50%;
            transition: 0.3s;
        }
        input:checked + .slider {
            background: #ff69b4; /* Pink toggle */
        }
        input:checked + .slider:before {
            transform: translateX(20px);
        }
        /* Search Bar */
        .search-bar {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
        }
        .search-bar input {
            width: 100%;
            max-width: 500px;
            padding: 10px;
            border-radius: 20px;
            border: 1px solid #ddd;
            font-size: 0.9em;
        }
        /* Count Display */
        .counts {
            text-align: center;
            margin-bottom: 20px;
            font-size: 1em;
            color: #555;
        }
        .counts span {
            background: #e7f3ff;
            padding: 5px 10px;
            border-radius: 10px;
            margin: 0 10px;
        }
        /* Table Styles */
        .table-container { overflow-x: auto; }
        table { width: 100%; border-collapse: collapse; margin-top: 10px; }
        th, td { padding: 12px; text-align: left; border-bottom: 1px solid #ddd; }
        th { background: #f8f9fa; font-weight: bold; color: #333; }
        tr:hover { background: #f5f5f5; }
        .promo { background: #d4edda; padding: 4px 8px; border-radius: 4px; font-size: 0.85em; }
        .action-btn { 
            background: #007bff; 
            color: white; 
            border: none; 
            padding: 8px 16px; 
            border-radius: 4px; 
            cursor: pointer; 
            text-decoration: none; 
            display: inline-block; 
        }
        .action-btn:hover { background: #0056b3; }
        /* Firm Column Clickable */
        .firm-name { 
            color: #007bff; 
            cursor: pointer; 
            text-decoration: underline; 
        }
        .firm-name:hover { color: #0056b3; }
        .firm-details { 
            display: none; 
            padding: 15px; 
            background: #f9f9f9; 
            border: 1px solid #ddd; 
            border-radius: 8px; 
            margin: 10px 0; 
            text-align: center;
        }
        .firm-details.active { display: block; }
        .firm-details img { 
            max-width: 100px; 
            height: auto; 
            border-radius: 50%; 
            margin-bottom: 10px;
        }
        .firm-details h3 { 
            font-size: 1.4em; 
            color: #007bff; 
            margin: 10px 0;
        }
        .firm-details p { 
            font-size: 0.9em; 
            color: #555; 
            line-height: 1.4;
        }
        .firm-details button { 
            background: #28a745; 
            color: white; 
            border: none; 
            padding: 12px 24px; 
            border-radius: 6px; 
            cursor: pointer; 
            font-size: 1em;
            margin-top: 10px;
        }
        .firm-details button:hover { background: #218838; }
        @media (max-width: 600px) {
            .nav-menu { flex-wrap: wrap; }
            .filter-bar { flex-direction: column; align-items: stretch; }
            th, td { padding: 8px 4px; font-size: 0.85em; }
            .firm-details { padding: 10px; }
        }
    </style>
</head>
<body>
    <!-- Navigation Menu -->
    <nav class="nav-menu">
        <a href="#firms">Firms</a>
        <a href="#challenges" class="active">Challenges</a>
        <a href="#offers">Offers</a>
        <a href="#reviews">Reviews</a>
    </nav>

    <!-- Filter Bar -->
    <div class="filter-bar">
        <button class="filter-btn">Filter</button>
        <select name="assets">
            <option value="FX" selected>FX</option>
            <option value="Crypto">Crypto</option>
            <option value="Indices">Indices</option>
            <option value="Commodities">Commodities</option>
        </select>
        <select name="size">
            <option value="100K" selected>$100K</option>
            <option value="50K">$50K</option>
            <option value="200K">$200K</option>
            <option value="400K">$400K</option>
        </select>
        <select name="steps">
            <option value="2 Steps" selected>2 Steps</option>
            <option value="1 Step">1 Step</option>
            <option value="3 Steps">3 Steps</option>
        </select>
        <div class="toggle-container">
            <label>Apply Discount</label>
            <label class="toggle-switch">
                <input type="checkbox">
                <span class="slider"></span>
            </label>
        </div>
        <button class="all-btn">All</button>
        <button class="bookmarks-btn">Bookmarks</button>
    </div>

    <!-- Search Bar -->
    <div class="search-bar">
        <input type="text" placeholder="Search for Challenges">
    </div>

    <!-- Challenge and Firm Count -->
    <div class="counts">
        <span>Total Challenges: 1</span>
        <span>Total Firms: 1</span>
    </div>

    <!-- Prop Firms Table Section -->
    <section id="prop-firms-table" class="section">
        <h2>Prop Firms Overview</h2>
        <p>Compare top prop firms. Click the firm name for more details. (Static for demo; will fetch from API later.)</p>
        <div class="table-container">
            <table>
                <thead>
                    <tr>
                        <th>Firm</th>
                        <th>Rank / Reviews</th>
                        <th>Country</th>
                        <th>Years in Operation</th>
                        <th>Assets</th>
                        <th>Platforms</th>
                        <th>Max Allocations</th>
                        <th>Promo</th>
                        <th>Profit Split</th>
                        <th>Action</th>
                    </tr>
                </thead>
                <tbody id="table-body">
                    <!-- Static row populated by JS below -->
                </tbody>
            </table>
        </div>
    </section>

    <script>
        // Static Table Data (FTMO only for demo)
        const firmsTableData = [
            {
                id: 1,
                firm: 'FTMO',
                rankReviews: '1 / 4.8 (25K+)',
                country: 'Czech Republic',
                years: '10',
                assets: 'Forex, Indices, Commodities, Crypto',
                platforms: 'MT4, MT5, cTrader',
                maxAllocations: '$2,000,000',
                promo: '25% Off Challenges',
                profitSplit: 'Up to 90%',
                affiliateLink: 'https://ftmo.com/en/affiliate-program/?ref=yourid',
                description: 'Leading prop firm for forex traders with two-phase challenges, scaling up to $2M, and support for MT4/MT5/cTrader platforms.',
                logo: 'https://ftmo.com/wp-content/themes/ftmo/assets/images/ftmo-logo-white.svg'
            }
            // Add more, e.g., FundedNext: { id: 2, firm: 'FundedNext', rankReviews: '2 / 4.7 (15K+)', ... }
        ];

        // Render Table Rows
        const tableBody = document.getElementById('table-body');
        firmsTableData.forEach(row => {
            const tr = document.createElement('tr');
            tr.innerHTML = `
                <td><span class="firm-name" data-firm-id="${row.id}">${row.firm}</span></td>
                <td>${row.rankReviews}</td>
                <td>${row.country}</td>
                <td>${row.years}</td>
                <td>${row.assets}</td>
                <td>${row.platforms}</td>
                <td>${row.maxAllocations}</td>
                <td><span class="promo">${row.promo}</span></td>
                <td>${row.profitSplit}</td>
                <td><a href="${row.affiliateLink}" target="_blank" rel="noopener noreferrer" class="action-btn">View Details</a></td>
            `;
            tableBody.appendChild(tr);

            // Add hidden details row
            const detailsRow = document.createElement('tr');
            detailsRow.innerHTML = `
                <td colspan="10">
                    <div class="firm-details" id="details-${row.id}">
                        <img src="${row.logo}" alt="${row.firm} Logo" onerror="this.src='https://via.placeholder.com/100x100/CCCCCC/FFFFFF?text=${row.firm.charAt(0)}';">
                        <h3>${row.firm}</h3>
                        <p>${row.description}</p>
                        <p><strong>Profit Split:</strong> ${row.profitSplit}</p>
                        <a href="${row.affiliateLink}" target="_blank" rel="noopener noreferrer">
                            <button>Visit Broker</button>
                        </a>
                    </div>
                </td>
            `;
            tableBody.appendChild(detailsRow);
        });

        // Toggle Firm Details on Click
        document.querySelectorAll('.firm-name').forEach(firm => {
            firm.addEventListener('click', () => {
                const firmId = firm.getAttribute('data-firm-id');
                const details = document.getElementById(`details-${firmId}`);
                details.classList.toggle('active');
            });
        });
    </script>
</body>
</html>
