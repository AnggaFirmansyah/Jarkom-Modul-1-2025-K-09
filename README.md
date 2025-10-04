# Jarkom-Modul-1-2025-K-09

## Anggota Kelompok

Angga Firmansyah 5027241062


Naruna Vicrantyo Putra Gangga 5027241105

### Soal 1

### Topografi 

<img width="683" height="658" alt="image" src="https://github.com/user-attachments/assets/318d7b1e-8ec2-4dbe-aaf2-df77a87c005e" />
```
Diatas adalah topografi dari router eru yang berperan sebagai router yang memiliki 2 switch/gateaway
```
### Soal 2

<img width="723" height="331" alt="image" src="https://github.com/user-attachments/assets/8294f78d-2f9b-47ba-9e00-50ce9b48448b" />

```
cat /etc/resolv.conf   //Lihat DNS 
echo nameserver 192.168.122.1 > /etc/resolv.conf // Masukkan ke dalam config agar dapat akses internet
ping google.com -c 3 //tes internet

```
### Soal 3 - 4

```
Sama seperti Nomor sebelumnya
```


### Soal 5

```

nano /root/.bashrc
apt update && apt install -y vsftpd
apt udpadte && apt install -y ftp
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.227.0.0/16
echo nameserver 192.168.122.1 > /etc/resolv.conf

```
### Soal 6

```
nano traffic.sh
chmod +x traffic.sh
./traffic.sh

lalu capture di wireshark dengan filter ip.adr == 10.68.1.1
```

### Soal 7

Install FTP dan VSFTPD sebagai langkah awal

Node Eru : 

Nyalakan server vsftpd lalu buat kedua user : 

<img width="639" height="112" alt="image" src="https://github.com/user-attachments/assets/0691386f-2447-4c76-88a2-13073cc03e19" />

<img width="694" height="171" alt="image" src="https://github.com/user-attachments/assets/5fd76af8-de6a-429f-bab8-86b7029d5cb8" />

Lalu masuk ke direktori tersebut untuk melakukan konfigurasi : 

Tambahkan / pastikan ada:
local_enable=YES
write_enable=YES
chroot_local_user=YES
allow_writeable_chroot=YES
user_sub_token=$USER
user_config_dir=/etc/vsftpd_user_conf


<img width="708" height="233" alt="image" src="https://github.com/user-attachments/assets/2ae89d4f-afb1-4c07-acf4-fe61b77d1667" />

mkdir -p /home/ainur/shared
chown ainur:ainur /home/ainur/shared
chmod 755 /home/ainur /home/ainur/shared


Dapat ditinjau bahwa user ainur bisa melakukan read & write pada folder shared, serta pada gambar dibawah pada user melkor sama sekali tidak bisa mengakses folder shared dan tidak bisa masuk ke dalam direktori tersebut.

<img width="523" height="277" alt="image" src="https://github.com/user-attachments/assets/923d55b3-e37a-457f-8fe8-6061cd4a19d5" />

### Soal 8


Pertama tama login ke FTP Server dengan IP Eru, lalu login dengan user ainur yang telah dibuat pada soal nomor 7 sebelumnya. Lalu gunakan command wget untuk mendownload file tersebut

<img width="698" height="357" alt="image" src="https://github.com/user-attachments/assets/e79cab4a-8d5b-451c-94ee-1a0f1217ae47" />


Eru :
```
Wget “https://drive.google.com/file/d/11ra_yTV_adsPIXeIPMSt0vrxCBZu0r33/view?usp=drive_link” -O cuaca.zip
```
Setelah di downlaod di local, masuk kedalam server dengan ip addres eru dan kredensial ainur.

Gunakan command put untuk download file local ke ftp server.

Hasil WireShark : 
<img width="710" height="405" alt="image" src="https://github.com/user-attachments/assets/4336aa72-d488-408a-917d-ad7b386ce35f" />

<img width="695" height="363" alt="image" src="https://github.com/user-attachments/assets/ab27578f-0aea-4741-ac19-1d096218ac2b" />

### Soal 9 

Eru

```
“https://drive.google.com/file/d/11ua2KgBu3MnHEIjhBnzqqv2RMEiJsILY/view?usp=drive_link” -O Kitab_penciptaan.zip
```
Reminder : 
```

mkdir -p /home/ainur/shared
chown ainur:ainur /home/ainur/shared
chmod 755 /home/ainur
chmod 755 /home/ainur/shared

```

<img width="698" height="337" alt="image" src="https://github.com/user-attachments/assets/0a03ee3c-69bd-469c-a732-ba75f5446686" />

Manwe dengan login FTP user ainur :

<img width="713" height="302" alt="image" src="https://github.com/user-attachments/assets/2a664011-79d1-4deb-8789-d9d4c21158b1" />

Command pada node Eru untuk merubah akses read-only : 
```
chmod 555 /home/ainur/shared
chmod 444 /home/ainur/Kitab_Penciptaan.zip
```

Saat login menggunakan user ainur di node Menwa, tidak dapat login

<img width="703" height="77" alt="image" src="https://github.com/user-attachments/assets/8a243b58-b56d-4d1d-b078-2457b65a4908" />

<img width="703" height="357" alt="image" src="https://github.com/user-attachments/assets/b763c1d1-9b46-4e04-b26e-0c260bf4d407" />

<img width="699" height="365" alt="image" src="https://github.com/user-attachments/assets/76f1331b-3193-4b30-9904-29cc52a6727c" />

### Soal 10

ping -c 100 10.68.1.1

<img width="606" height="449" alt="image" src="https://github.com/user-attachments/assets/f5296b76-638a-4074-b7a7-e89fb32ee232" />

<img width="702" height="365" alt="image" src="https://github.com/user-attachments/assets/6fdf7895-e078-42e9-8ac5-38cac90e18e3" />


Dengan 100% packet loss karena tidak ada data yang ter transmisi dengan benar

### Soal 11

Dengan Node melkor, jalankan : 
```
apt update
apt install -y inetutils-telnetd

ss -tlnp | grep :23

which ufw && ufw status verbose || echo "ufw not installed"
which firewall-cmd && firewall-cmd --state || echo "firewalld not installed"which firewall-cmd && firewall-cmd --state || echo "firewalld not installed"iptables -L -n -v || echo "iptables not available"which nft && nft list ruleset || echo "nft not installed"


apt update
apt install -y ufw
ufw allow 23/tcp
apt update
apt install -y inetutils-telnetd openbsd-inetd
tcpdump -i any -s 0 -w telnet_capture.pcap port 23

```
WireShark : 

<img width="700" height="359" alt="image" src="https://github.com/user-attachments/assets/08f87e14-f550-4efa-b230-9e1260f94cb0" />

### Soal 12
Dengan Node Eru :
```
apt update && apt install -y netcat-openbsd

MELKOR=10.68.1.2
nc -zv $MELKOR 21
nc -zv $MELKOR 80
nc -zv $MELKOR 666


ss -tlnp | grep :21

apt install -y apache2
service apache2 start

ss -tlnp | grep :80

```
## Soal 14

### Setelah gagal mengakses FTP, Melkor melancarkan serangan brute force terhadap  Manwe. Analisis file capture yang disediakan dan identifikasi upaya brute force Melkor. (link file) nc 10.15.43.32 3401

Berdasarkan soal, kami disini disuruh untuk melihat file yang disediakan menggunakan wireshark. Lalu setelah dibuka bisa dilihat gambar dibawah, dibagian kanan bawah itu terdapat 500318 packet yang ada.
<img width="1919" height="1030" alt="Screenshot 2025-10-01 141200" src="https://github.com/user-attachments/assets/4a778263-5cb8-421c-96ad-87970fb12ed0" />

Setelah itu kita diminta untuk mencari data dari user yang berhasil login menggunakan brute force. Karena user menggunakan brute force, disini saya mencari dari packet paling bawah dan mengecek satu-satu packet karena biasanya yang paling bawah itu adalah packet yang berhasil login. Bisa dilihat digambar kalau saya menemukan packet yang berisikan informasi user pada packet 41824.
<img width="827" height="361" alt="Screenshot 2025-10-01 143108" src="https://github.com/user-attachments/assets/f1ae02c9-d0fa-4f33-93ef-af1cfe8b4763" />

### Berikut adalah flag dari soal 14
<img width="846" height="445" alt="Screenshot 2025-10-01 144514" src="https://github.com/user-attachments/assets/509f7123-5ee3-4d6d-a366-aaeff71e607b" />

## Soal 15

### Melkor menyusup ke ruang server dan memasang keyboard USB berbahaya pada node Manwe. Buka file capture dan identifikasi pesan atau ketikan (keystrokes) yang berhasil dicuri oleh Melkor untuk menemukan password rahasia. (link file) nc 10.15.43.32 3402

Disini untuk menemukan device apa yang digunakan, saya mengecek packet dari yang paling atas satu per satu. Lalu di packet nomor 16 itu dibagian string decriptor tertulis bahwa device yang digunakan adalah USB Keyboard
<img width="956" height="468" alt="Screenshot 2025-10-01 212142" src="https://github.com/user-attachments/assets/0fff07b4-4384-43e6-801f-501163ffe895" />

Selanjutnya kita disuruh untuk mencari apa yang ditulis Melkor di wireshark tersebut. Disini saya menggunakan skrip python3 untuk nge-decode hid ke ascii. Untuk skripnya sebagai berikut:
```python
import sys

HID_TO_ASCII = {
    0x04: 'a', 0x05: 'b', 0x06: 'c', 0x07: 'd', 0x08: 'e', 0x09: 'f', 0x0A: 'g',
    0x0B: 'h', 0x0C: 'i', 0x0D: 'j', 0x0E: 'k', 0x0F: 'l', 0x10: 'm', 0x11: 'n',
    0x12: 'o', 0x13: 'p', 0x14: 'q', 0x15: 'r', 0x16: 's', 0x17: 't', 0x18: 'u',
    0x19: 'v', 0x1A: 'w', 0x1B: 'x', 0x1C: 'y', 0x1D: 'z',
    0x1E: '1', 0x1F: '2', 0x20: '3', 0x21: '4', 0x22: '5', 0x23: '6', 0x24: '7',
    0x25: '8', 0x26: '9', 0x27: '0',
    0x28: '\n', 0x29: '[ESC]', 0x2A: '[BACKSPACE]', 0x2B: '\t', 0x2C: ' ',
    0x2D: '-', 0x2E: '=', 0x2F: '[', 0x30: ']', 0x31: '\\', 0x33: ';', 0x34: '\'',
    0x35: '`', 0x36: ',', 0x37: '.', 0x38: '/',
    0x59: '1', 0x5A: '2', 0x5B: '3', 0x5C: '4', 0x5D: '5', 0x5E: '6', 0x5F: '7',
    0x60: '8', 0x61: '9', 0x62: '0',
}

SHIFT_HID_TO_ASCII = {
    0x04: 'A', 0x05: 'B', 0x06: 'C', 0x07: 'D', 0x08: 'E', 0x09: 'F', 0x0A: 'G',
    0x0B: 'H', 0x0C: 'I', 0x0D: 'J', 0x0E: 'K', 0x0F: 'L', 0x10: 'M', 0x11: 'N',
    0x12: 'O', 0x13: 'P', 0x14: 'Q', 0x15: 'R', 0x16: 'S', 0x17: 'T', 0x18: 'U',
    0x19: 'V', 0x1A: 'W', 0x1B: 'X', 0x1C: 'Y', 0x1D: 'Z',
    0x1E: '!', 0x1F: '@', 0x20: '#', 0x21: '$', 0x22: '%', 0x23: '^', 0x24: '&',
    0x25: '*', 0x26: '(', 0x27: ')',
    0x2D: '_', 0x2E: '+', 0x2F: '{', 0x30: '}', 0x31: '|', 0x33: ':', 0x34: '"',
    0x35: '~', 0x36: '<', 0x37: '>', 0x38: '?',
}

def decrypt_hid_data(hid_codes):
    result = ""
    for report in hid_codes:
        if len(report) < 3:
            continue
        modifier_byte = report[0]
        keycode = report[2]
        is_shift_pressed = (modifier_byte & 2) or (modifier_byte & 32)
        char = ''
        if keycode == 0:
            continue
        if is_shift_pressed:
            char = SHIFT_HID_TO_ASCII.get(keycode, HID_TO_ASCII.get(keycode, ''))
        else:
            char = HID_TO_ASCII.get(keycode, '')
        result += char
    return result

def parse_hid_data_from_log(file_content):
    hid_codes = []
    for line in file_content.splitlines():
        if 'HID Data:' in line:
            hex_str = line.split(':')[-1].strip()
            
            try:
                byte_list = [int(hex_str[i:i+2], 16) for i in range(0, len(hex_str), 2)]
                hid_codes.append(byte_list)
            except (ValueError, IndexError):
                continue
    return hid_codes

def main():
    if len(sys.argv) < 2:
        print("Error: Mohon sertakan nama file input.")
        print("Contoh: python3 hid_decoder.py namafile.txt")
        return

    input_filename = sys.argv[1]
    
    try:
        with open(input_filename, 'r') as f:
            log_content = f.read()
    except FileNotFoundError:
        print(f"Error: File '{input_filename}' tidak ditemukan.")
        return

    hid_data_list = parse_hid_data_from_log(log_content)
    
    decoded_text = decrypt_hid_data(hid_data_list)
    print(decoded_text, end='')

if __name__ == "__main__":
    main()
```

### Cara menjalankan skrip
```
python3 hid_decoder.py plaintext.txt > decoded.txt
```

Setelah menggunakan skrip tersebut, maka kita menemukan apa yang kita cari, yaitu `UGx6X3ByMHYxZGVfeTB1cl91czNybjRtZV80bmRfcDRzc3cwcmQ=`

Selanjutnya kita menggunakan decoder base64 online untuk nge-decode pesan tadi agar mendapatkan flag nomor 15

<img width="1919" height="1027" alt="image" src="https://github.com/user-attachments/assets/610b62b2-4d4e-4a9d-b2f3-9176e6a6d8da" />

### Berikut adalah flag dari soal 15
<img width="919" height="433" alt="image" src="https://github.com/user-attachments/assets/b278979c-ed9c-40c8-9ac6-52ae98e8f2d2" />


## Soal 16

### Melkor semakin murka ia meletakkan file berbahaya di server milik Manwe. Dari file capture yang ada, identifikasi file apa yang diletakkan oleh Melkor. (link file) nc 10.15.43.32 3403

Untuk mencari kredensial apa yang digunakan penyerang untuk log in kita bisa lihat dari yang paling bawah karena urutan packet berdasarkan waktu. Disini saya membuka packet yang berwarna merah dengan keterangan RST (Reset) dan ACK (Acknowledge). Didalamnya terdapat informasi yang kita cari 

<img width="1034" height="149" alt="Screenshot 2025-10-01 213723" src="https://github.com/user-attachments/assets/c24dbe58-bd18-41bf-9255-6a4297e1d1e0" />
<img width="514" height="283" alt="Screenshot 2025-10-01 214154" src="https://github.com/user-attachments/assets/6b3e2702-0c19-46a5-8d52-496dd4dec765" />

Dibawahnya juga terdapat beberapa file .exe yang mencurigakan yaitu `q.exe w.exe e.exe r.exe t.exe`

<img width="85" height="85" alt="Screenshot 2025-10-01 214558" src="https://github.com/user-attachments/assets/267c2872-2cb9-4f78-b680-748c11b35766" />
<img width="99" height="86" alt="Screenshot 2025-10-01 214603" src="https://github.com/user-attachments/assets/e1def2a4-f154-44b9-b0f5-a76a2544025c" />
<img width="107" height="87" alt="Screenshot 2025-10-01 214607" src="https://github.com/user-attachments/assets/43d3388f-6d26-4310-9d0b-06f59ebc100a" />
<img width="97" height="88" alt="Screenshot 2025-10-01 214613" src="https://github.com/user-attachments/assets/7d96c7ef-de4d-424b-ab62-859646f44169" />
<img width="107" height="89" alt="Screenshot 2025-10-01 214616" src="https://github.com/user-attachments/assets/2cb43c68-b73d-4272-afda-844a17506cc6" />

Selanjutnya untuk mendapatkan hash dari file .exe tersebut kita harus memilih packet yang terdapat size .exe didalam keterangan packet. `misal SIZE q.exe`
Disini saya memilih acak packetnya karena isinya sama saja asal ada keterangan size .exe yang kita cari.

<img width="1919" height="1032" alt="Screenshot 2025-10-01 215041" src="https://github.com/user-attachments/assets/f5d7bbad-bb29-4be4-b6ec-c61a4032cfd2" />

Setelah kita save secara raw packet yang terdapat .exe, kita gunakan cmd sha256sum di bash untuk decrypt isi dari file tadi.

<img width="717" height="390" alt="Screenshot 2025-10-02 001524" src="https://github.com/user-attachments/assets/b11144df-d93b-432c-9edf-51d1fca18abb" />

### Berikut adalah flag dari soal 16

<img width="896" height="626" alt="Screenshot 2025-10-02 001615" src="https://github.com/user-attachments/assets/a6cb433b-4f3a-481c-858e-acdb510b2b8b" />

## Soal 17

### Manwe membuat halaman web di node-nya yang menampilkan gambar cincin agung. Melkor yang melihat web tersebut merasa iri sehingga ia meletakkan file berbahaya agar web tersebut dapat dianggap menyebarkan malware oleh Eru. Analisis file capture untuk menggagalkan rencana Melkor dan menyelamatkan web Manwe. (link file) nc 10.15.43.32 3404

Untuk mencari file yang mencurigakan disini saya membuka `file → export objects → http`. Disana terdapat 3 file, saya mencoba memasukkan nama dari masing-masing file pada soal hingga berhasil. Bisa disimpulkan bahwa file mencurigakan pertama adalah `Invoice&MSO-Request.doc` dan yang kedua adalah `knr.exe`

<img width="1919" height="877" alt="Screenshot 2025-10-01 223536" src="https://github.com/user-attachments/assets/fb0d3626-785b-4376-be1a-662e30e90a72" />
<img width="752" height="302" alt="Screenshot 2025-10-01 223551" src="https://github.com/user-attachments/assets/bcd3f59a-18ad-421d-ba1f-5793b31b55bd" />

Dan untuk mendapatkan hash dari `knr.exe` itu caranya sama seperti soal sebelumnya. Kita save lalu decrypt menggunakan sha256sum.

<img width="862" height="304" alt="Screenshot 2025-10-01 223755" src="https://github.com/user-attachments/assets/1d55e5b6-0386-4016-a537-d08725990daa" />

### Berikut adalah flag dari soal 17

<img width="815" height="338" alt="Screenshot 2025-10-02 001808" src="https://github.com/user-attachments/assets/1ab5d797-4cdd-4c8a-ab25-c2f8dcd920fa" />

## Soal 18

### Karena rencana Melkor yang terus gagal, ia akhirnya berhenti sejenak untuk berpikir. Pada saat berpikir ia akhirnya memutuskan untuk membuat rencana jahat lainnya dengan meletakkan file berbahaya lagi tetapi dengan metode yang berbeda. Gagalkan lagi rencana Melkor dengan mengidentifikasi file capture yang disediakan agar dunia tetap aman. (link file) nc 10.15.43.32 3405

Untuk soal 18 ini metodenya hampir sama seperti soal 17, namun di export objects kita pilih smb. Disini terdapat 2 file .exe yang mencurigakan.

<img width="1919" height="880" alt="Screenshot 2025-10-01 230011" src="https://github.com/user-attachments/assets/3cb247db-9843-4aa2-a1e7-d8ec91436566" />
<img width="753" height="254" alt="Screenshot 2025-10-01 230034" src="https://github.com/user-attachments/assets/0a83991f-4ee0-4beb-b907-ab93db0ddc9d" />

Dan untuk mendapatkan hash itu juga metodenya sama seperti sebelumnya.

<img width="862" height="393" alt="Screenshot 2025-10-01 230950" src="https://github.com/user-attachments/assets/173cbea5-32b2-4295-b353-8a153c3b3181" />

### Berikut adalah flag dari soal 18

<img width="822" height="569" alt="Screenshot 2025-10-02 002330" src="https://github.com/user-attachments/assets/a56f114c-a278-4b61-9ed6-e68b3154fb8d" />

## Soal 19

### Manwe mengirimkan email berisi surat cinta kepada Varda melalui koneksi yang tidak terenkripsi. Melihat hal itu Melkor sipaling jahat langsung melancarkan aksinya yaitu meneror Varda dengan email yang disamarkan. Analisis file capture jaringan dan gagalkan lagi rencana busuk Melkor. (link file) nc 10.15.43.32 3406

Untuk soal 19 ini cukup singkat, kita membuka packet yang ada keterangan `Mail From`. Disini saya ngecek dari yang paling atas dan kebetulan isinya sama dengan apa yang kita cari.

<img width="1919" height="900" alt="Screenshot 2025-10-01 232445" src="https://github.com/user-attachments/assets/494a3eab-1e5d-4e07-9ea7-9a8c1fb61607" />
<img width="1272" height="877" alt="Screenshot 2025-10-01 232555" src="https://github.com/user-attachments/assets/fcde5de2-762a-4302-bef0-b82feabecf52" />
<img width="1263" height="778" alt="Screenshot 2025-10-01 232653" src="https://github.com/user-attachments/assets/54313f88-5c4c-4f4b-8e7b-869a74781c6d" />

### Berikut adalah flag dari soal 19

<img width="842" height="433" alt="Screenshot 2025-10-02 002754" src="https://github.com/user-attachments/assets/8a42fb7b-fc1b-4486-9917-bd963911c8c7" />

## Soal 20

### Untuk yang terakhir kalinya, rencana besar Melkor yaitu menanamkan sebuah file berbahaya kemudian menyembunyikannya agar tidak terlihat oleh Eru. Tetapi Manwe yang sudah merasakan adanya niat jahat dari Melkor, ia menyisipkan bantuan untuk mengungkapkan rencana Melkor. Analisis file capture dan identifikasi kegunaan bantuan yang diberikan oleh Manwe untuk menggagalkan rencana jahat Melkor selamanya. (link file) nc 10.15.43.32 3407

Pada soal 20, lalu lintas data tidak lagi ditransmisikan dalam bentuk teks biasa seperti sebelumnya. Seluruh komunikasi berjalan melalui protokol terenkripsi, sehingga kontennya tidak bisa langsung dibaca. Berdasarkan penggunaan 	port tertentu dan payload yang tampak teracak, dapat disimpulkan bahwa teknik enkripsi yang digunakan adalah TLS.

<img width="1911" height="888" alt="Screenshot 2025-10-01 233411" src="https://github.com/user-attachments/assets/f47bda10-1ba1-4e9b-a8e0-294786d4f255" />

Selanjutnya untuk mencari file yang ditaruh penyerang, kita ke `file → export objects → http`.

<img width="1916" height="887" alt="Screenshot 2025-10-01 233432" src="https://github.com/user-attachments/assets/86921830-a647-4e7b-92a6-bbad597caaaa" />

Tetapi isinya kosong, itu dikarenakan kita belum memasukkan keylog pada TLS di Wireshark yang kita pakai.

<img width="749" height="544" alt="Screenshot 2025-10-01 233446" src="https://github.com/user-attachments/assets/fd34edd7-4c88-40aa-901c-03243c8565f4" />

Disini kita ke `edit → preferences → protocol → TLS` untuk memberi keylog.

<img width="829" height="615" alt="Screenshot 2025-10-01 233951" src="https://github.com/user-attachments/assets/7ebe3a2c-9280-466b-adfd-3bebd286aaf6" />

Setelah itu balik lagi ke http. Terdapat beberapa file mencurigakan dan yang mencurigakan adalah `invest_20.dll`

<img width="751" height="547" alt="Screenshot 2025-10-01 234349" src="https://github.com/user-attachments/assets/5b72612c-35ac-4fd7-9ec7-1713bdbea8a4" />

Sama seperti sebelumnya, untuk mendapatkan hash dari `invest_20.dll` kita save filenya lalu decrypt menggunakan sha256sum.

<img width="862" height="471" alt="Screenshot 2025-10-01 234545" src="https://github.com/user-attachments/assets/e61dfcdb-59d1-4038-9871-e6bfaef3567e" />

### Berikut adalah flag dari soal 20

<img width="830" height="519" alt="Screenshot 2025-10-02 002948" src="https://github.com/user-attachments/assets/4cd61d04-bbb4-45f0-8933-e7bb35575ddb" />

### REVISI

### Soal 9

<img width="1623" height="820" alt="image" src="https://github.com/user-attachments/assets/25fbbe0f-c83b-4cc4-90f1-1a27a04df7bc" />

Commands : 

```
wget -O /root/Kitab_Penciptaan.zip "https://drive.google.com/uc?export=download&id=11ua2KgBu3MnHEIjhBnzqqv2RMEiJsILY"

cp /root/Kitab_Penciptaan.zip /home/ainur/shared/
chown ainur:ainur /home/ainur/shared/Kitab_Penciptaan.zip
chmod 644 /home/ainur/shared/Kitab_Penciptaan.zip

```
Lalu login dengan FTP di node Eru dan gunakan command :
```
ftp> cd Shared
ftp> get Kitab_Penciptaan.zip
```

### Soal 11



<img width="1919" height="1021" alt="image" src="https://github.com/user-attachments/assets/8efaf1f3-fcf2-4bf0-9f7d-9918857dae23" />



<img width="1919" height="1016" alt="image" src="https://github.com/user-attachments/assets/2e5ff806-8ba5-42ad-9f65-891abb436287" />

Commands :

melkor
```
service openbsd-inetd start

nano /etc/inetd.conf
telnet  stream  tcp  nowait  root  /usr/sbin/tcpd  /usr/sbin/in.telnetd

service openbsd-inetd restart

netstat -tlnp | grep :23

adduser eru
passowrd 123

```
Capture dengan wireshark antara node eru dan melkor

eru

```
service openbsd-inetd start

telnet 10.68.1.2

login dengan eru dan passwordnya

```


### SOAL 12

<img width="724" height="135" alt="image" src="https://github.com/user-attachments/assets/0da09edd-dd69-417f-a47a-4d44039a2dea" />

Commands :

Eru
```
apt update && apt install -y netcat-openbsd

nc -zv 10.68.1.2 21
nc -zv 10.68.1.2 80
nc -zv 10.68.1.2 666

```
<img width="560" height="50" alt="image" src="https://github.com/user-attachments/assets/57add223-b1f1-4de2-a91f-49fa227c4b4a" />

Berubah saat menggunakan command pada melkor :
```
service vsftpd start
```

Lalu kembali ke node eru dan menggunakan command
```
nc -zv 10.68.1.2 80
```

### Soal 13    

<img width="725" height="134" alt="image" src="https://github.com/user-attachments/assets/3977f2de-ea43-4fc1-a6f8-35f9d5b5bf67" />


<img width="1919" height="1018" alt="image" src="https://github.com/user-attachments/assets/f04536aa-6ffb-419a-8886-34c252338d94" />

Penjelasan : Saat capture dengan wireshark dengan filter SSH di node Varda dan Eru, lalu follow stream 

Eru : 
```
service ssh start
```

Varda :
```
ssh eru@10.68.1.1
masukan password
```
Saat di wireshark dapat terlihat paket yang ter enkripsi
