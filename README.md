# Azonmedia PHP naming convention

## Introduction

Describes how the classes, methods and properties/arguments/variables should be named.

## Conventions
- as per [Basic Coding Standard](https://github.com/AzonMedia/php-coding-standard) object properties, method arguments and local variables should be named in $snake_case
- as mandated by [Basic Coding Standard](https://github.com/AzonMedia/php-coding-standard) the names that contain abbreviations like HTTP should not be kept in all CAPS. Instead of the Classes should be named like HttpRequest and properties/variables $http_request
- objects should be named $PascalCase. This includes closures/callbacks: `$Callback = function() : void {};`
- no property or variable should start with '_' except if the variable/argument is passed by reference. If an object is passed by reference then the object should be named as usual in $PascalCase without leading _.
- methods can not start with '__' (double underscore) as these should be reserved for future use by PHP.
- methods should not start with '_' as these are reserved for hook names in the framework
- _ in the name of a property or a method does not denote visibility (some projects use '_' to denote private visibility). In the case of variables, it denotes a reference and in the case of methods, it denotes a hook.
- objects that are scope references should always be named in $ALL_CAPS.

## Additional naming conventions related to the content or type of the variable
- variables bearing data for date or time MUST be named to reflect the format of the data as follows:
  * $pickup_date_ymd - YYYY-MM-DD (MySQL format for date)
  * $pickup_date_mdy - MM/DD/YYYY (the standard US date format)
  * $pickup_date_mdy_12time - MM/DD/YYYY 8:30 AM (date with 12 hours time)
  * $pickup_date_mdy_24time - MM/DD/YYYY 16:30 (date with 24 hours or military time)
  * $pickup_date_unixtime - for unixtimestamp (perhaps it would be better to use $pickup_time_unixtime but still allowed)
  * $pickup_time_12time - 8:30 AM (12 hours time)
  * $pickup_time_24time - 16:30 (24 hours or military time)
  * $pickup_time_unixtime - for unixtimestamp
  * $pickup_time_microtime - for `microtime(true)`
- variables that contain periods should be named:
  * $period_seconds
  * $period_minutes
  * $period_hours
  * $period_days
  * $period_weeks
  * $period_months
  * $period_years
- arrays must be named in plural so that this clearly denotes its type like $rows, $days etc. For multidimentional arrays it is preferred a suffix '_arr' like $fees_arr.
- naming reflection instnaces
  * $RClass for an instance of ReflectionClass - `$Rclass = new \ReflectionClass('some_class_name');`
  * $RMethod for an instnace of ReflectionMethod - `$Rmethod = $Rclass->getMethod('method_name');`
  * $RProperty for ReflectionProperty - `$Rproperty = $Rclass->getStaticProperties()[0];`
  * $RFunction for ReflectionFunction
  * $RClassConstant for ReflectionClassConstant
  * $RType
  * $RGenerator
  * $RParameter
  * $RNamedType
  * $RObject
  * $RExtension
  * $RZendExtension

## Classes and namespace conventions
- any class that inherits \Exception MUST have its name ending in "Exception" like RunTimeException
- the exceptions must be always in a separate namespace like Guzaba2\Http\Exceptions\SomeHttpException
- the interfaces must always be in a separate namespace like Guzaba2\Http\Interfaces\RequestInterface
- the interfaces must always end in "Interface" like "RequestInterface"
- the traits must always be in a separate namespace like Guzaba2\Patterns\Traits\ObservableTrait
- the traits must always end in "Trait" like "ObservableTrait"
- abstract classes can be mixed with the other classes. It is optional that the abstract classes contain the Abstract word in their name like Guzaba2\Orm\ActiveRecordAbstract
