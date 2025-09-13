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
                </select>

                <label for="profitSplit">Profit Split Agreement:</label>
                <select id="profitSplit" name="profitSplit" required>
                    <option value="">Select Profit Split</option>
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

            // Simulated API data for prop firms (replace with actual API in production)
            const propFirmData = {
                'FTMO': {
                    accountSizes: [
                        { size: '10000', price: 170 }, // USD, converted from ~155 EUR
                        { size: '25000', price: 275 }, // ~250 EUR
                        { size: '50000', price: 380 }, // ~345 EUR
                        { size: '100000', price: 594 } // ~540 EUR
                    ],
                    profitSplits: ['50/50', '60/40', '70/30']
                },
                'E8 Funding': {
                    accountSizes: [
                        { size: '5000', price: 59 },
                        { size: '10000', price: 99 },
                        { size: '25000', price: 208 },
                        { size: '50000', price: 338 },
                        { size: '100000', price: 588 }
                    ],
                    profitSplits: ['50/50', '60/40', '70/30']
                },
                'The5ers': {
                    accountSizes: [
                        { size: '5000', price: 39 },
                        { size: '10000', price: 85 },
                        { size: '25000', price: 165 },
                        { size: '50000', price: 260 },
                        { size: '100000', price: 350 }
                    ],
                    profitSplits: ['50/50', '60/40']
                }
            };

            // Simulate API call to fetch prop firm details
            function fetchPropFirmDetails(firm) {
                // TODO: Replace with actual API call, e.g.:
                // return fetch(`/api/propfirm/details?firm=${firm}`)
                //   .then(response => response.json());
                return Promise.resolve(propFirmData[firm] || { accountSizes: [], profitSplits: [] });
            }

            // Simulate API call to fetch price for specific account size
            function getPrice(firm, size) {
                // TODO: Replace with actual API call, e.g.:
                // return fetch(`/api/propfirm/price?firm=${firm}&size=${size}`)
                //   .then(response => response.json())
                //   .then(data => data.price);
                const firmData = propFirmData[firm];
                const account = firmData?.accountSizes.find(acc => acc.size === size);
                return Promise.resolve(account?.price || 0);
            }

            // Populate account size dropdown
            function populateAccountSizes(firm) {
                accountSize.innerHTML = '<option value="">Select Account Size</option>';
                const firmData = propFirmData[firm];
                if (firmData && firmData.accountSizes) {
                    firmData.accountSizes.forEach(acc => {
                        const option = document.createElement('option');
                        option.value = acc.size;
                        option.textContent = `$${parseInt(acc.size).toLocaleString()}`;
                        accountSize.appendChild(option);
                    });
                }
            }

            // Populate profit split dropdown
            function populateProfitSplits(firm) {
                profitSplit.innerHTML = '<option value="">Select Profit Split</option>';
                const firmData = propFirmData[firm];
                if (firmData && firmData.profitSplits) {
                    firmData.profitSplits.forEach(split => {
                        const option = document.createElement('option');
                        option.value = split;
                        option.textContent = split;
                        profitSplit.appendChild(option);
                    });
                }
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
            propFirm.addEventListener('change', async () => {
                const firm = propFirm.value;
                if (firm) {
                    await fetchPropFirmDetails(firm);
                    populateAccountSizes(firm);
                    populateProfitSplits(firm);
                    updateContributions();
                } else {
                    accountSize.innerHTML = '<option value="">Select Account Size</option>';
                    profitSplit.innerHTML = '<option value="">Select Profit Split</option>';
                    updateContributions();
                }
            });
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
