
# PROJECT UTS PENGOLAHAN CITRA 2024

Ketentuan Project :
- Potretlah sebuah citra yang berisi Nama Lengkap masing-masing
- Nama ditulis tangan menggunakan pena dengan tinta Merah,hijau,dan biru
- Pemilihan uratan warna dibebaskan.

Pengerjaan project menggunakan bahasa python dan yang dikerjakan sebegai berikut :
1. Deteksi warna pada citra
2. Carilah dan urutkan ambang batas terkecil sampai terbesar





## Authors

- [@angelnatassya](https://www.github.com/angelnatassya)


## Aplikasi

 Gunakan aplikasi Jupiter Notebook pada Anaconda Navigator.
 Gambar Inputan :
 ![Nama](https://github.com/angelnatassya/pcd_uts/blob/main/nm.jpg)
 
1. Deteksi warna pada Citra
   
⁂ Pendeteksian Warna Biru
- Import Library yang akan digunakan.
```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
```
- Import image (nama file 'nm').
```bash
img=cv2.imread('nm.jpg')
```
- Ubah warna gambar dari format BGR (Blue-Green-Red) menjadi HSV (Hue-Saturation-Value)
```bash
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
- Deteksi warna menggunakan HSV
```bash
lower_blue = np.array([90, 50, 50])
upper_blue = np.array([130, 255, 255])
```
- Gunakan mask untuk menggunakan rentang warna tertentu dari HSV
```bash
mask = cv2.inRange(hsv_img, lower_blue, upper_blue)
```
- Tampilkan gambar asli dan histogram menggunakan perintah berikut
```bash
plt.figure(figsize=(12, 6))
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Gambar Asli')

plt.subplot(2, 2, 2)
plt.hist(img.ravel(), 256, [0, 256])
plt.title('Histogram Gambar Asli')
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/histogramasli.png)
- Mask deteksi biru dan histogram
```bash
plt.subplot(2, 2, 3)
plt.imshow(mask, cmap='gray')
plt.title('Mask Deteksi Warna Biru')

plt.subplot(2, 2, 4)
plt.hist(mask.ravel(), 256, [0, 256])
plt.title('Histogram Mask Deteksi Warna Biru')

plt.show()
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/histoblue.png)


⁂ Pendeteksian Warna Merah
- Import Library yang akan digunakan.
```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
```
- Import image (nama file 'nm').
```bash
img=cv2.imread('nm.jpg')
```
- Ubah warna gambar dari format BGR (Blue-Green-Red) menjadi HSV(Hue-Saturation-Value)
```bash
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
- Deteksi warna merah yang telah dikonversi ke warna HSV. Lalu pada akhir kode gabungan dua mask yang telah dibuat sebelumnya untuk menambah elemen wise.
```bash
lower_red = np.array([0, 100, 100])
upper_red = np.array([10, 255, 255])
mask1 = cv2.inRange(hsv_img, lower_red, upper_red)

lower_red = np.array([160, 100, 100])
upper_red = np.array([179, 255, 255])
mask2 = cv2.inRange(hsv_img, lower_red, upper_red)

red_mask = mask1 + mask2
```
- Tampilkan gambar asli dan histogram menggunakan perintah berikut
```bash
plt.figure(figsize=(12, 6))
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Gambar Asli')

plt.subplot(2, 2, 2)
plt.hist(img.ravel(), 256, [0, 256])
plt.title('Histogram Gambar Asli')
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/histogramasli.png)
- Mask deteksi merah dan histogram
```bash
fig, axs = plt.subplots(1, 2, figsize=(12, 6))

axs[0].imshow(red_mask, cmap='gray')
axs[0].set_title('Deteksi Warna Merah')

red_hist = cv2.calcHist([img], [0], red_mask, [256], [0, 256])
axs[1].plot(red_hist, color='r')
axs[1].set_title('Histogram Deteksi Warna Merah')

plt.show()
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/histored.png)

⁂ Pendeteksian Warna Hijau
- Import Library yang akan digunakan.
```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
```
- Import image (nama file 'nm').
```bash
img=cv2.imread('nm.jpg')
```
- Ubah warna gambar dari format BGR (Blue-Green-Red) menjadi HSV(Hue-Saturation-Value)
```bash
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
- Deteksi warna hijau yang telah dikonversi ke warna HSV.
```bash
lower_green = np.array([35, 100, 100])
upper_green = np.array([90, 255, 255])
green_mask = cv2.inRange(hsv_img, lower_green, upper_green)
```
- Tampilkan gambar asli dan histogram menggunakan perintah berikut
```bash
plt.figure(figsize=(12, 6))
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Gambar Asli')

plt.subplot(2, 2, 2)
plt.hist(img.ravel(), 256, [0, 256])
plt.title('Histogram Gambar Asli')
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/histogramasli.png)
- Mask deteksi hijau dan histogram
```bash
fig, axs = plt.subplots(1, 2, figsize=(12, 6))
axs[0].imshow(green_mask, cmap='gray')
axs[0].set_title('Deteksi Warna Hijau')

green_hist = cv2.calcHist([img], [1], green_mask, [256], [0, 256])
axs[1].plot(green_hist, color='g')
axs[1].set_title('Histogram Deteksi Warna Hijau')

plt.show()
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/histogreen.png)
2. Ambang Batas
   
⁂ Ambang batas biru
- - Import Library yang akan digunakan.
```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
```
- Import image (nama file 'nm').
```bash
img=cv2.imread('nm.jpg')
```
- Ubah warna gambar dari format BGR (Blue-Green-Red) menjadi HSV (Hue-Saturation-Value)
```bash
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
- Deteksi ambang batas bawah dan atas warna menggunakan HSV
```bash
lower_blue = np.array([90, 50, 50])
upper_blue = np.array([130, 255, 255])
```
- Penerapan masker biru pada gambar
```bash
blue_mask = cv2.inRange(hsv_img, lower_blue, upper_blue)
blue_image = cv2.bitwise_and(img, img, mask=blue_mask)
```
- Menampilkan gambar original dan deteksi biru
```bash
plt.figure(figsize=(12, 6))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(blue_image, cv2.COLOR_BGR2RGB))
plt.title('Blue Image')
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.show()
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/blue.png)

⁂ Pendeteksian Warna Merah-Biru
- Import Library yang akan digunakan.
```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
```
- Import image (nama file 'nm').
```bash
img=cv2.imread('nm.jpg')
```
- Ubah warna gambar dari format BGR (Blue-Green-Red) menjadi HSV(Hue-Saturation-Value)
```bash
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
- Deteksi warna merah yang telah dikonversi ke warna HSV. Lalu pada akhir kode gabungan dua mask yang telah dibuat sebelumnya untuk menambah elemen wise.
```bash
lower_red = np.array([0, 100, 100])
upper_red = np.array([10, 255, 255])
mask1 = cv2.inRange(hsv_img, lower_red, upper_red)

lower_red = np.array([160, 100, 100])
upper_red = np.array([179, 255, 255])
mask2 = cv2.inRange(hsv_img, lower_red, upper_red)

red_mask = mask1 + mask2
```
- Deteksi ambang batas bawah dan atas warna menggunakan HSV
```bash
lower_blue = np.array([90, 50, 50])
upper_blue = np.array([130, 255, 255])
```
- Penerapan masker biru pada gambar
```bash
blue_mask = cv2.inRange(hsv_img, lower_blue, upper_blue)
```
- Menampilkan dua gambar secara berdampingan: gambar asli dan hasil deteksi warna merah dan biru yang digabungkan.
```bash
fig, axs = plt.subplots(1, 2, figsize=(12, 6))
axs[0].imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
axs[0].set_title('Original Image')

result = cv2.bitwise_or(red_mask, blue_mask)
axs[1].imshow(result, cmap='gray')
axs[1].set_title('Red and Blue Detection')

plt.show()
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/rb.png)

⁂ Pendeteksian Warna Merah-Biru-Hijau
- Import Library yang akan digunakan.
```bash
import cv2
import matplotlib.pyplot as plt
import numpy as np
```
- Import image (nama file 'nm').
```bash
img=cv2.imread('nm.jpg')
```
- Ubah warna gambar dari format BGR (Blue-Green-Red) menjadi HSV(Hue-Saturation-Value)
```bash
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
```
- Deteksi warna merah yang telah dikonversi ke warna HSV. Lalu pada akhir kode gabungan dua mask yang telah dibuat sebelumnya untuk menambah elemen wise.
```bash
lower_red = np.array([0, 100, 100])
upper_red = np.array([10, 255, 255])
mask1 = cv2.inRange(hsv_img, lower_red, upper_red)

lower_red = np.array([160, 100, 100])
upper_red = np.array([179, 255, 255])
mask2 = cv2.inRange(hsv_img, lower_red, upper_red)

red_mask = mask1 + mask2
```
- Deteksi ambang batas bawah dan atas warna menggunakan HSV
```bash
lower_blue = np.array([90, 50, 50])
upper_blue = np.array([130, 255, 255])
```
- Penerapan masker biru pada gambar
```bash
blue_mask = cv2.inRange(hsv_img, lower_blue, upper_blue)
```
- Deteksi warna hijau yang telah dikonversi ke warna HSV.
```bash
lower_green = np.array([35, 100, 100])
upper_green = np.array([90, 255, 255])
green_mask = cv2.inRange(hsv_img, lower_green, upper_green)
result = cv2.bitwise_or(red_mask, blue_mask, green_mask)
```
- Menampilkan dua gambar secara berdampingan: gambar asli dan hasil deteksi gabungan warna merah, biru, dan hijau.
```bash
fig, axs = plt.subplots(1, 2, figsize=(12, 6))
axs[0].imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
axs[0].set_title('Original Image')

axs[1].imshow(result, cmap='gray')
axs[1].set_title('Red, Blue, and Green Detection')

plt.show()
```
![hist](https://github.com/angelnatassya/pcd_uts/blob/main/rgb.png)




