# OSSW_CAU2023

## What i do?
이 레포지토리는 Open Source SoftWare 강의의 프로젝트 제출물을 위한 레포지토리입니다.
기말 프로젝트는 중앙대학교 Open Source SoftWare 강의의 e-class에서 제공한 tumor dataset을 통해
뇌종양 데이터를 다양한 방법으로 학습시켜 최적의 랜덤 시드값, 분류 방법, 하이퍼 파라미터를 찾았습니다.

## 레포지토리 구조

레포지토리 구조는 다음과 같습니다.
```
📦OSSW_CAU2023
 ┣ 📂final_project
 ┃ ┣ 📂tumor_dataset
 ┃ ┗ 📜final_project.ipynb
 ┣ 📂midterm_project
 ┣ 📂practice
 ┃ ┣ 📜practice04.ipynb
 ┃ ┣ 📜practice05.ipynb
 ┃ ┣ 📜Practice06.ipynb
 ┃ ┣ 📜practice07.ipynb
 ┃ ┣ 📜Practice08.ipynb
 ┃ ┣ 📜Practice09.ipynb
 ┃ ┣ 📜Practice10.ipynb
 ┃ ┣ 📜Practice11.ipynb
 ┃ ┗ 📜Practice12.ipynb
 ┣ 📜LICENSE
 ┗ 📜README.md
```

## Version Info

- Python : 3.9.13
- IPython : 7.31.1
- ipykernel : 6.15.2
- scikit-learn : 1.2.2
- scikit-image : 0.22.0
- numpy : 1.24.1

## Getting Started

```bash
cd final_project
```
> run final_project.ipynb

## 사용한 데이터

뇌종양에 대해 4가지 케이스에 대한 분류가 되어있는 시각적 데이터인 tumor dataset을 사용하여 학습하였습니다. \
중앙대학교 Open Source SoftWare 강의의 e-class에서 제공한 tumor dataset에서 \
추가적인 정제나 수정, 삽입, 삭제 등은 하지 않았습니다.

## 사용한 알고리즘

학습을 위한 분류 방법으로는 Support Vector Machine을 사용했습니다.
from sklearn.svm import SVC 로 scikit-learn에서 제공하는 Support Vector Machine 모듈을 이용했습니다.

앞서 ADAboost를 이용해 정확도를 높이려는 시도를 해보았습니다.
Decision Tree 및 SVM 을 분류기로 사용해 ADAboost로 여러차례 학습을 시도한 결과
단순한 분류기를 여러개로 중첩해서 하나의 강력한 분류기를 만든다는 구조 자체가 복잡한 탓에, \ 
학습에 드는 시간과 비용이 매우 컸습니다.

때문에 상대적으로 구조가 단순해서 최적화하기에 효율적인 Support Vector Machine 단일 분류기를 채택하였습니다.

## 적용한 하이퍼파라미터 및 Code 설명
```python
# 랜덤 시드 설정
random_seed = 6
np.random.seed(random_seed)

# 모델 선택 (Support Vector Machine 사용)
model = SVC(C=100, kernel='rbf') # 하이퍼파라미터 튜닝

# 모델 훈련
model.fit(X_train, y_train)

# 모델 예측 및 평가
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print(f"Test Accuracy: {accuracy}")
```
> Test Accuracy: 0.9175377468060395

랜덤 시드는 6으로 설정하였고,

하이퍼 파라미터 튜닝은

오차를 보정하는 C 값을 100으로 설정하였습니다. \
C를 이 이상으로 올리게 되면 정확도가 소량 증가하지만, 오버 피팅의 우려가 있어서 100을 최적으로 판단했습니다.

kernal은 linear는 단순한 탓에 성능의 향상에 한계가 있고, \
poly로 선택하여 차원(degree)과 감마(gamma)를 조정해보았으나 성능을 개선하기에 매우 복잡하여 rbf로 선정하였습니다. 

감마(gamma)는 디폴트인 0.01이 가장 최적이었습니다.

## 결과
### Print accuracy (do not modify the following block)
```python
# Print accuracy (do not modify the following block)
print('Accuracy: %.2f' % sklearn.metrics.accuracy_score(y_test, y_pred))
```
> Accuracy: 0.92

## License
MIT License
자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

## 작성자
- Name : 손범준
- Major : 문헌정보학과
- Student Num : 20172206 
- Phone : 010-8338-5074
