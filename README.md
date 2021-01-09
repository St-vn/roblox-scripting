# Roblox Scripting
## Written by St_vn#3931, St_vnC(Roblox), St-vn(Github)

**Before you start reading, I would like to point out that most info here comes from docs that I've read before and some research.**
**I also apologize in advance if my wording is wrong, I'm just stupid. ¯\\_(ツ)_/¯**

[Lua 5.1 docs](https://www.lua.org/manual/5.1/manual.html#1.0)

[Luau docs](https://roblox.github.io/luau/)

[Roblox API](https://developer.roblox.com/en-us/api-reference/)

[Lua source code](https://www.lua.org/source/)


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


### 1.2 Operators and operands

Operations take an operator and operands to process its results. I will only review arithmethic ones because others won't do much for now.

* `+` adds `y` to `x`
* `-` subtracts `y` from `x`, 
* `*` multiplies `y` by `x`
* `/` divides `y` by `x`
* `^` gets `x` power `y`
* `%` gets the remainders of a division operation

2 + 1 = 3,
3 - 1 = 2,
4 * 6 = 24,
5 / 2 = 2.5,
6 ^ 2 = 36,
36 % 5 = 1

Operands are the "arguments" that the operator performs an operation on, 0 * 5's operands are 0 and 5 while * is the operator.


### 1.3 Variables

Variables, unlike in algebra are defined by you. You use variables to avoid repeat the same tasks to get the same values.
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

[sauce about the parent argument being bad](https://devforum.roblox.com/t/psa-dont-use-instance-new-with-parent-argument/30296)


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
The `field` is what you're indexing with, thus
```lua
local name = "Baseplate"

print(workspace[name].Transparency) -- 0
```
`name` is a field as well as Transparency.


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
print(not true, not false)
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
Which is basically a syntactic sugar(better looking) version of
```lua
p; p = function()

end
```
and not
```lua
p = function()

end
```
Which is the sole reason that you make recursive functions like that. Functions can be local, therefore should be used for the same reasons as local variables. You'd define a local function this way
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


### 4.1 Recursive functions

Recursive functions are functions that call themselves, not that useful in most cases and looping is better. You would find greater uses for it as you get better. This is how a recursive function looks like.
```lua
local function Recurse()
    print("hi")

    Recurse()
end
```
That would cause a stack overflow because that callstack would overflow due to the amount of functions being called within the same thread. As mentioned earlier, you have to do
```lua
local func; func = function()
    print("hi")
end
```
or its popular counterpart to be able to make recursive functions. The reason that you can't use
```lua
local func = function()

end
```
Is because unlike the former, it doesn't already have a reference of itself to call so it would error(attempt to call nil).


### 4.2 Returning

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


### 4.3 Parameters and ... in Lua

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
    print(...)
end

PrintWrapper(123, true, 0, nil) -- 0, nil, 123
```
... is considered as a tuple(real term being variadic), here is Roblox explaining what a tuple is.

![](https://cdn.discordapp.com/attachments/781886987366957058/792517515649351711/unknown.png)
[Source](https://developer.roblox.com/en-us/articles/Tuple)


### 4.4 Events/Signals and connections

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

Tables are a datatype that I've mentioned before in here. They are used to store multiple values in them including other tables. They are pretty different compared to datatypes like numbers, bools, etc. The reason being is that they exist as objects in memory which is the reason that they have a hexedecimal address to differenciate them, I will elaborate later in this chapter. To create a table you would use these brackets {}.
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
![](https://cdn.discordapp.com/attachments/781886987366957058/797339910650200064/unknown.png)

[actual sauce](https://roblox.github.io/luau/performance.html)

As I said at the beginning of this chapter, tables are their own individual objects in memory, meaning if you have multiple references to a table and made a change to one of them, it would apply those changes to all the other ones.
```lua
local tubl = {}
local tabl = tubl

print(tubl, tabl) -- same hexadecimal address
print(tubl.Hi, tabl.Hi) -- nil

tabl.Hi = "hi"
print(tubl.Hi, tabl.Hi) -- hi
```
But this wont apply to values like numbers and strings.
```lua
local x = 1
local y = x

y += 1

print(x, y) -- 1, 2
```
```lua
local str = "you're"
local second = str

str ..= " fat"
print(str, second) -- you're fat, you're
```

There is an operator called the length operator which gets a table or string's length
```lua
print(#{true, false}) -- 2
print(#"hello") -- 5
```
When calling a function, you can define the first and only parameter as a table by using curly brackets instead of regular ones. This also applies to strings
```lua
print(unpack{true, false, 1}) -- true, false, 1
print[[
    hi
    there
]] -- hi there, this is called a multi-line string
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
To define keys with specific datatypes, you would need to wrap them with square brackets like shown with the string earlier.
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

for k, v in pairs(dictionary) do -- the invisible key would get ignored because it is nil
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
**Note : next's speed is linear while ipairs and pairs aren't, that's because ipairs and pairs have "optimizations" based on their arguments which make them faster than next. Also because next only goes to the next value in a table, nothing else.**

`next` can also be used to get the next element in a table from a key, hence the name next.
```lua
local table = {
    hello = "world",
    bruh = "moment"
}

print(next(table, "hello")) -- bruh moment
```
I don't want to get too far into factory iterators and stuff though, those are some more advanced concepts. So that would be enough for iterators for now.


### 5.4 Table library

The table library is useful because it would allow you to have more control over tables. Here are the functions

1. table.concat
    This concatenates each element into a string with the option to add a separator.
    ```lua
    local tubl = {"hi", true, 1, 5}
    print(table.concat(tubl, ", ")) -- "hi", true, 1, 5
    print(table.concat(tubl, ", ", 2, 3)) -- true, 1, you can also specify the starting point(1) within the array and the ending point(#tubl)
    ```

2. table.create
    This creates an array with memory preallocated to the specified amount with the option to add a specified value to each index.
    ```lua
    local array = table.create(500, "hello")

    table.foreachi(array, print) -- hello(500x), foreachi is an iterator that calls the specified callback each iteration and has the index and the value as parameters, slower than using ipairs though.
    -- foreach is the dictionary counterpart
    ```

3. table.insert
    Would insert a value at the specified index
    ```lua
    local tubl = {true}
    table.insert(tubl, 2, false)

    print(tubl[2]) -- false
    ```
    This method is said to be faster though.
    ```lua
    local tubl = {true}
    table.insert(tubl, false) -- instead of using the position as the 2nd arg you would use the value you want to insert, works like stack push

    print(tubl[2]) -- false
    ```
    If you inserted it at an existing entry, it would shift the other elements instead of overwriting it like `tubl[i] = v` does.
    ```lua
    local tubl = {5, true, {}, "hi"}
    table.insert(tubl, 2, false) -- instead of using the position as the 2nd arg you would use the value you want to insert, works like stack push

    print(tubl[2], tubl[3], tubl[4]) -- false, true, table : hexadecimal
    ```
    ```lua
    local tubl = {5, true, {}, "hi"}
    tubl[2] = nil -- instead of using the position as the 2nd arg you would use the value you want to insert, works like stack push

    print(tubl[2], tubl[3], tubl[4]) -- nil, table : hexadecimal, hi
    ```
    If you inserted it at an entry where there aren't any former ones, then it would simply place it there.
    ```lua
    local tubl = {}
    table.insert(tubl, 2, true)

    print(tubl[2]) -- true
    ```

4. table.find
    This would perform a linear search algorithm(rudimentary iterating) and return the specified value's index if the value was found, if not then it returns nil. You also have the ability to specify a starting point.

5. table.move
    When too lazy to document this function   

    ![When too lazy to document table.move](https://cdn.discordapp.com/attachments/744073200651993109/792622202250985482/unknown.png)

6. table.remove
    Clears the specified index position and shift values similarly to table.insert while also returning the removed value. If the index was not specified, then it would act like stack pop
    ```lua
    local array = {123, true}
    print(table.remove(array)) -- true
    
    print(array[2]) -- nil
    ```
    ```lua
    local array = {123, true}
    print(table.remove(array, 1)) -- 123
    
    print(array[1]) -- true
    ```
    Some people think that table.remove removes the table, if you want to remove it then simple set the table to nil. Assuming that there aren't any other references to it, it would get gc'd.

7. table.sort
    This function sorts the table using the [quick sort algorithm](https://en.wikipedia.org/wiki/Quicksort). It uses the < operator when the comparator function isn't specified. But when it is, then it would receive the values as parameters and has to return a bool so that quick sort can sort it accordingly.
    ```lua
    local tubl = {50, 100, 75, 25, 0}

    table.sort(tubl, function(x, y)
        return x > y
    end)

    print(unpack(tubl)) -- 100, 75, 50, 25, 0

    table.sort(tubl)

    print(unpack(tubl)) -- 0, 25, 50, 75, 100
    ```
    [table.sort uses quicksort](http://lua-users.org/wiki/LuaSorting) the proof is in the first paragraph through this link.

Unpack and pack were reviewed earlier so I don't need to review them again.

**Please note that little to no functions of this library works with dictionaries.**

### 6.0 Player class, local player and the player service

The player class and service provides a lot of functionality for both the client and the server to handle player(s). The player object has info about the player such as their userid, account age, their appearance, etc. The local player can only be accessed from the client(localscript or module required by localscript). So if you can't get the localplayer on the server with a server(regular) script.
```lua
-- Client
print(game.Players.LocalPlayer) -- local player name
```
```lua
-- Server
print(game.Players.LocalPlayer) -- nil
```
The player service provides both server and client sided use. It detects player joining/leaving, can make the localplayer chat, report, etc. Instances have methods such as GetChildren and events like ChildAdded and ChildRemoved. The player service has its own events and methods that are optimized for handling player related tasks like saving data.
```lua
local playerService = game.Players

playerService.PlayerRemoving:Connect(function(player)
    print(player.Parent) -- Players
end)

playerService.ChildRemoved:Connect(function(player)
    print(player.Parent) -- nil, playerremoving fires right before the player gets removed from the playerservice in other words, destroyed. You can use that to save data if you're using instances to store data.
end)
```
The player holds a direct reference to its character model located in the workspace which can be useful. Except the character takes some time to load therefore wouldn't exist when the script first executes.
```lua
local player = game.Players.LocalPlayer
local character = player.Character

print(character) -- nil
```
So you would need to use `CharacterAdded` event.
```lua
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()

print(character) -- character
```
I've explained how a signal's :Wait() method and logical operators work before. If the character is nil, then it would yield the thread until CharacterAdded fires. The :Wait() method returns the event's parameters. This method is much more efficient than busy waiting, any method that revolves around using signals instead of busy waiting is always best. Busy waiting is just a loop that would run only until when the given condition is true, which is a waste of CPU cycles. To learn more about the player service and player class. Here's the API

[PlayerService](https://developer.roblox.com/en-us/api-reference/class/Players)
[Player Class](https://developer.roblox.com/en-us/api-reference/class/Player)


### 6.1 Server and client

Servers and clients are network stuff. The server being Roblox's servers and client being the user. The time it takes for the server and client to communicate is called the client's ping. This varies with the user's wifi speed and their distance between the server, a European playing in an Asian server would lead to larger pings due to the distance. Inputs like pressing a key, clicking a mouse button, etc are handled within the client. While handling databases would be server sided.

In Roblox, clients are marked as blue while the server is green. While play testing you can switch between the client and server by clicking on the upper half of the screen.

![](https://cdn.discordapp.com/attachments/730438914401370112/794301299189350441/unknown.png)

If you changed something from the client, generally it wont replicate to the server(or to other clients) but something that happens to the server would replicate to the clients. To make changes on the server while being on the client, you would use remotes. Remotes are the only communication method between clients and servers we have here on Roblox.


### 6.1.5 RemoteEvent and RemoteFunction

Those were the remotes I was referring to last chapter. You send data to where you want and let the other side handle it. Let's start with RemoteEvents. RemoteEvents are used a lot more than their function counterpart because they're signal based and wont yield the caller's thread. They use the term fire in their methods.
```lua
-- Client
local remote = pathToRemote

remote:FireServer(math.random(5)) -- FireServer cannot be called on the server and vice-versa meaning that this code is client-sided
remote:FireClient(game.Players.LocalPlayer) -- error
```
```lua
-- Server
local remote = pathToRemote

remote.OnServerEvent:Connect(function(player, number) -- the client who fired the server would always be the first parameter, if you sent the player as an argument then it would be the second parameter and would cause problem in your code.
    print(player) -- client name
    print(number) -- an integer between 0 and 5
end)

remote:FireServer() -- error
```
It is a good idea to send data through remotes to perform tasks with more efficiency instead of using a hacky solution. You can do the same with the server and fire clients.
```lua
-- Server

local remote = pathToRemote

remote:FireAllClients(true) -- You can fire every client with this function instead of looping through them individually

for _, player in ipairs(game.Players:GetPlayers()) do
    remote:FireClient("hi") -- You can loop through a specific group of players instead of firing clients for specific reasons
end
```
```lua
-- Client

remote.OnClientEvent:Connect(function(parameter)
    print(parameter) -- true, hi
end)
```
You would use RemoteFunctions because you expect them to return something after it's done playing with the data you sent. RemoteFunctions unlike RemoteEvents, use the `Invoke` term instead of `Fire` because it is the term used with functions. This piece of code should give you an idea about how RemoteFunctions work.
```lua
-- Client

local remote = pathToRemote

remote.OnClientInvoke = function(bool)
    return not bool
end

print(remote:InvokeServer()) -- false
```
```lua
-- Server

local remote = pathToRemote

remote.OnServerInvoke = function(player) -- the client is still the first parameter
    return remote:InvokeClient(player, true)
end
```
You can try returning values using RemoteEvents, it wont work. I don't find a lot of uses for RemoteFunctions since I don't need to yield my threads nor need a returned value. Some people InvokeServers for sanity checks from the server to "prevent exploiters" from ruining the game. That's a horrible idea because exploiters have 100% control of the client and can ruin part of the server depending on how the devs setup the remotes and the code. If you're doing server sided tasks and invoking clients to expect a value then exploiters could disrupt those as well.


### 6.2 Network Ownership

Network Ownership is something that parts have. It is used to prevent input delays and such, an example would be when a player pushes a part. There wouldn't be delay because the player has network ownership over that part. Unanchored parts' network owner can change and needs to be in a player's range to be have that player as their network owner. That range varies a lot. Yes, network owners can only be set on unanchored parts. When a client has network ownership over a part, any physical changes on their side would replicate to the server. That also means that exploiters can destroy part based hitboxes. To prevent that you could manually set a part's network owner to nil(server).
```lua
Part:SetNetworkOwner(nil)
```
You can manually set a parts' network owner to a player if they're not within the range.
```lua
if not Part:GetNetworkOwner() then -- sadge encapsulation :(
    Part:SetNetworkOwner(player)
end
```


### 6.3 Exploiters, Honeypots and securing your game

Exploiters, dependending on their competency and the anti-cheat's level, can get stopped easily by rudimentary sanity checks or can completely obliterate a game with ineffective anti-cheat like arsenal. You can easily break a simulator made by an incompetent scripter, just spam fire remotes that would likely increment the main currency and get stacked. To prevent that you could check the time elapsed since the previous click hence sanity checks.

Since exploiters have **full control** of their client, they would try to find something to cause chaos within a game. Since client sided changes almost never change you wont have to worry about how a client's UI looks like, that is their problem. So you should just prevent anything that could potentially become a nuisance to other players' fun like gaining infinite amounts of currency or aimbots.

To prevent currency giving remotes from getting spammed, you just don't use them, try using stuff like tools and detect the clicks from the server side and add a fake remote to perhaps punish the exploiter which is what a **honeypot** is. To prevent aimbots that shoot across walls, you could fire server sided rays to make sure that it isn't shooting across walls, of course this would be less effective in an open field therefore you should perhaps add a **cooldown** to see if they're firing too fast. For movement, there would be a problem being that a player could randomly get flung because of glitches and punishing someone over an **unintentional glitch** isn't very ideal either. So instead, you could **rubberband** the player to their previous location if they move too far.

**However it's important to note that stopping competent exploiters is unbelievably harder than stopping skids(script kiddie).**


### 6.4 Handling inputs with UserInputService, ContextActionService and the Mouse object

User inputs can range from key presses to screen touching. You would want to use services like UserInputService to create "keybinds" for your game. Note that user inputs only work on clients, not the server. I'll go through the old way to do stuff, the mouse object.

The mouse is the only fashioned way to handle inputs, also called `PlayerMouse`. `Mouse` doesn't support cross platform as much as the services that superseded it which is a reason for the mouse's supersedence. To get a player's mouse you use the GetMouse method that the player has or you can get it through tools' Equipped event.
```lua
local player = game.Players.LocalPlayer
local mouse = player:GetMouse()

print(mouse.X) --  the mouse's horizontal position
```
```lua
tool.Equipped:Connect(function(mouse)
    print(mouse.X)
end)
```
The mouse does still have some functionality that UIS and CAS don't have like getting its position in 3D space, however you can recreate all this functionality if you'd like to use the services and accept a little challenge. You can't change the mouse's icon with UIS nor CAS though. To detect a mouse click you use the Button1Down event.
```lua
mouse.Button1Down:Connect(function()
    print(1)
end)
```
Although you KeyDown and Up are deprecated they're still usable.
```lua
mouse.KeyDown:Connect(function(key)
    print(key)
end)
```

**UserInputService** has more uses than simply detecting inputs which is super useful. It can tell whether you have a touch screen or not, whether you're using a controller or not, etc. To detect inputs, you use the InputBegan event.
```lua
local inputService = game:GetService("UserInputService") -- you can choose whatever naming convention you want, mine is influenced by my friend's

inputService.InputBegan:Connect(function(input, gpe) -- gpe means gameprocessedevent which is a bool that determines if you're interacting with UI or not whether it's you typing or you clicking on a button
    if input.KeyCode == Enum.KeyCode.T then
        -- blah
    elseif input.UserInputType == Enum.UserInputType.MouseButton1 then
        -- blah
    end
end)
```
It's better to use elseifs than connecting multiple functions to detect different inputs. There is InputChanged to detect changes like when the mouse is still moving because InputBegan only detects the input beginning.
```lua
local inputService = game:GetService("UserInputService") -- you can choose whatever naming convention you want, mine is influenced by my friend's

inputService.InputBegan:Connect(function(input, gpe)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        print("hi")
    end
end)

inputService.InputChanged:Connect(function(input, gpe)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        print("bye")
    end
end)
```
`hi` would print when you start moving your mouse while `bye` would print every time you move your mouse. InputEnded shouldn't need an explanation on how it works, here's how it works in comparison with InputBegan
```lua
local inputService = game:GetService("UserInputService") -- you can choose whatever naming convention you want, mine is influenced by my friend's

inputService.InputBegan:Connect(function(input, gpe)
    if input.UserInputType == Enum.UserInputType.MouseButton2 then
        print("hi")
    end
end)

inputService.InputEnded:Connect(function(input, gpe)
    if input.UserInputType == Enum.UserInputType.MouseButton2 then
        print("bye")
    end
end)
```
GuiObjects also inherit these input events, I will talk about UI next chapter.
```lua
frame.InputBegan:Connect(function(input, gpe)
    if input.UserInputType == Enum.UserInputType.MouseButton2 then
        print("hello")
    end
end)
```
Everything else about this service is within the API and would include events that detect specific inputs, functions that can retrieve the mouse's position, etc. They'll be links to the API that talk about what you learned this chapter.

**ContextActionService** is better than UIS in terms of detecting inputs in general. UIS's input functions would fire upon any input unlike CAS that would only call the callback upon the correct input(s). It does have a bit more functionality than that but most of them are extraneous to the creation of keybinds. To bind to an input you use the `BindAction` function. `BindAction` would overwrite another bound action with the same input you can also bind an action with a certain priority with the function `BindActionAtPriority`. `UnbindAction` does what you expect it to do. With CAS you can also have buttons bound to the action that you can even customize. However I'll just teach the 3 basic functions that it provides.
```lua
local actionService = game:GetService("ContextActionService")

actionService:BindAction("hi", function(actionName, state, input) -- state is an enum called UserInputState and the input is an input object
    if state == Enum.UserInputState.Begin then
        print("hi, fat person")
    end
end, false, Enum.KeyCode.T, Enum.UserInputType.MouseButton3) -- arguments are the action's name, the callback, adds a button and the input(s) bound to the action

actionService:BindActionAtPriority("bruh", function(actionName, state, input) -- state is an enum called UserInputState and the input is an input object
    if state == Enum.UserInputState.Begin then
        print("steven writes pog docs")
    end
end, false, 2, Enum.KeyCode.L) -- the argument related to the priority is the integer `2`

actionService:UnbindAction("hi") -- unbinds an action from its name
```
More functionality in the API, API links :

[Mouse](https://developer.roblox.com/en-us/api-reference/class/PlayerMouse)

[UIS](https://developer.roblox.com/en-us/api-reference/class/UserInputService)

[Input Object](https://developer.roblox.com/en-us/api-reference/class/InputObject)

[CAS](https://developer.roblox.com/en-us/api-reference/class/ContextActionService)


### 6.5 Gui

Guis are 2D interface. They are mainly interacted with mouse related inputs. You should already know what Guis are, I wont review everything but just go through general classes and such. There are 4 LayerCollectors, they're the GuiObjects' containers and render them. They are ScreenGui, SurfaceGui, BillboardGui and PluginGui.

* ScreenGui

    ScreenGuis are the most used LayerCollector in general. They are the ones that you see on your screen and are usually parented to the StarterGui by default. It has a property IgnoreGUInset that ignores the CoreUI like the topbar so it wont get lowered because of it.

* SurfaceGui

    SurfaceGuis can only be descendants of BaseParts for them to render. They would render on the given surface, front by default.

* BillboardGui

    Billboards are UI that render on your screen but in "3D" space, it needs an adornee or a BasePart parent for it to stick to something.

* PluginGui

    Literally just the UI that plugins have that you interact with.

**GuiObjects** are the objects that get rendered onto your screen. An example would be a Frame. You insert a frame in a ScreenGui that is parented to the StarterGui in **editing mode** and you will see a 100x100 white square on your screen. The StarterGui replicates its contents to a player's PlayerGui when their character loads via CharacterAdded. You can look at GuiObjects yourself since the way you use them is pretty simple excluding `ViewportFrames`, I'll likely cover them eventually or just link the API. As mentioned in the previous chapter, they also inherited UIS related events like InputBegan.

There are **UIComponents** that **change GuiObjects' behaviors and/or properties.** When a property is overwritten by one of those, rewriting it wont do anything. An example would be UICorner, it rounds a UI. Its `CornerRadius` property is a UDim meaning that it has a scale and offset value in it. It will render GuiObjects' border related properties useless since there wont be any and you wont be able to do anything.

[LayerCollector](https://developer.roblox.com/en-us/api-reference/class/LayerCollector)

[GuiObject](https://developer.roblox.com/en-us/api-reference/class/GuiObject)

[UICorner](https://developer.roblox.com/en-us/api-reference/class/UICorner)

### 7.0 Modules

Waiting to be documented
