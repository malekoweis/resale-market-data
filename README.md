# Resale & E-commerce Price Data (Mercari, StockX, GOAT, Chrono24, Shopify, Etsy)

Free sample datasets of **real resale and e-commerce prices**, collected in October 2026 with open
[Apify](https://apify.com/malek_oweis) Actors. Use them to check what items actually sell for,
compare resale value against retail, or test a pricing model, then pull fresh data for any item
with the matching Actor.

| Dataset | Rows | What's inside | Get fresh data |
|---|---|---|---|
| [`mercari-us-sold-listings`](data/mercari-us-sold-listings.csv) | 462 | Mercari US **sold prices** (price comps) for Nintendo Switch OLED, Lite and Switch 2: price, original price, price drop %, condition, brand, category | [Mercari Sold Listings Scraper](https://apify.com/malek_oweis/mercari-sold-listings-scraper) |
| [`stockx-sneaker-sales-data`](data/stockx-sneaker-sales-data.csv) | 120 | StockX **resale market data** for Jordan 4, Nike Dunk Low, Yeezy 350: last sale, 90-day and 1-year average price, sales volume, volatility, premium vs retail | [StockX Sales Data Scraper](https://apify.com/malek_oweis/stockx-search-price-scraper) |
| [`goat-sneaker-prices-by-size`](data/goat-sneaker-prices-by-size.jsonl) | 25 | GOAT Air Jordan 4 prices **per size**: lowest ask, last sold, stock, instant-ship price, resale premium | [GOAT Sneaker Price Scraper](https://apify.com/malek_oweis/goat-sneaker-price-scraper) |
| [`chrono24-luxury-watch-listings`](data/chrono24-luxury-watch-listings.csv) | 60 | Chrono24 **Rolex and Omega** listings: reference number, year, price, condition, movement, case size, box & papers, seller country | [Chrono24 Watch Listing Scraper](https://apify.com/malek_oweis/chrono24-watch-listing-scraper) |
| [`shopify-store-catalogs`](data/shopify-store-catalogs.csv) | 600 | Full **Shopify catalogs** of allbirds.com and taylorstitch.com: price range, sale price, stock, vendor, type, tags | [Shopify Store Scraper](https://apify.com/malek_oweis/shopify-store-product-price-scraper) |
| [`etsy-shop-listings`](data/etsy-shop-listings.csv) | 30 | One **Etsy shop's** listings: price and variant range, rating, review count, stock, photo count | [Etsy Shop Scraper](https://apify.com/malek_oweis/etsy-shop-seo-auditor) |

Every dataset comes as **CSV** (flat columns) and **JSONL** (full records, including nested
per-size prices for GOAT).
Also on Hugging Face: [malekoweis/resale-market-data](https://huggingface.co/datasets/malekoweis/resale-market-data)
(load with `datasets.load_dataset("malekoweis/resale-market-data", "mercari-us-sold-listings")`).

## What the data shows (October 2026)

- **Used Nintendo Switch on Mercari US:** a Switch OLED in Good condition sold for a median of
  **$162** (Like new: **$189**). A Switch Lite in Good condition: **$94** (Like new: **$117**).
  Consoles category only, so games and accessories are excluded.
- **StockX sneaker resale:** the Jordan 4 search had a median 90-day average price of **$212**
  and **88,000+ sales in 90 days** across 40 products. The best seller was the Jordan 4 Retro
  Toro Bravo (2026) with 14,943 sales at about $179. Nike Dunk Low median: **$118**.
  Yeezy 350: **$185**.
- **GOAT Air Jordan 4:** the median product traded **15% above retail**. For 19 of 24 products,
  the priciest size cost **more than twice** the cheapest size of the same shoe.
- **Chrono24 watches:** median asking price **$10,948 for Rolex** and **$2,425 for Omega**.
  Listings **with box & papers** had a median of **$13,990** against **$4,500** without (the
  two groups also differ in model and age).
- **Shopify:** 45% of the 600 products across both stores were on sale at the time of collection.

## Questions this data helps answer

- How much does a used Nintendo Switch sell for on Mercari?
- What is the resale value of a Jordan 4 on StockX or GOAT, and which size is cheapest?
- Is a sneaker selling above or below retail?
- How much is a used Rolex or Omega on Chrono24, and do box & papers matter?
- What does a competitor's Shopify store sell, and how much of it is discounted?
- How are listings priced in an Etsy shop?

## Get fresh data for any item

The datasets above are snapshots. To get current prices for any item, run the matching Actor
on Apify (free tier available), or connect it to an AI assistant (Claude, ChatGPT, Cursor or any
MCP client) through Apify's MCP server:

```
https://mcp.apify.com/?tools=malek_oweis/mercari-sold-listings-scraper,malek_oweis/stockx-search-price-scraper,malek_oweis/goat-sneaker-price-scraper,malek_oweis/chrono24-watch-listing-scraper,malek_oweis/shopify-store-product-price-scraper,malek_oweis/etsy-shop-seo-auditor,malek_oweis/resale-price-checker
```

For a single answer per item across StockX, GOAT and Mercari, use the
[Resale Price Checker](https://apify.com/malek_oweis/resale-price-checker).

Then ask in plain language, for example: *"What did a used PS5 sell for on Mercari this
month?"* or *"Show the StockX 90-day average price for the Jordan 4 Black Cat."*

## Columns

<details><summary>Mercari US sold listings</summary>

`source` (search keyword), `itemId`, `url`, `title`, `status` (sold / on_sale), `price`,
`originalPrice`, `priceDropPct`, `condition`, `brand`, `category`, `categoryPath`, `size`,
`color`, `imageUrl`, `listedAt`
</details>

<details><summary>StockX sneaker sales data</summary>

`source`, `title`, `brand`, `model`, `gender`, `category`, `urlKey`, `productUrl`, `imageUrl`,
`releaseDate`, `colorway`, `retailPrice`, `styleId`, `lastSale`, `avgPrice90d`, `salesCount90d`,
`avgPriceYear`, `salesCountYear`, `salesCount72h`, `volatility`, `pricePremium`,
`pricePremiumPct`, `asksAvailable`, `expressAsksAvailable`, `sizeCount`
</details>

<details><summary>GOAT sneaker prices by size</summary>

`source`, `productId`, `title`, `brand`, `silhouette`, `releaseDate`, `productUrl`, `currency`,
`retailPrice`, `lowestPrice`, `instantShipLowestPrice`, `premiumVsRetailPct`, `underRetail`,
`inStock`, `sizes` (JSONL only: per-size `lowestAsk`, last sold, stock), `sizesListed`,
`sizesInStock`, `cheapestSize`, `cheapestSizeAsk`, `priciestSize`, `priciestSizeAsk`,
`avgLastSold`, `minLastSold`, `maxLastSold`
</details>

<details><summary>Chrono24 luxury watch listings</summary>

`source`, `listingId`, `url`, `title`, `brand`, `model`, `referenceNumber`, `year`, `price`,
`currency`, `condition`, `availability`, `movement`, `caseMaterial`, `caseDiameterMm`,
`crystal`, `strapMaterial`, `jewels`, `powerReserveHours`, `gender`, `sellerCountry`, `hasBox`,
`hasPapers`, `boxAndPapers`, `imageUrl`, `imageCount`, `description`
</details>

<details><summary>Shopify store catalogs</summary>

`store`, `title`, `handle`, `url`, `vendor`, `productType`, `tags`, `tagCount`, `createdAt`,
`updatedAt`, `publishedAt`, `variantCount`, `priceMin`, `priceMax`, `compareAtMax`, `onSale`,
`inStock`, `imageCount`, `descriptionLength`, `skuCoverage`, `flags`
</details>

<details><summary>Etsy shop listings</summary>

`shop`, `listingId`, `url`, `title`, `titleLength`, `price`, `priceMax`, `currency`,
`hasVariantRange`, `inStock`, `availability`, `rating`, `reviewCount`, `descriptionLength`,
`photoCount`, `sku`, `material`
</details>

## Notes

- Collected from **public pages only**, with no login, in October 2026. Seller IDs were removed.
- Prices are in USD. Chrono24 prices are asking prices; Mercari `sold` prices are final sale prices.
- Listing content (titles, images) belongs to the respective marketplaces and sellers.
  This compilation is shared under [CC BY 4.0](LICENSE) for research and analysis.
