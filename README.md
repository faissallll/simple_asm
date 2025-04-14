# simple_asm

testing.asm

Dalam konteks pemrograman, testing ASM berarti mengujicoba kode dalam bahasa assembly — bahasa pemrograman tingkat rendah yang langsung berinteraksi dengan arsitektur prosesor. Testing di sini bisa berupa:

 * Unit testing bagian kecil dari kode assembly.

 * Simulasi atau emulasi untuk melihat bagaimana instruksi bekerja di CPU.

 * Debugging menggunakan alat seperti GDB, NASM, atau emulator seperti QEMU.


![image](https://github.com/user-attachments/assets/69048c4d-bc9c-490b-9814-b943d4a59e35)

penjelasan dari codingan di atas :



* section .data: Tempat menyimpan data seperti string, angka, dsb.

* msg db ...: Mendefinisikan pesan "Testing pesan untuk workflow" sebagai array byte (db = define byte) diakhiri dengan 0xA (newline \n dalam ASCII).

* len equ $ - msg: Menghitung panjang pesan secara otomatis.

   $ adalah alamat saat ini.

   msg adalah alamat awal pesan.

   Maka len = jumlah byte dari pesan.

* section .text: Tempat untuk instruksi atau logika program.

* global _start: Memberi tahu linker bahwa label _start adalah titik masuk program.
  
* _start: Label ini adalah titik awal eksekusi program, mirip seperti main() dalam C.

* mov eax, 4: Set EAX ke 4, yaitu syscall number untuk write.

* mov ebx, 1: Set EBX ke 1, yaitu file descriptor untuk stdout (layar/terminal).

* mov ecx, msg: ECX berisi alamat data (pesan).

* mov edx, len: Panjang data yang akan ditulis.

* int 0x80: Memanggil interrupt untuk menjalankan syscall (panggilan ke kernel).

* mov eax, 1: Set EAX ke 1, yaitu syscall number untuk exit.

* xor ebx, ebx: Set EBX ke 0 (exit code = 0). Gunakan xor sebagai cara cepat dan efisien untuk set register ke nol.

* int 0x80: Jalankan syscall exit.

 # output dari program

 * Testing pesan untuk workflow

 Teks tersebut dicetak ke layar karena syscall write, lalu program keluar tanpa error karena syscall exit(0).

