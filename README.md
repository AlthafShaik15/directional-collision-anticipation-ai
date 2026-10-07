🚗 Directional Collision Anticipation AI

<p align="center">
  <strong>An AI-powered system that watches road video, understands what is happening around a vehicle, and warns about possible collision risks.</strong>
</p>

<p align="center">
  <b>See the road → Find objects → Track movement → Understand direction → Predict risk → Give a warning</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/FastAPI-Backend-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/React-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/YOLO-Object%20Detection-111111?style=for-the-badge" alt="YOLO">
  <img src="https://img.shields.io/badge/OpenCV-Computer%20Vision-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white" alt="OpenCV">
  <img src="https://img.shields.io/badge/ByteTrack-Object%20Tracking-orange?style=for-the-badge" alt="ByteTrack">
  <img src="https://img.shields.io/badge/PyTest-Testing-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white" alt="PyTest">
</p>

🧠 What Is This Project?

Imagine a camera placed on the front of a vehicle.

The camera continuously sees the road. This project uses Artificial Intelligence (AI) and Computer Vision to analyze that video.

It tries to answer questions such as:

🚗 Is there a vehicle in front of us?

🏍️ Is a motorcycle moving into our path?

🚶 Is a pedestrian crossing the road?

↔️ Which direction is an object moving?

📍 Is another road user getting closer?

⏱️ How quickly could a possible collision happen?

⚠️ Which nearby object is the biggest threat?

🔊 Should the driver receive a warning?

In simple words:

The system does not only look at what is on the road. It also studies how those objects are moving and estimates whether their movement could create a dangerous situation.

🎯 Why Was This Project Created?

Road traffic can be unpredictable, especially in mixed-traffic environments.

A road can contain:

Cars

Motorcycles

Buses

Trucks

Pedestrians

Bicycles

These road users may move in different directions, change lanes, cross paths, or suddenly enter another vehicle's path.

A normal object detector can tell us:

"There is a motorcycle."

But that is not enough.

This project tries to go one step further:

"There is a motorcycle, it is moving toward our path, and its movement may create a collision risk."

That is the main idea behind Directional Collision Anticipation.

🔄 How Does It Work?

The complete process can be understood as a series of simple steps.

Road / Dashcam Video
        ↓
1. Find Objects
        ↓
2. Keep Track of Objects
        ↓
3. Understand Their Movement
        ↓
4. Understand Their Direction
        ↓
5. Predict Where They May Go
        ↓
6. Check for Possible Collision
        ↓
7. Calculate Risk
        ↓
8. Find the Most Important Threat
        ↓
9. Decide LEFT / AHEAD / RIGHT
        ↓
10. Generate a Warning
        ↓
Web Dashboard

👀 Step 1 — Find Objects

The system first looks at each video frame and tries to identify important road users.

For example:

🚗 Car
🏍️ Motorcycle
🚌 Bus
🚚 Truck
🚶 Pedestrian
🚲 Bicycle

This is done using YOLO v11.

What is YOLO?

YOLO means You Only Look Once.

It is an AI model used for object detection.

Instead of manually telling the computer where every vehicle is, YOLO looks at an image and predicts:

What objects are present

Where they are located

What type of object they are

🎯 Step 2 — Track Objects

Finding an object once is not enough.

Suppose a motorcycle appears in frame 1, frame 2, frame 3, and frame 4.

The system needs to understand that these detections are probably the same motorcycle.

That is where ByteTrack is used.

Simple example

Frame 1 → Motorcycle #1
Frame 2 → Motorcycle #1
Frame 3 → Motorcycle #1
Frame 4 → Motorcycle #1

This allows the system to understand how an object moves over time.

🏃 Step 3 — Understand Movement

After tracking an object, the system studies its movement.

It can estimate things such as:

Speed

Direction of movement

Whether the object is approaching

Whether the object is moving away

How its position changes over time

For example:

Object A
   ↓
Moving closer

Object B
   ↑
Moving away

This information is important because a nearby object is not necessarily dangerous.

A vehicle moving away may be safe.

A vehicle moving quickly toward our path may be more important.

🧭 Step 4 — Understand Direction

The system also tries to determine where a possible threat is located relative to the vehicle.

The main directional categories are:

LEFT       AHEAD       RIGHT
  ←           ↑           →

For example:

A motorcycle entering from the left → LEFT

A vehicle directly in front → AHEAD

A vehicle approaching from the right → RIGHT

This makes the warning easier to understand.

🔮 Step 5 — Predict Future Movement

The system does not only look at where an object is right now.

It also estimates where the object could be in the near future.

The project uses multiple prediction horizons:

0.5 seconds
1.0 second
2.0 seconds

For example:

Current position
      ↓
   Prediction
      ↓
Future position

This helps the system reason about possible future conflicts.

💥 Step 6 — Check for Possible Collision

The next question is:

"Could two moving objects end up in the same dangerous area?"

The system considers information such as:

Distance

Movement speed

Direction

Predicted movement

Possible path intersection

If two paths appear likely to conflict, the situation receives more attention.

⏱️ Step 7 — Calculate Time to Collision

One important concept used by the system is TTC — Time to Collision.

What does TTC mean?

TTC is an estimate of how much time may remain before two moving objects could collide, assuming their current movement continues.

For example:

TTC = 5 seconds

means the estimated collision time is relatively far away.

TTC = 1 second

means the situation may be much more urgent.

TTC is an estimate, not a guarantee that a collision will happen.

⚠️ Step 8 — Calculate Risk

The system combines multiple pieces of information to estimate how serious a situation may be.

It considers factors such as:

⏱️ Time to collision

📏 Distance

🏎️ Speed

🛣️ Possible path intersection

A situation with several dangerous factors can receive a higher risk level.

🏆 Step 9 — Find the Main Threat

There may be many objects in a road scene.

For example:

10 cars
3 motorcycles
2 pedestrians
1 bus

Not every object is dangerous.

The system ranks possible threats and attempts to identify the primary threat — the object that deserves the most attention.

🚨 Step 10 — Give a Directional Warning

After analyzing the scene, the system can classify the main threat as:

⚠️ LEFT
⚠️ AHEAD
⚠️ RIGHT

The goal is to make the warning more useful than simply saying:

"Danger!"

Instead, the system can communicate the approximate direction of the possible threat.

🖥️ Web Dashboard

The project also includes a web interface.

The dashboard is built using:

React

TypeScript

Vite

Tailwind CSS

It provides an interface for interacting with the video-analysis system and viewing its results.

The Python backend communicates with the web interface through FastAPI.

✨ Main Features

Feature

In Simple Words

🔍 Object Detection

Finds cars, motorcycles, buses, trucks, pedestrians and bicycles

🎯 Object Tracking

Keeps track of the same object across video frames

🏃 Motion Analysis

Studies how objects are moving

🧭 Direction Detection

Determines whether a threat is on the left, ahead or right

🔮 Future Prediction

Estimates possible future positions

⏱️ TTC

Estimates possible time before a collision

⚠️ Risk Scoring

Gives higher importance to more dangerous situations

🏆 Threat Ranking

Finds the most important potential threat

🚨 Directional Alert

Provides LEFT / AHEAD / RIGHT warnings

🖥️ Web Dashboard

Provides a user-friendly interface

🧪 Automated Tests

Tests important parts of the system

🏗️ System Architecture

The project has two major parts:

1. AI / Backend

This part processes the video and performs the analysis.

Video
  ↓
OpenCV
  ↓
YOLO v11
  ↓
ByteTrack
  ↓
Motion Analysis
  ↓
Prediction
  ↓
Collision Analysis
  ↓
Risk Assessment

2. Web Frontend

This part allows the user to interact with the system.

AI Backend
     ↓
FastAPI
     ↓
React + TypeScript
     ↓
Web Dashboard

🛠️ Technologies Used

Backend / AI

Technology

What It Does

Python

Main programming language

OpenCV

Reads and processes video

Ultralytics YOLO

Detects objects in video

ByteTrack

Tracks objects across frames

NumPy

Performs numerical calculations

Pandas

Handles data

SciPy

Provides scientific computing utilities

FastAPI

Connects the AI system with the web application

Frontend

Technology

What It Does

React

Builds the web interface

TypeScript

Makes frontend code safer and easier to maintain

Vite

Runs and builds the frontend

Tailwind CSS

Styles the interface

Lucide React

Provides icons

📁 Project Structure

The project is organized into separate parts so that the AI, backend, frontend and tests are easier to maintain.

directional-collision-anticipation-ai/
│
├── api/                 # Backend API
├── config/              # Project configuration
├── docs/                # Documentation
├── frontend/            # React web application
├── models/              # Location for AI model files
├── scripts/             # Helper scripts
├── src/                 # Main AI and processing code
├── tests/               # Automated tests
│
├── .env.example         # Example environment settings
├── README.md            # Project documentation
├── requirements.txt     # Python dependencies
└── package files        # Frontend dependencies/configuration

🚀 How to Run the Project

You do not need to understand the entire AI system before running it.

Follow these steps.

1. Install the Requirements

You should have:

Python 3.9 or newer

Node.js 18 or newer

Git

pip

Check your installations:

python --version
node --version
git --version

2. Download the Project

Clone the repository:

git clone https://github.com/AlthafShaik15/directional-collision-anticipation-ai.git

Move into the project:

cd directional-collision-anticipation-ai

🐍 3. Set Up the Python Backend

Create a virtual environment:

Windows

python -m venv venv

Activate it:

venv\Scripts\activate

Install Python dependencies:

pip install -r requirements.txt

Create your environment file:

copy .env.example .env

🌐 4. Set Up the Frontend

Open a new terminal and move into the frontend folder:

cd frontend

Install the frontend dependencies:

npm install

▶️ 5. Start the Backend

From the project root:

uvicorn api.main:app --host 0.0.0.0 --port 8000

The backend will run on:

http://localhost:8000

▶️ 6. Start the Frontend

Inside the frontend folder:

npm run dev

Open the address shown by Vite, normally:

http://localhost:5173

You can now use the web interface.

🔌 API Endpoints

The backend provides APIs for interacting with the system.

Endpoint

Purpose

POST /api/upload

Upload a video

POST /api/process

Start video processing

GET /api/jobs/{id}

Check processing status

WS /ws/jobs/{id}

Receive live job updates

GET /api/videos/{filename}

Access processed videos

GET /api/source?path=<abs>

Access a source

POST /api/csv_report

Generate CSV report

GET /api/dataset/summary

View dataset information

POST /api/dataset/random

Select a random dataset item

POST /api/dataset/test

Run dataset testing

You do not need to understand APIs to use the web interface. These endpoints mainly allow the frontend and backend to communicate.

🧪 Testing

The project contains automated tests for important parts of the system.

Run the tests with:

pytest tests/ -v

To build the frontend:

cd frontend
npm run build

🎥 Example Scenarios

The system is designed to demonstrate situations such as:

🏍️ Motorcycle Lane Cut-In

A motorcycle suddenly moves into another vehicle's path.

🚶 Pedestrian Crossing

A pedestrian crosses the road and may enter the vehicle's path.

🚗 Vehicle Merge

Another vehicle moves into the current traffic path.

🚦 Mixed Traffic

Cars, motorcycles, pedestrians and other road users move together.

🧪 Current Project Scope

This project is currently a software-based simulation prototype.

Recorded traffic videos are used as simulated dashcam footage.

The current prototype demonstrates:

Object detection

Object tracking

Motion analysis

Trajectory prediction

Collision-risk analysis

Directional reasoning

Driver-response simulation

Collision alerts

Web dashboard visualization

⚠️ Important Limitations

This project is a prototype and should not be treated as a real vehicle safety system.

The current version does not include:

❌ Physical dashcam hardware integration

❌ Real vehicle sensors

❌ CAN Bus integration

❌ Vehicle actuator control

❌ Production-level ADAS hardware

❌ Guaranteed collision prediction

The results depend on the quality of the input video, object detection, tracking and prediction.

This project is intended for research, learning, demonstration and hackathon purposes.

🔮 Future Improvements

The system can be extended in the future with:

📷 Real dashcam integration

🚗 CAN Bus integration

📍 GPS and IMU sensors

🛡️ ADAS actuator integration

📡 V2X communication

⚡ Edge deployment using NVIDIA Jetson

📹 Multi-camera support

🌙 Better night-time vision

🌧️ Better performance in rain and difficult weather

💡 Why This Project Is Different

A simple object-detection system may say:

"There is a motorcycle."

This project tries to answer a more useful question:

"Is that motorcycle moving in a way that could create a collision risk, where is it coming from, and how urgent is the situation?"

That difference is the core idea of this project.

🏆 SIH / Hackathon Context

This project was developed as a software prototype for a Smart India Hackathon (SIH) use case involving collision anticipation and driver assistance.

The focus is on moving from:

Detecting Danger
       ↓
Understanding Danger
       ↓
Predicting Danger
       ↓
Warning the Driver

🤝 Contributing

If you want to improve this project:

Fork the repository.

Create a new branch.

Make your changes.

Test your changes.

Create a pull request.

Example:

git checkout -b feature/my-improvement
git add .
git commit -m "Add my improvement"
git push origin feature/my-improvement

👨‍💻 Author

Althaf Shaik

GitHub:
https://github.com/AlthafShaik15

Project Repository:
https://github.com/AlthafShaik15/directional-collision-anticipation-ai

⭐ Support the Project

If you find this project interesting:

⭐ Star the repository
🍴 Fork the project
💡 Share your ideas
🐛 Report issues
🤝 Contribute improvements

❤️ Final Note

You do not need to be an AI expert to understand the basic idea of this project.

At its simplest:

A camera sees the road → AI identifies road users → the system watches how they move → it predicts possible danger → it identifies where the danger is coming from → and it provides a warning.

That is the idea behind Directional Collision Anticipation AI.
