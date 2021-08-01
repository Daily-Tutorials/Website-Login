# HTML Website-Login

Hello and welcome to my first Tutorial!

Today, I'll be showing how to make a "Website-Login" Prompt.

here's a preview:
![Passcode login](https://user-images.githubusercontent.com/88277347/127772493-124be5d7-a863-4923-8be8-b9f02c48acad.png)


On something like, for example, "an IP camera".

If you try to preview by browser, It'll prompt you to 
enter a username and password.


First, the natural way. here are is a way of doing this:

# 1: The real way (HTML)

#### Full source code [here](source-code)

1. Go to your favorite HTML editor >
2. Create a new file. >
3. Name the file "web-login.html" >
4. begin coding (steps below)

## Coding it with HTML/JavaScript
Make a **.js** file for **JavaScript**

on the first **JavaScript** line, write:
```
window.onload = function(){
prompt("Title of the box here", "");
}
```

_before_ the window loads, It'll make a popup box called "Title of the box here",

_Replace "Title of the box here",_ with your title.

**Notice:** The 2nd line after the title, is blank. You want to keep it blank because that's the text box for the passcode.

The page will keep loading until the box is gone.

## Make incorrect passcode attempt

in your **HTML** file, write:
```
<input type="text" id="your_id" />
```

let me explain,

The textbox "`<input>`" tag you just made, it's very important in our project. 

When you type the text in the **prompt** box, it'll return it's value to the box.

But the box is visible! 

**Add CSS:** 

```
<input style="display: none;" type="text" id="your_id" />
```

## How to return the value to the textbox?

In your **JavaScript** file, replace the first step "`window.onload = function { prompt(...); }`",
with: 
```
var passcode = prompt("Title of the box here", "");
```
the prompt will still appear before the page loads.

next, write:
```
document.getElementById("your_id").value = passcode;
```
It's taking the prompt box value from the user, and giving it to the text box value.

now, we need to test the value of the box:
```
var passcodeValue = document.getElementById("your_id").value;
```
Now, we have the value stored in a variable.

## Test the passcode
Make a `testPass()` function to test if the input was changed, automatically:
```
window.onload = setTimeout(function(){ testPass() }, 200);

function testPass() {

}
```
Again, in your **JavaScript** file, we need to make an `if` statement:
```
function testPass() {
  if (passwordValue.includes("The_Passcode")) {
  // password is correct
  }
}
```
**Notice:** `The_Passcode`, Change that to the true passcode you want. for example: 52719, or 1ceCr3am.

Now you have a password! But what if someone **didn't** want to use your passcode?

Make an incorrect passcode tester!

###### Test if value is incorrect

It's very simple. We just need an `else` statement after the `if`.

So, on the same **}** bracket the `if` statement ends on, write an `else`:
```
if (password_value.includes("The_Passcode")) {
// password is correct
} else {

}
```
###### make a system that makes it impossible to get in

in the `else` statement, make an alert(), then a page refresh:
```
else {
alert("Incorrect passcode!"");
// then, refresh the page:
location.replace(window.location.href);
}
```
you're probably wondering, why do you need to refresh the page?

if you put in the wrong passcode, it'll tell you it's wrong, 
then, if you put in the right passcode, it'll still tell you it's wrong.
You need to reset the page so there are no issues.

**TADA! ~ You have a prompt system.**

## Replacing the page after correct passcode

just use the "replace page" technique:
```
var page = '<p>Your HTML here.</p>';

function pageContents(NC) {
document.open();
document.write(NC);
document.close();
}
// replace the page
function replacePage() {
pageContents(page);
}
```
when you trigger the correct passcode, just run the `replacePage()` function shown above, and it'll replace the entire page with your HTML contents.

#source-code

```
<input style="display: none;" type="text" id="your_id" />

<script>
var passcode = prompt("Title of the box here", "");

document.getElementById("your_id").value = passcode;

var passwordValue = document.getElementById("your_id").value;

window.onload = setTimeout(function(){ testPass() }, 200);
function testPass() {
if (passwordValue.includes("The_Passcode")) {
replacePage();
} else {
alert("Incorrect passcode!");
// then, refresh the page:
location.replace(window.location.href);
  }
}

var page = '<p>Your HTML here.</p>';

function pageContents(NC) {
document.open();
document.write(NC);
document.close();
}
// replace the page
function replacePage() {
pageContents(page);
}
</script>
```

### Before you go, [here's a live demo!](https://web-login-demo.w3spaces.com/index.html?bypass-cache=1627829062)


### Thanks for checking out this tutorial!
