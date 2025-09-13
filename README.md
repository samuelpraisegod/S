```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pacific Prop Firm Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
        }
        #main-content {
            max-width: 600px;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
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
    <div id="main-content">
        <h1>Pacific Prop Firm Co-Funding Calculator</h1>
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
                    <option value="E8 Funding">E8 Funding</option>
                    <option value="The5ers">The5ers</option>
                </select>

                <label for="accountSize">Account Size:</label>
                <select id="accountSize" name="accountSize" required>
                    <option value="">Select Account Size</option>
                    <option value="5000">$5,000</option>
                    <option value="10000">$10,000</option>
                    <option value="25000">$25,000</option>
                    <option value="50000">$50,000</option>
                    <option value="100000">$100,000</option>
                </select>

                <label for="profitSplit">Profit Split Agreement:</label>
                <select id="profitSplit" name="profitSplit" required>
                    <option value="">Select Profit Split</option>
                    <option value="50/50">50/50</option>
                    <option value="60/40">60/40</option>
                    <option value="70/30">70/30</option>
                </select>

                <div id="contributionDetails">
                    <h3>showTab - Contribution Breakdown</h3>
                    <p><strong>Account Price:</strong> <span id="accountPrice">TBD</span></p>
                    <p><strong>Profit Split:</strong> <span id="selectedProfitSplit">TBD</span></p>
                    <p><strong>Requester Contribution:</strong> <span id="requesterContribution">TBD</span></p>
                    <p><strong>Partner Contribution:</strong> <span id="partnerContribution">TBD</span></p>
                </div>

                <button type="submit" id="submitButton">Submit Request</button>
                <p id="result"></p>
            </form>
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

            // Price mapping based on prop firm and account size (simulating API data; in production, fetch from API)
            // Prices approximated from 2025 data: FTMO in USD (converted from EUR @ ~1.1 rate), others in USD
            // Note: MyForexFunds removed as it's defunct per 2025 status
            const priceMap = {
                'FTMO': {
                    '5000': 0,   // Not available for FTMO
                    '10000': 170,
                    '25000': 275,
                    '50000': 380,
                    '100000': 594
                },
                'E8 Funding': {
                    '5000': 59,
                    '10000': 99,
                    '25000': 208,
                    '50000': 338,
                    '100000': 588
                },
                'The5ers': {
                    '5000': 39,
                    '10000': 85,
                    '25000': 165,
                    '50000': 260,
                    '100000': 350
                }
            };

            // Function to simulate API fetch for price (replace with actual fetch in production)
            function getPrice(firm, size) {
                // TODO: Integrate real prop firm API here, e.g.:
                // return fetch(`/api/propfirm/price?firm=${firm}&size=${size}`)
                //   .then(response => response.json())
                //   .then(data => data.price);
                // For now, use local map
                return Promise.resolve(priceMap[firm]?.[size] || 0);
            }

            // Update contributions
            async function updateContributions() {
                const firm = propFirm.value;
                const size = accountSize.value;
                const splitValue = profitSplit.value;
                const split = splitValue ? parseInt(splitValue.split('/')[0]) : 0;

                let price = 0;
                if (firm && size) {
                    price = await getPrice(firm, size);
                }

                accountPrice.textContent = price ? `$${price.toFixed(2)}` : 'TBD';
                selectedProfitSplit.textContent = splitValue || 'TBD';
                
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
            propFirm.addEventListener('change', updateContributions);
            accountSize.addEventListener('change', updateContributions);
            profitSplit.addEventListener('change', updateContributions);

            // Form submission
            form.addEventListener('submit', async (e) => {
                e.preventDefault();

                if (!calculatorToggle.checked) {
                    result.textContent = 'Calculator is turned off. Please turn it on to submit.';
                    result.className = 'error';
                    return;
                }

                const firm = propFirm.value;
                const size = accountSize.value;
                const split = profitSplit.value;

                if (firm && size && split) {
                    const price = await getPrice(firm, size);
                    const requesterShare = (price * parseInt(split.split('/')[0])) / 100;
                    result.textContent = `Request submitted! Your contribution of $${requesterShare.toFixed(2)} is locked.`;
                    result.className = '';
                } else {
                    result.textContent = 'Please fill in all fields.';
                    result.className = 'error';
                }
            });

            // Initial setup
            toggleCalculator();
            updateContributions();
        });
    </script>
</body>
</html>
```
