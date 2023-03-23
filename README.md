# GrayScale

# 1.Image preprocessing
## 1.1. IMREAD_GRAYSCALE
> 이미지를 IMREAD_GRAYSCALE로 읽어옵니다.
```c++
src = imread("Lab_GrayScale_TestImage.jpg", IMREAD_GRAYSCALE);
```
<div style="text-align:center">
    <img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227127072-82ee3e97-7473-48b5-8069-5cb1136d4027.png" alt="이미지 제목">
</div>

## 1.2. GaussianBlur
> 가우시안 블러는 이미지의 노이즈를 감소시키거나 경계선 부드러움 효과를 적용할 때 사용됩니다.
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
> 이미지를 확장하거나 축소하고, 노이즈를 제거하고, 경계를 강조하고, 객체의 크기를 변경하는 등의 다양한 연산을 수행할 수 있습니다.
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
  * **anchor**: kernel의 중심점
  * **iterations**: 연산 반복 횟수

``` c++

void cv::morphologyEx	(int 	shape,
                        Size 	ksize,
                        Point 	anchor = Point(-1,-1)                     
                        )	
```
* **shape**: MORPH_RECT, MORPH_CROSS,MORPH_ELLIPSE 
* **anchor**: kernel의 중심점

### 1.3.2 Code

```c++
Mat element = getStructuringElement(MORPH_RECT, Size(5, 5));
morphologyEx(blur_img, Morphology, CV_MOP_OPEN, element); 
```
<img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227135450-7c2f90c2-edce-467b-acc1-7f06938a7505.png">


## 1.4. Threshold
> OpenCV 라이브러리에서 이미지 처리를 할 때, 이미지의 임계값(threshold)을 기준으로 이진화(Binarization)를 수행하는 함수입니다. 이진화란, 이미지의 모든 픽셀 값을 0 또는 255로 설정하여, 이미지를 흑백으로 만드는 작업을 의미합니다. 이미지에서 원하는 특정 객체나 특징을 추출하기 위해 많이 사용됩니다.

### 1.4.1 Definition

<img width="250" alt="image" src="https://user-images.githubusercontent.com/127065880/227134689-ac87a318-d719-48e0-8ea5-deeff2007f29.png">
