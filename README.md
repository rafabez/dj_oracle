# DjOracle - The Musical Crystal Ball 🎶

Welcome to **DjOracle**, an AI-powered music recommendation tool designed for **DJs, music curators, and enthusiasts** who love discovering fresh, alternative tracks. With DjOracle, simply input a song, artist, or style, and the **Oracle** will generate a unique playlist just for you! ✨

![DjOracle Preview](https://www.imaginaia.com.br/djoracle/crystal_ball_thumb.jpg)

🔗 **Live Demo:** [DjOracle](https://imaginaia.com.br/djoracle/)  
👤 **GitHub Profile:** [rafabez](https://github.com/rafabez)  
📜 **License:** MIT  

---

## 🚀 Features

- 🎵 **AI-Powered Music Curation** – Generates **10 unique, alternative tracks** based on your input.
- 🎨 **Dynamic Backgrounds** – Uses AI-generated images to **set the mood** of your selection.
- 🔥 **DJ-Optimized Selections** – Avoids mainstream choices, **focusing on underground gems**.
- 📱 **Fully Responsive** – Designed for **mobile and desktop** with a fixed layout.
- ⚡ **Fast & Lightweight** – Runs on **vanilla JavaScript**, no frameworks needed.

---

## 🛠️ Tech Stack

- **HTML, CSS, JavaScript** – Core technologies for the frontend.
- **Pollinations.ai API** – Powers both **text-based music recommendations** and **AI-generated background images**.
- **Fetch API** – Handles API calls for dynamic content.

---

## 📜 How It Works

1. **Enter a song, artist, or genre** in the input field.
2. Click **"Consult the Oracle"**.
3. The AI generates **10 alternative tracks** that fit the mood of your input.
4. A **dynamic AI-generated background** is fetched based on your selection.

---

## 📂 Project Structure

```
dj_oracle/
│-- index.html      # Main HTML structure
│-- script.js       # JavaScript logic (API calls, background fetching, etc.)
│-- style.css       # Styling and responsiveness
│-- assets/         # Images and static files
```

---

## 📝 Code Overview

### **1. API Configuration**
```js
const API = {
  IMAGE: "https://image.pollinations.ai/prompt/",
  TEXT: "https://text.pollinations.ai/"
};
```
- Defines the **Pollinations.ai API** endpoints for **image and text generation**.

### **2. Fetching the AI-Generated Background**
```js
async function setBackgroundImage(prompt) {
  const background = document.getElementById("background");
  const imageUrl = `${API.IMAGE}${encodeURIComponent(prompt)}`;
  
  try {
    const img = new Image();
    img.src = imageUrl;
    img.onload = () => {
      background.style.backgroundImage = `url('${imageUrl}')`;
    };
  } catch (error) {
    console.error("Error fetching background image:", error);
  }
}
```
- Fetches an **AI-generated image** based on the user’s input.
- Dynamically updates the **background image** for an immersive experience.

### **3. Fetching Music Recommendations**
```js
async function fetchMusicRecommendations(query) {
  const output = document.getElementById("suggestionsOutput");

  if (!query) {
    output.innerHTML = "Please enter a song or artist.";
    return;
  }

  output.innerHTML = "Consulting the Oracle... Please wait.";
  setBackgroundImage(query);

  const prompt = `DJ Oracle is an expert in curating unique, alternative playlists tailored for DJ sets.\n\nAnalyze: \"${query}\" and provide 10 related, creative tracks.`;

  try {
    const response = await fetch(`${API.TEXT}${encodeURIComponent(prompt)}`);
    const text = await response.text();
    output.innerHTML = text;
  } catch (error) {
    console.error("Error consulting DjOracle:", error);
    output.innerHTML = "An error occurred while consulting the Oracle.";
  }
}
```
- Calls the **Pollinations.ai text API** to generate a **list of 10 alternative tracks**.
- Uses **async/await** to handle the request efficiently.

### **4. Event Listener for Button Click**
```js
document.addEventListener("DOMContentLoaded", () => {
  setBackgroundImage("DjOracle - Musical Crystal Ball");
  document.getElementById("consultDjOracleBtn").addEventListener("click", () => {
    fetchMusicRecommendations(document.getElementById("songQuery").value.trim());
  });
});
```
- Ensures the **background image loads on page startup**.
- Attaches a click event to the **"Consult the Oracle" button**.

---

## 🎨 Styling & Responsive Design

DjOracle uses a **fixed layout** with a **centered UI**. The background is **dynamically updated**, and all elements scale properly for both **desktop and mobile screens**.

### **Key CSS Features:**
```css
body {
    overflow: hidden; /* Prevents scrolling */
    display: flex;
    justify-content: center;
    align-items: center;
}
.centered-column {
    width: 50%;
    text-align: center;
    background: rgba(64, 65, 79, 0.85);
    padding: 20px;
    border-radius: 10px;
}
textarea {
    width: 90%;
    height: 300px;
    resize: none;
}
```
- **Locks scrolling** for a more immersive experience.
- **Fully responsive**, adjusting for different screen sizes.
- **Modern UI with shadows and transparency**.

---

## 🤝 Contributing

Want to improve DjOracle? Feel free to fork the repo, submit pull requests, or open issues.

### **To Contribute:**
1. Fork the repository.
2. Clone it: `git clone https://github.com/rafabez/dj_oracle.git`
3. Create a new branch: `git checkout -b feature-branch`
4. Make your changes and commit: `git commit -m "Added a cool feature"`
5. Push to your fork and submit a PR.

---

## 📜 License

This project is open-source under the **MIT License**.

---

## 🎧 Final Thoughts

DjOracle is a **fun, AI-powered way to discover music** beyond mainstream playlists. Whether you're a **DJ, music enthusiast, or just exploring new sounds**, DjOracle provides an **intelligent curation experience**. Give it a try at **[DjOracle Live](https://imaginaia.com.br/djoracle/)!** 🚀

