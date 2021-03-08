# 컴퓨터 비전

## Contents
- [Camera Geometry](#Camera-Geometry)  

## Camera Geometry

Computer Vision System : Scene(3차원 공간)을 빛을 통해 들어온 정보를 이용,  
카메라로 Image를 만들어 낸 다음 Computer로 인식을 하는 System  

**대부분 카메라는 Pinhole 카메라의 수학적 원리와 동일**  

### Pinhole Camera  

물체에 반사된 빛을 하나의 평면에 상이 맺히도록 하려면?  
:point_right: 여러개의 빛이 섞이면 안된다! 하나의 Point에서 하나의 빛만 투영이 되도록 한다.  
 
 <p align="center">
 <img width="400"  src="Image/Image1.JPG">
 </p>

Aperture의 크기는 빛의 파장과 연관이 되어있다. 작으면 작을수록 Blurring이 안 일어나지만 너무 어두워진다.  
Aperture의 크기가 너무 작아도 초점이 맞지않아 흐려진다.  

Pinhole 모델을 사용하게 되면 너무 어두워지는 단점을 **Lens를 사용하여 단점을 보완**한다.  
이상적인 렌즈는 하나의 평면에 한 점에 많은 빛이 모이도록 해준다.  

 <p align="center">
 <img width="600"  src="Image/Image2.JPG">
 </p>

렌즈를 사용했을 때 나타나는 단점  
1. Spherical Aberration  
2. Chromatic Aberration  
3. Vignette  
4. Radial Distortion and Tangential Distortion  

#### Spherical Aberration  

렌즈가 오목하게 생기기 때문에 생기는 곡률로 인해 중앙에서 생기는 빛의 굴절률과 측면에서 생기는 빛의 굴절률이 다르다.  
:point_right: Non-Spherical Lens(오목하게 생기지 않은 Lens), Multiple Lens(여러 개의 Lens)를 사용하여 빛이 한 점으로 모이도록 해준다!  

 <p align="center">
 <img width="550"  src="Image/Image3.JPG">
 </p>

#### Chromatic Aberration  

빛의 파장이 색깔마다 각자의 고유값이 있기 때문에 생기는 차이  
:point_right: 카메라의 구조를 바꿔서 해결할 수 있는 문제는 아니다. :cry:  
 
 <p align="center">
 <img width="550"  src="Image/Image4.JPG">
 </p>

 <p align="center">
 <img width="400"  src="Image/Image4_1.JPG">
 </p>

#### Vignette  

다양한 Aperture에 의해 빛이 부분적으로 들어오는 문제점  
이미지의 가운데 부분보다 측면 부분이 어둡게 나오는 것이 문제점이다.   
:point_right: 측면에 좀 더 많은 빛을 투과해주는 식으로 해결  

 <p align="center">
 <img width="400"  src="Image/Image5.JPG">
 </p>

##### Radial Distortion and Tangential Distortion  

이미지 평면에서 보이는 위치와 실제 위치가 다르게 나타나는 현상  
이상적인 축보다 볼록하게 보이거나 오목하게 보이는 것이 특징이다.  
:point_right: Brown DC Model을 이용하여 보정을 통해 해결  
 
 <p align="center">
 <img width="400"  src="Image/Image6.JPG">
 </p>








