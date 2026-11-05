Real-Time Driver Drowsiness Detection System 🚗💤

A real-time, non-intrusive computer vision application designed to detect driver fatigue and prevent road accidents. This hybrid system uses OpenCV Haar Cascades for rapid spatial face/eye tracking and a custom Convolutional Neural Network (CNN) built with TensorFlow/Keras to classify the driver's ocular state (Awake vs. Sleepy).

🌟 Key Features

Real-Time Tracking: Captures live webcam feed and processes frames with minimal latency using CPU.

Dynamic Bounding Boxes: Draws dynamic visual indicators around the face (Blue) and eyes (Green for Awake, Red for Sleepy).

Smart Alert System: Filters out natural blinking by triggering a "DROWSINESS ALERT!" only when the eyes remain closed for over 15 consecutive frames.

Lightweight CNN Architecture: Optimized for edge-computing with high accuracy (~97%) and a small parameter footprint.

🛠️ Tech Stack

Language: Python

Deep Learning Framework: TensorFlow / Keras

Computer Vision: OpenCV (cv2)

Environment: Jupyter Notebook

📂 Dataset Specification

The model is trained on a localized Kaggle eye dataset consisting of over 67,000 cropped images.

Classes: awake (0), sleepy (1)

Format: Grayscale, resized to 24x24 pixels.

Preprocessing: Pixel values normalized via rescale=1./255.

⚙️ Installation & Setup

1. Clone the repository or download the project files.
Ensure your project folder contains your Jupyter Notebook and the extracted dataset folder.

2. Install required dependencies:
Run the following command in your terminal or command prompt:

pip install tensorflow opencv-python numpy scikit-learn


3. Download Haar Cascades:
The system requires two XML files from OpenCV for spatial detection. The provided code automatically downloads these if they are missing:

haarcascade_frontalface_default.xml

haarcascade_eye.xml

🚀 How to Run

Open the Jupyter Notebook (.ipynb) file.

Train the Model: Run the training cells to load the dataset and train the CNN. The model will automatically save as drowsiness_model.keras in your current directory.
(Note: You can reduce the epochs parameter for faster training).

Run the Inference Engine: Execute the final webcam script block.

Exit: Click on the active video window and press the q key to safely release the webcam and close the application.

🧠 Model Architecture

The custom CNN is built using the Sequential API:

Conv2D + MaxPooling2D (x2): Extracts hierarchical visual features (edges, curves, eyelid shapes).

Flatten: Converts 3D spatial matrices to 1D vectors.

Dense (128 units): Fully connected layer with ReLU activation.

Dropout (0.5): Randomly deactivates 50% of neurons to prevent dataset memorization (overfitting).

Dense (1 unit): Output node with a Sigmoid activation function mapping predictions to binary states (0 = Awake, 1 = Sleepy).

🔮 Future Enhancements

Infrared Camera Integration: For seamless night-time operation inside vehicle cabins.

Head Pose Estimation: To track pitch and yaw (e.g., head nodding) for detecting micro-sleeps even when eyes are obscured by sunglasses.

Hardware Porting: Deploying the model onto edge devices like a Raspberry Pi for embedded automotive functionality.

Author: Prithviraj Chandrashekhar Bari

Institution: K.K. Wagh Institute of Engineering Education and Research (KKWIEER)
