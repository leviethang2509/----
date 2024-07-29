<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Envelope + Letter (Open/Close on Click) with Snowfall Effect</title>
    <link rel="stylesheet" href="./style.css">
    <style>
        .snowflake {
            width: 30px;
            height: 30px;
            background-image: url('./snow.png');
            background-size: contain;
            background-repeat: no-repeat;
            position: absolute;
            animation: snowfall 10s linear infinite;
        }

        @keyframes snowfall {
            0% {
                transform: translateY(-100vh);
            }
            100% {
                transform: translateY(100vh);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="envelope-wrapper">
            <div class="envelope">
                <div class="letter">
                    <div class="text">
                        <strong>gửi chị pé</strong>
                        <br>     ----------------------------------------------------
                                Trước khi rời khỏi nhà chị pé nhớ
                                kt đồ đạc nhóa!!!
                                vd:thước,viết,căn cước công dân....
                                và mang thêm sự tự tin của mình nữa nhe<br></br>
                            
                                -------------------thi tốt nha-----------------------
                        </p>
                    </div>
                </div>
            </div>
            <div class="heart"></div>
        </div>
    </div>
    <audio id="myAudio" loop>
        <source src="./music.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>
    <script>
        const envelope = document.querySelector('.envelope-wrapper');
        envelope.addEventListener('click', () => {
            envelope.classList.toggle('flap');
            var audio = document.getElementById("myAudio");
            if (envelope.classList.contains('flap')) {
                audio.play();
            } else {
                audio.pause();
            }
        });

        function createSnowflake() {
            const snowflake = document.createElement('div');
            snowflake.classList.add('snowflake');
            snowflake.style.left = Math.random() * window.innerWidth + 'px';
            snowflake.style.animationDelay = Math.random() * 10 + 's';
            document.body.appendChild(snowflake);

            setTimeout(() => {
                snowflake.remove();
            }, 10000);
        }

        setInterval(createSnowflake, 100);
    </script>
    <style>
    :root{
    --primary: #fff;
    --bg-color: aqua;
    --bg-envelope-color: #f5edd1;
    --envelope-tab: #ecdeb8;
    --envelope-cover: #e6cfa7;
    --shadow-color: rgba(0, 0, 0, 0.2);
    --txt-color: #444;
    --heart-color: rgb(252, 8, 231);
  }
  body{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    background: var(--bg-color);
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .container {
    height: 100vh;
    display: grid;
    place-items: center;
  }
  .container > .envelope-wrapper {
    background: var(--bg-envelope-color);
    box-shadow: 0 0 40px var(--shadow-color);
  }
  .envelope-wrapper > .envelope {
    position: relative;
    width: 300px;
    height: 230px;
  }
  .envelope-wrapper > .envelope::before {
    content: "";
    position: absolute;
    top: 0;
    z-index: 2;
    border-top: 130px solid var(--envelope-tab);
    border-right: 150px solid transparent;
    border-left: 150px solid transparent;
    transform-origin: top;
    transition: all 0.5s ease-in-out 0.7s;
  }
  .envelope-wrapper > .envelope::after {
    content: "";
    position: absolute;
    z-index: 2;
    width: 0px;
    height: 0px;
    border-top: 130px solid transparent;
    border-right: 150px solid var(--envelope-cover);
    border-bottom: 100px solid var(--envelope-cover);
    border-left: 150px solid var(--envelope-cover);
  }
  .envelope > .letter {
    position: absolute;
    right: 20%;
    bottom: 0;
    width: 54%;
    height: 80%;
    background: var(--primary);
    text-align: center;
    transition: all 1s ease-in-out;
    box-shadow: 0 0 5px var(--shadow-color);
    padding: 20px 10px;
  }
  
  .envelope > .letter > .text {
    font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    color: var(--txt-color);
    text-align: left;
    font-size: 10px;
  }
  .heart {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 15px;
    height: 15px;
    background: var(--heart-color);
    z-index: 4;
    transform: translate(-50%, -20%) rotate(45deg);
    transition: transform 0.5s ease-in-out 1s;
    box-shadow: 0 1px 6px var(--shadow-color);
    cursor: pointer;
  }
  .heart:before, 
  .heart:after {
    content: "";
    position: absolute;
    width: 15px;
    height: 15px;
    background-color: var(--heart-color);
    border-radius: 50%;
  }
  .heart:before {
    top: -7.5px;
  }
  .heart:after {
    right: 7.5px;
  }
  .flap > .envelope:before {
    transform: rotateX(180deg);
    z-index: 0;
  }
  .flap > .envelope > .letter {
    bottom: 100px;
    transform: scale(1.5);
    transition-delay: 1s;
  }
  .flap > .heart {
    transform: rotate(90deg);
    transition-delay: 0.4s;
  }
    </style>
</body>
</html>
