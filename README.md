# magento2-opensource-mirror-lab

This repository will provide useful notes on how to leverage Magento2 OpenSource Mirror repository (https://github.com/roma-glushko/magento2-opensource-mirror) to find differences between
Magento 2 releases.

## Commands

Check whenever step-navigator.js file was changed in 2.3.3 comparing to its state in 2.2.6:

```bash
git diff 2.2.6..2.3.3 -- vendor/magento/module-checkout/view/frontend/web/js/model/step-navigator.js  
```

Get diff file between Magento 2.3.2-p2 version and Magento 2.3.3:

```bash
git diff 2.3.2-p2..2.3.3 > difference.diff
```

Get changes between 2.3.2 and 2.3.2-p2 in Magento packages and without tests: 

```bash
git diff 2.3.2 2.3.2-p2  -- vendor/magento/* vendor/amzn/* vendor/temando/* vendor/klarna/* vendor/dotmailer/*  ":(exclude)*Test.php" ":(exclude)*/tests/*"
```

Get changes in all phtml templates that were done from 2.3.2 to 2.3.2-p2:

```bash
git diff 2.3.2 2.3.2-p2 -- `find . -name '*.phtml'`
```

Get all classes marked as @api from 2.2.0 to 2.3.0:

```bash
git diff 2.2.0 2.3.0 -G "@api"
```

Find all deprecated classes from 2.2.10 to 2.3.3:

```bash
git diff 2.2.10 2.3.3 -G "@deprecated" -- vendor/magento/*
```

Get all deleted files between 2.2.10 and 2.3.3:

```bash
git diff 2.2.10 2.3.3 --diff-filter=D -- vendor/magento/* ":(exclude)*Test.php" ":(exclude)*/tests/*"
```
