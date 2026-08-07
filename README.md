# Image-Handling-and-Pixel-Transformations-Using-OpenCV
## AIM:
Write a Python program using OpenCV that performs the following tasks:

1.Read and Display an Image.
2.Adjust the brightness of an image.
3.Modify the image contrast.
4.Generate a third image using bitwise operations.

## Software Required:
Anaconda - Python 3.7
Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
Name: DEVADHAARINI.R

Register Number:212225040061.

Ex. No. 01
#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```
import cv2
import matplotlib.pyplot as plt
img = cv2.imread('pic .jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```
#### 2. Print the image width, height & Channel.
```
h, w = img_rgb.shape[:2]
print(h, w)
```
#### 3. Display the image using matplotlib imshow().
```
plt.imshow(img_rgb, cmap='viridis')
plt.title("Original Image")
plt.axis('off') 
plt.show()
```
#### 4. Save the image as a PNG file using OpenCV imwrite().
```
img = cv2.imread('pic .jpg', cv2.IMREAD_GRAYSCALE)
```
#### 5. Read the saved image above as a color image using cv2.cvtColor().
```
image = cv2.imread('pic .jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```
img = cv2.imread('pic.png')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
print("Width =", img_rgb.shape[1])
print("Height =", img_rgb.shape[0])
print("Channel =", img_rgb.shape[2])
plt.imshow(img_rgb)
plt.title("Color Image")
plt.axis('off')
plt.show()
```
#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```
image = cv2.imread('pic .jpg')
image.shape
roi = image[50:350, 50:350]
roi_rgb = cv2.cvtColor(roi, cv2.COLOR_BGR2RGB)
plt.imshow(roi_rgb)
plt.title("Cropped Region of Interest (ROI)")
plt.axis("off")
plt.show()
```
#### 8. Resize the image up by a factor of 2x.
```
image = cv2.imread('pic .jpg')
image.shape
resized_image = cv2.resize(image, (768 // 2, 600 // 2))
resized_image_rgb = cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB)
resized_image_rgb.shape
plt.imshow(resized_image_rgb)
plt.title("Resized Image (Half Size)")
plt.axis("off")
plt.show()
```
#### 9. Flip the cropped/resized image horizontally.
```
image = cv2.imread('pic .jpg')
flipped_horizontally = cv2.flip(image, 1)
flipped_horizontally_rgb = cv2.cvtColor(flipped_horizontally, cv2.COLOR_BGR2RGB)
# Horizontal flip
plt.imshow(flipped_horizontally_rgb)
plt.title("Flipped Horizontally")
plt.axis("off")
```
```
flipped_vertically = cv2.flip(image, 0)
flipped_vertically_rgb = cv2.cvtColor(flipped_vertically, cv2.COLOR_BGR2RGB)
plt.imshow(flipped_vertically_rgb)
plt.title("Flipped Vertically")
plt.axis("off")
```
#### 10. Read in the image ('Apollo-11-launch.jpg').
```
img = cv2.imread('pic .jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```
image = cv2.imread('pic .jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
_ = cv2.putText(img_rgb, "SAADHANA", (10,30),
                cv2.FONT_HERSHEY_SIMPLEX,
                1,
                (255,255,255),  
                2)
```
#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```
image = cv2.imread('pic .jpg')
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
h, w = img_rgb.shape[:2]
plt.imshow(rect_img)
plt.title("Rectangle")
plt.axis('off')
plt.show()
```
#### 13. Display the final annotated image.
```
img = cv2.imread('pic .jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
h, w = img_rgb.shape[:2]
print(h, w)
plt.imshow(img_rgb, cmap='viridis')
plt.title("Annotated Image")
plt.axis('off')
plt.show()
```
#### 14. Read the image ('Boy.jpg').
```
img = cv2.imread('pic .jpg', cv2.IMREAD_COLOR)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
#### 15. Adjust the brightness of the image.
```
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m)
```
#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```
#### 18. Modify the image contrast.
```
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```
#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```
#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```
#### 21. Merged the R, G, B , displays along with the original image
```
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```
#### 22. Split the image into the H, S, V components & Display the channels.
```
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```
## Output:
i) Read and Display an Image.
<img width="449" height="418" alt="Screenshot 2026-08-06 135448" src="https://github.com/user-attachments/assets/bf164db5-e380-4e40-a35c-8db724dcda6f" />
<img width="426" height="418" alt="Screenshot 2026-08-06 135455" src="https://github.com/user-attachments/assets/3df885a6-8245-4b08-b675-a9f8e5521824" />
<img width="442" height="425" alt="Screenshot 2026-08-06 135501" src="https://github.com/user-attachments/assets/a34b2408-ab46-4742-9ef7-1cc84dc8483c" />
<img width="442" height="429" alt="Screenshot 2026-08-06 135508" src="https://github.com/user-attachments/assets/5d6efba4-efb9-4500-b376-09cc2872879f" />
<img width="421" height="416" alt="Screenshot 2026-08-06 135522" src="https://github.com/user-attachments/assets/fa773f0b-7381-41ba-9619-e3031fedbeaa" />


ii) Adjust Image Brightness.
<img width="566" height="458" alt="Screenshot 2026-08-06 135743" src="https://github.com/user-attachments/assets/d424a309-f7f5-4334-9759-0c431649a7b5" />
<img width="449" height="407" alt="Screenshot 2026-08-06 135749" src="https://github.com/user-attachments/assets/15e007ea-aea3-4010-aa83-fddba0bd23c1" />
<img width="385" height="423" alt="Screenshot 2026-08-06 140029" src="https://github.com/user-attachments/assets/75be785a-4a35-45a1-809f-76941dd5952a" />

iii) Modify Image Contrast.
<img width="394" height="428" alt="Screenshot 2026-08-06 135757" src="https://github.com/user-attachments/assets/b0a73489-25ff-4f5c-ba6f-7627406b4f56" />

iv) Generate Third Image Using Bitwise Operations.
<img width="412" height="426" alt="Screenshot 2026-08-06 140101" src="https://github.com/user-attachments/assets/b0678370-87e9-4cd1-894a-95a2f52b1089" />
<img width="411" height="423" alt="Screenshot 2026-08-06 140108" src="https://github.com/user-attachments/assets/6be143f4-6e63-4ea7-bc56-dbd361377a0b" />
<img width="412" height="430" alt="Screenshot 2026-08-06 140114" src="https://github.com/user-attachments/assets/c311c476-bf6e-402b-aba4-108d167dc0d4" />
<img width="399" height="430" alt="Screenshot 2026-08-06 140120" src="https://github.com/user-attachments/assets/b73ada69-d210-4f10-a7e1-5b60a4185666" />
<img width="398" height="408" alt="Screenshot 2026-08-06 140127" src="https://github.com/user-attachments/assets/099b2720-9d88-4f55-98a5-65a60856ef7b" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
