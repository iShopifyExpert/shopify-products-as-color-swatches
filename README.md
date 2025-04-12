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

1. Create a snippet called colors-as-products.liquid
2. Copy the main code into a Shopify snippet
3. Find this in Sections > main-product.liquid
```liquid
   {%- when '@app' -%}
```
and replace with this
```liquid
   {%- when 'custom_product_varient' -%}
     {% render 'colors-as-products', product: product, block: block %}
   {%- when '@app' -%}
```
4. Need to add the schema also
```json
"blocks": [
    {
      "type": "@app"
    },
    {
      "type": "custom_product_varient",
      "name": "custom_product_varient",
      "limit": 1,
      "settings": [
        {
          "type": "textarea",
          "id": "all_colors",
          "default": "red,blue",
          "label": "Add All Color"
        },
      ]
    },
]
```
🖼 Example Handle Structure
Your product handles should follow a consistent naming pattern, such as:

      aka-mens-solid-polo-shirt-classic-fit-black
      aka-mens-solid-polo-shirt-classic-fit-navy

✅ Requirements
You must use consistent product handles where the color name can be replaced.
Colors in the list must match those in the URL (handleized format).

