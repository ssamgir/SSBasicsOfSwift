
#Basics of Swift Language

##Constants and Variables

In Swift, you make a variable using the var keyword, like this:

### var name = "Suresh"


Functions let you define re-usable pieces of code that perform specific pieces of functionality. Usually functions are able to receive some values to modify the way they work, but it's not required.
Let's start with a simple function

###func favoriteAlbum() 
###{
###    print("My favorite is Fearless")
###}


If you put that code into your playground, nothing will be printed. And yes, it is correct. The reason nothing is printed is that we've placed the "My favorite is Fearless" message into a function called favoriteAlbum(), and that code won't be called until we ask Swift to run the favoriteAlbum() function. To do that, add this line of code:
favoriteAlbum()

That runs the function (or "calls" it), so now you'll see "My favorite is Fearless" printed out.
As you can see, you define a function by writing func, then your function name, then open and close parentheses, then a block of code marked by open and close braces. You then call that function by writing its name followed by an open and close parentheses.
Of course, that's a silly example – that function does the same thing no matter what, so there's no point it existing. But what if we wanted to print a different album each time? In that case, we could tell Swift we want our function to accept a value when it's called, then use that value inside it.
Let's do that now:

###func favoriteAlbum(album: String) 
###{
###  print("My favorite is \(album)")
###}

That tells Swift we want the function to accept one value (called a "parameter"), named "album", that should be a string. We then use string interpolation to write that favorite album directly into our output message.
