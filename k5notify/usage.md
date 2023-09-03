# Usage

We will check out a short tutorial on how to use the script

?>This is a standalone, ready to use script that does nothing by itself. You have to add it in your scripts to call the notification export.

!>This is not a replacement script for your framework . If you wish to replace every notification to use this script, you have to manually do it. It **will not** update the default behavior for any of your scripts. I created a small tutorial on how to replace the default ESX notification, but it is note 100% perfect.

## Export

Use the export on the client side to call the notification. The first parameter will be the title of the notification. The second is the content. You can include HTML to style the message. The third parameter is the type of the notification (e.g. `'error'`, `'info'`, `'myNewNotification'`). You can add a fouth parameter that will be the duration of the notification. If you leave it, the default duration will be used.

```lua
exports["k5_notify"]:notify('Notification', 'This is a notification!', 'myNewNotification', '1000')
```

## Event

You can call the event on either server or client side.

?>It is preferred to call the export on the client side

To call the notification on the server side, you have to include the player source for the event, but other than that, everything is the same as the export.

```lua
TriggerClientEvent("k5_notify:notify", source, 'Notification', 'This is a notification', 'myNotification', 10000)
```

## Replacing the Framework notification

You can replace the default notifications on your framework to use the K5 notifications. This is a bit harder method, make sure you know what you're doing.

### ESX

To replace the ESX notification, you have to navigate to the `es_extended/client/functions.lua` file

Here you have to find the `ESX.ShowNotification` function

```lua
...

function ESX.ShowNotification(message, type, length)
    if GetResourceState("esx_notify") ~= "missing" then
        return exports["esx_notify"]:Notify(type, length, message)
    end

    print("[^1ERROR^7] ^5ESX Notify^7 is Missing!")
end

...
```

Here, you have to replace the return line to use our export instead

```lua
...

function ESX.ShowNotification(message, type, length)
    return exports["k5_notify"]:notify('YOUR SERVER NAME', message, type)
end

...
```

!>**IMPORTANT**<br/>
The script does not support the tilde coloring that the default FiveM notification uses. This causes some messages to appear in an unformatted way.
To remove this, you have to manually delete the tilde colorings from your message strings

### QBCore (WIP)

?> **Work In Progress**<br/>
I'm not using QBCore at all, so I would love to get help on Discord or GitHub about this.
