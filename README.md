
# Jawaban Soal Pelatihan Linux 2025

Ni'mah Fauziyyah A//5027241103

#### [1] Membuat folder baru & masuk ke dalam folder tersebut
```
mkdir artists_who_can_sing && cd artists_who_can_sing
```

#### [2] Mendownload file zip menggunakan wget
```
wget "https://drive.usercontent.google.com/u/0/uc?id=1lV1HVmPTY_BOAK6ToXymRu7V5eVfR0ut&export=download" -O tutorials.zip
```

#### [3] Unzip ke dalam folder baru yang bernama singing_tutorials
```
unzip tutorials.zip -d singing_tutorials
```

#### [4] Masuk ke dalam folder, menampilkan list file, dan menampilkan list yang tersembunyi di singing_tutorials
```
cd singing_tutorials && ls && ls -lah
```

#### [5] Mencari FLAG 1 dari di dalam beberapa tutorial opera - NBAYoungboy, Lalu menyimpannya dalam "flag.txt"
```
find . -type f -iname "*_opera_*_NBAYoungboy*" -exec grep -ho "FLAG{.*}" {} + | sed 's/FLAG{//; s/}//' > ../flag.txt
```

#### [6] Mundur satu file & Mendownload sebuah file baru dengan ketentuan nama "plsrunmeiamnotmalwarefr"
```
cd .. && wget -O plsrunmeiamnotmalwarefr "$(cat flag.txt)"
```

#### [7] Merubah izin execute & menjalankan program tersebut
```
chmod +x plsrunmeiamnotmalwarefr && ./plsrunmeiamnotmalwarefr
```

#### [8] Melihat program yang dijalankan menggunakan CLI
```
file plsrunmeiamnotmalwarefr && ps aux | grep plsrunmeiamnotmalwarefr
```

#### [9] Membuat file bernama ransom.moolah & Cek kembali keadaan ransom
```
touch ransom.moolah && ls -l ransom.moolah
```

#### [10] Mematikan proses tersebut
```
Ctrl + ^C
```

#### [11] Membuat user baru, menambahkan user baru ke group, memastikan user sudah ada di group, lalu login sebagai user tsb.
```
sudo adduser yabadabadoo && sudo usermod -aG sudo yabadabadoo && sudo passwd yabadabadoo && su - yabadabadoo
```

#### [12] Membuat folder fufufafa yang hanya bisa di akses oleh owner, masuk ke folder tsb.
```
mkdir fufufafa && chmod 770 fufufafa && ls -ld fufufafa && cd fufufafa
```

#### [13] Mencari FLAG 2 di sebuah puzzle
```
grep -rhP '^[0-9A-Fa-f]{8}: (?!0000( 0000){7}$)([0-9A-Fa-f]{4} ){7}[0-9A-Fa-f]{4}$' /var/tmp/pls_solve_this_puzzle/ | awk -F ': ' '!seen[$2]++ {print $2}' | uniq | sed -E 's/0000//g; s/ //g' | tr -d '\n' | xxd -r -p > flag2.txt
```

#### [14] Membuat salinan file flag.txt di artists_who_can_sing ke dalam fufufafa
```
su - peacemaker
sudo cp ~/artists_who_can_sing/flag.txt /home/yabadabadoo/fufufafa/
sudo chown yabadabadoo:yabadabadoo /home/yabadabadoo/fufufafa/flag.txt
su - yabadabadoo
ls -lah ~/fufufafa/
cat ~/fufufafa/flag.txt
```

#### [15] Menghapus folder "pls_solve_this_puzzle" beserta seluruh isinya
```
rm -rf /var/tmp/pls_solve_this_puzzle
```

#### [16] Login github & Push github
```
cd ~/fufufafa
gh auth login
git config --global user.email "nmhfauziyyah@gmail.com"
git config --global user.name "nmhfauziyyah@gmail.com"
gh repo create Pelatihan-Linux-2025 --public --confirm
git init
git remote add origin https://github.com/nmhfauziyyah/Pelatihan-Linux-2025.git
git remote -v
git branch * master
git checkout -b main
git add flag.txt
git add flag2.txt 
git commit -m "Operating linux is so ez fr fr"
git push -u origin main -> username github -> token
```
