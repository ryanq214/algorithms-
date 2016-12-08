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


