# Setup SSH for Git on Windows

**SSH Key** adalah metode alternatif untuk autentikasi ke Gitlab. SSH Key cukup kita buat satu kali dan bahkan bisa digunakan lagi di tempat lain seperti Github dan Bitbucket.

Jika anda pengguna Windows gunakan cara ini untuk membuat SSH Key saat anda menggunakan Git. Secara default, sistem akan menambahkan key pada folder /Users//.ssh directory.

**Setup SSH Key**

Gunakan Git Bash Window (Yang otomatis terinstal saat menginstal Git di Windows.)

** Langkah 1 Men-generate public/private rsa key pair**, tulis commandline seperti di bawah ini:

ssh-keygen -t rsa

** Langkah 2 Tekan enter untuk menerima default file path ** pada:

/c/Users/<username>/.ssh/id_rsa.

**Langkah 3 Enter dan enter pertanyaan "passphrase", untuk membuat default identitas dari public dan private keys.**

**Langkah 4 Menampilkan konten folder .ssh untuk melihat "key files" nya:**

dir .ssh

#hasilnya id_rsa id_rsa.pub

**Langkah 5 Menambahkan key ke ssh-agent**, jika anda tidak ingin mengetikan password setiap saat anda menggunakan key, cara nya sbb:

Start agent:

 eval $(ssh-agent)
 
 #hasilnya contoh agent pid 9700

Ketikan ssh-add dan path private key file nya:

 ssh-add ~/.ssh/id_rsa

**Langkah 6 Menambahkan public key ke github anda. Buka public key anda di ~/.ssh/id_rsa.pub atau dengan perintah:

cat ~/.ssh/id_rsa.pub

Copy semua teks yang ditampilkan, lalu pada github.com anda, klik Settings > SSH and GPG Keys > buat key baru klik New SSH Key > paste kan key ke dalam kotak > klik add SSH Key button.

**Langkah 7 Ketik perintah dibawah untuk menguji koneksi SSH ke Github:**

ssh -T git@github.com
Jika berhasil pesannya kurang lebih seperti dibawah ini:

Hi, You've successfully authenticated, but Github does not provide shell acess.
Langkah 8 Lakukan push dengan perintah:

git push -u origin master