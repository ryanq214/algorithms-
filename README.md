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

