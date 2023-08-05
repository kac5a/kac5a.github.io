# Configuration

---

## Segment and target

You might want to make the skillcheck easier or harder for different difficulty levels. For that, navigate to the `html/js/index.js` file.

There are objects that define a skillcheck difficulty:

| Variable                    | Value     | Usage                                                                                            |
| --------------------------- | --------- | ------------------------------------------------------------------------------------------------ |
| **_segmentStartPositions_** | 0 - 360   | At which angle the segment should start.<br />The lower the value, the harder to hit the segment |
| **_segmentLengths_**        | 0.0 - 1.0 | The length of the segment for each level.<br />The bigger the value, the easier to hit           |
| **_speeds_**                | 0.0 - 2.0 | The speed of the target.<br />The higher the value the faster the target moves                   |

## Sounds

To change the sounds, head over to the `html/assets` folder and change the sound files. Make sure the files have the same name as the original sounds.
