# PHP Notes

<?php

/* PHP NOTES */

$variable = 123; //All variables will begin with "$"
$variable2 = "String"; //They can be numbers, strings, or arrays
$variable3 = array("One", "two", "three"); // Example of an array
$variable4 = array(array('1', '2', '3'), // Arrays can be nested
                   array('4', '5', '6')); // inside other arrays
echo $variable4[0][2]; // echos "3" (First array, third value)
                
/* Arithmetic Operators */
// +,-,*,/ are used for Addition, subtraction, multiplication, division
// % is used as a modulus (the remainder after a division)
// ++ increments and -- decrements
// ** Is used to indicate an exponent/power

// Assignment Operators
// =, +=, -=, *=, /=, .=, %=

// Comparison Operators
// ==, !=, >, <, >=, <=
// <> (is not equal to)
// === (is identical to)
// !== (is not identical to)

// Logical Operators
// &&, and
// ||, or
// ! (not)
// xor (exclusive or)

// String types
// Single quotes = literal string
// Double qutoes = value of variables included (can be escaped with \)

// Multi-line commands can be made with "....." or <<<_END ..... _END;

define("CONSTANT", "blah"); // define global constant
$constant = CONSTANT;
// Predefined constants include __LINE__, __FILE__, __DIR__, __FUNCTION__, __CLASS__, __METHOD__, __NAMESPACE__

// print vs echo
// cannot use echo in $b ? print "TRUE" : print "FALSE";

function longdate($timestamp){ // function function_name([parameter [, ...]]) - parameters are optional
    $date = date("l F jS Y", $timestamp);
    return "The date is $date";
    static $static = "This can store value for future iterations";
}

global $GLOBAL_VAR;
// Superglobal Variables include $GLOBALS, $_SERVER, $_GET, $_POST, $_FILES, $_COOKIE, $_SESSION, $_REQUEST, $_ENV

htmlentities($_SERVER['HTTP_REFERRER']); // converts all special characters to HTML entities (&gt;, etc.)

if ($if = 2){

}
elseif ($elseif = 1){
    echo "do this";
}
else {
    echo "this is an else statement";
}

switch ($switch){
    case "Case1":
        echo "This is case 1";
    break;
    case "Case2":
        echo "case 2";
    break;
    default:
        echo "this is the default";
    break;
}

while ($number > 1){
    echo "greater than 1";
}

do
    echo "test";
while ($number >=1);

for ($initialize = 1 ; $condition <=12 ; ++$modification) {
    echo "test";
    if ($something == FALSE) break;
}

$object = new User; // To create an object with a specified class, use the "new" keyword
$object->name   = "Bob"; // Accessing an object's property
class Something { // Declare a class like this
    public $name, $password; // Property that can be references anywhere, including other classes and instances of the object
    protected $stuff, $things; // Can be referenced only by the object's class methods and those of any subclass
    private $secret, $privates; // Can be referenced only by methods within the same class
    function save_user() { // function inside of class
        echo "Code to save user data goes here"; // statement within function
    }
    function __construct($param1, $param2) // Constructor, initializes various properties
    {
        echo "this is a constructor";
    }
    function __destruct() {
        echo "destruction code here";
        const RANDOM = 1234; // define local constant
    }
}

$_GET

echo ;

?>
