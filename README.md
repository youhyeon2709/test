# GrayScale

# 1.Image preprocessing
## 1.1. IMREAD_GRAYSCALE
> Read the image as IMREAD_GRAYSCALE.
```c++
src = imread("Lab_GrayScale_TestImage.jpg", IMREAD_GRAYSCALE);
```
<div style="text-align:center">
    <img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227127072-82ee3e97-7473-48b5-8069-5cb1136d4027.png" alt="이미지 제목">
</div>

## 1.2. GaussianBlur
> Gaussian blur is used to reduce noise in an image or to apply a border softening effect.
### 1.2.1 Definition
``` c++

void cv::GaussianBlur	(InputArray src,
                        OutputArray dst,Size ksize,
                        double sigmaX,double sigmaY = 0, 
                        int borderType = BORDER_DEFAULT)	
```
* **src**: input image
* **dst**: output image of the same size and type as src.
* **ksize**: 	Gaussian kernel size. 

### 1.2.2 Code
```c++
GaussianBlur(src, blur_img, Size(7, 7), 0);
```
<img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227125610-f18cc437-9aa6-4d71-bb33-ba49989176bb.png">

## 1.3. Morphology
> You can expand or contract images, remove noise, highlight boundaries, change the size of objects, and more.
### 1.3.1 Definition
``` c++

void cv::morphologyEx	(InputArray src,
                        OutputArray dst,
                        int op, 
                        InputArray kernel,
                        Point anchor = Point(-1,-1),
                        int iterations = 1,
                        int borderType = BORDER_CONSTANT,
                        const Scalar& borderValue = morphologyDefaultBorderValue() 
                        )	
```
  * **op**: Type of a morphological operation
    * MORPH_ERODE, MORPH_DILATE 
    * MORPH_OPEN : erode -> dilite
    * MORPH_ClOSE : dilite -> erode
    * MORPH_GRADIENT 
  * **anchor**: The center point of the kernel
  * **iterations**: Number of iterations of the operation

``` c++

void cv::morphologyEx	(int 	shape,
                        Size 	ksize,
                        Point 	anchor = Point(-1,-1)                     
                        )	
```
* **shape**: MORPH_RECT, MORPH_CROSS,MORPH_ELLIPSE 
* **anchor**: The center point of the kernel

### 1.3.2 Code

```c++
Mat element = getStructuringElement(MORPH_RECT, Size(5, 5));
morphologyEx(blur_img, Morphology, CV_MOP_OPEN, element); 
```
<img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227135450-7c2f90c2-edce-467b-acc1-7f06938a7505.png">


## 1.4. Threshold
> When processing images in the OpenCV library, this function performs binarization based on a threshold in the image. Binarization means setting all pixel values in the image to 0 or 255, making the image black and white. It is often used to extract certain desired objects or features from an image.

### 1.4.1 Definition
```c++
double cv::threshold(
    cv::InputArray src, // 입력 이미지
    cv::OutputArray dst, // 출력 이미지
    double thresh, // 임계값
    double maxval, // 임계값보다 큰 값에 할당할 값
    int type // 이진화 방법
);
```


<img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227134689-ac87a318-d719-48e0-8ea5-deeff2007f29.png">
