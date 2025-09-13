<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DivoraSplit - Create Co-Funding Request</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #333;
            color: white;
            padding: 10px 20px;
        }
        #hamburger {
            cursor: pointer;
            font-size: 24px;
        }
        .auth-buttons .auth-btn {
            color: white;
            text-decoration: none;
            margin-left: 10px;
        }
        nav {
            background-color: #444;
            padding: 10px;
            display: none;
        }
        nav ul {
            list-style: none;
            padding: 0;
        }
        nav ul li {
            margin: 10px 0;
        }
        nav ul li a {
            color: white;
            text-decoration: none;
        }
        .sub-menu {
            margin-left: 20px;
        }
        #main-content {
            max-width: 600px;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        .settings-section {
            margin-bottom: 20px;
        }
        .toggle-container {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        .toggle-container label {
            margin-right: 10px;
            font-weight: bold;
        }
        .toggle-switch {
            position: relative;
            display: inline-block;
            width: 60px;
            height: 34px;
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
            background-color: #ccc;
            transition: .4s;
            border-radius: 34px;
        }
        .slider:before {
            position: absolute;
            content: "";
            height: 26px;
            width: 26px;
            left: 4px;
            bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }
        input:checked + .slider {
            background-color: #2196F3;
        }
        input:checked + .slider:before {
            transform: translateX(26px);
        }
        form label {
            display: block;
            margin: 10px 0 5px;
        }
        form select, form button {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 4px;
            border: 1px solid #ccc;
        }
        form button {
            background-color: #2196F3;
            color: white;
            border: none;
            cursor: pointer;
        }
        form button:disabled {
            background-color: #cccccc;
            cursor: not-allowed;
        }
        #contributionDetails {
            background: #f9f9f9;
            padding: 15px;
            border-radius: 4px;
            margin-top: 20px;
        }
        #result {
            color: green;
            margin-top: 10px;
        }
        .error {
            color: red;
        }
    </style>
</head>
<body>
    <header>
        <div id="hamburger">☰</div>
        <h2>DivoraSplit Dashboard</h2>
        <div class="auth-buttons">
            <a href="signup.html" class="auth-btn">Sign Up</a>
            <a href="login.html" class="auth-btn">Log In</a>
        </div>
    </header>
    <nav id="navigation-menu">
        <ul>
            <li><a href="index.html" data-emoji="🏠">Home</a></li>
            <li><a href="profile.html" data-emoji="👤">Profile</a>
                <ul class="sub-menu">
                    <li><a href="view-profile.html">View Profile</a></li>
                    <li><a href="edit-profile.html">Edit Profile</a></li>
                    <li><a href="settings.html">Settings</a></li>
                    <li><a href="logout.html">Logout</a></li>
                </ul>
            </li>
            <li><a href="balance.html" data-emoji="🏦">Balance</a>
                <ul class="sub-menu">
                    <li><a href="wallet-overview.html">Wallet Overview</a></li>
                    <li><a href="transaction-history.html">Transaction History</a></li>
                </ul>
            </li>
            <li><a href="deposit.html" data-emoji="➕">Deposit</a>
                <ul class="sub-menu">
                    <li><a href="bank-transfer.html">Bank Transfer</a></li>
                    <li><a href="crypto-wallet.html">Crypto Wallet</a></li>
                </ul>
            </li>
            <li><a href="withdrawals.html" data-emoji="💵">Withdrawals</a>
                <ul class="sub-menu">
                    <li><a href="bank-withdrawal.html">Bank Withdrawal</a></li>
                    <li><a href="crypto-withdrawal.html">Crypto Withdrawal</a></li>
                </ul>
            </li>
            <li><a href="firms.html" data-emoji="🏦">Firms</a>
                <ul class="sub-menu">
                    <li><a href="popular-firms.html">Popular</a></li>
                    <li><a href="favorite-firms.html">Favourite (0/5)</a></li>
                    <li><a href="new-firms.html">New Added</a></li>
                    <li><a href="all-firms.html">All</a></li>
                </ul>
            </li>
            <li><a href="challenges.html" data-emoji="🎯">Challenges</a>
                <ul class="sub-menu">
                    <li><a href="fx-challenges.html">Assets FX</a></li>
                    <li><a href="account-size.html">Size Account</a></li>
                    <li><a href="steps-challenges.html">Steps</a></li>
                    <li><a href="discount-challenges.html">Apply Discount</a></li>
                    <li><a href="bookmarks-challenges.html">Bookmarks</a></li>
                </ul>
            </li>
            <li><a href="offers.html" data-emoji="🎁">Offers</a>
                <ul class="sub-menu">
                    <li><a href="september-offers.html">September Offers</a></li>
                    <li><a href="exclusive-offers.html">Exclusive Offers</a></li>
                    <li><a href="all-offers.html">All Current Offers</a></li>
                </ul>
            </li>
            <li><a href="reviews.html" data-emoji="⭐">Review</a>
                <ul class="sub-menu">
                    <li><a href="all-reviews.html">All Reviews</a></li>
                    <li><a href="funded-reviews.html">Funded Reviews</a></li>
                    <li><a href="paidout-reviews.html">Paid Out Reviews</a></li>
                </ul>
            </li>
            <li><a href="cofunding.html" data-emoji="🤝">Co-Funding</a>
                <ul class="sub-menu">
                    <li><a href="create-cofunding.html">Create Co-Funding Request</a></li>
                    <li><a href="cofunding.html?state=pending">Pending</a></li>
                    <li><a href="cofunding.html?state=active">Active</a></li>
                    <li><a href="cofunding.html?state=accepted">Accepted</a></li>
                    <li><a href="cofunding.html?state=canceled">Canceled</a></li>
                </ul>
            </li>
        </ul>
    </nav>
    <div id="main-content">
        <h1>Create Co-Funding Request</h1>
        <div class="settings-section">
            <h2>Request Details</h2>
            <div class="toggle-container">
                <label for="calculatorToggle">Calculator:</label>
                <label class="toggle-switch">
                    <input type="checkbox" id="calculatorToggle" checked>
                    <span class="slider"></span>
                </label>
                <span id="toggleStatus">ON</span>
            </div>
            <form id="coFundingForm">
                <label for="propFirm">Prop Firm:</label>
                <select id="propFirm" name="propFirm" required>
                    <option value="">Select Prop Firm</option>
                    <option value="FTMO">FTMO</option>
                    <option value="MyForexFunds">MyForexFunds</option>
                    <option value="E8 Funding">E8 Funding</option>
                    <option value="The5ers">The5ers</option>
                </select>

                <label for="accountSize">Account Size:</label>
                <select id="accountSize" name="accountSize" required>
                    <option value="">Select Account Size</option>
                    <option value="1000">$1,000</option>
                    <option value="2000">$2,000</option>
                    <option value="5000">$5,000</option>
                    <option value="10000">$10,000</option>
                    <option value="system">System/Partner Will Choose</option>
                </select>

                <label for="profitSplit">Profit Split Agreement:</label>
                <select id="profitSplit" name="profitSplit" required>
                    <option value="">Select Profit Split</option>
                    <option value="50/50">50/50</option>
                    <option value="60/40">60/40</option>
                    <option value="70/30">70/30</option>
                </select>

                <div id="contributionDetails">
                    <h3>Contribution Breakdown</h3>
                    <p><strong>Account Price:</strong> <span id="accountPrice">TBD</span></p>
                    <p><strong>Profit Split:</strong> <span id="selectedProfitSplit">TBD</span></p>
                    <p><strong>Requester Contribution:</strong> <span id="requesterContribution">TBD</span></p>
                    <p><strong>Partner Contribution:</strong> <span id="partnerContribution">TBD</span></p>
                </div>

                <button type="submit" id="submitButton">Submit Request</button>
                <p id="result"></p>
            </form>
        </div>
        <div class="settings-section">
            <h2>Overview</h2>
            <p>Current Date and Time: <span id="date-time">02:36 PM WAT, Saturday, September 13, 2025</span></p>
        </div>
    </div>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const form = document.getElementById('coFundingForm');
            const propFirm = document.getElementById('propFirm');
            const accountSize = document.getElementById('accountSize');
            const profitSplit = document.getElementById('profitSplit');
            const accountPrice = document.getElementById('accountPrice');
            const selectedProfitSplit = document.getElementById('selectedProfitSplit');
            const requesterContribution = document.getElementById('requesterContribution');
            const partnerContribution = document.getElementById('partnerContribution');
            const result = document.getElementById('result');
            const calculatorToggle = document.getElementById('calculatorToggle');
            const toggleStatus = document.getElementById('toggleStatus');
            const submitButton = document.getElementById('submitButton');
            const contributionDetails = document.getElementById('contributionDetails');

            // Price mapping based on account size
            const priceMap = {
                '1000': 15,
                '2000': 30,
                '5000': 50,
                '10000': 100,
                'system': 0
            };

            // Session check
            function isLoggedIn() {
                return localStorage.getItem('isLoggedIn') === 'true';
            }

            function redirectToLogin(url) {
                const targetUrl = url || window.location.href;
                localStorage.setItem('redirectAfterLogin', targetUrl);
                window.location.href = 'login.html';
            }

            if (!isLoggedIn()) {
                redirectToLogin();
            }

            // Update contributions
            function updateContributions() {
                const size = accountSize.value;
                const split = profitSplit.value ? parseInt(profitSplit.value.split('/')[0]) : 0;
                const price = priceMap[size] || 0;

                accountPrice.textContent = price ? `$${price.toFixed(2)}` : 'TBD';
                selectedProfitSplit.textContent = profitSplit.value || 'TBD';
                
                if (price && split) {
                    const requesterShare = (price * split) / 100;
                    const partnerShare = price - requesterShare;
                    requesterContribution.textContent = `$${requesterShare.toFixed(2)}`;
                    partnerContribution.textContent = `$${partnerShare.toFixed(2)}`;
                } else {
                    requesterContribution.textContent = 'TBD';
                    partnerContribution.textContent = 'TBD';
                }
            }

            // Toggle calculator functionality
            function toggleCalculator() {
                const isEnabled = calculatorToggle.checked;
                toggleStatus.textContent = isEnabled ? 'ON' : 'OFF';
                propFirm.disabled = !isEnabled;
                accountSize.disabled = !isEnabled;
                profitSplit.disabled = !isEnabled;
                submitButton.disabled = !isEnabled;
                contributionDetails.style.display = isEnabled ? 'block' : 'none';
                if (isEnabled) {
                    updateContributions();
                } else {
                    accountPrice.textContent = 'TBD';
                    selectedProfitSplit.textContent = 'TBD';
                    requesterContribution.textContent = 'TBD';
                    partnerContribution.textContent = 'TBD';
                    result.textContent = '';
                }
            }

            // Event listeners
            calculatorToggle.addEventListener('change', toggleCalculator);
            accountSize.addEventListener('change', updateContributions);
            profitSplit.addEventListener('change', updateContributions);
            propFirm.addEventListener('change', updateContributions);

            // Form submission
            form.addEventListener('submit', (e) => {
                e.preventDefault();
                if (!isLoggedIn()) {
                    result.textContent = 'Please log in to submit a request.';
                    result.className = 'error';
                    redirectToLogin();
                    return;
                }

                if (!calculatorToggle.checked) {
                    result.textContent = 'Calculator is turned off. Please turn it on to submit.';
                    result.className = 'error';
                    return;
                }

                const propFirmValue = propFirm.value;
                const size = accountSize.value;
                const split = profitSplit.value;

                if (propFirmValue && size && split) {
                    const price = priceMap[size];
                    const requesterShare = (price * parseInt(split.split('/')[0])) / 100;
                    result.textContent = `Request submitted! Your contribution of $${requesterShare.toFixed(2)} is locked. Redirecting to Pending status...`;
                    result.className = '';
                    // Simulate redirect to cofunding.html?state=pending after 2 seconds
                    setTimeout(() => {
                        window.location.href = 'cofunding.html?state=pending';
                    }, 2000);
                } else {
                    result.textContent = 'Please fill in all fields.';
                    result.className = 'error';
                }
            });

            // Hamburger menu toggle
            document.getElementById('hamburger').addEventListener('click', () => {
                const nav = document.getElementById('navigation-menu');
                nav.style.display = nav.style.display === 'block' ? 'none' : 'block';
            });

            // Initial setup
            toggleCalculator();
            updateContributions();

            // Update date and time
            function updateDateTime() {
                const now = new Date();
                const options = { 
                    hour: '2-digit', 
                    minute: '2-digit', 
                    hour12: true, 
                    weekday: 'long', 
                    year: 'numeric', 
                    month: 'long', 
                    day: 'numeric', 
                    timeZone: 'Africa/Lagos' 
                };
                document.getElementById('date-time').textContent = now.toLocaleString('en-US', options) + ' WAT';
            }
            updateDateTime();
            setInterval(updateDateTime, 60000);
        });
    </script>
</body>
</html>
