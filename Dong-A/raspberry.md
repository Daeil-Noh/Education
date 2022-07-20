# 라즈베리파이 4에 Yolov5 적용해보기

## 기본 리눅스 명령어
```
# change directory
cd A #A라는 폴더 안으로 이동
cd .. #상위폴더로 이동 (ex. yolov5/runs/train에서의 상위폴더는 yolov5/runs이다.)

# list segments
ls #현재 폴더안의 내용 출력

# print working directory
pwd #현재 폴더의 절대경로 출력

# move
mv A.txt ../B.txt #A.txt를 상위폴더에 B.txt로 이동.
```

## 라즈베리파이 세팅
1. 작업할 폴더로 이동 
ex:`cd Desktop`

2. yolov5 다운로드
```
git clone https://github.com/ultralytics/yolov5
```

3. yolov5로 이동
```
cd yolov5
```

4. yolov5가 돌아갈 환경 구축
```
pip install -r requirements.txt
```

5. numpy upgrade
```
pip install --upgrade numpy
```

6. `.pt`파일 라즈베리파이에 다운로드  
`yolov5/runs/train/result*/weights/best.pt` 파일 혹은 `result.zip파일`(이는 Colab의 "3-4. 모델을 zip 파일로 저장" 단계에서 실행하여 얻은 파일이다.)을 e-mail이나 USB 등을 이용해서 라즈베리파이에 넣어준다.

6-1. 메일을 통해 다운받은 파일은 `~/Downloads`에 존재한다.

6-2. `A.zip`파일은 `unzip A.zip`를 통해서 압축을 풀 수 있다.

6-3. best.pt를 yolov5의 작업폴더로 이동해두면 편함. `mv best.pt ~/Desktop/yolov5/best.pt`

7. 실행  
USB CAM을 라즈베리파이에 연결해준 후 Desktop의 yolov5로 이동한다.

다음 명령어를 실행한다.
```
python3 detect.py --weights "best.pt가 있는 경로" --source 0
```

잘 돌아가는지 확인한다.