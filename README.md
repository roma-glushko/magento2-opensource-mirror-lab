# magento2-opensource-mirror-lab

This repository will provide useful notes on how to leverage Magento2 OpenSource Mirror repository (https://github.com/roma-glushko/magento2-opensource-mirror) to find differences between
Magento 2 releases.

## Prerequisites 
To be able to use the diff commands described in the section below, you will need to clone the [Magento2 OpenSource Mirror repository](https://github.com/roma-glushko/magento2-opensource-mirror) and make sure that you have the branches which you are going to compare in the list of your local branches.
You can significantly speedup the process by using the following commands when cloning the [Magento2 OpenSource Mirror repository](https://github.com/roma-glushko/magento2-opensource-mirror)

```bash
cd ~/Projects/
```

```bash
git clone --mirror https://github.com/roma-glushko/magento2-opensource-mirror.git magento2-opensource-mirror/.git
```

```bash
cd magento2-opensource-mirror
```

```bash
git config --bool core.bare false
```

```bash
 git checkout 2.3.3
```

This way you will [clone repository with all remotely tracked branches.](https://git.wiki.kernel.org/index.php/Git_FAQ#How_do_I_clone_a_repository_with_all_remotely_tracked_branches.3F)
   
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
git diff 2.2.10 2.3.3 --diff-filter=D -- vendor/magento/* ":(exclude)*Test.php"
```
