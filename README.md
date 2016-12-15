# algorithms-
algorithms that i solve either from code wars or coderbyte.  I try to do at least 2 a day and add them on. 

// Make a function that reverse an array without using the reverse method 
//and without putting it into another array.  
function reverseArrayInPlace(arr){
  var l=arr.length*2, d=arr.length;
  for (var i=0; i<l; i+=2){
    arr.unshift(arr[i]);
  }
  for (var i=0; i<d; i++){
       arr.pop();
       }
  return arr;}
var arrayValue = [1, 2, 3, 4, 5];
reverseArrayInPlace(arrayValue);
console.log(arrayValue);
//-->[5,4,3,2,1]

//You are boarding a train and your friend wants to know how long until you arrive.  Round the answer to the nearest half hour.   
// answer "The train will be there in ? hours."
function reachDestination(distance, speed) {
	var x=distance/speed;
  x=(Math.round(x*2))/2;   
  // this rounds it to the nearest half or whole number .
  return "The train will be there in " + x + " hours.";
}
console.log(reachDestination(74,20));
//-->The train will be there in 3.5 hours.
// a pretty simple one.  the hardest part was finding a way to round to the nearest half or whole number. 

//you are given a number and you need to return two arrays.  
//The first will have any number that when squared equals a factor of the number given or the number itself.
// the second array will have any numbers that when cubed equal a factor or the number itself. 
function factor(n) {
  var factors=[], sq=[], cub=[];
  for (var i=0; i<=n; i++){
    for(var d=0; d<=n; d++){
      if (i*d===n){ factors.unshift(d);}
    }
  }
  factors.shift();
  for (var i=2; i<=n; i++){
    if (factors.indexOf(i*i)!=-1){ sq.push(i);}
  }
  for (var i=2; i<=n; i++){
    if(factors.indexOf(i*i*i)!=-1){cub.push(i);}
  }
  return [sq, cub];
}
console.log(factor(81));
//-->[[3, 9], [3]]

///shorter version of the above function 
function factor(n) {
  var factors=[], sq=[], cub=[];
  for (var i=0; i<=n; i++){
    for(var d=0; d<=n; d++){
      if (i*d===n){ factors.unshift(d);}
    }
  }
  factors.shift();
  for (var i=0; i<=Math.sqrt(n); i++){
 		if(Math.sqrt(factors[i])%1===0){ sq.push(Math.sqrt(factors[i]))};
    	if(factors.indexOf(i*i*i)!=-1){cub.push(i);}
  }
  return[sq, cub];
}


//The function should take one parameter: an object/dict with two or more name-value pairs which represent the members of the group and the amount spent by each.
//The function should return an object/dict with the same names, showing how much money the members should pay or receive.
//round decimals to the 2nd place
function splitTheBill(x) {
    var t= 0,a=0;
    for( var i in x){
      t=t+x[i];
      a+=1;
    }
  t=t/a;
  for(var i in x){
    x[i]= (t-x[i])*-1;
    if(x[i]===0){x[i]*-1}
    x[i]=1*x[i].toFixed(2);
  }
	return x;
}
var a={
    A: 40, B: 25, X: 10
}
console.log(splitTheBill(a));
//-->{A: 5, B: 0, C: -5}

//you are given two strings and you need to creat a function that adds these two strings
//together, sorts them from a-z, and gets rid of any duplicates.
function longest(s1, s2) {
  var ar=(s1+s2).split("")
  ar=ar.sort()
    ar=ar.filter(function (c,i,a){ if(c!=a[i+1]){ return c;} })
  return ar.join("");
}
var a = "xyaabbbccccdefww";
var b = "xxxxyyyyabklmopq";
console.log(longest(a,b));
//-->"abcdefklmopqwxy"

//creat a function that takes a number and returns the number in the descending order.
function descendingOrder(n){
  var ar=n.toString().split("").sort(function(a,b){ return b-a;}).join("");
  return ar*1;
}
console.log(descendingOrder(1254859723));
//Input: 145263 Output: 654321
//Input: 1254859723 Output: 9875543221

//create a function that counts the number of vowels in a string and returns the number.
function getCount(str) {
  var c = 0, v=["a", "e", "i", "o", "u"];
  str=str.toLowerCase().split("");
  for(var i=0; i<str.length; i++){
    for(var d=0; d<v.length; d++){
      if(str[i]===v[d]){ c++;}
    }
  }
  return c;
}
console.log(getCount("abracadabra"));
//-->5
//this is a better version using regular expressions.  
function getCount(str) {
  return str.match(/[aeiou]/gi).length;
}

//you are given a start and end number and you should return the count of all numbers from the start to the end,
// except numbers with a 5 in it. The start and the end number are both included in the count
function dontGiveMeFive(x,y){
 var arr=[], n=0;
  for (var i=x; i<=y; i++){
    n=i.toString().split("");
  	if(n.indexOf("5")===-1){
      arr.push(i);
    }
  }
  return arr.length;
}
console.log(dontGiveMeFive(4,17));
//dontGiveMeFive(1,9) -> [1,2,3,4,6,7,8,9] -> Result 8
//dontGiveMeFive(4,17) -> [4,6,7,8,9,10,11,12,13,14,16,17] -> Result 12

//Given an array of numbers, return an array, with each member of input array rounded to 
//the nearest number, divisible by 5.return the list with all numbers rounded to nearest 0 or 5
function roundToFive(num){
  var x=0,y=0
  for(var i=0; i<num.length; i++){
    x=num[i].toString().split("");
    if(x[x.length-1]>5){ x[x.length-1]-=5;}
    if(x[x.length-1]>=2.5){
      num[i]=Math.ceil(num[i]);
      while(num[i]%5!=0){
        num[i]+=1;
      }
    }
    else {
      num[i]=Math.floor(num[i]);
      while(num[i]%5!=0){
        num[i]-=1;
      }
  }
  }
  return num
}
console.log(roundToFive([2,46,8,71.3]));
//-->[0, 45, 10, 75]

//you have to create a function that will produce a multi-dimensional array out of the 
//four digit number given. Each inner dimension of the array represents an individual 
//digit from the given number, and will include all numbers that come before it, going back to 0.
function counterEffect(hitCount) {
 var arr=String(hitCount).split(""),na=[], ans=[];
 for(var i=0; i<arr.length; i++){
   	for(var d=0; d<=arr[i]; d++){
     na.push(d);
    }
   ans.push(na);
   na=[];
 }
  return ans;
}
console.log(counterEffect("0050"));
//-->[[0,1],[0,1,2],[0,1,2,3,4,5],[0]]);
//input=("0050"),  answer= [[0],[0],[0,1,2,3,4,5],[0]]);
//input=("0000"),  answer=[[0],[0],[0],[0]]);

//Your task is to write an update for a lottery machine. 
//Its current version produces a sequence of random letters and integers (passed as a 
//string to the function lottery()). Your code inside lottery() must filter out all 
//letters and return unique integers as a string. 
//If there are no integers in the string return - “One more run!”.
function lottery(str){
  var ar=str.split(""), ans=""
  for (var i=0; i<ar.length; i++){
    if(isNaN(ar[i]) === false && ans.split("").indexOf(ar[i])===-1){ 
      ans= ans + ar[i];}
  }
  if (ans.length===0){ return "One more run!";}
  return ans 
}

console.log(lottery("wQ8Hy0y5m5oshQPeRCkG"))
//-->"805"
//input=("hPrBKWDH8yc6Lt5NQZWQ"), answer="865"
// input="ynMAisVpHEqpqHBqTrwH", answer="One more run!"

function lottery(str){
  var ar=str.replace(/[a-z]/gi, "");
 	ar=ar.split("").filter(function (c,i,a){ return a.indexOf(c)==i;}).join("");
  if(ar.length===0){ return "One more run!";}
  return ar
}

//Is every value in the array an array?
//This should only test the second array dimension of the array. The values of the 
//nested arrays don't have to be arrays.
function arrCheck(x){
  var ans=true;
  for (var i=0; i<x.length; i++){
    if(Array.isArray(x[i]) != true){
     return false;
    }
  }
  return ans
}
console.log(arrCheck([{1:1},{2:2}]));
//[[1],[2]] => true
//['1','2'] => false
//[{1:1},{2:2}] => false

// a better version of the funciton above using the Each() method for arrays (that i just learned)
function arrCheck(x){
  return x.every (Array.isArray);
}

//write a function that finds the ascii value of a given name where a=65 and A=97.  Any 
//character that is not in the alphabet= 0.
function getWeight(name){
  var val={a:65, b:66, c:67, d:68, e:69, f:70, g:71, h:72, i:73, j:74, k:75, l:76, m:77, n:78,
         o:79, p:80, q:81, r:82, s:83, t:84, u:85, v:86, w:87, x:88, y:89, z:90};
	var s=name.replace(/\s/, "").trim().split(""), ans=0,x=0;
  for(var i=0; i<s.length; i++){
    x=s[i];
    if(val[x]==undefined && val[x.toLowerCase()]==undefined){ continue;}
    if (s[i].toLowerCase()!=s[i]){
        ans+=32;
    	x=s[i].toLowerCase();}
   ans+=val[x];
    }
  return ans
}
console.log(getWeight("Joe"))
//--> 254
//console.log(getWeight("J45 oe*&")) -->254
//console.log(getWeight("CJ"))// 205);
//console.log(getWeight("cj"))// 141);
// this one was a little tougher than the last few.  

// write a funciton that is given a string and a horizontal value(k) and a vertical value(v).
// the horizonatal value is number of times you should repeat each character, except for "\n".
// Ex: if k=2 and the string is "abc".  the result should be "aabbcc".
//the vertical value is the number of times you should repeat each section of letter between the "\n"
// Ex: if v=2 and the string given is "abc\ndef\nji".  you answer should be 
//"abc\nabc\ndef\ndef\nji\nji".
// so if you are given a string "abc\nde", k=2, v=2.  then your answer should be this
//"aabbcc\naabbcc\nddee\nddee"
function scale(string, k, v) {
 if(string.length===0) { return string;}
  a= string.split(""),arr=[],ar=[],y="",x="";
  for (var i=0; i<a.length; i++){
    for (var d=0; d<k; d++){
      if(y!="\n"){
      y+=a[i];
    }; }
    ar.push(y);
    y="";
  }
	ar=ar.join("").split("\n");  
  for (var i=0; i<ar.length; i++){
    for(var d=0; d<v; d++){
    	x= x+ar[i]+"\n";
    }
    arr.push(x);
    x="";
  }
 arr=arr.join("").split("");
  arr.pop();
  arr=arr.join("");
  return arr
}
var a = "abcd\nefgh\nijkl\nmnop"
console.log(scale(a,2,3));
//--> "aabbccdd\naabbccdd\naabbccdd\neeffgghh\neeffgghh\neeffgghh\niijjkkll\niijjkkll\niijjkkll\nmmnnoopp\nmmnnoopp\nmmnnoopp"

//Your task is to write a function which returns the sum of following series upto the 
// nth term(parameter). Series: 1 + 1/4 + 1/7 + 1/10 + 1/13 + 1/16 +...
//You need to round the answer upto 2 decimal places and return it as String.
//If the given value is 0 then it should return 0.00
function SeriesSum(n){
  if(n===0){ return "0.00";}
  var arr=[1],x=0;
  for (var i=1; i<n; i++){
    arr.push( 1/(4+x));
    x+=3;
  }
  arr=arr.reduce(function (tv, cv) { return tv+=cv;});
  return arr.toFixed(2);
}
console.log(SeriesSum(1))//--> "1.00"
console.log(SeriesSum(2))//--> "1.25"
console.log(SeriesSum(3))//--> "1.39"
console.log(SeriesSum(4))//--> "1.49"

//this is a shorter version of the above function.  I don't know why i put it into an array first. 
function SeriesSum(n){
  var x=0;
  for (var i=0; i<n; i++){
   x=x+1/(1+i*3);
  }
 return x.toFixed(2);
}

//Given a number, return the maximum value by rearraning it's digits.
function rotateToMax(n){
  n=n.toString().split("").sort(function (a,b){ return b-a;}).join("");
  return n*1;
}
console.log(rotateToMax("001"))
//-->321
//(786) --> 876
//("001") --> 100

