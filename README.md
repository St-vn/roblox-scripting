# Roblox Scripting
## Written by St_vn#3931, St_vnC(Roblox), St-vn(Github)


### 1.0 printing

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


### 1.1 printing words/strings

If you wanted to print words then you'd have to wrap whatever you want to print inside of quotation marks "" or apostrophes ''
```lua
print("hi")
```
If you don't wrap them in any of those then it would print nil which means that it doesn't exist, those words are values just like numbers they're called string values and nil is a value as well.

Just like numbers, you can use operators with strings.
```lua
print("hello".. " there")
```
This would print `hello there`, `..` is called string concatenation which is an operation just like `+`.


### 2.0 Variables

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
