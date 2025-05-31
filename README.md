<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Hiệu ứng yêu thương</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: black;
      font-family: Arial, sans-serif;
    }

    .text, .heart {
      position: absolute;
      color: #ff99ff;
      font-weight: bold;
      white-space: nowrap;
      text-shadow: 0 0 10px #ff99ff, 0 0 20px #ff99ff;
      animation: fall linear forwards;
    }

    .heart {
      color: #ff3366;
      font-size: 18px;
      text-shadow: 0 0 8px #ff3366, 0 0 15px #ff3366;
    }

    @keyframes fall {
      0% {
        transform: translateY(-50px);
        opacity: 0;
      }
      10% {
        opacity: 1;
      }
      100% {
        transform: translateY(110vh);
        opacity: 0;
      }
    }

    audio {
      display: none;
    }
  </style>
</head>
<body>

<!-- Nhạc nền -->
<audio id="bgMusic" autoplay loop>
  <source src="music.mp3" type="audio/mpeg">
  Trình duyệt không hỗ trợ audio.
</audio>

<script>
    const texts = [
        "Chúc em yêu của anh ngày 1/6 vui vẻ",
        "Cảm ơn vì em đã đến 💖",
        "Anh sẽ luôn bên cạnh em",
        "Anh yêu em nhiều lắm",
        "Nơi nào đều có 2 ta, chắc chắn",
        "Đào Trung Hiếu 💖 Nguyễn Thị Trang",
    ];

    // Tạo hiệu ứng chữ rơi
    function createFallingText() {
        const el = document.createElement('div');
        el.className = 'text';
        el.innerText = texts[Math.floor(Math.random() * texts.length)];
        el.style.fontSize = (Math.random() * 20 + 20) + 'px';
        el.style.left = Math.random() * (window.innerWidth - 150) + 'px';
        el.style.animationDuration = (Math.random() * 5 + 6) + 's';
        document.body.appendChild(el);

        setTimeout(() => el.remove(), 15000);
    }

    // Tạo hiệu ứng tim rơi
    function createFallingHeart() {
        const el = document.createElement('div');
        el.className = 'heart';
        el.innerText = '❤';
        el.style.left = Math.random() * window.innerWidth + 'px';
        el.style.fontSize = (Math.random() * 10 + 14) + 'px';
        el.style.animationDuration = (Math.random() * 5 + 5) + 's';
        document.body.appendChild(el);

        setTimeout(() => el.remove(), 15000);
    }

    // Tạo liên tục
    setInterval(createFallingText, 500);
    setInterval(createFallingHeart, 200);

    // Khởi động nhạc nếu bị chặn
    document.addEventListener('click', () => {
        const music = document.getElementById('bgMusic');
        if (music.paused) music.play();
    });
</script>

</body>
</html>
