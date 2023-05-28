<html>
<head>
<style>
* {
  box-sizing: border-box;
}

.container {
  width: 50%;
  margin: 0 auto;
  background-color: #f0f0f0;
  padding: 20px;
}

.button {
  display: block;
  width: 100%;
  height: 50px;
  background-color: #4CAF50;
  color: white;
  font-size: 20px;
  text-align: center;
  line-height: 50px;
  cursor: pointer;
}

.progress {
  display: none;
  width: 100%;
  height: 20px;
  background-color: #ddd;
}

.bar {
  width: 0%;
  height: 20px;
  background-color: #4CAF50;
}
</style>
</head>
<body>

<div class="container">
<h1>Trang tải về</h1>
<p>tên file</p>
<p>Bạn có thể tải file của bạn bằng cách nhấn vào nút bên dưới.</p>
<!-- Add an onclick attribute to the button -->
<button class="button" onclick="confirmDownload()">Tải về</button>
<div class="progress">
<div class="bar"></div>
</div>
<p id="time"></p>
</div>

<script>
var progress = document.querySelector(".progress");
var bar = document.querySelector(".bar");
var time = document.getElementById("time");

// Define a function to confirm the download
function confirmDownload() {
  // Ask the user to confirm the download
  var answer = window.confirm("bạn muốn thử trải nghiệm tính năng mới không?");
  // If the user confirms, proceed with the download
  if (answer) {
    download();
  }
}

function download() {
  // Giả sử quá trình tải mất 10 giây
  var duration = 10; 
  // Hiển thị thanh tiến trình và thời gian còn lại
  progress.style.display = "block";
  time.style.display = "block";
  
  // Cập nhật thanh tiến trình và thời gian còn lại mỗi giây
  var interval = setInterval(function() {
    // Tăng chiều rộng của thanh tiến trình theo tỷ lệ phần trăm
    bar.style.width = (100 - duration * 10) + "%";
    // Hiển thị thời gian còn lại
    time.innerHTML = "Thời gian còn lại: " + duration + " giây";
    // Giảm thời gian còn lại
    duration--;
    // Nếu quá trình tải hoàn thành
    if (duration < 0) {
      // Dừng cập nhật thanh tiến trình và thời gian còn lại
      clearInterval(interval);
      // Hiển thị thông báo hoàn thành
      time.innerHTML = "Tải về hoàn thành!";
      // Mở file đã tải về
      window.open("file.png");
    }
    
  },1000);
}
</script>

</body>
</html>
