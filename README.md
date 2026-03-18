<h1 align="center">ASOS Lost Revenue Analysis</h1>
<table align="center">
  <tr>
    <td width="1440">
      <h2 align="center">Project Background</h2>
      <body>
        <strong>ASOS</strong> is a UK-based global eCommerce fashion platform offering thousands of products across brands ranging from in-house labels to third-party names like Topshop, New Look, River Island, and Barbour. With a catalogue spanning clothing, accessories, and footwear across a wide range of price points, inventory management and size availability are critical drivers of revenue performance. <br>
        <br>
        This analysis examines <strong>18,378 product listings</strong> scraped from the ASOS platform, focusing on out-of-stock size variants across high-demand items. By quantifying how many sizes are unavailable per product and what each stockout event costs at list price, the project estimates the <strong>phantom revenue</strong> — sales that ASOS is positioned to make but cannot fulfill due to inventory gaps. <br>
        <br>
        The analysis focuses on the following key areas:
      </body>
      <h3>Northstar Metrics</h3>
      <h4>
        <ul>
          <li>Stockout identification — Parsing size availability strings to flag out-of-stock size variants per product.</li>
          <li>Lost revenue estimation — Modeling phantom revenue by multiplying out-of-stock size counts by product list price.</li>
          <li>Brand-level analysis — Aggregating stockout rates and lost revenue by brand to surface the highest-risk labels.</li>
          <li>Strategic segmentation — Identifying brands that combine high average price with high stockout rates as priority targets for restocking.</li>
        </ul>
      </h4>
    </td>
  </tr>
</table>

<table align="center">
  <tr>
    <div width="920">
      <h1 align="center">Executive Summary</h1>
      <h3 align="center">Dataset Overview</h3>
      <td width="1440" valign="top">
        <ol>
          <li>
            <strong>Dataset Scale:</strong>
            <ul>
              <li>18,378 product rows loaded from the ASOS product catalogue CSV.</li>
              <li>After filtering for valid price data and brands with more than 5 listings, the dataset was cleaned to a focused brand set for analysis.</li>
              <li>Columns analyzed: URL, product name, size availability string, category, price, color, SKU, description, and images.</li>
            </ul>
          </li>
          <li>
            <strong>Top 5 Brands by Listing Volume:</strong>
            <ul>
              <li><strong>ASOS</strong> — 4,844 listings (dominant in-house label)</li>
              <li><strong>Topshop</strong> — 1,017 listings</li>
              <li><strong>New Look</strong> — 511 listings</li>
              <li><strong>River Island</strong> — 467 listings</li>
              <li><strong>Miss Selfridge</strong> — 429 listings</li>
            </ul>
          </li>
          <li>
            <strong>Lost Revenue Methodology — "Phantom Revenue":</strong>
            <ul>
              <li>Each product's size availability string was parsed to count the number of size variants marked "Out of stock."</li>
              <li>A <strong>Stockout Rate</strong> was calculated as: <em>out-of-stock sizes ÷ total sizes listed</em>.</li>
              <li><strong>Lost Revenue</strong> per product was estimated as: <em>price × out-of-stock size count</em>, representing the revenue ceiling lost per item due to unavailable inventory.</li>
            </ul>
          </li>
        </ol>
      </td>
    </div>
  </tr>
</table>

<h2 align="center">Dataset Structure</h2>
<body align="center">The dataset consists of a single flat CSV with 9 columns: <strong>url, name, size, category, price, color, sku, description,</strong> and <strong>images</strong>. Stockout metrics and brand fields were engineered during analysis.</body>

<h1 align="center">Insights Deep-Dive</h1>

<table align="center">
  <tr>
    <h2 align="center">Top Products by Estimated Lost Revenue</h2>
    <td width="1440">
      <ul>
        <li>The <strong>Barbour Beadnell wax jacket in black</strong> led all individual products with an estimated <strong>£1,971 in lost revenue</strong> — 9 out-of-stock sizes at a £219 list price.</li>
        <li>The <strong>Topshop premium real leather collared zip-through jacket</strong> ranked second at <strong>£1,820 lost</strong> — 7 sizes unavailable at £260, the highest unit price in the top 5.</li>
        <li>The <strong>ASOS DESIGN premium real leather trench coat</strong> came in third at <strong>£1,540 lost</strong> — 7 sizes out of stock at £220.</li>
        <li>The <strong>ASOS EDITION geo embellished fringe plunge midi dress</strong> saw <strong>£1,500 in phantom revenue</strong> — 6 sizes missing at £250.</li>
        <li>The <strong>Topshop Baggy co-ord jeans in green cord</strong> had the highest raw stockout count in the top 5: <strong>27 size variants out of stock</strong> at £50, totaling £1,350 in lost revenue — demonstrating that lower-priced items with broad size ranges can still drive significant loss at scale.</li>
      </ul>
    </td>
  </tr>
</table>

<table align="center">
  <h2 align="center">Brand Strategy Analysis</h2>
  <tr>
    <td width="1440" align="center">
      <img width="900" alt="Brand Strategy Scatter Plot — Average Price vs Stockout Rate, bubble size = Total Lost Revenue" src="[brand_strategy_chart.png](https://res.cloudinary.com/dcqk5bgqe/image/upload/v1773872245/brand_strategy_chart_qdmpme.png)" />
    </td>
  </tr>
  <tr>
    <td width="1440" valign="top">
      <ul>
        <li>Brands in the <strong>upper-right quadrant</strong> (average price above £40, stockout rate above 40%) represent the highest-priority restocking targets — they charge premium prices AND frequently run out of stock, maximizing lost revenue per incident.</li>
        <li><strong>ASOS own-label</strong> dominates by volume and contributes the largest share of total lost revenue in absolute terms, driven by its 4,844-listing footprint across the catalogue.</li>
        <li><strong>Topshop</strong> sits in a high-risk zone — a mid-to-high average price point combined with elevated stockout rates makes it the most strategically important third-party brand for inventory recovery.</li>
        <li>Brands with <strong>large bubbles in the lower-left quadrant</strong> (low price, low stockout rate) still contribute meaningful lost revenue through sheer volume and broad size ranges — the Topshop jeans example (27 stockouts at £50) illustrates this effect.</li>
        <li>The red dashed lines at <strong>£40 average price</strong> and <strong>40% stockout rate</strong> serve as segmentation thresholds to identify "high risk / high reward" brands where restocking investment would yield the greatest revenue recovery.</li>
      </ul>
    </td>
  </tr>
</table>

<table align="center">
  <h1>Recommendations</h1>
  <h4>Based on the uncovered insights, here are actionable items that ASOS can take away from this analysis.</h4>
  <ul>
    <h3>Inventory Prioritization</h3>
    <li>Restock high-price, high-stockout-rate products first — these represent the greatest revenue recovery per unit restocked.</li>
      <ul>
        <li>Items like the Barbour Beadnell wax jacket (£1,971 phantom revenue) and Topshop leather jacket (£1,820) are individually significant and should be flagged for urgent replenishment.</li>
        <li>Brands in the upper-right quadrant of the Brand Strategy chart (above £40 avg. price, above 40% stockout rate) are priority labels for inventory investment.</li>
      </ul>
    <h3>Topshop Brand Management</h3>
    <li>Topshop appears in the top 5 lost revenue products twice and shows elevated stockout rates across its catalogue — signaling a systemic fulfillment issue rather than isolated incidents.</li>
      <ul>
        <li>ASOS should work with Topshop supply chain partners to improve size-level replenishment cycles, especially for leather and premium outerwear categories.</li>
      </ul>
    <h3>Size Range Strategy</h3>
    <li>Don't overlook volume-driven stockouts on lower-priced items with large size curves.</li>
      <ul>
        <li>The Topshop Baggy co-ord jeans had 27 out-of-stock sizes — more than any other product in the top 5. At scale, items like this can accumulate significant lost revenue despite modest unit prices.</li>
        <li>Wide-fit and co-ord collections should be monitored for size availability gaps, particularly in popular extended sizes.</li>
      </ul>
    <h3>ASOS Own-Label</h3>
    <li>ASOS's in-house label (4,844 listings) is the single largest contributor to total phantom revenue and warrants dedicated inventory health tracking.</li>
      <ul>
        <li>Premium own-label lines (ASOS DESIGN, ASOS EDITION) at £220–£250 price points are especially high-impact when they stock out — the ASOS trench coat and embellished dress both appear in the top 5.</li>
        <li>ASOS should implement automated size-level restock alerts for own-label products priced above £100.</li>
      </ul>
    <h3>Data Infrastructure</h3>
    <li>The current analysis uses list price × stockout count as a proxy for lost revenue. Future iterations should incorporate demand signals (views, saves, basket adds) to weight the true revenue impact more precisely.</li>
      <ul>
        <li>Products with high demand signals and partial stockouts (e.g., most sizes in stock but popular sizes like UK 10 and UK 12 out) likely represent a higher true revenue loss than the model currently captures.</li>
      </ul>
  </ul>
</table>
