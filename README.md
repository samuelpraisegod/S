<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Compare top forex prop firms by lowest account price with detailed challenge, offer, and review information.">
    <meta name="keywords" content="prop trading, forex trading, prop firms, funded trading">
    <title>Prop Firms Overview - Sorted by Lowest Price</title>
    <style>
        /* General Styles */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            line-height: 1.6;
            background-color: #f4f4f4;
        }
        h1 {
            text-align: center;
            color: #333;
        }

        /* Table Styles (Desktop) */
        .prop-firms-table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
            background: #fff;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .prop-firms-table th, .prop-firms-table td {
            padding: 12px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        .prop-firms-table th {
            background: #007BFF;
            color: #fff;
        }
        .prop-firms-table tr:hover {
            background: #f9f9f9;
        }
        .firm-logo img {
            width: 50px;
            height: 50px;
            vertical-align: middle;
            margin-right: 10px;
        }
        .overview-btn {
            background: #007BFF;
            color: #fff;
            border: none;
            padding: 8px 12px;
            cursor: pointer;
            border-radius: 4px;
            font-size: 14px;
        }
        .overview-btn:hover {
            background: #0056b3;
        }
        .accordion-content {
            display: none;
            padding: 15px;
            background: #f1f1f1;
            border-top: 1px solid #ddd;
        }
        .accordion-content.active {
            display: block;
        }

        /* Card Styles (Mobile) */
        @media (max-width: 768px) {
            .prop-firms-table {
                display: none;
            }
            .prop-firms-cards {
                display: flex;
                flex-direction: column;
                gap: 15px;
            }
            .prop-firm-card {
                background: #fff;
                border-radius: 8px;
                padding: 15px;
                box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            }
            .prop-firm-card h3 {
                margin: 0 0 10px;
                font-size: 18px;
                color: #333;
            }
            .prop-firm-card img {
                width: 40px;
                height: 40px;
                vertical-align: middle;
                margin-right: 10px;
            }
            .prop-firm-card p {
                margin: 5px 0;
                font-size: 14px;
            }
            .overview-btn {
                width: 100%;
                text-align: center;
            }
        }

        /* Desktop Hide Cards */
        @media (min-width: 769px) {
            .prop-firms-cards {
                display: none;
            }
        }

        /* Accessibility */
        .overview-btn:focus {
            outline: 2px solid #007BFF;
        }
    </style>
</head>
<body>
    <h1>Prop Firms Overview - Sorted by Lowest Price</h1>

    <!-- Desktop Table -->
    <table class="prop-firms-table">
        <thead>
            <tr>
                <th>Firm (Logo + Name)</th>
                <th>Review</th>
                <th>Offers</th>
                <th>Discount</th>
                <th>Price</th>
                <th>Overview</th>
            </tr>
        </thead>
        <tbody>
            <!-- DNA Funded -->
            <tr data-firm-id="1">
                <td><span class="firm-logo"><img src="https://dnafunded.com/logo.png" alt="DNA Funded Logo" loading="lazy"></span><a href="https://dnafunded.com/">DNA Funded</a></td>
                <td>4.8/5 (CBS News: "Low fees, broker-backed")</td>
                <td>20% off; Profit Booster; Early payout; Discord</td>
                <td>15-20% (code: DNA20); Free 5K</td>
                <td>$15 for 2K</td>
                <td><button class="overview-btn" aria-expanded="false" aria-controls="dna-funded-details">Overview</button></td>
            </tr>
            <tr class="accordion-content" id="dna-funded-details">
                <td colspan="6">
                    <strong>Account Sizes & Prices</strong>: 2K: $15, 5K: $29, 10K: $59, 25K: $139, 50K: $199, 100K: $398, 200K: $699.<br>
                    <strong>Phases</strong>: 1-Phase (10% target, 5% daily/10% max drawdown) or 2-Phase (8%/5%). No time limits; Custom add-ons.<br>
                    <strong>Rules</strong>: No weekend holding restrictions; EAs, news trading, scalping allowed; Max 5% daily loss, 10% overall loss.<br>
                    <strong>Payout Policy</strong>: 80-90% profit split; Payouts every 14 days (7 days with add-on); First payout after 14-day min trading.<br>
                    <strong>Offers</strong>: 20% off (code: PROPFIRMS20); Profit Booster (80-90%); Early payout (7 days). Discord community.<br>
                    <strong>Discounts</strong>: 15-20% via codes (e.g., DNA20); Seasonal free 5K account.<br>
                    <strong>Reviews</strong>: 4.8/5 (CBS News: "Low fees, broker-backed" – Top-rated 2025). Excellent for spreads/support.<br>
                    <strong>Affiliate Link</strong>: <a href="https://dnafunded.com/affiliate">Join DNA Funded</a><br>
                    <strong>Max Funding</strong>: $600K (scalable).<br>
                    <strong>Leverage (Forex)</strong>: Up to 1:100.<br>
                    <strong>Platforms</strong>: MT5, DX Trade, TradeLocker.<br>
                    <strong>Forex Features</strong>: 800+ CFDs, 0.0 pips via DNA Markets (ASIC), $3-$7/lot commission.<br>
                    <strong>Notes</strong>: ASIC-backed; US access; Scaling to $600K every 4 months.
                </td>
            </tr>
            <!-- Axi Select -->
            <tr data-firm-id="2">
                <td><span class="firm-logo"><img src="https://www.axi.com/logo.png" alt="Axi Select Logo" loading="lazy"></span><a href="https://www.axi.com/int/funded-trader-program">Axi Select</a></td>
                <td>4.6/5 (Investing.com: "Free entry, transparent")</td>
                <td>Free to join ($500 deposit); 90% split; Edge tools</td>
                <td>Up to 20% (code: AXIPROP20)</td>
                <td>Free ($500 deposit)</td>
                <td><button class="overview-btn" aria-expanded="false" aria-controls="axi-select-details">Overview</button></td>
            </tr>
            <tr class="accordion-content" id="axi-select-details">
                <td colspan="6">
                    <strong>Account Sizes & Prices</strong>: Free join; Min deposit $500 (no challenge fees; all sizes scale from $5K base).<br>
                    <strong>Phases</strong>: No traditional phases; 6 Stages (Seed to Pro M) based on Edge Score (50+ required after 20 trades). Live account progression.<br>
                    <strong>Rules</strong>: No EAs; News trading allowed; Max 5% daily loss, 10% overall loss; Min 20 trades for progression.<br>
                    <strong>Payout Policy</strong>: 65-90% profit split; On-demand payouts after 30 days; No min trading period post-stage.<br>
                    <strong>Offers</strong>: 100% free to join (min $500 deposit); Up to 90% split; Add-ons: Edge score tools, community access. No membership fees.<br>
                    <strong>Discounts</strong>: Up to 20% via affiliate codes (e.g., AXIPROP20).<br>
                    <strong>Reviews</strong>: 4.6/5 (Investing.com: "Free entry, transparent" – 10k+ reviews). Praised for no eval fees, but score-based.<br>
                    <strong>Affiliate Link</strong>: <a href="https://www.axi.com/affiliate">Join Axi Select</a><br>
                    <strong>Max Funding</strong>: $1M.<br>
                    <strong>Leverage (Forex)</strong>: Up to 1:100.<br>
                    <strong>Platforms</strong>: MT4.<br>
                    <strong>Forex Features</strong>: 250+ assets, 0.0 pips, crypto/forex focus, $5/lot commission.<br>
                    <strong>Notes</strong>: ASIC-regulated hybrid; Live trading from start; Fraud prevention; Global, US-friendly.
                </td>
            </tr>
            <!-- Add other firms: FundingPips, GoatFundedTrader, OANDA Prop Trader, The5%ers, FundedNext, FXIFY, SabioTrade, FTMO -->
        </tbody>
    </table>

    <!-- Mobile Cards -->
    <div class="prop-firms-cards">
        <div class="prop-firm-card" data-firm-id="1">
            <h3><img src="https://dnafunded.com/logo.png" alt="DNA Funded Logo" loading="lazy"> <a href="https://dnafunded.com/">DNA Funded</a></h3>
            <p><strong>Review</strong>: 4.8/5 (CBS News: "Low fees, broker-backed")</p>
            <p><strong>Offers</strong>: 20% off; Profit Booster; Early payout; Discord</p>
            <p><strong>Discount</strong>: 15-20% (code: DNA20); Free 5K</p>
            <p><strong>Price</strong>: $15 for 2K</p>
            <p><button class="overview-btn" aria-expanded="false" aria-controls="dna-funded-card-details">Overview</button></p>
            <div class="accordion-content" id="dna-funded-card-details">
                <p><strong>Account Sizes & Prices</strong>: 2K: $15, 5K: $29, 10K: $59, 25K: $139, 50K: $199, 100K: $398, 200K: $699.</p>
                <p><strong>Phases</strong>: 1-Phase (10% target, 5% daily/10% max drawdown) or 2-Phase (8%/5%). No time limits; Custom add-ons.</p>
                <p><strong>Rules</strong>: No weekend holding restrictions; EAs, news trading, scalping allowed; Max 5% daily loss, 10% overall loss.</p>
                <p><strong>Payout Policy</strong>: 80-90% profit split; Payouts every 14 days (7 days with add-on); First payout after 14-day min trading.</p>
                <p><strong>Offers</strong>: 20% off (code: PROPFIRMS20); Profit Booster (80-90%); Early payout (7 days). Discord community.</p>
                <p><strong>Discounts</strong>: 15-20% via codes (e.g., DNA20); Seasonal free 5K account.</p>
                <p><strong>Reviews</strong>: 4.8/5 (CBS News: "Low fees, broker-backed" – Top-rated 2025). Excellent for spreads/support.</p>
                <p><strong>Affiliate Link</strong>: <a href="https://dnafunded.com/affiliate">Join DNA Funded</a></p>
                <p><strong>Max Funding</strong>: $600K (scalable).</p>
                <p><strong>Leverage (Forex)</strong>: Up to 1:100.</p>
                <p><strong>Platforms</strong>: MT5, DX Trade, TradeLocker.</p>
                <p><strong>Forex Features</strong>: 800+ CFDs, 0.0 pips via DNA Markets (ASIC), $3-$7/lot commission.</p>
                <p><strong>Notes</strong>: ASIC-backed; US access; Scaling to $600K every 4 months.</p>
            </div>
        </div>
        <!-- Add other firms similarly -->
    </div>

    <script>
        // Accordion Functionality
        document.querySelectorAll('.overview-btn').forEach(button => {
            button.addEventListener('click', () => {
                const contentId = button.getAttribute('aria-controls');
                const content = document.getElementById(contentId);
                const isExpanded = button.getAttribute('aria-expanded') === 'true';

                // Close all other accordions
                document.querySelectorAll('.accordion-content').forEach(otherContent => {
                    if (otherContent !== content) {
                        otherContent.classList.remove('active');
                        otherContent.previousElementSibling?.querySelector('.overview-btn')?.setAttribute('aria-expanded', 'false');
                        otherContent.previousElementSibling?.querySelector('.overview-btn')?.textContent = 'Overview';
                    }
                });

                // Toggle current accordion
                content.classList.toggle('active');
                button.setAttribute('aria-expanded', !isExpanded);
                button.textContent = isExpanded ? 'Overview' : 'Collapse';

                // Fetch full details dynamically (example)
                if (!isExpanded) {
                    const firmId = button.closest('[data-firm-id]').getAttribute('data-firm-id');
                    fetch(`/api/prop-firms/${firmId}/details`)
                        .then(response => response.json())
                        .then(data => {
                            content.innerHTML = `
                                <p><strong>Account Sizes & Prices</strong>: ${data.price_list.map(item => `${item.size}: $${item.price}`).join(', ')}</p>
                                <p><strong>Phases</strong>: ${data.overview_details.phases}</p>
                                <p><strong>Rules</strong>: ${data.overview_details.rules}</p>
                                <p><strong>Payout Policy</strong>: ${data.overview_details.payout_policy}</p>
                                <p><strong>Offers</strong>: ${data.offers}</p>
                                <p><strong>Discounts</strong>: ${data.discount}</p>
                                <p><strong>Reviews</strong>: ${data.review}</p>
                                <p><strong>Affiliate Link</strong>: <a href="${data.overview_details.affiliate_link}">Join ${data.name}</a></p>
                                <p><strong>Max Funding</strong>: ${data.overview_details.max_funding}</p>
                                <p><strong>Leverage (Forex)</strong>: ${data.overview_details.leverage}</p>
                                <p><strong>Platforms</strong>: ${data.overview_details.platforms}</p>
                                <p><strong>Forex Features</strong>: ${data.overview_details.forex_features}</p>
                                <p><strong>Notes</strong>: ${data.overview_details.notes}</p>
                            `;
                        })
                        .catch(error => console.error('Error fetching details:', error));
                }
            });
        });
    </script>
</body>
</html>
