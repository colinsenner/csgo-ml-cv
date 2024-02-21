# CS:GO machine learning cv model

flick.gg was envisioned as a tool to help players improve their aim and game sense by providing instant replays so they could analyze their performance and learn from their mistakes. Based on the belief that the best way to improve is to spend time watching your mistakes.

https://github.com/colinsenner/csgo-ml-cv/assets/13701799/6775f3b1-aaa3-4366-97db-fc368c5e9385

The project was developed using Python, OpenCV, and Keras/TensorFlow. The model was trained on a dataset of ~5,000 images of enemies and non-enemies. The dataset was created by hooking into the game and capturing frames and labels in real-time.

Me, after dying in a CS:GO silver game.

![ron-throwing-computer.gif](images/ron-throwing-computer.gif)

As it was originally envisioned to run via a streamer's OBS, the model was designed to be lightweight and fast, so it could run in real-time on a single GPU. We needed object detection in less than 33ms for 30fps stream and YOLOv3 was the only model even close.

Here's a demo of what the user would see immediately after dying.

https://github.com/colinsenner/csgo-ml-cv/assets/13701799/b07b3e05-b072-48e2-87f0-267938d8cdc5

The model got good eventually, but it was quite a road to get there. 

https://github.com/colinsenner/csgo-ml-cv/assets/13701799/8d81699f-bd74-4898-b9cb-66799a9ab5dd

It's worth mentioning that the user doesn't see the detections on their screen, the detections are visible in the replays only and help score the user's performance and detect clippable portions of their gameplay (death, kill, etc.).

There were some not so great models along the way, this one was pretty sure our gun was an enemy.

https://github.com/colinsenner/csgo-ml-cv/assets/13701799/786f3102-8360-46b8-adf6-8bb053e4122c

A big problem with the original approach was I trained the model on full quality pngs, but ran the prediction against the compressed stream with quantized jpeg artifacts. Doh!

https://github.com/colinsenner/csgo-ml-cv/assets/13701799/606e8134-545a-4863-9cee-0d1aa7ab63d2

Your training set needs to resemble your prediction case as much as possible...
