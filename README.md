# Tugas 2 ASDL #

Kelompok 4 - TI Reg A
Anggota :
> Nur Su’udiyah (09021182126020)
> Agustian (09021182126022)
> Agus Tusilawati (09021182126024)
> Ana Safira (09021182126025)
> Tri Yogta Rahmadhan (09021182126026)
> Affandi Arrizal (09021182126027)


-# TUGAS 2A #-


import java.io.IOException;
import java.util.Scanner;

public class Main {
  public static void main(String[] args) throws IOException {
  
    Scanner userOption = new Scanner(System.in);
    String pilihanUser;
    boolean lanjutkan = true;
    
    while (lanjutkan){
      System.out.println("*** DOUBLE LINKED LIST ***\n");
      System.out.println("1. \tManual");
      System.out.println("2. \tPustaka");
      System.out.println("3. \tKeluar");

      System.out.print("\nSilahkan Pilih [1/2/3] : ");
      pilihanUser = userOption.next();

      switch (pilihanUser) {
        case "1":
          break;
        case "2":
          break;
        case "3":
          break;
        default:
          System.err.println("\nInputan anda tidak ditemukan\nSilahkan pilih [1/2/3]");   
       }
      
     }
    
   }
   private static tampilkanData() throws IOException{
   }
}
