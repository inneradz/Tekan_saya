# Tekan_saya
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Do you love me?</title>
  <style>
    body {
      background-color: #fff0f5;
      font-family: 'Comic Sans MS', cursive, sans-serif;
      text-align: center;
      padding-top: 100px;
    }

    h1 {
      font-size: 2.5em;
      color: #d6336c;
    }

    #message {
      margin-top: 30px;
      font-size: 1.2em;
      color: #ff69b4;
    }

    .button-container {
      margin-top: 40px;
      position: relative;
      height: 300px;
    }

    button {
      padding: 15px 25px;
      font-size: 1.2em;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      position: absolute;
    }

    #yesBtn {
      background-color: #ff85a2;
      color: white;
      transition: 0.3s ease;
    }

    #noBtn {
      background-color: #888;
      color: white;
      right: 40%;
    }
  </style>
</head>
<body>

  <h1>Do you love me?</h1>
  <div id="message"></div>

  <div class="button-container">
    <button id="yesBtn">Yes</button>
    <button id="noBtn">No</button>
  </div>

  <script>
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const message = document.getElementById('message');
    let clickCount = 0;

    const container = document.querySelector('.button-container');

    function getRandomPosition() {
      const containerRect = container.getBoundingClientRect();
      const btnWidth = yesBtn.offsetWidth;
      const btnHeight = yesBtn.offsetHeight;

      let x, y, noRect;
      let attempts = 0;

      do {
        x = Math.random() * (containerRect.width - btnWidth);
        y = Math.random() * (containerRect.height - btnHeight);
        noRect = noBtn.getBoundingClientRect();
        attempts++;

        // elakkan bertindih dengan butang No
      } while (
        (x + containerRect.left < noRect.right &&
         x + containerRect.left + btnWidth > noRect.left &&
         y + containerRect.top < noRect.bottom &&
         y + containerRect.top + btnHeight > noRect.top)
        && attempts < 100
      );

      return { x, y };
    }

    yesBtn.addEventListener('mouseenter', () => {
      if (clickCount < 59) {
        const { x, y } = getRandomPosition();
        yesBtn.style.left = `${x}px`;
        yesBtn.style.top = `${y}px`;
        message.innerText = 'Hehe kejar la saya 😝';
        clickCount++;
      } else if (clickCount === 59) {
        yesBtn.style.left = '35%';
        yesBtn.style.top = '0';
        message.innerText = '';
      }
    });

    yesBtn.addEventListener('click', () => {
      if (clickCount >= 60) {
        message.innerHTML = `<strong>Yes - I love you so much baby 💖</strong>`;
      }
    });

    noBtn.addEventListener('click', () => {
      message.innerHTML = `<em>OHW you don’t love me, bro? Okayyy, I get it.<br>Okayyy, no worries, I’ll just be over here, serving looks and sipping tea. Byeeee ☕💅</em>`;
    });
  </script>

</body>
</html>