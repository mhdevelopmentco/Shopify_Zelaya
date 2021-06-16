Zelaya - Shopify
===================================

Full Site with given design files.
Included design files in design folder.

Project Period
----------------------
- Start: 2016.9.22
- Updated: 2016.10.12
- Finished: 2016.10.25

## Environment
- CMS: Shopify
- Theme: Zelaya_v1.0
- Site Link: [ZelayaNewYork](https://zelayanewyork.com/)

## Project History

- Added Page Template: Home, News, About, Contact, PreOrder
- Added Pre-order Feature

## How to do pre orders on Shopify

### Authorize Pre order Payments

Do not capture payments for pre orders immediately until a customer is aware that the product they are ordering is out of stock. You can allow the payments without capturing funds until you have the product ready to dispatch.

- Go to Shopify Admin, click Settings, then click Payments
- Search for Payment Authorization Section
- Click Manually capture payment for orders
- Click Save

Note: The authorization period for Shopify is 7 days. For longer duration, use third part payment gateway.


### Create a pre order product page template

A new product template is created to change the Add to cart button for the pre order products

- Go to Shopify admin, click Online Store, then click Themes
- Click Actions for the theme you want to edit, then click Edit Code
- Templates directory —-> Add a new Template
- Select product from the dropdown menu, and name the template as pre-order
- Click Create template. Your new pre-order.liquidtemplate will open in the code editor.
- Look for the code:

```
	{% section ‘product-template’ %}
```

Change it to:

````
	{% section ‘product-pre-order-template’ %}
````

- Click Save.
- Section directory —-> Add a new Section. Enter product-pre-order-template in the field given
- Click Create Section. Code editor will open. Delete all the default to empty the file
- Section Directory —-> click product-template.liquid —-> Copy all the content —> Paste to product-pre-order-template.liquid
- Search for Add to cart button text, in the product-pre-order-template.liquid file and change it to as below:

- Search for this code:
````
	<span id=”AddToCartText”>{{ ‘products.product.add_to_cart’ | t }}</span>
````

- Change it to:
````
	<span id=”AddToCartText”>{{ ‘Pre-order’ | json | remove: ‘”‘ }}</span>
````

- Then, in the same file find:
````
	addToCart: {{ ‘products.product.add_to_cart’ | t | json }}
````
Change it to:
````
	addToCart: {{ ‘Pre-order’ | json }},
````

- Finally, click Save

### Assign Template to a product

- Go to Shopify admin —-> Click Products
- Click the name of the product you want to make available for pre-order.
- Go to Theme Templates section, Change products to product.pre-order
- Click Save
 

### Edit Inventory Levels

To edit the inventory level of the product, that has inventory amount 0, but you still want customers to purchase it as pre-orders. Then follow the following steps:

- Go to Shopify admin —-> Click Products
- Click the name of the product you want to make available for pre-order.
- Click Edit

### Product Stock Inventory Policy

- Click Allow customers to purchase this product when it’s out of stock
- Click Save
 