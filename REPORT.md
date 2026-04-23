# VisualDerm: A Full-Stack AI Application for Skin Lesion Classification

---

## 1. Objectives

Skin cancer is one of the most common cancers worldwide, and early diagnosis significantly improves patient outcomes. Dermoscopy images are widely used by dermatologists to examine lesions, but access to specialist review is not always immediate. This project aimed to build a web application that allows a user to upload a dermoscopy image and receive an automated classification result, including a confidence score and a risk level indicator.

The intended users are medical students, researchers, and members of the general public who want to learn more about skin lesion classification. The primary goal was to produce a working full-stack application that runs a real deep learning model, stores user predictions, and presents results through a clear and usable interface.

---

## 2. System Requirements

The functional requirements for this application are: user registration and login, image upload, classification output with a confidence score and risk level, and the ability to view a history of past predictions. Non-functional requirements include fast inference response times, secure user authentication, and a responsive design that works across screen sizes.

The technical stack used is React with Vite and Tailwind CSS for the frontend, Node.js with Express for the middleware layer, Python with Django and Django REST Framework for the backend, SQLite as the database, and ONNX Runtime for running the trained model.

---

## 3. Design and Architecture

The application follows a three-tier architecture. The React frontend communicates with the Node.js service, which handles authentication and forwards prediction requests to the Django service. Django is responsible for running the AI model and managing the database.

MobileNetV2 was selected as the model architecture because it is computationally lightweight and performs well on image classification tasks. Transfer learning was applied using weights pretrained on ImageNet. A custom output layer was added for the seven target classes. Training was carried out in two phases: the first phase trained only the classification head while keeping the base frozen, and the second phase fine-tuned the upper layers of the network.

---

## 4. Implementation

The model was trained on the HAM10000 dataset, which contains 10,015 dermoscopy images across seven lesion classes: melanoma, melanocytic nevi, basal cell carcinoma, actinic keratoses, benign keratosis-like lesions, dermatofibroma, and vascular lesions. Training was performed on a Kaggle GPU environment.

In phase one, only the classification head was trained, which reached a validation accuracy of 76.4%. In phase two, the top 30 layers of the base model were unfrozen and the network was fine-tuned, reaching a final validation accuracy of 78.4%. The trained model was exported to ONNX format at a file size of 9.1 MB, which allows fast inference without requiring TensorFlow at runtime.

On the backend, Django REST Framework exposes the prediction and history endpoints. Predictions are saved to a SQLite database through the Django ORM. Authentication is handled in the Node.js layer using JSON Web Tokens.

The React frontend includes a drag-and-drop image upload interface, a probability bar chart showing confidence scores for all seven classes, and color-coded risk badges that indicate whether a predicted class is low, medium, or high risk.

---

*This application was built for educational and research purposes only. It is not a substitute for professional medical advice, diagnosis, or treatment. Users should consult a qualified healthcare provider for any concerns about skin lesions.*
