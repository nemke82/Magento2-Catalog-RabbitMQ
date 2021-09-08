# Magento2-Catalog-RabbitMQ
Patch to convert product_action_attribute.update and product_action_attribute.website.update consumers from MySQL to RabbitMQ Broker

-- To apply patch --

Add the cweagans/composer-patches plugin to the composer.json file.
```
composer require cweagans/composer-patches
```

Edit the composer.json file and add the following section to specify:
```
    "extra": {
        "magento-force": "override",
        "patches": {
            "magento/module-catalog": {
                "Catalog-RabbitMQ: product_action_attribute.update and product_action_attribute.website.update conversion to amqp": "https://raw.githubusercontent.com/nemke82/Magento2-Catalog-RabbitMQ/main/module-catalog.patch"
          }    
```
Text is added in the "extra": { section, with following content:

Explanations: <BR>
Module: "magento/module-name"   ← That’s the Magento 2 Core module we are patching <BR>
Title: We link this with internal subject name. <BR>
URL to patch: That’s link from above and our demo repository. <BR>
<BR>
Apply the patch. Use the -v option only if you want to see debugging information.
```
composer -v install
```

Update the composer.lock file. The lock file tracks which patches have been applied to each  Composer package in an object.
```
composer update --lock
```
