LAPORAN PRAKTIKUM MONOLITH VS MICROSERVICES
LANGKAH LANGKAH PRAKTIKUM
1. Membuat dan Masuk ke Folder Proyek
   ```bash
   mkdir praktikum-flask-architecture
   ```
   ```bash
   cd praktikum-flask-architecture
   ``` 
2. Membuat Virtual Environment (venv)
   ```bash
   python -m venv env
   ```
3. Mengaktifkan Virtual Environment di Git Bash
   ```bash
   source env/scripts/activate
   ```
4. Menginstal Dependencies
   ```bash
   python -m pip install Flask requests
   ```
5. Membangun Aplikasi Monolith
   Pada arsitektur Monolith, fitur Buku dan Pesanan digabungkan ke dalam satu file 
tunggal monolith_app.py. Membuat nya di visual code.
 Langkah Pengujian Monolith
   * Eksekusi Server (Terminal 1 Git Bash): 
```bash 
python monolith_app.py
```
  * Pengujian Endpoint (Terminal 2 Git Bash): 
Melihat Daftar Buku: 
```bash 
curl http://localhost:5000/books
```
Membuat Pesanan: 
```bash 
curl -X POST -H "Content-Type: application/json" -d '{"book_id": 1}' 
http://localhost:5000/orders
```
6. Membangun Aplikasi Microservices
    Pada arsitektur Microservices, fitur dipecah menjadi 2 aplikasi/layanan terpisah 
yang berjalan pada port berbeda: Book Service (Port 5001) dan Order Service 
(Port 5002).
Langkah Pengujian Microservices 
   * Jalankan Terminal 1 (Book Service): 
```bash 
source env/scripts/activate 
python book_service.py
```
  * Jalankan Terminal 2 (Order Service): 
```bash 
source env/scripts/activate 
python order_service.py
```
  * Uji Coba di Terminal 3 (Client): 
```bash 
curl -X POST -H "Content-Type: application/json" -d '{"book_id": 1}' 
http://localhost:5002/orders
```
7.  Eksperimen Kegagalan
  * Hentikan book_service.py pada Terminal 1 dengan perintah Ctrl + C.  
  * Kirim ulang pesanan melalui Terminal 3 ke order_service.py (Port 5002):  
```bash 
curl -X POST -H "Content-Type: application/json" -d '{"book_id": 1}' 
http://localhost:5002/orders
```





   
