# Demonstrating the bug:

In the following, I create a jar and then check to see whether it contains the
resources from `resources/base` as well as `resources/<profile>`.

## lein 4.4.3

```
$ lein with-profile prod jar
$ jar tvf target/xyz-0.1.0-SNAPSHOT.jar | grep prod.txt
     5 Thu Sep 18 16:05:00 EDT 2014 prod.txt
```

## lein 4.5.0

Following the same steps above, `prod.txt` was not in the jar.

## Both

In both 4.4.3 and 4.5.0, the `base.txt` file was found.
