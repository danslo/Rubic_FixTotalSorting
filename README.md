IMPORTANT
=========

This bug has been solved, and proper behavior can be enabled by passing ``-vEval.EnableZendSorting=1`` to HHVM. This module is no longer necessary and only exists for historical purposes.

Rubic_FixTotalSorting
=====================

It's not certain if HHVM will merge a ([currently pending](https://github.com/facebook/hhvm/pull/2484)) patch that makes it follow PHP's behavior, so for now the fix is to explicitly specify after / before directives to get them to align with both runtimes.
