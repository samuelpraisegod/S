<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prop Firm Brokers Table - 2025 Demo</title>
    <style>
        body { 
            font-family: Arial, sans-serif; 
            background-color: #f4f4f4; 
            padding: 20px; 
            margin: 0;
        }
        h2 { text-align: center; color: #333; }
        .section { margin: 40px 0; padding: 20px; background: white; border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1); }
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
            th, td { padding: 8px 4px; font-size: 0.85em; }
            .firm-details { padding: 10px; }
        }
    </style>
</head>
<body>
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
