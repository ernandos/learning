# COR

The chain-of-responsibility consists of a source of command objects and a series of processing objects. Each processing object contains logic that defines the types of command objects that it can handle; the rest are passed to the next processing object in the chain. A mechanism also exists for adding new processing objects to the end of this chain.

```php
<?php

// it gives us the ability to chain object calls while
// giving each of these objects the ability to end
// the request or send the request up the chain

abstract HomeChecker {
  protected $successor;

  public abstract function check(HomeStatus $home);

  public function succeedWith(HomeChecker $home) {
      if ($this->successor) {
          $this->successor = $successor;
      }
  }
}

class Locks extends HomeChecker {
  public function check(HomeStatus $home) {
      if ( ! $home->locked) {
          throw new Exception('the doors are not locked!');
      }

      $this->next($home);
  }
}

class Lights extends HomeChecker {
  public function check(HomeStatus $home) {
      if ( ! $home->lightsOff) {
          throw new Exception('the lights are on!');
      }

      $this->next($home);
  }
}

class Alarm extends HomeChecker {
  public function check(HomeStatus $home) {
      if ( ! $home->alarmOn) {
          throw new Exception('the alarm are not on!');
      }

      $this->next($home);
  }
}

class HomeStatus {
  public $alarmOn = true;
  public $locked = true;
  public $lightsOff = true;
}

$locks = new Locks;
$lights = new Lights;
$alarm = new Alarm;

$locks->succeedWith($lights);
$lights->succeedWith($alarm);

$locks->check(HomeStatus);
```