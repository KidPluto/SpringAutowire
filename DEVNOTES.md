# Development Notes

* Switched to pay version of IDEA, and now have all sorts of warnings.
  * Didn't like this, had to comment it out. xmlns:tx="http://www.springframework.org/schema/tx"
  * Then it tells me "must have even number of URI's" for schemaLocation values. Found this one.
  * But it still runs, with the same thing not working.  The differentColors bean is not being used.
    * Moving bean definition in applicationContext.xml doesn't make any difference.
    * Defined another bean, still not working.