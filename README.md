# magento2-opensource-mirror-lab

This repository will provide useful notes on how to leverage Magento2 OpenSource Mirror repository (https://github.com/roma-glushko/magento2-open-source-mirror) to find differences between
Magento 2 releases.

## Commands

Check whenever step-navigator.js file was changed in 2.3.3 comparing to its state in 2.2.6:

```bash
git diff 2.2.6..2.3.3 -- vendor/magento/module-checkout/view/frontend/web/js/model/step-navigator.js  
```

Generate diff file between Magento 2.3.2-p2 version and Magento 2.3.3:
```bash
git diff 2.3.2-p2..2.3.3 > difference.diff
```

Changes between 2.3.2 and 2.3.2-p2 in Magento packages and without tests: 
```bash
git diff 2.3.2 2.3.2-p2  -- vendor/magento/* vendor/amzn/* vendor/temando/* vendor/klarna/* vendor/dotmailer/*  ":(exclude)*Test.php" ":(exclude)*/tests/*"
```

Changes in all phtml templates that were done from 2.3.2 to 2.3.2-p2:
```bash
git diff 2.3.2 2.3.2-p2 -- `find . -name '*.phtml'`
```
