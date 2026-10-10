import 'dart:io';
void main() {
  var jalan = true;
  var pin = "112233";
  var akses = false;
  var Saldo = 2000000;
  var masukPIN;
  
  menuPin() {
    print(' ');
    print('==============================');
    print('SISTEM BANK');
    print('==============================');
    print(' ');
  }

  menuLayanan() {
    print(' ');
    print('==============================');
    print('SISTEM BANK');
    print('==============================');
    print('1. Cek Saldo');
    print('2. Setor Tunai');
    print('3. Tarik Tunai');
    print(' ');
  }


  while (jalan == true) {

    if (akses == false) {
         menuPin();
    stdout.write('Masukkan PIN :');
    masukPIN = stdin.readLineSync();
    }

    if (masukPIN == pin) {
      akses = true;
      menuLayanan();

       stdout.write('Pilih Layanan (1/2/3) :');
      var masukMenu = stdin.readLineSync();

      if (masukMenu == "1") {
        print('==============================');
        print('Saldo Anda Saat ini : ${Saldo} ');
      }

      if (masukMenu == "2") {
         stdout.write('Nominal Setor :');
        var nSetor = stdin.readLineSync()!;

        Saldo = Saldo + int.parse(nSetor);
      }

      if (masukMenu == "3") {
        stdout.write('Nominal Tarik :');
        var nTarik = stdin.readLineSync()!;

        if (int.parse(nTarik) % 50000 == 0 || int.parse(nTarik) >= 50000) {

        print('==============================');
        print("1. Pecahan Rp 50.000");
        print("2. Pecahan Rp 100.000");
        print('=============================='); 

        stdout.write('Pilih Pecahan (1/2) : ');
        var pilihPecahan = stdin.readLineSync()!;

        if (pilihPecahan == "1") {
          print("Rp 50.000 x ${(int.parse(nTarik) / 50000).floor()} Lembar");
        }

        if (pilihPecahan == "2") {
          
          num vTarik = num.parse(nTarik);

          print("Rp 100.000 x ${(vTarik / 100000).floor()} Lembar");
          vTarik = vTarik % 100000;
          
          if (vTarik > 0) {
            print("Rp 50.000 x ${(vTarik / 50000).floor()} Lembar");
          }

        }

        Saldo = Saldo - int.parse(nTarik);

        } else {
          print("Saldo Tidak Dapat Ditarik");
        }
      }
    }
  }
}