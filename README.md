# magento2-opensource-mirror-lab

This repository will provide useful notes on how to leverage Magento2 OpenSource Mirror repository (https://github.com/roma-glushko/magento2-open-source-mirror) to find differences between
Magento 2 releases.

## Commands

Check whenever step-navigator.js file was changed in 2.3.3 comparing to its state in 2.2.6:

```bash
git diff 2.2.6..2.3.3 -- vendor/magento/module-checkout/view/frontend/web/js/model/step-navigator.js  
```
