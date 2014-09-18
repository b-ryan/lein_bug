# Demonstrating the bug:

In the following, I create a jar and then check to see whether it contains the
resources from `resources/base` as well as `resources/<profile>`.

### Create the jar with 'prod' profile

```bash
$ lein clean
$ lein with-profile prod jar
Created /home/vagrant/src/xyz/target/xyz-0.1.0-SNAPSHOT.jar
```

### Check :resource-paths using pprint

```bash
$ lein with-profile prod pprint
...
:resource-paths
("/home/vagrant/src/xyz/resources/prod"
 "/home/vagrant/src/xyz/resources/base"),
 ...
 ```

 Looks good so far!

### Check the contents of the jar for base.txt and prod.txt

 ```bash
$ jar tvf target/xyz-0.1.0-SNAPSHOT.jar | grep '\.txt'
     5 Thu Sep 18 16:04:42 EDT 2014 base.txt
```

Oh noes!
