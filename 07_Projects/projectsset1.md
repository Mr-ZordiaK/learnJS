# projects related to DOM

## project link
[Click here](https://stackblotz.com/edit/dom-project-chaiaurcode?file=index.html) 

# Solution code

## project 1

```javascript
console.log("Bhavit)

const butt = document.querySelectorAll('.button');
const body = document.querySelector('body');

butt.forEach(function (b) {
  console.log(b);
  b.addEventListener('click', function (e) {
    console.log(e.target);
    body.style.backgroundColor = e.target.id;
  });
});

```

## project 2

``` javascript
const frm = document.querySelector('form');

frm.addEventListener('submit', function (e) {
  e.preventDefault();
  const ht = parseInt(document.querySelector('#height').value);
  const wt = parseInt(document.querySelector('#weight').value);
  const ans = ((wt)/(ht*ht/10000));
  const res = document.querySelector('#results')
  if(ht ==='' || ht <0 || isNaN(ht))
  {
    res.innerHTML = `enter valid ht`
  }
  else if(wt ==='' || wt <0 || isNaN(wt))
  {
    res.innerHTML = `enter valid wt`
  }
  else {if(ans < 18.6) res.innerHTML = `You are Under weight , BMI : ${ans}`
  if(ans >= 18.6 && ans < 25) res.innerHTML = `You are in normal range , BMI : ${ans}`
  if(ans >= 25) res.innerHTML = `You are over weight , BMI : ${ans}`}
});


```

## project 3
``` javascript

const clock = document.querySelector("#clock")
setInterval(function(){
  
  let t = new Date();
  clock.innerHTML = t.toLocaleTimeString()
} , 1000)


```

## project 4

``` javascript

const form = document.querySelector('form');
let prevarr = [];
let randNum = Math.floor(Math.random()*100 + 1);
let rem = 10
let bool = false

form.addEventListener('submit' , function(e){
  e.preventDefault();
  if(!bool)
  {
    const val = parseInt(document.querySelector('#guessField').value)
    verify(val);
    // document.querySelector('#guessField').value = '';
    if(rem===0) 
    {
      // alert("you failed")
      // document.querySelector('#subt').disabled = true;
      endgame();
    }
  }
})

function verify(val) {
  if(val < 1 || val ==='' || isNaN(val) || val>100) {alert("Enter valid No.");
}
else {--rem; 
  checker(val);}
}

function checker(val)
{
  if(val == randNum)
    {
      alert("You guessed it correctly");
      bool = true

    }
    else if(val < randNum)
    {
      prevarr.push(val);
      displayer('a', prevarr , "low" , rem);
    }
    else{
      prevarr.push(val);
      displayer('b' , prevarr, "high" , rem)
    }
}

function displayer(cond , arr , msg , rem)
{
  if('a'){
    document.querySelector('.guesses').innerHTML = prevarr;
        document.querySelector('.lowOrHi').innerHTML = "low"
        document.querySelector('.lastResult').innerHTML = rem
  }
  else{
    document.querySelector('.guesses').innerHTML = prevarr;
      document.querySelector('.lowOrHi').innerHTML = "high"
      document.querySelector('.lastResult').innerHTML = rem
  }
}
function endgame(){
  document.querySelector('#guessField').value = '';
  document.querySelector('#guessField').setAttribute('disabled' , '');
  let np = document.createElement('button');
  np.innerHTML = "Start a new Game";
  document.querySelector('.resultParas').appendChild(np);
  bool = true;
  newgame(np);
}
function newgame(np){
  np.addEventListener('click' , function(e){
    document.querySelector(".lastResult").innerHTML = 10;
    document.querySelector(".guesses").innerHTML = '';
    // document.querySelector(".lowOrHigh").innerHTML=''

    prevarr = [];
    randNum = Math.floor(Math.random()*100 + 1);
    rem = 10
    document.querySelector('.resultParas').removeChild(np);
    document.querySelector('#guessField').removeAttribute("disabled");
    bool = false
  })
}


```