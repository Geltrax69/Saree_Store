# 🥻 Saree Store Dynamic Catalog

A premium, elegant Saree Store frontend built with vanilla HTML, CSS, and JavaScript. It features a dynamically generated product catalog powered by a simple text file.

## <img src="https://api.iconify.design/mdi:cogs.svg" width="28" height="28" align="center"> How It Works

This project is designed to be incredibly easy to update. Instead of hardcoding product cards into the HTML, the website reads from a local text file and generates the UI on the fly.

### 1. The Image Links File
<img src="https://api.iconify.design/mdi:file-document-outline.svg" width="24" height="24" align="center"> **`imageslinks`**
This is a simple text file located in the root of the project. It contains a list of direct image URLs (e.g., Pinterest image links), with exactly one URL per line.

### 2. Reading the Data
<img src="https://api.iconify.design/mdi:database-search.svg" width="24" height="24" align="center"> **`script.js` Fetch API**
When the webpage loads, `script.js` uses the native JavaScript `fetch()` API to read the contents of the `imageslinks` file. 
- It fetches the text and splits it by newlines (`\n`) to create an array of individual URLs.
- A "cache-buster" timestamp is appended to the fetch request to guarantee the browser always reads the latest version of the file instead of a blank cached version.
- *Note:* Because modern browsers restrict reading local files directly via the `file://` protocol for security, a local web server is required to serve the files so `fetch()` can read them.

### 3. Rendering the UI
<img src="https://api.iconify.design/mdi:web.svg" width="24" height="24" align="center"> **Dynamic HTML Generation**
For every valid link found in the file, the script dynamically constructs an HTML template (a product card) using JavaScript template literals.
- **Titles & Descriptions:** Cycled sequentially from a predefined list of premium saree types.
- **Prices:** Generated randomly between ₹ 5,000 and ₹ 80,000.
- **Ratings:** Randomly assigned between 4.0 and 5.0 with hover animations.

Finally, these generated cards are injected directly into the DOM (inside the `#products-container` div). This instantly transforms the simple list of links into a beautiful, fully functional storefront!

## <img src="https://api.iconify.design/mdi:rocket-launch.svg" width="24" height="24" align="center"> Running the Project Locally

1. Open your terminal in the project folder.
2. Start a local server:
   ```bash
   python3 -m http.server 8000
   ```
3. Open your browser and navigate to `http://localhost:8000`.
