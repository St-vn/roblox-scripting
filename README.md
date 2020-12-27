# Roblox Scripting
## Written by St_vn#3931, St_vnC(Roblox), St-vn(Github)


### 1.0 Printing

Hello welcome to the introduction on learning how to script in Roblox. To get started, make sure to have both the output and the command bar.

![](https://cdn.discordapp.com/attachments/781561020018851850/781561817049595904/unknown.png)

Write this in the command bar and press enter
```lua
print(1)
```
It would print `1` in the output, 1 is a number. The print function would make anything that is inputed within the brackets.

You can also print mathematical operations or operations of any kind
```lua
print(1+1)
```
`1+1` which we all know is 2 would be printed in the output since it would always output an operation's result when there is one.


### 1.1 Printing words/strings

If you wanted to print words then you'd have to wrap whatever you want to print inside of quotation marks "" or apostrophes ''
```lua
print("hi")
```
If you don't wrap them in any of those then it would print `nil` which means that it doesn't exist, those words are values just like numbers they're called string values and nil is a value as well.

Just like numbers, you can use operators with strings.
```lua
print("hello".. " there")
```
This would print `hello there`, `..` is called string concatenation which is an operation just like `+`.


### 1.3 Variables

Variables, unlike in algebra are defined by you. You use variables to avoid repeat the same tasks to get the same values..
```lua
local variable = "hi"
print(variable) -- hi
```

You can name your variable whatever you want just make sure that it is meaningful so you can remember what it is later. You use the `local` keyword so it makes the variable local which is faster than not using the local keyword. When you reference your variable or redefine it, the local keyword is not needed.

```lua
local x = 10
x = x + 1
print(x) -- 10
```
You can also increment numbers by referencing them and increment by how much you want. Though, there is a better method in Luau(Roblox's version of Lua) to do such tasks. When you have an already existing reference to something, you can use assignment operators.
```lua
local x = 5
x += 2
print(x) -- 7
```
You can also concatenate strings that way.
```lua
local hi = "aaa"
hi ..= "hi"
print(hi) -- aaahi
```


### 2.0 Making your first script and basic properties.

Now that you know about that, you're able to make your first script. Insert a script in the ServerScriptService. click the Plus button on the right when hovering over the SSS and insert a script.

![](https://cdn.discordapp.com/attachments/781561020018851850/781576718527365140/unknown.png)

Now that you're in the script, remove the `print("hello world")` and write the following
```lua
local baseplate = game.Workspace.Baseplate -- note that you can use the workspace variable instead
baseplate.Transparency += .5 -- would increment the baseplate's transparency to .5 assuming it was at 0
baseplate.CanCollide = false
```
Try play testing that code you just copy pasted.

![](https://cdn.discordapp.com/attachments/782001435264942140/792226712418910208/unknown.png)

You will notice there is a semi transparency part and you would no-clip through it. Setting the Baseplate's CanCollide property to false made you no clip through it. When you look in the properties window, you can see that the CanCollide property isn't checked which means that it's set to false. If it is checked then it is true. When a value is either true or false then it's called a bool/boolean value.

Just like strings and numbers they're a type of value(datatype). Now lastly your last question is about the `.` right? Well it's called indexing, when you have a value that has accessible properties then you would be able to index it with something that exists within the value.
```lua
print(workspace.Baseplate.Name) -- Baseplate, you've indexed the baseplate with its Name property which holds a reference to "Baseplate"
```


### 2.1 Datatypes

Datatypes define what kind of value a value is and its characteristics. There are datatypes you won't be able to index like numbers, bools and nil. Stuff that you could find in the explorer window are called Instances. They're a datatype as well, except they're made by Roblox and are considered as userdata to Lua.
```lua
print(type(workspace)) -- userdata, type defines a value's datatype in Lua
```
But if you used `typeof` instead, it would print Instance. That is because typeof accounts for Roblox datatypes as well.
```lua
print(typeof(workspace)) -- Instance
```


### 2.1.5 Roblox datatypes :

So roblox have datatypes of their own that are considered as userdata by Lua. You don't need to worry about userdata. An example would be Vector3 and Instance. Vector3 defines something in 3D space like position, orientation, direction, etc. An instance is what you can see within the explorer, what you can you create with Instance.new() and more. A `Color3` defines something's color and can be created with HSL and RGB while you have a limited amount of colors to pick from when using `BrickColor`. Most datatypes' constructor functions are datatype.new().

[Every Roblox datatype is listed in the API](https://developer.roblox.com/en-us/api-reference/data-types)


### 2.2 Explorer hierarchy

Like you've seen earlier, `game` is at the top of the hierarchy. Direct "descendants" of the DataModel(game) are called "Services", the workspace is an example of a service and so is the Lighting that you see in the Explorer. Here are some services.

![](https://cdn.discordapp.com/attachments/781561020018851850/781579680636862474/unknown.png)


### 2.3 Instances

Instances are what you can see in the explorer, most people know them as objects. They include but aren't limited to parts, particles, meshes, screen guis, frames. To create an instance via code you use the Instance.new() function.
```lua
local part = Instance.new("Part") -- Don't specify the parent within the function because it is slower than parenting it manually
part.Size = Vector3.new(1, 1, 1) -- Vector3 is another datatype
part.Parent = workspace
```
The code above creates a 1 x 1 x 1 part that is parented to the workspace.


### 2.4 Services

Some services provide functions to use like TweenService that can help you with making your game while others are used as a form of storage like the ServerStorage and ReplicatedStorage, there are tons of services that Roblox uses internally that you will never have a need to touch. Not all Services are not visible in the Explorer and you can't get them directly with an index. You'd have to use the :GetService() function.
```lua
game:GetService("RunService") -- run service isnt something that you have to learn about yet.
```


### 2.5 Indexing

In some languages including Lua, you're able to index using square brackets. In most cases you wouldn't be need to use them. You can't index stuff with Names that have a space in them e.g.
```lua
print(workspace.Base plate.Size) -- syntax error
```
You would need to index like this
```lua
print(workspace["Baseplate"].Size) -- some Vector3 value
```
Whatever is between those square brackets would be what you'll be indexing with e.g. a reference to a variable.
```lua
local name = "Baseplate"

print(workspace[name].Transparency) -- 0
```


### 3.0 Numeric loop(for loop)

Now that you know how to perform some basic tasks you would need to know how to perform them multiple times as well. In coding you can loop, it repeats a specified task and would end depending on what kind of loop it is. The most simple of them is the for loop, the numeric loop. In coding it is common sense to not repeat yourself which is the reason that using loops would be useful.  Follow the `DRY` principle (Don't repeat yourself).
```lua
for i = 1, 10, 1 do -- 1, 10, 1 are called arguments
    print(i) -- i means the current iteration/loop
end
```
In terms of arguments, the first defines its origin, the 2nd the end point and the last determines by how many iterations does it skip (it is 1 by default).
```lua
local baseplate = workspace.Baseplate -- better make a variable for the baseplate since you're gonna be referencing it 10 times

for i = 0, 10 do
    baseplate.Transparency = i / 10 -- this would be instantaneous obviously because there isn't a delay of any kind
end

for i = 0, 1, .1 do
    baseplate.Transparency = i
    wait(.1) -- note that the minimum wait time is 1/30 seconds
end
```


### 3.1 Conditions, relational and logical operators

Before you learn about how to use conditional loops you would need to understand how conditions work. Conditions would either return true or false after the series of operations have been made. You would use specific operators to perform conditional operations and such.
```lua
print(workspace.Baseplate.Name == "Baseplate") -- true, checks if the baseplate's name is equal to "Baseplate". also Lua is case sensitive ;)
```
The one operator above is a relational operator, its opposite ~=, is a relational operator as well.
```lua
print(workspace.Baseplate.Name ~= "bruh moment") -- true, Baseplate's name is indeed not equal to bruh moment
```
the other ones, are pretty self-explanatory : `>, <, >=, <=`
Whenever using those operators, a boolean would be returned as the operations' results. You could manipulate those results to get other results by using logical operators aka : `not, or, and`.

`not` negates a bool value, `or` checks if the preceding condition was false and returns the succeeding one. `and` checks for the preceding value and then return the succeeding one regardless of what it is.
```lua
print(not true, not false) -- false, true, false, true
print(false or true, true or false, false or false) -- true, true, false
print(true and true, false and true, true and false) -- true, false, false
```
In Lua, you could also use logical operators to create stuff like default values
```lua
print(nil or 1) -- 1, being the default value and nil being what you tried to input.
```
This works that way because `nil` is considered as a faulty value by Lua. But it doesn't mean that it is == to false.
```lua
print(false == nil) -- false
print(false == not not nil) -- would negate nil, a faulty value to true and negate it again.
```
That works the same with valid values like numbers and strings.
```lua
print(not 1) -- false
print(1 == true) -- false
print(not not 1 == true) -- true
```
This is what I meant by `and` returning the succeeding value
```lua
print(true and 123) -- 123
```


### 3.1.5 Precedence

Precedence of operators is worth taking a look at, Source : Lua 5.1 docs.

![](https://cdn.discordapp.com/attachments/781561020018851850/781632597776007178/unknown.png)


### 3.2 if statements, elseif and else

Now that you know how conditions work, you're gonna learn how to execute tasks depending on the condition. If statements are used to check conditions and then run the statement in it if the condition was true/valid.
```lua
if true then -- the condition is `true` so it would run
    print("hello there")
end
```
The else statement would only run if all previous conditions were false.
```lua
if false then
    print("lol this wouldn't run")
else
    print("hello there")
end
```
You can have as many elseifs as you want. If the former condition was false, it would check if the current is true and run if that's the case.
```lua
if false then
    print("xd")
elseif true then
    print("hi")
else
    print("when a condition is true and the code has ran, the rest of the chain would break"
end
```


### 3.3 While loops and repeat until

Since you understand how conditions and if statements work, you're able to understand how `while` loops work. A while loop is a loop that would run indefinitely until the condition is false.
```lua
local x = 5

while x < 1 do -- the condition being x < 1
    x -= 1
    wait(1)
end

print(x) -- 0, the loop needs to break before it can reach this part.
```
while loops have a counterpart in Lua that is called a `repeat until` loop. The only difference is that the condition is checked at the **end of each iteration** and would **break if the condition is met** unlike the while loop that checks for the **condition to be false at the beginning**.
```lua
local x = 2

repeat
    x += 1
until x == 10

print(x) -- 10
```
Of course this is pretty unnecessary because of numeric loops' existence. There are also keywords that you could use to manipulate loops. One of them being `continue` and the other being `break`. So I've used the word break earlier and that's what i meant.
```lua
while true do
    print("hi") -- you would realize that this would print once and not crash roblox
    break
end
```
Another example
```lua
for i = 1, 10 do
    if i == 5 then break end -- wont print 5
    print(i)
end
```
Using continue
```lua
for i = 1, 10 do
    if i == 5 then continue end -- would skip 5 but print the succeeding ones
    print(i)
end
```
Note that continue is a Luau and not a Lua keyword. These keywords work with loops only.


### 4.0 Functions

Functions are tasks that can be executed multiple times. They take arguments, process them and return the results. An example is `print`, print is a function that takes arguments and prints it in the output. `wait` is also a function, it `yields` the thread for x amount of time with a minimum wait time of 1/30 seconds.
```lua
wait(1)
print("a") -- a
```
To make a function you write the keyword `function`, its name and then the parentheses where it would contain parameters(arguments) that you would input.
```lua
function p()

end
```
You can also write
```lua
p = function()

end
```
Except the former is a syntatic sugar version of the latter. This would create a variable that holds a reference to the function. Just like with regular variables, it is better to define it as a local one for the same reasons.
```lua
local function yes()

end
```
To call a function, you do this
```lua
local function PrintWrapper(toPrint) -- parameters
    print(toPrint)
end

PrintWrapper(123) -- 123
```
A wrapper function is a function in a software library or a computer program whose main purpose is to call another second function.


### 4.1 Returning

`return` returns the value at the end of the function and is the last statement within the function, if you try adding statements after it, it would error. An example of a function returning a value would be `math.pow` from the math library.
```lua
math.pow(2, 2) -- returns 2 ^ 2, 4
```
Of course doing 2 ^ 2 is better than calling a function. Here is a remake of this function in Lua.
```lua
local function pow(x, y)
    return x ^ y
end

pow(5, 3) -- 125
```
Some functions, allow a lot of arguments like `math.max` and `math.min`
```lua
print(math.max(1, 5, 6, 9 ^ 2, 25 ^ .5)) -- 81, 9 ^ 2
print(math.min(-2, 55, 0, .25)) -- -2
```
What they return should be self explanatory since I've just show an example of how to use them. Other functions like `math.clamp` need a specific amount of arguments otherwise it would error.
```lua
math.clamp(5 + 5, 1, 7) -- returns the x if it's within the min and max, if it isn't then it would return either the min or max.
math.clamp(2) -- error
```


### 4.2 Parameters and ... in Lua

Parameters work as variables defined by arguments upon a function call. You can also use `...` as a parameter which would remove the need to add extra parameters from the current and the latter ones.
```lua
local function PrintWrapper(...)
    print(...)
end

PrintWrapper(123, true, 0, nil) -- 123, true, 0, nil
```
If you specify the first parameter and use ... afterwards, each parameter after the first would be part of ...
```lua
local function PrintWrapper(parameter1, ...)
    print(..., parameter1)
end

PrintWrapper(123, true, 0, nil) -- true, 0, nil, 123
```
... is considered as a tuple, here is Roblox explaining what a tuple is.

![](https://cdn.discordapp.com/attachments/781886987366957058/792517515649351711/unknown.png)
[Source](https://developer.roblox.com/en-us/articles/Tuple)


### 4.3 Events/Signals and connections

Events/signals, are things that happens within the game/engine, it could fire after a task is done, after an input, etc.

What you can do with events is connecting them to a `callback` and then it would call the callback every time it is fired. An example of an event changing a property. A `callback` is essentially a function that you pass as an argument in another function that you can call when specified.
```lua
workspace.Baseplate.Changed:Connect(function(property) -- returns a connection
    -- task
end)
```
Just like regular functions there would be parameters in the callback function except they are automatically passed by the event. When you connect an event, you get a connection. Signals and Connections in roblox are called `RBXScriptSignal` and `RBXScriptConnection`, they're their respective datatypes that inherit their own methods. A connection can be used to disconnect the event via the `Disconnect` method.
```lua
local connection = workspace.Baseplate.Changed:Connect(function(property)
    print(property)
end)

wait(1) -- wait for seconds to disconnect the function
connection:Disconnect()
```
You can also yield(pause) the current thread by using Signal:Wait(). It would yield until the signal fires.
```lua
print(game:GetService("RunService").Heartbeat:Wait()) -- when the event fires it would return the parameters so it would print the deltatime in our case.
```
Heartbeat fires every frame and you would learn about RunService later on.

### 5.0 Tables

Tables are a datatype that I've mentioned before in here. They are used to store multiple values in them including other tables. To create a table you would use these brackets {}.
```lua
local tubl = {}
```
You would have to insert the values inside of the brackets like u would input arguments in a function call.
```lua
local tubl = {true, "hello"}
```
To access the contents of a table you index it with a number.
```lua
local tubl = {true, "hello"}

print(tubl[1]) -- true
print(tubl[2]) -- hello
print(tubl[3]) -- nil, undefined
```
To define something after the table has been created you'd have to index it as well.
```lua
local tubl = {}

print(tubl[1]) -- nil

tubl[1] = 3

print(tubl[1]) -- 3
```
Defining the values in a table when creating it is better than after table creations because of Luau optimizations. Therefore
```lua
local tubl = {true, "hello"}
```
is better than
```lua
local tubl = {}
tubl[1] = true
tubl[2] = "hello"
```


### 5.1 Packing and unpacking arrays

Arrays are the kinds of tables you've been using so far. You can pack a tuple and get an array with the tuple values as well.
```lua
local function pack(...)
    return {...} -- table.pack already does that and doing {...} is more than enough
end
```
You can do the opposite and unpack arrays as well
```lua
local tubl = {5, true, nil, "hello"}
print(tubl) -- table : hexadecimal address
print(unpack(tubl)) -- 5, true, nil, hello
```


### 5.2 Arrays and dictionaries

Tables are lists like such as a whole, because arrays and dictionaries are considered as tables in Lua. An array is the kind of table you've created so far, with a numeric index. A dictionary is a table with non numeric keys(indices). Usually those keys would be strings. To define a string dictionary you would do
```lua
local dictionary = {
    key = "door" -- haha funny pun
}

print(dictionary.key) -- door
```
This is also possible
```lua
local dictionary = {
    ["door"] = "opened"
}

print(key.door, key["door"]) -- opened opened, indexing tables is the same thing as indexing instances which you are already familiar with.
```
To define a dictionary with keys that aren't array indices nor string keys, you would need to wrap them with square brackets like shown with the string earlier.
```lua
local keyCodes = {
    [Enum.KeyCode.P] = "hi"
}

game:GetService("UserInputService").InputBegan:Connect(function(input) -- UIS would be covered later
    print(keyCodes[input.KeyCode]) -- thats how you index Enum with keys, would print nil for any other kind of input
end)
```
You can do the same with instances except you have to be more careful because it could cause memory leak if not used properly. To avoid memory leak you have to set the value to nil before/after instance destruction that way it can gc(garbage collection). If it has a reference of some sort then it wouldn't be able to gc.


### 5.3 Iterating through tables

So tables are great, you can do lots of stuff with them. Too bad you can't loop through them, oh wait you can. You would even utilize the `for` keyword. There are different ways to do so.

One of them is `pairs` it's the most famous one actually. It can be used to loop through any kinds of tables including mixed tables which isn't recommended to use(because it Lua doesn't have a lot of support for it and not to mention the fact that other languages don't support it at all).
```lua
local array = {1, true, "ewqwsd"}
local dictionary = {
    hello = "world",
    you = "are fat"
    invisible = nil
}

for i, v in pairs(array) do
    print(i, v) -- i represents the index or key and v represents the value
end

for k, v in pairs(array) do -- the invisible key would get ignored because it is nil
    print(k, v) -- the term key is used in dictionaries
end
```

Side note : pairs loop through array elements before dictionary ones if it looping through a mixed table.

`ipairs` is used for properly organized arrays only and wouldn't run mixed tables, etc
```lua
local array = {1, true, "a", nil, 50} -- nil and 50 wouldnt get printed

for i, v in ipairs(array) do
    print(i, v)
end
```
`next` is like pairs but slower, pairs uses next internally though. The syntax is a teensy bit different.
```lua
local array = {1, true, "ewqwsd"}
local dictionary = {
    hello = "world",
    you = "are fat"
    invisible = nil
}

for i, v in next, array do
    print(i, v)
end

for k, v in next, dictionary do
    print(k, v)
end
```
**Note : next is linear while ipairs and pairs aren't, that's because ipairs and pairs have optimizations which make them faster than next**

`next` can also be used to get the next element in a table from a key, hence the name next.
```lua
local table = {
    hello = "world",
    bruh = "moment"
}

print(next(table, "hello")) -- bruh moment
```
I don't want to get too far into factory iterators and stuff though, those are some more advanced concepts. So that would be enough for iterators for now.
