# MWAD_EX05_image-carousel-in-react
## Date: 16/05/2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM

APP.JS

```
import React, { useState, useEffect } from "react";
import "./App.css";

const images = [
  "/11.jpeg",
  "/22.webp",
  "/33.jpg",  
];

function App() {
  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex((currentIndex - 1 + images.length) % images.length);
  };

  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  },);

  return (
    <div className="app">
      <h1 className="carousel-title">Image Carousel</h1>
      <div className="carousel-container">
        <img
          src={images[currentIndex]}
          alt={`Slide ${currentIndex + 1}`}
          className="carousel-image"
        />
        <div className="carousel-buttons">
          <button onClick={prevImage}>Previous</button>
          <button onClick={nextImage}>Next</button>
        </div>
      </div>
    </div>
  );
}

export default App;
```
APP.CSS

```

.app {
  min-height: 100vh;
  background: linear-gradient(135deg, #cea82a 0%, #eb3706 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.carousel-title {
  font-size: 3rem;
  color: #fff;
  margin-bottom: 30px;
  text-decoration: underline;
  text-shadow: 2px 2px 4px #00000050;
}

.carousel-container {
  width: 500px;
  background-color: #ffffff;
  border-radius: 15px;
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
  overflow: hidden;
  text-align: center;
  padding: 20px;
}

.carousel-image {
  width: 100%;
  height: auto;
  border-radius: 10px;
}
.carousel-buttons {
  margin-top: 20px;
}

.carousel-buttons button {
  padding: 10px 20px;
  margin: 0 10px;
  font-size: 16px;
  font-weight: bold;
  cursor: pointer;
  border: none;
  background-color: #007bff;
  color: white;
  border-radius: 8px;
  transition: background-color 0.3s ease, transform 0.2s;
}

.carousel-buttons button:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

```

## OUTPUT

![alt text](image.jpg)

## RESULT
The program for creating Image Carousel using React is executed successfully.
