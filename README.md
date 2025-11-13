from zipfile import ZipFile
import os
from PIL import Image

# Prepare folder
folder = "/mnt/data/vapehub_site"
os.makedirs(folder, exist_ok=True)

# Save logo
logo_path = "/mnt/data/981D958A-EC29-469A-B6EF-D94D768F58E8.jpeg"
img = Image.open(logo_path)
img.save(f"{folder}/logo.jpeg")

# Create index.html
index_html = """<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VAPE HUB Barcelona</title>
<style>
body{margin:0;font-family:Arial;background:#0b0b0b;color:white;}
header{padding:20px;text-align:center;font-size:32px;background:#000;}
.hero{height:300px;display:flex;align-items:center;justify-content:center;background:#000;}
.hero img{height:180px;}
.section{padding:40px 20px;text-align:center;}
.products{display:flex;flex-wrap:wrap;justify-content:center;gap:20px;}
.product{background:#111;padding:20px;border-radius:10px;width:250px;}
footer{background:#000;padding:20px;text-align:center;margin-top:40px;font-size:14px;}
a{color:#f7c15a;}
</style>
</head>
<body>
<header>VAPE HUB</header>

<div class="hero">
<img src="logo.jpeg">
</div>

<div class="section">
<h2>Welcome to VAPE HUB Barcelona</h2>
<p>Your premium destination for disposables, e-liquids, pods, CBD and more.</p>
</div>

<div class="section">
<h2>Product Categories</h2>
<div class="products">
<div class="product"><h3>Disposables</h3><p>Lost Mary, Elfbar, Micro, DrippedBar, CrystalSK</p></div>
<div class="product"><h3>E‑Liquids</h3><p>Driffter</p></div>
<div class="product"><h3>Pods / Devices</h3><p>Smok, Aspire, Geekvape, Vaporesso, Voopoo</p></div>
<div class="product"><h3>CBD</h3><p>Iguana Smoke</p></div>
</div>
</div>

<footer>
<p><b>Address:</b> Carrer Ample, 52, Ciutat Vella, 08002 Barcelona, España</p>
<p><b>Phone:</b> +34 615 43 86 98</p>
<p><b>Instagram:</b> @vapehub_barcelona</p>
<p><b>Email:</b> Vapehub77158@gmail.com</p>
</footer>

</body>
</html>
"""

with open(f"{folder}/index.html", "w") as f:
    f.write(index_html)

# Zip the folder
zip_path = "/mnt/data/VAPE_HUB_WEBSITE.zip"
with ZipFile(zip_path, 'w') as zipf:
    zipf.write(f"{folder}/index.html", arcname="index.html")
    zipf.write(f"{folder}/logo.jpeg", arcname="logo.jpeg")

zip_path
