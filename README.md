# Gesture-Canvas
This project has been built using MediaPipe and OpenCV. The MediaPipe framework is mainly used for rapid prototyping of perception pipelines with AI models for inferencing and other reusable components. It also facilitates the deployment of computer vision applications.

**MediaPipe** offers two models for detection. The **Palm Detection model** locates hands within the input image, and the **Hand Landmarks Detection model** identifies specific hand landmarks on the cropped hand image defined by the Palm Detection model.

**Understanding the Hand Landmark Detection Model**
It allows you to detect the landmarks of the hands in an image. You can use this task to locate key points of hands and render visual effects on them. This task operates on image data with a machine learning (ML) model as static data or a continuous stream and outputs hand landmarks in image coordinates, hand landmarks in world coordinates, and the handedness of multiple detected hands.

### Parameters it primarily works on

- **static_image_mode**: If set to false, the solution treats the input image as a video stream.
- **max_num_hands**: The maximum number of hands that can be detected by the model; the default value is 2.
- **model_complexity**: Landmark accuracy depends on this parameter, which ranges between 0 and 1. The default value is 1.
- **min_detection_confidence**: The minimum value for which the detection should be considered successful, ranging from 0 to 1. The default value is 0.5.
- **min_tracking_confidence**: The minimum value for tracking confidence, ranging from 0 to 1. The default value is 0.5.



**About Gesture Canvas**

The project lets users draw using hand gesture recognition. At the top, there is a panel with brushes of blue, orange, purple, and red, along with an eraser to clear the drawing. There are 5 images designed on the canvas of size 640x62 to show the selections made for each color along with the eraser. The header of the display keeps updating the images based on the selection made by the user.

**By default, the thickness of each brush has been set to 10, while for the eraser, it is 40. These values can't be changed using gestures and have to be done manually.**

**Different Modes of Operation**

For selection or drawing, it depends on the number of fingers that are up. A `fingers[]` list stores values 4, 8, 12, 16, 20, which correspond to the tips of the five fingers:
  4  -- tip of the thumb
  8  -- tip of the index finger
  12 -- tip of the middle finger
  16 -- tip of the ring finger
  20 -- tip of the pinky finger

You can refer to the following image to understand the different landmarks and their values

![images (2)](https://github.com/parth9504/Gesture-Canvas/assets/127659489/7ac99966-6388-4384-a12c-136c87818272)



The Hand Landmarks Detection model checks for the fingers that are held up and makes selections based on that.

- If all five fingers are held up, the **entire board is cleared**.
- If the index and middle fingers are held up, **selection mode** is enabled, allowing the user to choose among the colors or eraser.
- If the index finger is held up, **drawing mode** is enabled.

When drawings are made, OpenCV's **`cv2.line()` function draws lines accordingly at the specific coordinates. The drawings are simultaneously shown on a canvas which is overlaid on the webcam's screen**

**Note**: The webcam resolution was 640x480. You are advised to check your resolution and set the values accordingly in the code.
