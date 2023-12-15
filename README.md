# OSSW_CAU2023

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

## Result
### Code
```
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

### Print accuracy (do not modify the following block)
```
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
