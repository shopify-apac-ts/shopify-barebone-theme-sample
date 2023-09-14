# Overview
This is an _unoffical_ sample code for scratch building [Shopify theme](https://shopify.dev/docs/themes) _without_ [cloning Dawn](https://github.com/Shopify/dawn) for understanding the [theme architecture](https://shopify.dev/docs/themes/architecture) with simpler and fewer [Liquid](https://shopify.dev/docs/api/liquid) code.

If you are a theme beginner and feel it tough to grab the high volume source code of Dawn, this basic theme may work as a tutorial, but you are expected to be familiar with basic HTML / JavaScript / CSS.

# Code structure
The exact same as the [Shopify theme structure](https://shopify.dev/docs/themes/architecture).

For better understanding of the theme mechanism, you should check these first. 

- [Layout](https://shopify.dev/docs/themes/architecture/layouts) = the theme main file
- [Templates](https://shopify.dev/docs/themes/architecture/templates) = each page configuration to render the sections below, most of which are **JSON** files (some are Liquid)
- [Sections](https://shopify.dev/docs/themes/architecture/sections) = each page content written by HTML / JavaScript / CSS with Liquid code, most of which are **Liquid** files (some are JSON)
- [Section schema](https://shopify.dev/docs/themes/architecture/sections/section-schema) = definitions of how each section works with the [theme editor](https://shopify.dev/docs/themes/tools/online-editor)
- [App blocks](https://shopify.dev/docs/themes/architecture/sections/app-blocks) = special blocks in each section to render [theme app extensions](https://shopify.dev/docs/apps/online-store/theme-app-extensions)
- [Dynamic sources](https://shopify.dev/docs/themes/architecture/settings/dynamic-sources) = theme editor function to connect store data instances to liquid objects

# How to run
Just for running this theme on your store, simply download this as a zip to upload to your store. However, most of this theme users must be developers who want to modify the code to apply the change immediately, which can be done by [Shopify CLI](https://shopify.dev/docs/themes/tools/cli) with the following steps.

1. Install the CLI followging the steps in the page above (note that the CLI for theme is different from [the app CLI](https://shopify.dev/docs/apps/tools/cli) given as a npm module).

2. Clone this GitHub repo. or download as a ZIP to extract in your PC.

3. Go to the directory of this theme above to run [shopify theme dev](https://shopify.dev/docs/themes/tools/cli/commands#dev) in your terminal.

4. If you're asked to login, follow the steps and copy and paste the two URLs shown on the CLI output for theme editor and storefront to your browser address bars.

# How to install
The steps above are for development mode that gets terminated once you stop the running, if you install the theme to your store permanently, run [shopify theme push --unpublished](https://shopify.dev/docs/themes/tools/cli/commands#push) to create a new theme named by you in your store (For the second update, the `push` only without the parameter updates the current live theme).

# Sample list
All samples are available at [Wiki](https://github.com/benzookapi/shopify-barebone-theme-sample/wiki).

# Trouble shooting 
- If your change to files are not applied to the theme editor or storefront, make sure the `dev` output of CLI shows `Synced` without errors. 

# TIPS
- Shopify Liquid has [the powerful internationalization features](https://shopify.dev/docs/themes/markets/multiple-currencies-languages), and your liquid object doesn't need to change the code for translation and currencies.
For example, once you access the language path like `/ja`, liquid objects return Japanese translated data such as product titles if they have the translation. Also once you pass the currency and country parameters like `currency=JPY&country=JP`, liquid objects return the price in the specified currency with country.
```
{{ product.title }} returns 'Test product' in `/` in English (when English is the default language), 
does 'テスト商品' in `/ja` in Japanese without accepting any language parameters.

{{ product.price | money_with_currency }} returns $5.00 USD in with after passing `currency=USD&country=US`,
does ¥700 JPY with `currency=JPY&country=JP` without reading those parameters.
```

# Disclaimer
- This code is fully _unofficial_ and NOT guaranteed to pass [the public theme review](https://shopify.dev/docs/themes/store/review-process/submit-theme) for Shopify theme store. The official requirements are described [here](https://shopify.dev/docs/themes/store/requirements).
