# 컴퓨터 비전

## Contents
- [Camera Geometry](#Camera-Geometry)  
- [Color Transform](#Color-Transform)

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

Aperture(조리개)의 크기는 빛의 파장과 연관이 되어있다. 작으면 작을수록 Blurring이 안 일어나지만 너무 어두워진다.  
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

#### 1. Spherical Aberration  

렌즈가 오목하게 생기기 때문에 생기는 곡률로 인해 중앙에서 생기는 빛의 굴절률과 측면에서 생기는 빛의 굴절률이 다르다.  
:point_right: Non-Spherical Lens(오목하게 생기지 않은 Lens), Multiple Lens(여러 개의 Lens)를 사용하여 빛이 한 점으로 모이도록 해준다!  

 <p align="center">
 <img width="550"  src="Image/Image3.JPG">
 </p>

#### 2. Chromatic Aberration  

빛의 파장이 색깔마다 각자의 고유값이 있기 때문에 생기는 차이  
:point_right: 카메라의 구조를 바꿔서 해결할 수 있는 문제는 아니다. :cry:  
 
 <p align="center">
 <img width="550"  src="Image/Image4.JPG">
 </p>

 <p align="center">
 <img width="400"  src="Image/Image4_1.JPG">
 </p>

#### 3. Vignette  

다양한 Aperture에 의해 빛이 부분적으로 들어오는 문제점  
이미지의 가운데 부분보다 측면 부분이 어둡게 나오는 것이 문제점이다.   
:point_right: 측면에 좀 더 많은 빛을 투과해주는 식으로 해결  

 <p align="center">
 <img width="400"  src="Image/Image5.JPG">
 </p>

##### 4. Radial Distortion and Tangential Distortion  

이미지 평면에서 보이는 위치와 실제 위치가 다르게 나타나는 현상  
이상적인 축보다 볼록하게 보이거나 오목하게 보이는 것이 특징이다.  
:point_right: Brown DC Model을 이용하여 보정을 통해 해결  
 
 <p align="center">
 <img width="500"  src="Image/Image6.JPG">
 </p>

### Projection  

Perspective Projection - 3차원 정보들을 2차원 이미지에 투영하는데 사용하는 기술  

 <p align="center">
 <img width="600"  src="Image/Image7.JPG">
 </p>

:point_right: 오른쪽 위에 보이는 점 X가 사실 평면 1에 투영되지만  
Aperture(Camera center)의 원점 대칭하여 평면 2에 맺히는 것으로 생각을 한다.  
(좀 더 직관적으로 이해하기 쉽기 때문이다.)

Perspective Projection을 이해하기 전에 Homogeneous 좌표계를 이해해야 한다!  
참고 : [[영상 Geometry #2] Homogeneous Coordinates](https://darkpgmr.tistory.com/78)  

3차원 공간에서 한 점을 (x,y,z)라고 할 때 이것을 Homogeneous로 나타내면 (x,y,z,1)로 나타낼 수 있다.  
이 점 (x,y,z,1)을 이미지 평면에 한 점 (u', v')로 투영시킬 때 어떻게 하는지 알아보자.  

아래 사진에서는 이미지 평면도 Homogeneous Coordinates 표현하면 (u', v', 1) = (U, V, S)로 나타낼 수 있다.  

 <p align="center">
 <img width="600"  src="Image/Image8.JPG">
 </p>

이 때 이미지 좌표계는 이미지의 중심이 아니라 좌측 상부(or 좌측 하부)이므로 평행이동 값을 고려하여 다시 matrix를 써보면  
(Homogeneous Coordinates를 간략하게 쓸 때 알파벳 위에 ~를 붙여 표시한다.)  

 <p align="center">
 <img width="600"  src="Image/Image9.JPG">
 </p> 
 <p align="center">
 <img width="600"  src="Image/Image10.JPG">
 </p>

Camera 좌표계와 World 좌표계에는 Rotation과 Translation Matrix로 표현할 수 있다.  
이 두개의 Matrix를 **extrinsic camera parameters**이라고 표현한다.  

 <p align="center">
 <img width="300"  src="Image/Image11.JPG">
 </p>


 [위로](#Contents) / [뒤로](https://github.com/Taeyoung96/Robotics-Summary)   

## Color Transform  

사람 눈에 보이는 가시광선 - 400nm(blue) ~ 700nm(red)  

기본적으로 색을 표현하는 RGB channel은 밝기의 영향에 따라 색도 바뀐다.  
따라서 밝기 변화에 강인한 HSV, YUV 색공간으로 변화 후 처리를 하기도 한다.  

<p align="center">
 <img width="500"  src="Image/Image12_1.JPG">
 </p>

 <p align="center">
 <img width="400"  src="Image/Image12.JPG">
 </p>  
 
 NRG는 Normalized RG의 약자. 다음과 같은 식을 만족하도록 R,G,B 값을 정규화과정을 거친다.  
 
<p align="center">
 <img width="350"  src="Image/Image13.JPG">
</p>  

다양한 색공간이 존재하는 이유는?  
:point_right: 컴퓨터 비전 응용에 따라 밝기 정보를 무시하고 순수한 색공간을 이용하는 경우가 있다.  
:point_right: 응용과 상황에 따라 어떤 색공간을 활용할 것인지 선택해야 한다.  

- Gray : 색 공간 정보를 이용하지 않고 밝기 정보만 이용 (0(Black)~ 255(White))  
- RGB : 가장 기본적인 색상모델, 색을 R(Red), B(Blue), G(Green)의 조합으로 표현  
- HSV : 색을 가장 직관적으로 표현할 수 있는 모델, H(색조 - 색깔의 정도), S(채도 - 색의 진해지는 정도), V(명도 - 밝기)  
- YUV : 색정보를 인코딩할 때 많이 사용하는 색공간 모델, Y(휘도 - 밝기 성분),  U와 V는 크로미넌스(색) 컴포넌트를 대표  

### Contrast  

다른 물체와 배경을 구분할 수 있게 해주는 시각적인 특성의 차이  

- 분산이 작으면 흐릿하게 보이고, 분산이 크면 선명하게 보인다.  

<p align="center">
 <img width="500"  src="Image/Image14.JPG">
</p>  

<p align="center">
 <img width="500"  src="Image/Image15.JPG">
</p>  

Intensity를 Linear하게 변환을 하여 Contrast를 크게 만들면 이미지가 좀 더 선명하게 보일 수 있다.  

<p align="center">
 <img width="500"  src="Image/Image16.JPG">
</p>





