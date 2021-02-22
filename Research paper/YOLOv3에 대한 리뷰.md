# YOLOv3에 대한 리뷰
*-YOLOv3논문을 읽고 스스로 정리하고 요약해본다.*  
*-헷갈리거나 아직 정립되지 않은 딥러닝 개념을 찾아본다.*

##### 

* Abstract에서 소개되었다시피 yolo가 update되었다는 내용을 전체적으로 담고 있다. 이전보다 little bigger해짐과 동시에 more accurate되었다고 한다. __At 320 × 320 YOLOv3 runs in 22 ms at 28.2 mAP, as accurate as SSD but three times faster__ 로 되어있듯이 SSD처럼 정확해졌지만 3배 빨라졌다고 한다.
 이제 그동안 우세했던 SSD를 뛰어넘은것이다..!
   - SSD란) Single Shot Detectors의 약자이며, object detector이다. 아래 그림에서 보다시피 Faster R-CNN보다는 성능이 조금 낮지만(어떤사이트에선 
   Faster R-CNN에선 7fps,73.2%이었지만 인용한 SSD의 경우에선 59fps,74.3%의 결과를 가져왔다고 한다. Maybe case by case인것같다.) YOLO보다는 성능과 속도에서 앞선다.
SSD는 YOLO처럼 네트워크 하나만 사용하여 오브젝트의 bounding box를 찾고 class classification을 한다. SSD의 핵심은 작은 conv filter들을 사용한 default box들을 여러 feature
map에 적용시켜 score와 box좌표를 예측하는것이다. 여기서 정확도를 높이기 위해 여러 크기의 다른 feature map들로부터 여러 크기의 predict를 수행하고 비율또한
다르게 적용했다. 
   ![https://camo.githubusercontent.com/fea95a2bfb69f9c0f1f883e1c877f2b013da516de413aabc93c53c6ed507d156/687474703a2f2f6269742e6c792f316e6d68476a45](https://blog.kakaocdn.net/dn/bcPhT2/btqDaUoZeET/cNkt1wpy6Ifcpyfc8McP10/img.png)
     - 위의 그림은 SSD Framework로 진행되는 과정을 간략히 말하자면 training 과정에서 [각 object에 대한 input image와 ground truth box만 필요로 함.=>
     convolutional 방식에서 다른크기의 (여기선 4x4 와 8x8) feature map의 각 위치에 다른 비율의 default box set로 평가함=> 각 default box에서 shape
     offset과 모든 object 카테고리에 대한 confidence를 예측함]     
     - 여기서 default box는 Faster R-CNN의 Anchor와 유사하다.
    - SSD의 알고리즘을 한 문장으로 정리하면 ***아웃 풋을 만드는 공간을 나누고(multi feature map), 각 피쳐맵(아웃풋맵)에서 다른 비율과 스케일로 default box를 생성하고 모델을 통해 계산된 좌표와 클래스값에 default box를 활용해 최종 bounding box를 생성한다.*** 
   ![https://camo.githubusercontent.com/fea95a2bfb69f9c0f1f883e1c877f2b013da516de413aabc93c53c6ed507d156/687474703a2f2f6269742e6c792f316e6d68476a45](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FuPIrY%2FbtqA2U6ksbw%2FqbPncjMKsIQMfZH12uOSP0%2Fimg.png)
    - 번외로 SSD는 특별하게 classification을 할때 fully-connected layer가 아닌 fully convolutional network 구조를 사용했는데 YOLOv2에서도 SSD처럼 CNN구조로 변경시켰다가 결국 Yolov3에서 FC가 컴백한걸봐선 SSD를 따라했다가
    바로 철수한듯하다..(->더찾아보기)
    
* 다시 원론으로 돌아와서, 
    



-------
# References  
https://murra.tistory.com/17  
https://hohodu.tistory.com/8  
https://taeu.github.io/paper/deeplearning-paper-ssd/
https://github.com/zzsza/Deep_Learning_starting_with_the_latest_papers/blob/master/Lecture_Note/03.%20CNN%20Application/10.Image-Detection(2).md  
https://yeomko.tistory.com/47
