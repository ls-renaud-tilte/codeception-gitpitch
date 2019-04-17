# Introduction to Codeception

_2019/04/17_

---

### Presentation Summary

- The different types of tests
- Codeception for Retail
- Codeception code structure
- Codeception for UI testing

---

### The different types of tests - The pyramid
![testing pyramid](http://thelatestsoftwaretestingnews.co.uk/wp-content/uploads/2018/07/Screen-Shot-2018-07-04-at-10.35.26.png)

---

### The different types of tests - State of the "art"

- Unit tests => PHPUnit
- Integration / Functional / API / Feature tests => currently using a mix of internal test framework (PHP), and pytest 
- GUI / Acceptance tests => currently none

---

### The different types of tests - Where we want to go

- Unit tests => PHPUnit
- Functional tests (Consolidation of everything that is not unit nor UI tests) => Codeception suites and pytest
- Acceptance tests => Codeception suites or pytest

---

### The different types of tests - Where we want to go

**It is actually very important to draw the line defining the responsibility of developers and the one of TAs**

---

### Codeception for Retail

- Currently we have ~100 functional tests that are covering every single entry point of the Retail application
- All tests are in a single suite
- Helper classes have been created to support current functional tests

---

### Codeception code structure - Cept files

- No OOP structure, equivalent to single scripts
- Everything is very sequential, can be used to test user workflows the same way pytest is working
- Access to Helper classes, DB (for assertions and seeding/setup/teardown), Redis/Memcache ...
- If tests are part of Retail codebase, possibility to bootstrap the application and use fixture generators

---

### Codeception code structure - Cest files

- Use OOP to test pieces of the application in small chuncks
- Possibility to test as many scenarii as we want in a single class
- Same access to Helper classes, DB and other component if required
- Possibility to bootstrap the retail application to get access to fixture generators

---

### Codeception code structure - Intuitive functions

```php
$I->amOnUrl('https://www.google.com');
$I->sendGet($endpoint, $payload);
$I->seeResponseCodeIs(200);
$I->seeElement("//xpath/to/element");
```

---

### Many debugging tools for developers writing tests

- `-- steps` option to out the full sequence of steps included in the test
- `--debug` for a verbose output
- Codeception provides the `codecept_debug()` function that will print additional data in the console