# Mishawash-X
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>DehoMesh — Layer One</title>

    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: Arial, Helvetica, sans-serif;
            background: #f7f7f5;
            color: #111;
            min-height: 100vh;
            overflow-x: hidden;
        }

        .app {
            width: min(1100px, 94%);
            margin: auto;
            padding: 35px 0 50px;
        }

        /* ---------------- TITLE ---------------- */

        .layer-title {
            text-align: center;
            font-size: 34px;
            font-weight: 500;
            letter-spacing: 4px;
            margin-bottom: 7px;
        }

        .title-line {
            width: 160px;
            height: 2px;
            background: #111;
            margin: auto;
        }

        .brand {
            width: fit-content;
            margin: 22px auto 35px;
            padding: 12px 35px;
            border: 2px solid #111;
            border-radius: 18px;
            background: white;
            font-size: 30px;
            font-weight: 700;
            box-shadow: 0 3px 0 #111;
        }

        /* ---------------- METRICS ---------------- */

        .metrics {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 18px;
            max-width: 850px;
            margin: auto;
        }

        .metric {
            border: 2px solid #111;
            border-radius: 35px;
            background: white;
            min-height: 75px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            font-size: 21px;
            cursor: pointer;
            transition: 0.2s ease;
            box-shadow: 0 3px 0 #111;
            user-select: none;
        }

        .metric:hover {
            transform: translateY(-3px);
        }

        .metric.active {
            background: #111;
            color: white;
            box-shadow: 0 3px 0 #555;
        }

        .icon {
            font-size: 27px;
        }

        /* ---------------- BODY AREA ---------------- */

        .body-section {
            position: relative;
            min-height: 650px;
            margin-top: 35px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .human {
            position: relative;
            width: 300px;
            height: 590px;
        }

        /* Head */

        .head {
            position: absolute;
            width: 75px;
            height: 92px;
            border: 3px solid #111;
            border-radius: 48% 48% 45% 45%;
            top: 8px;
            left: 50%;
            transform: translateX(-50%);
            background: #fff;
        }

        /* Neck */

        .neck {
            position: absolute;
            width: 42px;
            height: 48px;
            border-left: 3px solid #111;
            border-right: 3px solid #111;
            top: 90px;
            left: 50%;
            transform: translateX(-50%);
            background: #fff;
        }

        /* Torso */

        .torso {
            position: absolute;
            width: 125px;
            height: 230px;
            border: 3px solid #111;
            border-radius: 45% 45% 25% 25%;
            top: 125px;
            left: 50%;
            transform: translateX(-50%);
            background: white;
        }

        /* Arms */

        .arm {
            position: absolute;
            width: 36px;
            height: 225px;
            border: 3px solid #111;
            border-radius: 30px;
            background: white;
            top: 137px;
        }

        .arm.left {
            left: 50px;
            transform: rotate(12deg);
        }

        .arm.right {
            right: 50px;
            transform: rotate(-12deg);
        }

        /* Hands */

        .hand {
            position: absolute;
            width: 38px;
            height: 48px;
            border: 3px solid #111;
            border-radius: 50%;
            background: white;
            top: 348px;
        }

        .hand.left {
            left: 27px;
        }

        .hand.right {
            right: 27px;
        }

        /* Legs */

        .leg {
            position: absolute;
            width: 52px;
            height: 260px;
            border: 3px solid #111;
            background: white;
            top: 320px;
            border-radius: 20px 20px 15px 15px;
        }

        .leg.left {
            left: 98px;
            transform: rotate(2deg);
        }

        .leg.right {
            right: 98px;
            transform: rotate(-2deg);
        }

        /* Feet */

        .foot {
            position: absolute;
            width: 85px;
            height: 37px;
            border: 3px solid #111;
            border-radius: 50% 50% 40% 40%;
            background: white;
            top: 558px;
        }

        .foot.left {
            left: 65px;
            transform: rotate(-5deg);
        }

        .foot.right {
            right: 65px;
            transform: rotate(5deg);
        }

        /* ---------------- HEART ---------------- */

        .heart {
            position: absolute;
            top: 185px;
            left: 50%;
            transform: translateX(-50%);
            font-size: 39px;
            color: #d71920;
            cursor: pointer;
            z-index: 10;

            transition:
                transform 0.15s ease,
                filter 0.15s ease;
        }

        .heart:hover {
            transform: translateX(-50%) scale(1.18);
            filter: drop-shadow(0 0 5px rgba(215, 25, 32, 0.5));
        }

        /* ---------------- TOOLTIP ---------------- */

        .tooltip {
            position: absolute;
            top: 135px;
            left: calc(50% + 85px);
            width: 220px;
            padding: 18px 20px;
            background: white;
            border: 2px solid #111;
            border-radius: 15px;
            font-size: 18px;
            line-height: 1.5;
            opacity: 0;
            transform: translateY(8px);
            pointer-events: none;
            transition: 0.2s ease;
            box-shadow: 4px 4px 0 #111;
            z-index: 20;
        }

        .tooltip.show {
            opacity: 1;
            transform: translateY(0);
        }

        .tooltip strong {
            color: #d71920;
        }

        .hover-text {
            position: absolute;
            top: 270px;
            left: calc(50% + 100px);
            font-size: 14px;
            color: #555;
        }

        /* ---------------- INFO PANEL ---------------- */

        .info-panel {
            width: min(700px, 90%);
            margin: -10px auto 0;
            background: white;
            border: 2px solid #111;
            border-radius: 20px;
            padding: 22px;
            text-align: center;
            min-height: 100px;
            box-shadow: 4px 4px 0 #111;
        }

        .info-panel h2 {
            margin-bottom: 8px;
            font-size: 23px;
        }

        .info-panel p {
            color: #444;
            line-height: 1.6;
        }

        /* ---------------- BOTTOM NOTE ---------------- */

        .note {
            width: min(700px, 90%);
            margin: 35px auto 0;
            background: white;
            border-radius: 18px;
            padding: 18px 22px;
            border: 1px solid #ddd;
            box-shadow: 0 4px 15px rgba(0,0,0,0.08);
            font-size: 17px;
        }

        .red {
            color: #d71920;
            font-weight: bold;
        }

        /* ---------------- RESPONSIVE ---------------- */

        @media (max-width: 700px) {

            .layer-title {
                font-size: 27px;
            }

            .brand {
                font-size: 25px;
            }

            .metrics {
                grid-template-columns: repeat(2, 1fr);
            }

            .metric {
                font-size: 17px;
                min-height: 65px;
            }

            .body-section {
                transform: scale(0.88);
                transform-origin: top center;
                min-height: 590px;
            }

            .tooltip {
                left: calc(50% + 65px);
            }

            .hover-text {
                left: calc(50% + 70px);
            }
        }

        @media (max-width: 450px) {

            .metrics {
                grid-template-columns: 1fr;
            }

            .metric {
                min-height: 60px;
            }

            .body-section {
                transform: scale(0.75);
                margin-bottom: -100px;
            }

            .tooltip {
                left: calc(50% + 45px);
            }

            .hover-text {
                left: calc(50% + 50px);
            }
        }

    </style>
</head>

<body>

<div class="app">

    <!-- TITLE -->

    <div class="layer-title">
        LAYER ONE
    </div>

    <div class="title-line"></div>

    <div class="brand">
        DehoMesh
    </div>


    <!-- METRIC BUTTONS -->

    <div class="metrics">

        <div class="metric active" data-title="Steps">
            <span class="icon">👣</span>
            <span>steps</span>
        </div>

        <div class="metric" data-title="BPM">
            <span class="icon">♡</span>
            <span>BPM</span>
        </div>

        <div class="metric" data-title="Oxygen">
            <span class="icon">O₂</span>
            <span>oxygen</span>
        </div>

        <div class="metric" data-title="Sleep">
            <span class="icon">☾</span>
            <span>sleep</span>
        </div>

        <div class="metric" data-title="Gravity">
            <span class="icon">⇩</span>
            <span>gravity</span>
        </div>

        <div class="metric" data-title="Radiation">
            <span class="icon">☢</span>
            <span>radiation</span>
        </div>

    </div>


    <!-- HUMAN BODY -->

    <div class="body-section">

        <div class="human">

            <div class="head"></div>

            <div class="neck"></div>

            <div class="torso"></div>

            <div class="arm left"></div>
            <div class="arm right"></div>

            <div class="hand left"></div>
            <div class="hand right"></div>

            <div class="leg left"></div>
            <div class="leg right"></div>

            <div class="foot left"></div>
            <div class="foot right"></div>


            <!-- HEART -->

            <div
                class="heart"
                id="heart"
                title="Hover over heart">
                ♥
            </div>

            <!-- HEART TOOLTIP -->

            <div class="tooltip" id="tooltip">

                <strong>Cardio Score: 60</strong>
                <br>

                BPM: <span id="bpm">70</span>

            </div>

            <div class="hover-text">
                🖱 Hover over heart
            </div>

        </div>

    </div>


    <!-- INFORMATION -->

    <div class="info-panel">

        <h2 id="infoTitle">
            Steps
        </h2>

        <p id="infoText">
            Daily movement and activity level of the astronaut.
        </p>

    </div>


    <!-- NOTE -->

    <div class="note">

        <span class="red">Red → Mouse</span>

        <br><br>

        Hover over the red heart to reveal the astronaut's
        cardiovascular information.

    </div>

</div>


<script>

    /* ----------------------------------
       HEART INTERACTION
    ---------------------------------- */

    const heart = document.getElementById("heart");
    const tooltip = document.getElementById("tooltip");

    heart.addEventListener("mouseenter", () => {
        tooltip.classList.add("show");
    });

    heart.addEventListener("mouseleave", () => {
        tooltip.classList.remove("show");
    });


    /* ----------------------------------
       METRIC DATA
    ---------------------------------- */

    const metricData = {

        Steps: {
            title: "Steps",
            text: "Tracks astronaut movement and daily physical activity."
        },

        BPM: {
            title: "BPM",
            text: "Monitors heart rate and helps identify cardiovascular changes."
        },

        Oxygen: {
            title: "Oxygen",
            text: "Monitors oxygen-related health parameters for astronaut safety."
        },

        Sleep: {
            title: "Sleep",
            text: "Tracks sleep duration and sleep quality during the mission."
        },

        Gravity: {
            title: "Gravity",
            text: "Provides information about the astronaut's exposure to the space environment."
        },

        Radiation: {
            title: "Radiation",
            text: "Monitors radiation exposure, an important environmental risk in space."
        }

    };


    /* ----------------------------------
       BUTTON INTERACTION
    ---------------------------------- */

    const metrics = document.querySelectorAll(".metric");

    const infoTitle = document.getElementById("infoTitle");
    const infoText = document.getElementById("infoText");


    metrics.forEach(metric => {

        metric.addEventListener("click", () => {

            metrics.forEach(item => {
                item.classList.remove("active");
            });

            metric.classList.add("active");

            const selected = metric.dataset.title;

            infoTitle.textContent =
                metricData[selected].title;

            infoText.textContent =
                metricData[selected].text;

        });

    });

</script>

</body>
</html>
