# sloppy and strict equals

```html
@samantha#2997 
```html
<script>
let myBool = true;
let anotherBool = true;
if(myBool+anotherBool+1===3) {
  console.log("bool strictly true")
} else { console.log("bool strictly false")
}
// the above returns true
if(myBool+anotherBool+1==3) {
  console.log("bool sorta true")
} else { console.log("bool sorta false")
}
// the above returns true
// javascript sees boolean data values as 0 for false and 1 for true
// to compute boolean true+true+true it is typecast as numerical 1+1+1.
// the + functions as a mathematical +, so the answwer i smathematical number 3.
// the + has transformed 'true' from boolean to numerical before the strict equals operation occurs
// so to it, the equation looks like: number 3 = number 3
// and this is strictly true so passes both tests
if(1+1+'1'===21) {
  console.log("string strictly true")
} else { console.log("string strictly false")
}
// the above returns false
if(1+1+'1'==21) {
  console.log("string sorta true")
} else { console.log("string sorta false")
}
// the above returns true
// / unalike booleans, strings can only be logicaly added, so the last + is understood as a logical add
// logical addition is One + Two = OneTwo
// mathematical addition is 1 + 2 = 3
// so 1+1=2 is typecast as a string and logically added to '1' to make 21
// 21 as a string does not strictly equal the number 21
// because it is a hybrid of a number and a string, two numbers side by side, read as 'two one'
// that the sloppy equals is treating as the number 21 for the sake of returning a true result
// the === just threw it's hands up because it doesn't put up with ambiguity
// this is useful, because we wouldn't want to confuse 3 and 21 if the result is later used in further math or logic
// so we can see that strict equals is a way of preserving mathematical and logical integrity
// as strings can only be logically added and booleans can only be mathematically added 
// true+"1" does not compute, so cannot pass either test.
</script>
```
