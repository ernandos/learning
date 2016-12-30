# Multiple implements 

A Strategy defines a set of algorithms that can be used interchangeably. Modes of transportation to an airport is an example of a Strategy. Several options exist such as driving one's own car, taking a taxi, an airport shuttle, a city bus, or a limousine service. For some airports, subways and helicopters are also available as a mode of transportation to the airport. Any of these modes of transportation will get a traveler to the airport, and they can be used interchangeably. The traveler must chose the Strategy based on trade-offs between cost, convenience, and time.

```php
<?php

interface Logger {
  public function log($data);
}

class LogToFile implements Logger {
  public function log($data) {
      var_dump('log the data to a file');
  }
}

class LogToDatabase implements Logger {
  public function log($data) {
      var_dump('log the data to database');
  }
}

class LogToXWebService implements Logger {
  public function log($data) {
    var_dump('log the data to ssass');
  }
}

class App {
  public function log($data, Logger $logger = null) {
    $logger = $logger ?: new LogToFile;
    $logger->log();
  }
}
```