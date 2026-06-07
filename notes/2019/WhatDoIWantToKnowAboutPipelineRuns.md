# What do I want to know about pipeline runs?

## Pipelines & Activities

* Is it failing?
* How many records got moved?
* What highwater mark value is it using?
* How long is it taking?
* Which activities are failing?
* What errors are we getting?

## Safran Oracle

* ```select count(*) from safransa.activities;```
* ```select count(*) from safransa.activities where ora_rowscn >= 50675529;```
* ```select SCN_TO_TIMESTAMP(50675529) from dual;```
* ```select count(*) from safransa.activities where ora_rowscn >= 54920218;```
* ```select max(ora_rowscn) from safransa.activities;```
