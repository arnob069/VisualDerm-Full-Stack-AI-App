# VisualDerm — AI-Powered Skin Lesion Classifier

## Module Information

| Field | Details |
|-------|---------|
| Module | Full Stack Application Development |
| Unit Code | CMS22204 |
| Level | 5 |
| Institution | Ravensbourne University London |
| Deadline | 24 April 2026 |
| Presentation | 28–29 April 2026 |
| Author | Md Akiduzzaman Arnob |
| Student ID | 98088024 |
| GitHub | https://github.com/arnob069/VisualDerm-Full-Stack-AI-App |

---

## 1. Introduction

VisualDerm is a full-stack AI-based web application created to accomplish automated
dermoscopic skin lesion image classification. The system is solving a major healthcare
issue, since early-detection of skin cancer (and especially, melanoma) greatly enhances
the chances of survival in patients. A powerful image-based diagnostic system has become
achievable due to the development of deep learning, particularly convolutional neural
networks (CNNs), and computer-aided dermatology has become a feasible option
(Tschandl, Rosendahl and Kittler, 2018; Debelee, 2023). This project will achieve this
by incorporating such a model in a web-based platform that is deployable to be used in
learning and research.

---

## 2. System Architecture and Design

The application is based on a three-layer architecture, which includes presentation,
middleware and backend layers. React, Vite and Tailwind CSS were used to implement
the frontend, providing effective user interaction and efficient rendering. The middleware
is written in Node.js and Express and implements authentication with JSON Web Tokens
(JWT) and serves as an intermediate between the frontend and backend services.

Django and Django REST Framework were used to create the backend that exposes REST
APIs to make predictions and handle data. SQLite database contains user credentials and
history of predictions. This modular design enhances the scalability, maintainability and
separation of concerns, which are essential in the contemporary full-stack system design.

---

## 3. Machine Learning Model Development

The training dataset of the classification model consists of HAM10000 that comprises
more than 10,000 dermoscopic images of seven types of lesions and is commonly used to
benchmark dermatological AI systems (Tschandl, Rosendahl and Kittler, 2018).
MobileNetV2 was selected since it is a lightweight CNN with low computational costs,
which makes it appropriate to use in real-time inference.

Transfer learning strategy was used. During the pre-training stage, only the
classification head was trained, with a frozen pretrained convolutional base (trained on
ImageNet). The second stage involved fine-tuning the top layers, where the model could
make adjustments to domain characteristics. This method is consistent with the
literature that reports better performance and quicker convergence of medical imaging
tasks with transfer learning (Hosny, Kassem and Foaud, 2019; Shetty et al., 2022).

---

## 4. Implementation and Performance

The training was done in a GPU-enabled setup (Kaggle). The original training stage had
a validation accuracy of 76.4%, which went to 78.4% following fine-tuning. Although
this performance is average when compared to the state-of-the-art models, it is good
enough when a prototype system is concerned with full-stack deployment, as opposed to
a system that is purely predictive optimisation (Debelee, 2023).

The trained model was then exported to the ONNX format, decreasing the reliance on
the training framework, and allowing it to perform inference effectively. This resulted
in a final model size of about 9.1 MB and enables quick response time in a web
environment. The frontend shows predictions in the form of probability distributions
and colour-coded risk indicators and makes them easier to understand by users.

---

## 5. System Functionality

The system has a few important features: the registration and log-in of users is secure,
users can upload images, it will automatically classify them with confidence scores, and
the history of predictions will be stored. The use of AI inference into a web application
serves as an example of a practical implementation of machine learning models in the
real world. These systems could be used in education and initial analysis but should be
further validated to be used in clinical practice.

---

## 6. Conclusion

VisualDerm illustrates how deep learning, combined with full-stack web development,
can be effectively applied to develop an AI-based dermatological tool. The project
underscores the practicability of implementing lightweight CNN models in real-time
applications. Nonetheless, as per ethical standards, the system is only meant to be used
in research and educational activities and should not be used to substitute professional
medical diagnosis.

---

## 7. Bibliography

Debelee, T.G. (2023) 'Skin lesion classification and detection using machine learning
techniques: A systematic review', *Diagnostics*, 13(19), p. 3147.
https://doi.org/10.3390/diagnostics13193147

Hosny, K.M., Kassem, M.A. and Foaud, M.M. (2019) 'Classification of skin lesions
using transfer learning and augmentation with Alex-net', *PLOS ONE*, 14(5), e0217293.
https://doi.org/10.1371/journal.pone.0217293

Shetty, B., Fernandes, R., Rodrigues, A.P., Chengoden, R. and Bhattacharya, S. (2022)
'Skin lesion classification of dermoscopic images using machine learning and
convolutional neural network', *Scientific Reports*, 12, p. 18134.
https://doi.org/10.1038/s41598-022-22644-9

Tschandl, P., Rosendahl, C. and Kittler, H. (2018) 'The HAM10000 dataset, a large
collection of multi-source dermatoscopic images of common pigmented skin lesions',
*Scientific Data*, 5, p. 180161.
https://doi.org/10.1038/sdata.2018.161