# Shopify Products as Color Swatches

This Shopify Liquid snippet dynamically displays related products as clickable color swatches. Each swatch links to a separate product page representing the same product in a different color.

## ✨ Features

- Automatically detects current product's color from the URL
- Replaces color keywords in the handle to find other product URLs
- Prevents duplicate swatches even if colors or handles overlap
- Renders a swatch using the second image (or fallback to featured image)
- Only shows the "Color" label if valid alternate swatches exist

## 🧠 How It Works

1. You define a list of all color names (as a comma-separated string).
2. The script detects the current color from the product handle.
3. It loops through all other colors, replaces the current color in the handle, and checks if those product handles exist.
4. Valid matches are rendered as swatches with image previews and links.

## 💡 Usage

1. Copy the main code into a Shopify snippet or section.
2. Update the `colors` variable with all colors used across your product handles:
   ```liquid
   {% assign colors = 'Black,White,Red,Blue,Navy,Turquoise,...' | split: ',' %}
