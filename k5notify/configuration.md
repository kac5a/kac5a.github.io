# Configuration

---

## Add new notifications

Navigate to the `html/notifications.js` file

You can find the default notifications here. Feel free to edit them to your preferences.

?>There are many properties that you can customize. Read carefully what each of them does

To create a new notification, simply copy one of the existing ones and add it at the bottom of the `k5Notification` object.

```js
const k5Notifications = {

  ...

  ['myNewNotification']: {
    background: 'red',
    titleColor: '#FFF',
    messageColor: '#FFF',
    boldTitle: true,
    borderRadius: '2px',
    border: '2px solid blue',
    duration: 4000,
    audio: 'assets/k5_notify.ogg',
  },
}
```

!>Make sure you name the notification properly and remember it. You will need it in the future.

| Variable     | What it does                                                                                                                                                                                                |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| background   | The background color. Can be anything that CSS accepts (rgb, rgba, hex, etc.).                                                                                                                              |
| titleColor   | The color of the notification title. Can be anything that CSS accepts (rgb, rgba, hex, etc.).                                                                                                               |
| italicTitle  | Whether or not the title should be italic. Can be `true` or `false`.                                                                                                                                        |
| boldTitle    | Whether or not the title should be bold. Can be `true` or `false`.                                                                                                                                          |
| messageColor | The color of the notification message. Can be anything that CSS accepts (rgb, rgba, hex, etc.).                                                                                                             |
| borderRadius | The roundness of the corners. Can be any value that CSS accepts (px, em, rem, etc.).                                                                                                                        |
| border       | The CSS border. For example: `"2px solid #F00"`. Can be anything that CSS accepts as border.                                                                                                                |
| icon         | The starting icon in the title. Can be any icon pack that's includable, but make sure it's include it properly. By default [fontawesome](https://fontawesome.com/search?m=free)'s free icons are available. |
| startImage   | The start image leading the notification body. This image has to be included in the resource folder. For that, you can use the `assets` folder. Example value: `"assets/bennys.png"`.                       |
| audio        | If you want to add custom notification sounds, include them in the same `assets` folder the same way. This will be played when the notification shows.                                                      |
| duration     | How long should the notification be on the screen in millis.                                                                                                                                                |
