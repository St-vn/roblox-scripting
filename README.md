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
