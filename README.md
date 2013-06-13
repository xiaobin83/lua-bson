## Introduction

This is a simple BSON library for Lua. 

## Building

```
make win
```
or
```
make linux
```

## Types

<table>
<th>Lua Type</th><th>BSON Type</th><th>Notes</th>
<tbody>
<tr><td>bson.null</td><td>Null</td><td></td></tr>
<tr><td>boolean</td><td>Boolean</td><td></td></tr>
<tr><td>number</td><td>Double</td><td></td></tr>
<tr><td>number</td><td>32-bit integer</td><td></td></tr>
<tr><td>number</td><td>64-bit integer</td><td>precision lost</td></tr>
<tr><td>string</td><td>String</td><td></td></tr>
<tr><td>table</td><td>BSON Document</td><td></td></tr>
<tr><td>table</td><td>BSON Array</td><td>Lua table must be a sequence. (Continuous number key base 1)</td></tr>
<tr><td>bson.date(os.time())</td><td>UTC Datetime</td><td>milliseconds since epoch</td></tr>
<tr><td>bson.timestamp(os.time())</td><td>Timestamp</td><td>special mongodb type, two 32-bit number</td></tr>
<tr><td>bson.regex(regex,option)</td><td>Regular Expression</td><td></td></tr>	
<tr><td>bson.objectid()</td><td>ObjectID</td><td><a href="http://www.mongodb.org/display/DOCS/Object+IDs">MongoDB document ID</a></td></tr>
<tbody>
</table>

## Getting started

See test.lua