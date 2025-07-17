

## 🌊 YOLO11-Flood Victim Detection and Rescue Alert System

###  Abstract

This project presents a real-time deep learning system for detecting humans and animals during floods and immediately alerting rescue teams via email. Using **YOLOv11**, the model identifies and classifies multiple live entities (humans, dogs, cows, goats, horses) in flooded regions and sends annotated images along with count-based summaries to aid in **emergency rescue operations**.

---

###  Core Features

* ⚡ Real-time object detection using **YOLOv11**
* 📩 **Email alert system** for rescue team communication
* 🐄 Detection of **multiple classes**: person, dog, cow, goat, horse
* 🔍 Trained on a custom annotated dataset from Roboflow
* 📊 Evaluated using **Precision, Recall, mAP\@0.5 and mAP\@0.5–0.95**
* 🛠️ Powered by **PyTorch** and **SMTP email protocols**

---

###  System Pipeline

```
graph TD
    A[Input: Real-time Flood Image] --> B[YOLOv11 Detection]
    B --> C[Count Objects by Class]
    C --> D[Generate Alert Message]
    D --> E[Send Email with Alert + Annotated Image]
    E --> F[Rescue Team Takes Action]
```

---

### Object Detection Classes

* 🧍 Person
* 🐶 Dog
* 🐄 Cow
* 🐐 Goat
* 🐎 Horse

---

### Dataset Details

| Attribute     | Details                       |
| ------------- | ----------------------------- |
| Source        | Roboflow                      |
| Total Images  | 500 annotated images          |
| Classes       | Person, Dog, Cow, Goat, Horse |
| Preprocessing | Resizing, normalization       |

---

###  Technologies Used

| Component        | Tool/Library                 |
| ---------------- | ---------------------------- |
| Object Detection | YOLOv11 (PyTorch)            |
| Email Alerts     | SMTP protocol (Python)       |
| Dataset Creation | Roboflow                     |
| Visualization    | Matplotlib, Seaborn          |
| Deployment Ready | Lightweight YOLOv11 for edge |

---

###  Model Performance

| Metric     | Value |
| ---------- | ----- |
| Precision  | 92%   |
| Recall     | 53.8% |
| mAP\@0.5   | 0.751 |
| mAP\@50–95 | 0.448 |

####  Class-wise Evaluation

| Class  | Precision | Recall | mAP\@0.5 | mAP\@50–95 |
| ------ | --------- | ------ | -------- | ---------- |
| Person | 0.933     | 0.628  | 0.805    | 0.413      |
| Dog    | 0.928     | 0.802  | 0.884    | 0.565      |
| Cow    | 1.000     | 0.160  | 0.580    | 0.386      |
| Goat   | 1.000     | 0.600  | 0.800    | 0.427      |
| Horse  | 0.750     | 0.500  | 0.686    | 0.448      |

---

### Getting Started

#### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/flood-rescue-alert-system.git
cd flood-rescue-alert-system
```

#### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

#### 3. Train the Model (optional)

```bash
python train.py
```

#### 4. Run the Alert System

```bash
python flood_alert.py
```

---

### Key Algorithms

#### Object Count Calculation

```python
for detected_object in detections:
    class_counts[detected_object.class_id] += 1
```

####  Email Alert System (SMTP)

```python
import smtplib
from email.mime.multipart import MIMEMultipart

# Setup server
server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
server.login(sender_email, password)

# Create email
msg = MIMEMultipart()
msg.attach(MIMEText(alert_message))
msg.attach(annotated_image)

# Send email
server.sendmail(sender_email, rescue_team_email, msg.as_string())
server.quit()
```

---

###  Example Output

| Input Image       | YOLO11 Detection          | Email Alert                      |
| ----------------- | ------------------------- | -------------------------------- |
|<img width="304" height="425" alt="image" src="https://github.com/user-attachments/assets/5180a767-9a41-4c4c-89b2-56d8bf2917ee" /> | 9 persons, 1 dog detected | Email with bounding box & counts |

---

### Comparison with YOLOv8

| Model   | Detection Accuracy                     | Recall              |
| ------- | -------------------------------------- | ------------------- |
| YOLOv11 | High (9 humans, 1 dog)               | Better at occlusion |
| YOLOv8  |  Missed 2 humans, misclassified a cow | Lower               |
<img width="740" height="564" alt="image" src="https://github.com/user-attachments/assets/9593943e-a952-4813-ad7c-05f642c7c7db" />

---

###  Future Enhancements

*  Improve recall via dataset augmentation
* Add **SMS/Push notifications** via Twilio/Telegram
*  Add **Geo-location** metadata to alerts
*  Train on **multi-modal data** (e.g., LiDAR, infrared)
*  Secure alert communication

---

###  Contributors

* Shribhakti S Vibhuti
* **Bhoomika Marigoudar**
* Shruti Sutar

