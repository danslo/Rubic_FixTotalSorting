Rubic_FixTotalSorting
=====================

When defining a [custom sorting function](https://github.com/LokeyCoding/magento-mirror/blob/94e611e127d5c14008990b256ed06ded622dcee9/app/code/core/Mage/Sales/Model/Config/Ordered.php#L205) in PHP, one can return the number 0 to state that the two parameters are equal to eachother. The [PHP Docs](http://www.php.net/manual/en/function.usort.php) say the following about that:

```
Note:
If two members compare as equal, their relative order in the sorted array is undefined.
```

Since PHP assumes the first argument is less than the second when we return 0, and HHVM assumes it is greater, we will get inconsistent sorting results due to the undefined behavior.

It's not certain if HHVM will merge a ([currently pending](https://github.com/facebook/hhvm/pull/2484)) patch that makes it follow PHP's behavior, so for now the fix is to explicitly specify after / before directives to get them to align with both runtimes.
