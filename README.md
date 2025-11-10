import zipfile, os

# Prepare ZIP with the files created earlier
zip_path = "/mnt/data/flappy_citypop_package.zip"

with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as zf:
    zf.write("/mnt/data/flappy_citypop_embedded.html", "flappy_citypop_embedded.html")
    zf.write("/mnt/data/flappy_sprite_32.png", "flappy_sprite_32.png")
    zf.write("/mnt/data/icon_192.png", "icon_192.png")
    zf.write("/mnt/data/icon_512.png", "icon_512.png")

zip_path