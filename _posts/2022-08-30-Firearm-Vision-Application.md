---
layout: post
title: Firearm Vision Application
subtitle: A real-time object detection app that spots firearms on a live camera feed and sends out alerts.
thumbnail-img: /assets/img/fva-thumbnail.jpg
gh-repo: https://github.com/James-Hagerman/Firearm-Detection
gh-badge: [star, fork]
tags: [Computer Vision, Object Detection, Deep Learning, TensorFlow]
comments: true
---
When someone shows up with a gun, every second between the weapon being seen and help being called matters. Most security cameras only record what happens. Someone still has to be watching the feed to notice anything, and by the time the footage gets reviewed it is usually too late.

The Firearm Vision Application (FVA) is a computer vision app that watches a live camera feed for firearms. The moment it detects one, it takes a snapshot and sends a text message and an email with the picture to the people who need to know, so they can act right away instead of finding out later.

<span style="color:gray">*Testing the app on my webcam with a gun drawn on a sticky note. The model boxed it and labeled it a gun with 96% confidence.*</span>
![](/assets/img/fva-detection.png)

<span style="color:gray">*Running the model on a test clip. The box pops up once the model is at least 75% confident it sees a gun, which is the same threshold the app uses to send an alert.*</span>
![](/assets/img/fva-demo.gif)

## How it works

* The app reads a frame from the webcam about once every second.
* Each frame is passed through our object detection model, which draws a box around anything it thinks is a gun with at least 60% confidence.
* Once the model is at least 75% confident, the app saves the frame as a snapshot.
* The snapshot is uploaded to Imgur so that Twilio can send it as a picture text to a phone number.
* At the same time, an email with the snapshot attached is sent out to a list of recipients through Outlook.

## Machine Learning pipeline

Training an object detection model from scratch takes a huge amount of data and computing power, so we used transfer learning instead. We started with an SSD MobileNet V2 FPNLite model from the TensorFlow Object Detection API that was already trained on the COCO dataset, which means it already knew how to pick out shapes, edges, and everyday objects. We replaced its output with a single class, gun, and fine-tuned it on our own labeled images of firearms.

To prepare the data, we drew bounding boxes around the guns in each image and converted the images and labels into TFRecord files, which is the format the Object Detection API trains on. We set the batch size to 12 and used random horizontal flips and random crops to augment the images, so the model would see more variety than what was in the original dataset. MobileNet is a lightweight network made for fast predictions, which is what makes it possible to run the detection on a live video feed with a regular laptop.

## Insights

We evaluated the model on a held-out test set after 5,000 and 10,000 training steps. The main metric for object detection is mean average precision (mAP), which measures how well the predicted boxes line up with the real ones. At an overlap threshold of 50%, the model's mAP improved from 62.2% at 5,000 steps to 65.0% at 10,000 steps. With the stricter 75% overlap threshold it reached 44.1%, and its average recall, which measures how many of the real guns it found, was 54.1%.

Breaking the scores down by object size shows where the model struggles. It reached 49.5% mAP on large objects, where the gun takes up a big part of the frame, but it was not able to detect small guns at all. In practice this means the app works best when the firearm is fairly close to the camera. More training data with guns at a distance, along with a higher resolution model, would be the next steps to improve it.
