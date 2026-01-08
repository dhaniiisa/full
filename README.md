<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<title>Balok Tengah</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    background: #c4fcff; position: relative;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
  }

  /* Balok utama */
  .balok-utama {
    width: 450px;
    padding: 90px;
    background: #fff9fd;
    border-radius: 16px;
    text-align: center;
    box-shadow: 0 8px 20px rgba(0,0,0,0.1);
    margin-bottom: 25px;
  }

  .balok-utama h2 {
    margin:10 0 10px;
    color: #333;
  }

  .balok-utama p {
    margin: 10 0 10px;
    font-size: 14px;
    color: #666;
  }

  /* Balok tombol */
  .balok-next {
    width: 200px;
    height: 50px;
    background: #4caf50;
    color: white;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: 0.2s;
  }

  .balok-next:hover {
    background: #43a047;
    transform: scale(1.05);
  }
</style>
</head>
<body>

  <div class="balok-utama">
    <h2>HIIIII👋 Akhirnya kita ketemu lagi</h2>
    <p>Did anything feel a bit odd today?
       Feel free to share your story here. take ur time.
       </p>
  </div>

  <div class="balok-next" onclick="nextPage()">
    go there 
  </div>

<script>
  function nextPage() {
    window.location.href = "next.html";
  }
</script>

</body>
</html>
