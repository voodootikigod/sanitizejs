sanitizerjs
===========

A library that properly sanitizes and cleanses a string value to varying level of complexity. This enhances the string prototype so it will be available for all Strings in the environment, which means that it is always available, like good security functions should be.

whitelist
---------

The most stringent and fine grained control of string cleansing and sanitization in the library. This function will allow you to systematically identify which HTML elements and attributes will be allowed as part of the resulting string. This will allow you present semi-rich output without inadvertantly risking security.

To Use:

"<script>aaa</script>".whitelist([{"a"=>["href"]},"b", "attr"])

The parameters to the function allow you to specify an array of allowable tags and for each you can use a JavaScript object with an array of allowable attributes. The above translates to:

Only allow
     "a" tags and only "href" will be allowed
     "b" tags and all attributes will be filtered out
     "attr" tags with all attributes will be filtered out

This provides a very terse, yet flexible method for describing a whitelist of allowable html elements. 

This function will always fail safe either by filtering the attribute values properly and by encoding entities if they cannot be whitelisted.

h
-

HTML entity encode the string, using the standard HTML encodings for characters that would yield problematic if directly output, including &, <, and >.

