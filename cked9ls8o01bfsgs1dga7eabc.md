## Build a Journal App w/ Quote Generator

Hello everyone! I will be going through a step-by-step tutorial on how you can plan, design, and build your very own Journal site.

### Prerequisites

*   Beginner to intermediate knowledge in JavaScript
*   An IDE installed

# Planning our Journal App

For this tutorial, we will be making a simple Journal App. And as always, you can make it whatever you want.

To plan our app, we must first outline steps.

*   Create a function that searches through attributes
*   Make a _new XMLHttpRequest()_
*   Parse JSON to HTML
*   Add current year (optional)

## Step 1: function includeHTML()

### **HTML**


```
// element, year, and tag name can be anything you want
<section id="2020"></section>
<section include-html="2019.json"></section>
<section include-html="2018.json"></section>
<section include-html="2017.json"></section>
```


### JS


```
function includeHTML() {
  var z,
    elmnt,
    file,
    xhttp,
    i,
    sect,
    div,
    yearJSON,
    txt = '';
  z = document.getElementsByTagName('*');
  for (i = 0; i < z.length; i++) {
    elmnt = z[i];
    file = elmnt.getAttribute('include-html');
    // new XMLHttpRequest();
    }
 }
```


### JSON


```
{
  "year": 2019,
  "div": [
    { "month": "December", "p": "" },
    { "month": "November", "p": "" },
    { "month": "October", "p": "" },
    { "month": "September", "p": "" },
    { "month": "August", "p": "" },
    { "month": "July", "p": "" },
    { "month": "June", "p": "" },
    { "month": "May", "p": "" },
    { "month": "April", "p": "" },
    { "month": "March", "p": "" },
    { "month": "February", "p": "" },
    { "month": "January", "p": "" }
  ],
  "message": "success"
}
```


## Step 2: new XMLHttpRequest()

### JS

```
var currentYear = [
  { month: 'December', p: '' },
  { month: 'November', p: '' },
  { month: 'October', p: '' },
  { month: 'September', p: '' },
  { month: 'August', p: '' },
  { month: 'July', p: '' },
  { month: 'June', p: '' },
  { month: 'May', p: '' },
  { month: 'April', p: '' },
  { month: 'March', p: '' },
  { month: 'February', p: '' },
  { month: 'January', p: '' },
];

var txt = '';

for (i in currentYear) {
  txt += `
                                <div>
                                    <h3>${currentYear[i].month}</h3>
                                    <p>${currentYear[i].p}</p>
                                </div>`;
}

document.getElementById('2020').innerHTML = `<h2>2020</h2>` + txt;

function includeHTML() {
  var z,
    elmnt,
    file,
    xhttp,
    i,
    x,
    sect,
    div,
    yearJSON,
    txt = '';
  z = document.getElementsByTagName('*');
  for (i = 0; i < z.length; i++) {
    elmnt = z[i];
    file = elmnt.getAttribute('include-html');
    x = document.getElementsByTagName('h2');
    if (x.length === 3) {
      document.getElementById('button').style.display = 'none';
    }
    // new XMLHttpRequest();
    if (file) {
      xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function () {
        if (this.readyState === 4) {
          if (this.status === 200) {
            // parse json
          }
          if (this.status === 404) {
            elmnt.innerHTML = 'Page not found.';
          }
          elmnt.removeAttribute('include-html');
        }
      };
      xhttp.open('GET', file);
      xhttp.send();
      return;
    }
  }
}
```


## Step 3: Parse JSON

### JS

```
var currentYear = [
  { month: 'December', p: '' },
  { month: 'November', p: '' },
  { month: 'October', p: '' },
  { month: 'September', p: '' },
  { month: 'August', p: '' },
  { month: 'July', p: '' },
  { month: 'June', p: '' },
  { month: 'May', p: '' },
  { month: 'April', p: '' },
  { month: 'March', p: '' },
  { month: 'February', p: '' },
  { month: 'January', p: '' },
];

var txt = '';

for (i in currentYear) {
  txt += `
                                <div>
                                    <h3>${currentYear[i].month}</h3>
                                    <p>${currentYear[i].p}</p>
                                </div>`;
}

document.getElementById('2020').innerHTML = `<h2>2020</h2>` + txt;

function includeHTML() {
  var z,
    elmnt,
    file,
    xhttp,
    i,
    x,
    sect,
    div,
    yearJSON,
    txt = '';
  z = document.getElementsByTagName('*');
  for (i = 0; i < z.length; i++) {
    elmnt = z[i];
    file = elmnt.getAttribute('include-html');
    x = document.getElementsByTagName('h2');
    if (x.length === 3) {
      document.getElementById('button').style.display = 'none';
    }
    // new XMLHttpRequest();
    if (file) {
      xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function () {
        if (this.readyState === 4) {
          if (this.status === 200) {
            // parse json
            sect = JSON.parse(this.responseText);
            div = sect.div;
            yearJSON = sect.year;
            for (i in div) {
              txt += `
                                <div>
                                    <h3>${div[i].month}</h3>
                                    <p>${div[i].p}</p>
                                </div>`;
            }
            elmnt.innerHTML = `<h2>${yearJSON}</h2>` + txt;
          }
          if (this.status === 404) {
            elmnt.innerHTML = 'Page not found.';
          }
          elmnt.removeAttribute('include-html');
        }
      };
      xhttp.open('GET', file);
      xhttp.send();
      return;
    }
  }
}
```


## Step 4: Add current year (optional)

### JS

Before all the code we’ve written:


```
var currentYear = [
  { month: 'December', p: '' },
  { month: 'November', p: '' },
  { month: 'October', p: '' },
  { month: 'September', p: '' },
  { month: 'August', p: '' },
  { month: 'July', p: '' },
  { month: 'June', p: '' },
  { month: 'May', p: '' },
  { month: 'April', p: '' },
  { month: 'March', p: '' },
  { month: 'February', p: '' },
  { month: 'January', p: '' },
];

var txt = '';

for (i in currentYear) {
  txt += `
                                <div>
                                    <h3>${currentYear[i].month}</h3>
                                    <p>${currentYear[i].p}</p>
                                </div>`;
}

document.getElementById('2020').innerHTML = `<h2>2020</h2>` + txt;

// function includeHTML()...
```

Please let me know your thoughts down in the comments. Thanks!