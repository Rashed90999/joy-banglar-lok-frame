# joy-banglar-lok-frame
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>জয় বাংলা পোস্টার মেকার</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
    <style>
        body { font-family: 'SolaimanLipi', sans-serif; background: #121212; color: #fff; text-align: center; margin: 0; padding: 20px; }
        .container { max-width: 500px; margin: auto; }
        #canvas-container { position: relative; width: 500px; height: 500px; background: #000; overflow: hidden; margin-top: 20px; border: 2px solid #333; }
        #user-photo { position: absolute; top: 150px; left: 50%; transform: translateX(-50%); width: 220px; cursor: move; z-index: 1; }
        .frame-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; z-index: 2; pointer-events: none; }
        .controls { margin-top: 20px; background: #222; padding: 15px; border-radius: 10px; }
        input[type="file"] { margin: 10px 0; }
        button { background: #e74c3c; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-size: 16px; margin-top: 10px; }
        button:hover { background: #c0392b; }
    </style>
</head>
<body>

<div class="container">
    <h2>পোস্টার তৈরি করুন</h2>
    <p>আপনার ছবি আপলোড করুন এবং ডাউনলোড বাটনে ক্লিক করুন</p>

    <div id="canvas-container">
        <img id="user-photo" src="https://via.placeholder.com/200?text=Upload+Photo" alt="Your Photo">
        <img class="frame-overlay" src="https://i.ibb.co/XRL7KPr/frame-overlay.png" alt="Frame Overlay">
    </div>

    <div class="controls">
        <input type="file" accept="image/*" onchange="previewImage(event)">
        <br>
        <button onclick="downloadPoster()">ডাউনলোড করুন</button>
    </div>
</div>

<script>
    function previewImage(event) {
        var reader = new FileReader();
        reader.onload = function(){
            var output = document.getElementById('user-photo');
            output.src = reader.result;
        };
        reader.readAsDataURL(event.target.files[0]);
    }

    function downloadPoster() {
        html2canvas(document.querySelector("#canvas-container")).then(canvas => {
            let link = document.createElement('a');
            link.download = 'joy-bangla-poster.png';
            link.href = canvas.toDataURL();
            link.click();
        });
    }
</script>

</body>
</html>
