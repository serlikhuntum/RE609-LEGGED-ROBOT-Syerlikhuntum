# RE609-LEGGED-ROBOT-Syerlikhuntum
# 🦿 Hexapod Leg Simulation (Forward & Inverse Kinematics)

## 📌 Deskripsi

Project ini merupakan simulasi pergerakan kaki robot **hexapod 3 DOF (Degree of Freedom)** menggunakan dua pendekatan utama:

* **Forward Kinematics (FK)** → menghitung posisi ujung kaki berdasarkan sudut sendi
* **Inverse Kinematics (IK)** → menghitung sudut sendi berdasarkan posisi target

Simulasi divisualisasikan menggunakan **Matplotlib Animation** dalam bentuk gerakan real-time dan loop non-stop.

---

## ⚙️ Struktur Kaki Robot

Kaki robot terdiri dari 3 bagian utama:

| Bagian | Panjang  |
| ------ | -------- |
| Coxa   | 22.50 mm |
| Femur  | 60.00 mm |
| Tibia  | 71.45 mm |

---

## 📐 1. Forward Kinematics

### 🎯 Tujuan

Menentukan posisi ujung kaki `(x, z)` berdasarkan sudut:

* θ_femur
* θ_tibia

---

### 📊 Persamaan

Posisi lutut:

```
x2 = x1 + L_femur * cos(θ_femur)
z2 = z1 + L_femur * sin(θ_femur)
```

Posisi ujung kaki:

```
x3 = x2 + L_tibia * cos(θ_femur + θ_tibia)
z3 = z2 + L_tibia * sin(θ_femur + θ_tibia)
```

---

### 🔄 Cara Kerja

1. Sudut dibuat menggunakan fungsi sinus & cosinus (osilasi)
2. Posisi dihitung menggunakan rumus FK
3. Hasil divisualisasikan sebagai animasi kaki bergerak
4. Jejak kaki ditampilkan secara permanen

---

### 🎥 Output

* Gerakan kaki naik-turun dan maju-mundur
* Trajectory (jejak) berwarna **orange**
* Visual real-time

---

## 📐 2. Inverse Kinematics

### 🎯 Tujuan

Menentukan sudut:

* β (Femur)
* γ (Tibia)

berdasarkan target posisi `(x, z)`

---

### 📊 Persamaan

Jarak ke target:

```
r = x - L_coxa
s = sqrt(r² + z²)
```

Sudut lutut:

```
cos(γ) = (L_femur² + L_tibia² - s²) / (2 * L_femur * L_tibia)
γ = acos(cos(γ)) - π
```

Sudut femur:

```
β = atan2(z, r) + acos((L_femur² + s² - L_tibia²) / (2 * L_femur * s))
```

---

### 🔄 Cara Kerja

1. Ditentukan beberapa titik target (trajectory)
2. Sistem menghitung sudut untuk tiap titik
3. Kaki bergerak mengikuti jalur tersebut
4. Jejak trajectory ditampilkan

---

### 🎥 Output

* Gerakan mengikuti jalur (trajectory)
* Jejak berwarna **kuning**
* Target titik ditandai dengan **merah**

---

## 🎨 Visualisasi

Fitur visual:

* Background gelap (dark mode)
* Grid koordinat
* Animasi real-time
* Trajectory permanen
* Informasi posisi & sudut

---

## ▶️ Cara Menjalankan

### 1. Install dependency

```bash
pip install numpy matplotlib
```

### 2. Jalankan program

#### Forward Kinematics

```bash
python forward_kinematics.py
```

#### Inverse Kinematics

```bash
python inverse_kinematics.py
```

---

## 📊 Perbandingan FK vs IK

| Aspek        | Forward Kinematics | Inverse Kinematics |
| ------------ | ------------------ | ------------------ |
| Input        | Sudut              | Posisi             |
| Output       | Posisi             | Sudut              |
| Kompleksitas | Rendah             | Lebih kompleks     |
| Penggunaan   | Simulasi           | Kontrol robot      |

---

## 🚀 Aplikasi

Project ini dapat digunakan untuk:

* Simulasi robot hexapod
* Kontrol kaki robot nyata
* Dasar pergerakan robot (ROS / Gazebo)
* Penelitian robotika

---

## 📌 Catatan

* Sistem menggunakan 2D plane (X-Z)
* Coxa dianggap sebagai offset horizontal
* Gerakan dapat dikembangkan ke 3D

---

## 👨‍💻 Author

Nama: *[Syerli Khuntum Khaira]*
Project: Forward kinematics dan Invers kinematics

---

## ⭐ Future Development

* Integrasi ke ROS 2
* Simulasi di Gazebo
* Kontrol real hardware (ESP32)
* 6 kaki (full hexapod)

---

## 📷 Preview
<img width="937" height="920" alt="Screenshot 2026-04-07 100346" src="https://github.com/user-attachments/assets/5500bcbc-36db-4692-9426-043e7a96af4c" />
<img width="895" height="908" alt="Screenshot 2026-04-07 100724" src="https://github.com/user-attachments/assets/810c1dd4-f696-49f2-9ca6-491cbe9eaadf" />

*()*

---
