# Usage

?>This is a standalone, ready to use script that does nothing by itself. You have to call the export on the client side. Check out the [example script](https://github.com/kac5a/k5_skillcheck_example) that utilizes the skillCheck export for further information.

## Export

Use the export on the client side to start a skillcheck event. The export takes a hardness level as a string parameter. It returns wether or not the skillcheck was successful.

```lua
exports["k5_skillcheck"]:skillCheck("easy")
```

## Use Case

Let's say we want to create a skillcheck session where the player has to hit a normal and a hard difficulty skillcheck in order to complete the task.

1. We create a thread in which we check if the player pressed the button

?> **Note:** It is important that we call the export in a Citizen thread. The export will halt that thread and will not let it proceed until the player finishes the skillcheck task.

```lua
Citizen.CreateThread(function()
    while true do
        -- Did the player press the E key?
        if IsControlJustPressed(0, 38) then
            -- Our logic goes here...
        end
    end
end)
```

2. If the player pressed the key, we would like the skillcheck script to take action and show the player the UI. If they succeed, the export return `true` and we can proceed. If they failed, we can handle that in the `else` branch.

```lua
Citizen.CreateThread(function()
    while true do
        -- Did the player press the E key?
        if IsControlJustPressed(0, 38) then
            -- Start the skillcheck with normal difficulty
            if exports["k5_skillcheck"]:skillCheck("normal") then
                -- Success
            else
                -- Fail
            end
        end
    end
end)
```

3. If the player succeeds, we want to start a new skillcheck task with hard difficulty. If they fail, we print the result on the console.

```lua
Citizen.CreateThread(function()
    while true do
        -- Did the player press the E key?
        if IsControlJustPressed(0, 38) then
            -- Start the skillcheck with normal difficulty
            if exports["k5_skillcheck"]:skillCheck("normal") then
                -- If the player succeeded we want to start a new
                -- skillcheck, but this time with hard difficulty
                if exports["k5_skillcheck"]:skillCheck("hard") then
                    -- Success
                else
                    -- Fail
                end
            else
                -- The player failed, so we print a message
                -- to the console.
                print("You failed the normal skillcheck")
            end
        end
    end
end)
```

4. Lastly we will handle the hard difficulty skillcheck aswell.

```lua
Citizen.CreateThread(function()
    while true do
        -- Did the player press the E key?
        if IsControlJustPressed(0, 38) then
            -- Start the skillcheck with normal difficulty
            if exports["k5_skillcheck"]:skillCheck("normal") then
                -- If the player succeeded we want to start a new
                -- skillcheck, but this time with hard difficulty
                if exports["k5_skillcheck"]:skillCheck("hard") then
                    -- The player succeeded both skillchecks
                    print("Congrats! You made it!")
                else
                    -- The player failed the hard skillcheck
                    print("You failed the hard skillcheck")
                end
            else
                -- The player failed, so we print a message
                -- to the console.
                print("You failed the normal skillcheck")
            end
        end
    end
end)
```
