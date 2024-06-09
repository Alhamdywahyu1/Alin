### Transformasi Matriks Linier

#### Skalasi Matriks

Skalasi matriks mengubah ukuran objek dengan faktor skalar tertentu pada sumbu x dan y.

Skalasi Matriks:

\[ S = \begin{bmatrix} sx & 0 \\ 0 & sy \end{bmatrix} \]

Jika faktor skalasi \(sx\) dan \(sy\) sama, maka objek diperbesar atau diperkecil secara proporsional.

Pada contoh kode di bawah ini dengan nilai skalasi 2 ada perubahan matriks yaitu yang awalnya ada pada lokasi (1,1) berubah menjadi (2,2) dan (0,1) menjadi (0,2) yang berarti posisi akan berubah mengikuti nilai skalasi.

```python
import numpy as np
import matplotlib.pyplot as plt

def plot_square(points, title, color, label_prefix):
    plt.scatter(points[:, 0], points[:, 1], color=color, label=title)
    for i in range(points.shape[0]):
        plt.text(points[i, 0], points[i, 1], f'{label_prefix}({points[i, 0]},{points[i, 1]})', fontsize=12, color=color)
    plt.plot(points[:, 0], points[:, 1], color=color, alpha=0.3)

# Skalar untuk Skalasi
scaling_factor = 2

# Matriks Skalasi
scaling_matrix = np.array([[scaling_factor, 0],
                           [0, scaling_factor]])

# Titik-titik persegi
square_points = np.array([[0, 0],
                          [1, 0],
                          [1, 1],
                          [0, 1]])

# Titik-titik setelah Skalasi
scaled_square = np.dot(square_points, scaling_matrix)

# Visualisasi Skalasi Matriks
plt.figure(figsize=(8, 8))
plt.axhline(0, color='grey', linewidth=0.5)
plt.axvline(0, color='grey', linewidth=0.5)
plt.grid(True, which='both')

plot_square(square_points, "Original Square", 'blue', 'O')
plot_square(scaled_square, "Scaled Square (x2)", 'red', 'S')

plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Skalasi Matriks (x2)')
plt.legend()
plt.axis('equal')
plt.show()
Rotasi Matriks
Rotasi matriks memutar titik-titik dalam suatu ruang dengan sudut tertentu 
�
θ terhadap titik asal.

Rotasi Matriks:

�
�
=
[
cos
⁡
�
−
sin
⁡
�
sin
⁡
�
cos
⁡
�
]
R 
θ
​
 =[ 
cosθ
sinθ
​
  
−sinθ
cosθ
​
 ]

Pada contoh kode di bawah adalah contoh rotasi matriks 45 derajat dan perubahan yang terjadi adalah bentuk matriks berputar sesuai derajat yang telah ditentukan.

python
Salin kode
import math

theta_deg = 45
theta_rad = math.radians(theta_deg)

# Matriks Rotasi
rotation_matrix = np.array([[math.cos(theta_rad), -math.sin(theta_rad)],
                            [math.sin(theta_rad), math.cos(theta_rad)]])

# Titik-titik persegi
square_points = np.array([[0, 0],
                          [1, 0],
                          [1, 1],
                          [0, 1]])

# Vektor setelah Rotasi
rotated_square = np.dot(square_points, rotation_matrix)

# Visualisasi Rotasi Matriks
plt.figure(figsize=(8, 8))
plt.axhline(0, color='grey', linewidth=0.5)
plt.axvline(0, color='grey', linewidth=0.5)
plt.grid(True, which='both')

plot_square(square_points, "Original Square", 'blue', 'O')
plot_square(rotated_square, "Rotated Square (45 degrees)", 'red', 'R')

plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Rotasi Matriks (45 Derajat)')
plt.legend()
plt.axis('equal')
plt.show()
Refleksi Matriks
Refleksi matriks mencerminkan titik-titik terhadap sumbu tertentu, seperti sumbu x atau sumbu y.

Refleksi Matriks:

Refleksi terhadap sumbu y:

�
�
=
[
−
1
0
0
1
]
R 
y
​
 =[ 
−1
0
​
  
0
1
​
 ]

Refleksi terhadap sumbu x:

�
�
=
[
1
0
0
−
1
]
R 
x
​
 =[ 
1
0
​
  
0
−1
​
 ]

Pada contoh kode refleksi matrik pada sumbu y di bawah menunjukkan sebuah perubahan pada lokasi matriksnya yang awalnya (1,1) menjadi (-1,1) dan (1,0) menjadi (-1,0) yang berarti ketika refleksi matriks terhadap sumbu y maka lokasi dari koordinat x-nya (angka koordinat pertama) akan berubah menjadi negatif atau positifnya.

Dan untuk refleksi sumbu x memiliki konsep yang sama hanya saja berbeda lokasi refleksi-nya saja.

python
Salin kode
# Matriks Refleksi terhadap Sumbu Y
reflection_matrix = np.array([[-1, 0],
                              [0, 1]])

# Titik-titik persegi
square_points = np.array([[0, 0],
                          [1, 0],
                          [1, 1],
                          [0, 1]])

# Terapkan Refleksi terhadap Titik-titik Persegi
reflected_square = np.dot(square_points, reflection_matrix)

# Visualisasi Refleksi Matriks
plt.figure(figsize=(8, 8))
plt.axhline(0, color='grey', linewidth=0.5)
plt.axvline(0, color='grey', linewidth=0.5)
plt.grid(True, which='both')

plot_square(square_points, "Original Square", 'blue', 'O')
plot_square(reflected_square, "Reflected Square", 'red', 'R')

plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Refleksi Terhadap Sumbu Y')
plt.legend()
plt.axis('equal')
plt.show()
Shear Matriks
Shear matriks menggeser satu sumbu objek dengan faktor tertentu tanpa mengubah sumbu lainnya.

Shear Matriks:

Shear terhadap sumbu x:

�
ℎ
�
=
[
1
�
�
0
1
]
Sh 
x
​
 =[ 
1
0
​
  
k 
x
​
 
1
​
 ]

Shear terhadap sumbu y:

�
ℎ
�
=
[
1
0
�
�
1
]
Sh 
y
​
 =[ 
1
k 
y
​
 
​
  
0
1
​
 ]

Contoh kode di bawah adalah contoh kode matriks shear terhadap sumbu X dan dapat dilihat pada salah satu elemennya yang awalnya (1,1) menjadi (1,2.5) dan (1,0) menjadi (1,1.5) tetapi 2 elemen lainnya tidak berubah.

python
Salin kode
# Matriks Shear
shear_matrix = np.array([[1, 1.5],
                         [0, 1]])

# Titik-titik persegi
square_points = np.array([[0, 0],
                          [1, 0],
                          [1, 1],
                          [0, 1]])

# Terapkan Shear
sheared_square = np.dot(square_points, shear_matrix)

# Visualisasi Shear Matriks
plt.figure(figsize=(8, 8))
plt.axhline(0, color='grey', linewidth=0.5)
plt.axvline(0, color='grey', linewidth=0.5)
plt.grid(True, which='both')

plot_square(square_points, "Original Square", 'blue', 'O')
plot_square(sheared_square, "Sheared Square", 'red', 'S')

plt.xlabel('X-axis')
plt.ylabel('Y-axis')
plt.title('Shear Matriks')
plt.legend()
plt.axis('equal')
plt.show()ini_test
