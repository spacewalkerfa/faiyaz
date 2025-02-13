<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Be My Valentine?</title>
    <style>
        /* General Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        #intention-image{
            height: 300px;
            width: 200px;
        }

        /* Body Styling */
        body {
            font-family: 'Arial', sans-serif;
            background-color: #ffb3c6;
            color: #fff;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            overflow: hidden;
            position: relative;
            background-image: url('https://cdn.pixabay.com/photo/2017/08/30/06/05/heart-2692780_960_720.jpg');
            background-size: cover;
            background-position: center;
            text-align: center;
            animation: fadeInBackground 2s ease-out;
        }

        /* Animation for Background Fade */
        @keyframes fadeInBackground {
            0% { opacity: 0; }
            100% { opacity: 1; }
        }

        /* Floating Circle Styling */
        @keyframes float {
            0% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-30px);
            }
            100% {
                transform: translateY(0);
            }
        }

        .circle {
            position: absolute;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.6);
            animation: float 3s ease-in-out infinite;
            opacity: 0.8;
        }

        /* Add pastel colors to the circles */
        .circle:nth-child(1) {
            background-color: #f9a8d4;
            top: 10%;
            left: 20%;
            animation-duration: 4s;
        }

        .circle:nth-child(2) {
            background-color: #a7c7e7;
            top: 25%;
            left: 35%;
            animation-duration: 3.5s;
        }

        .circle:nth-child(3) {
            background-color: #ffddc1;
            top: 50%;
            left: 55%;
            animation-duration: 5s;
        }

        .circle:nth-child(4) {
            background-color: #c3c3f4;
            top: 65%;
            left: 75%;
            animation-duration: 4.2s;
        }

        /* Title Styling */
        h1, h2 {
            color: white;
            animation: fadeIn 2s ease-out;
        }

        h1 {
            font-size: 3rem;
        }

        h2 {
            font-size: 2rem;
            color: #ff385c;
        }

        /* Button Container Styling */
        .btn-container {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }

        /* Common Button Styling */
        .btn {
            background-color: #ff385c;
            color: white;
            font-size: 1.5rem;
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.3s;
            font-weight: bold;
            box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
        }

        .btn:hover {
            background-color: #e31b3d;
            transform: scale(1.1);
        }

        /* Page Transition Effects */
        .page {
            display: none;
            animation: fadeInPage 1s ease-out;
        }

        .active {
            display: block;
        }

        /* Fade-in Animation */
        @keyframes fadeInPage {
            0% {
                opacity: 0;
            }
            100% {
                opacity: 1;
            }
        }

        /* No Button Animation */
        .no-btn {
            position: relative;
            transition: all 0.3s ease-in-out;
        }

        .yes-btn {
            position: relative;
            z-index: 10;
        }

        /* Image Styling */
        .dress-image, .intention-image {
            width: 80%;
            max-width: 400px; /* Adjusted for better responsiveness */
            height: auto; /* Maintain aspect ratio */
            margin-top: 20px;
            border-radius: 10px;
            object-fit: cover; /* Ensure the image fits well */
        }

        /* Final Confirmation Message */
        #message {
            font-size: 1.5rem;
            color: #ff385c;
            text-align: center;
            margin-top: 30px;
            font-weight: bold;
            display: none;
        }

    </style>
</head>
<body>

    <!-- Floating Circles -->
    <div class="circle"></div>
    <div class="circle"></div>
    <div class="circle"></div>
    <div class="circle"></div>

    <!-- First Page (Main Question) -->
    <div class="page active" id="page1">
        <h1>To the Cutest girl there ^^ ! 💖</h1>
        <h2>Will You Be My Valentine?</h2>
        <div class="btn-container">
            <button class="btn no-btn" id="noBtn" onclick="moveButton()">No 😞</button>
            <button class="btn yes-btn" onclick="nextPage('page2')">Yes, I Will! 😍</button>
        </div>
    </div>

    <!-- Second Page (Location Choices) -->
    <div class="page" id="page2">
        <h1>Where would you like to go? ✈️</h1>
        <h2>Pick your favorite location!</h2>
        <div class="btn-container">
            <button class="btn" onclick="nextPage('page3')">CAFE ❤️</button>
            <button class="btn" onclick="nextPage('page3')">EXCITING RIDES  🍣</button>
            <button class="btn" onclick="nextPage('page3')">NETFLIX & CHILL  🍕</button>
        </div>
    </div>

    <!-- Third Page (Food Choices) -->
    <div class="page" id="page3">
        <h1>What food would you like to try? �</h1>
        <h2>Let me know your cravings!</h2>
        <div class="btn-container">
            <button class="btn" onclick="nextPage('page4')">Dominos 🍣</button>
            <button class="btn" onclick="nextPage('page4')">Anything until free 🍕</button>
            <button class="btn" onclick="nextPage('page4')">will decide later 🍝</button>
        </div>
    </div>

    <!-- Fourth Page (Dress Suggestion) -->
    <div class="page" id="page4">
        <h1>Ready for a hot look? 👗</h1>
        <h2>Here’s a dress I think you’d look stunning in!</h2>
        <!-- <img class="dress-image" src="https://outcasts.in/cdn/shop/files/larelle-4.jpg?v=1736336802" alt="Black Dress" /> -->
        <div class="btn-container">
            <button class="btn" onclick="nextPage('page5')">I Love It! 😍</button>
        </div>
    </div>

    <!-- Fifth Page (Final Confirmation Message) -->
    <div class="page" id="page5">
        <h1>💖 I’m so happy you said yes! 💖</h1>
        <p>Can’t wait to spend tomorrow with you, exited to celebrate our second valentine together!</p>
        <div class="btn-container">
            <button class="btn" onclick="nextPage('page6')">Let’s Go! 🎉</button>
        </div>
    </div>

    <!-- Sixth Page (Intention Page) -->
    <div class="page" id="page6">
        <h1>My Intention With You 💖</h1>
        <h2>shh i want this badly rn with u </h2>
        <img id="intention-image" src="https://us.123rf.com/450wm/bialasiewicz/bialasiewicz1702/bialasiewicz170201345/72232297-erotic-couple-having-sex-under-the-shower.jpg?ver=6" alt="Intention Image" />
        <div class="btn-container">
            <button class="btn" onclick="showMessage()">I also want this! 💖</button>
        </div>
    </div>

    <!-- Confirmation Message -->
    <div id="message">
        <p>💌 I’m so happy you said yes! I love u soooo much Simran. so as per my plan wil tomorrow morning at 10 ,
             and i want u to look the best , stunning and amazing than ever , my jaws should drop seeing u  💖</p>
    </div>

    <script>
        function moveButton() {
            // Get the "No" button
            const noBtn = document.getElementById("noBtn");

            // Get the current position of the button
            const randomX = Math.floor(Math.random() * 200) - 100;
            const randomY = Math.floor(Math.random() * 200) - 100;

            // Move the "No" button away from the click
            noBtn.style.transform = `translate(${randomX}px, ${randomY}px)`;
        }

        function nextPage(pageId) {
            // Hide the current page and show the next one
            const currentPage = document.querySelector('.active');
            currentPage.classList.remove('active');
            
            const nextPage = document.getElementById(pageId);
            nextPage.classList.add('active');
        }

        function showMessage() {
            document.getElementById("message").style.display = "block";
        }
    </script>

</body>
</html>
