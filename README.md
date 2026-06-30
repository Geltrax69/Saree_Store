# 🥻 Saree Store Dynamic Catalog

A premium, elegant Saree Store frontend built with vanilla HTML, CSS, and JavaScript. It features a dynamically generated product catalog powered by a simple text file.

## <img src="https://api.iconify.design/mdi:cogs.svg" width="28" height="28" align="center"> System Architecture & Workflow

This project is designed to be incredibly easy to update. Instead of hardcoding product cards into the HTML, the website reads from a local text file and generates the UI on the fly.

### 1. High-Level Data Pipeline
Here is a flowchart demonstrating how raw URLs are transformed into the final User Interface.

```mermaid
graph TD
    A[Client Browser] -->|Loads| B(index.html)
    B -->|Imports| C(script.js)
    B -->|Imports| D(styles.css)
    C -->|Fetch API Request| E[imageslinks File]
    E -.->|Returns Raw Text| C
    C -->|Splits Text by Newline| F[Array of URLs]
    F -->|Maps Over Array| G[Generate HTML Templates]
    G -->|Injects into DOM| H((Final Saree Store UI))
    
    style A fill:#e1f5fe,stroke:#0288d1,stroke-width:2px
    style E fill:#fff3e0,stroke:#f57c00,stroke-width:2px
    style H fill:#e8f5e9,stroke:#388e3c,stroke-width:3px
```

### 2. Execution Sequence
The following sequence diagram outlines exactly what happens the moment you open the website in your browser.

```mermaid
sequenceDiagram
    participant Browser
    participant App as script.js
    participant Server as Local HTTP Server
    
    Browser->>Server: Request /index.html
    Server-->>Browser: Return HTML Structure
    Browser->>App: DOMContentLoaded Triggered
    
    App->>Server: fetch('imageslinks?t=CACHE_BUSTER')
    Server-->>App: Return Plain Text (URLs)
    
    App->>App: Parse text into Array
    
    loop For Every Image URL
        App->>App: Calculate Random Price (₹5k - ₹80k)
        App->>App: Assign Random Rating (4.0 - 5.0)
        App->>App: Construct Product Card HTML
        App->>Browser: insertAdjacentHTML into #products-container
    end
    
    App->>Browser: Attach Cart & Bookmark Event Listeners
```

### 3. Component Structure
Each product card is built dynamically. Here is a visual representation of how the `imageslinks` file provides data for the generated components.

```mermaid
classDiagram
    class ImagesLinks {
        +Line 1 : URL
        +Line 2 : URL
        +Line N : URL
    }
    
    class Script_JS {
        +fetchLinks()
        +parseLines()
        +attachCartEvents()
    }

    class GeneratedProductCard {
        <<HTML Component>>
        +Image : Pinterest URL
        +Title : String (Cycled)
        +Description : String
        +Price : Number (Random)
        +Rating : Number (Random)
    }
    
    ImagesLinks "1" --> "*" GeneratedProductCard : Supplies Image Source
    Script_JS --> GeneratedProductCard : Generates & Injects
```

## <img src="https://api.iconify.design/mdi:rocket-launch.svg" width="24" height="24" align="center"> Running the Project Locally

1. Open your terminal in the project folder.
2. Start a local server:
   ```bash
   python3 -m http.server 8000
   ```
3. Open your browser and navigate to `http://localhost:8000`.
