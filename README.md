# lfs-mekanik
Lfs Yönergeleri Doğrultusunda Dağıtım Oluşturma Mekanizması

 KURULUM YÖNERGELERİ

 git clone https://github.com/milisarge/lfs-mekanik.git lfs-mekanik
 cd lfs-mekanik
 export LFS=/mnt/lfs

 gerekli kaynak kodların indirilmesi 
 ./lfs-mekanizma -ki

 birinci ayarlar yapılır.
 ./lfs-mekanizma -ba

 lfs kullanıcısıyla oturum acılmış olur..

chroot derlenmeye baslanır.
 cd lfs-mekanik
 ./lfs-mekanizma -cd

 =======>  '/home/lfs/lfs-mekanik/chroot/cards/talimat' derleme basarili 
 yukarıdaki ifade goruldukten sonra exit komutu ile lfs kullanıcısından çıkılır.

lfs tools uretici sistemin sıkıstırılması(yedeklemek için)
 ./lfs-mekanizma -cs

üretici sistemin yedeklenmesinden sonra üretici sisteme girmek için gerekli ayarlar yapılır.

 ./lfs-mekanizma -ia

 üretici sisteme girilir.

 ./lfs-mekanizma -cg

 root [ / ]#   ekranına dusulur.

uretici sistem içersindeyken gerekli exportlar yapılır.

 export PATH=/bin:/usr/bin:/sbin:/usr/sbin:/tools/bin:/root/bin
 export FORCE_UNSAFE_CONFIGURE=1

 cd /root/base 

base paket dizinine girilir.

 base_derle

 komutu verilip base sistemin kurulumu sağlanır.

 "bash chroot dışına çıkıp elle kurulmalıdır."  yazısı görülünce
 "exit" ile chroot dışına çıkılır

 ./lfs-mekanizma -bk

 komutu verilir.işlem aşagıdaki şekilde sonlanmalıdır.
 bash 4.3.30-3
 bash.tr 4.3.30-3

 tekrar chroot içine girilir.ortam değişkenleri ayarlandıktan sonra,base derlenmeye devam edilir.

 ./lfs-mekanizma -cg
 export PATH=/bin:/usr/bin:/sbin:/usr/sbin:/tools/bin:/root/bin
 export FORCE_UNSAFE_CONFIGURE=1
 cd /root/base
 base_derle 

 enson bu bilgi ile derleme bitmelidir.
 =======> Installing 'ca-certificates1454658816x86_64.mps' succeeded.
 =======> compress ca-certificates1454658816x86_64.mps

 base paketlerin paket_depo altında toplanması

 paketlerin arsivlenmesi

 paketleri_arsivle

 chroottan cıkılıp,base sistemin yedegi alınır.

 exit 
 ./lfs-mekanizma -ui
 ./lfs-mekanizma -bs

 pisi paketçinin derlenmesi

 paketçi derlenmesi yapmak için ikincil ayarlar çalıştırılır.

 ./lfs-mekanizma -ia

 sisteme girmek için

 ./lfs-mekanizma -cg

 python derleme

 cd /root/base/python && omps

 perl modulu XML-parser kurulumu
 cpan shelline girilir

 cpan

 shellde bu komutla kurulur.sorular enterla geçilir.

 install XML::Parser
 /usr/bin/make install  -- OK  ifadesini görülürse kurulum tamamdır.exit le shellden cıkılır.

 intltool kurulumu

 cd /root/base/intltool && omps

 daha sonra pisi-arge icindeki "siralama"daki python modulleri kurulur.aşağıdaki formda.

 tar xf kaynak_kod
 cd kymak_kod
 python setup.py install

en son sistemi pisi kurulduktan sonra core klonlanır.
daha sonra işlemleri 32 bit de yaptıysanız etc/pisi/pisi.conf dosyasına gerekli ayarlar yapılır.
