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

import java.util.Scanner;

class Pilihan {
	public static boolean Yesorno(String pesan) {
		System.out.println("\n" + pesan + "\nJika Lanjut Masukkan (y)" + "\nJika Berhenti Masukan (n)");

		Scanner scan = new Scanner(System.in);
		String pilihan = scan.next();
		while (!pilihan.equalsIgnoreCase("Y") && !pilihan.equalsIgnoreCase("n")) {
			System.err.println("Pilihan Anda bukan Y ataupun N ");
			System.out.println("\n" + pesan + "(y/n)");
			pilihan = scan.next();
		}
		return pilihan.equalsIgnoreCase("y");
	}
}

class Node {
	int nilai;
	Node next;
	Node prev;
}

public class LinkedList2a {
	Node kepala;
	Node tail;

	public void SisipBelakang(int nilai) {
		Node node = new Node();
		node.nilai = nilai;
		node.next = null;
		if (kepala == null) {
			kepala = node;
		} else {
			Node n = kepala;
			while (n.next != null) {
				n = n.next;
			}
			n.next = node;
		}
	}

	public void SisipDepan(int nilai) {
		Node node = new Node();
		node.nilai = nilai;
		node.next = kepala;
		kepala = node;
	}

	public void SisipTengah(int nilai, int index) {
		Node node = new Node();
		node.next = null;
		node.nilai = nilai;
		if (kepala == null) {
			SisipDepan(nilai);
		} else {
			Node n = kepala;
			for (int i = 0; i < index - 1; i++) {
				n = n.next;
			}
			node.next = n.next;
			n.next = node;
		}
	}

	public void TampilData(boolean a) {
		Node x = null;
		if (a) {
			x = kepala;
		} else {
			x = tail;
		}
		System.out.print("[ ");
		while (x != null) {
			System.out.print(x.nilai + " ");
			if (a) {
				x = x.next;
			} else {
				x = x.prev;
			}
		}
		System.out.println("]");
	}

	public void sortList() {
		Node n = kepala;
		Node index = null;
		int temp;
		if (kepala == null) {
			return;
		} else {
			while (n != null) {
				index = n.next;
				while (index != null) {
					if (n.nilai < index.nilai) {
						temp = n.nilai;
						index.nilai = temp;
					}
					index = index.next;
				}
				n = n.next;
			}
		}
	}

	public void DeletAngkaDenganNilai(int nilai) {
		Node n = kepala;
		Node n1 = null;
		int count = 0;
		if (nilai == kepala.nilai) {
			kepala = kepala.next;
		} else {
			while (n.next != null) {
				n = n.next;
				if (nilai == n.nilai) {
					count++;
					break;
				}
				count++;
			}
			n = kepala;
			for (int i = 0; i < count - 1; i++) {
				n = n.next;
			}
			n1 = n.next;
			n.next = n1.next;
		}
	}

	public void DeletDepan() {
		kepala = kepala.next;
	}

	public void DeletBelakang() {
		if (kepala.next == null) {
			DeletDepan();
		} else {
			Node n = kepala;
			Node n1 = null;
			while (n.next.next != null) {
				n = n.next;
			}
			n1 = n.next;
			n.next = n1.next;

		}
	}

	private static void programExit() {
		System.exit(0);
	}

	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		int x, y;
		boolean ProgramRun = true;
		int pilihan1;
		int pilihan2;

		LinkedList2a op = new LinkedList2a();
		while (ProgramRun) {
			System.out.println("\n.: PROGRAM MENU :." 
								+ "\n 1. Tambah Data" 
								+ "\n 2. Hapus Data"
								+ "\n 3. Exit Program"
								+ "\n 4. Info Program");

			System.out.print("Masukkan Pilihan :");
			pilihan1 = scan.nextInt();
			switch (pilihan1) {
			case 1:
				boolean dataRun = true;
				while (dataRun) {
					System.out.println("\n 1. Tambah Data Depan");
					System.out.println(" 2. Tambah Data Belakang");
					System.out.println(" 3. Tambah Data Tengah");
					System.out.println(" 4. Menu Utama");
					System.out.print("Masukkan Pilihan [1-4] :");
					pilihan2 = scan.nextInt();
					switch (pilihan2) {
					case 1:
						System.out.print("Masukkan Angka : ");
						x = scan.nextInt();
						op.SisipDepan(x);
						op.TampilData(true);
						break;
					case 2:
						System.out.print("Masukkan Angka : ");
						x = scan.nextInt();
						op.SisipBelakang(x);
						op.TampilData(true);
						break;
					case 3:
						System.out.print("Masukkan Angka : ");
						x = scan.nextInt();
						System.out.print("Masukkan Index : ");
						y = scan.nextInt();
						op.SisipTengah(x, y);
						op.TampilData(true);
						break;
					case 4:
						dataRun = Pilihan.Yesorno("Ingin tambah data lagi? ");
						break;
					}
				}
				break;
			case 2:
				boolean dataRun2 = true;
				while (dataRun2) {
					System.out.println("\n 1. Hapus Data Depan");
					System.out.println(" 2. Hapus Data Belakang");
					System.out.println(" 3. Hapus Data Tengah");
					System.out.println(" 4. Menu Utama");
					System.out.println(" Masukkan Angka [1-4]: ");
					pilihan2 = scan.nextInt();
					switch (pilihan2) {
					case 1:
						op.DeletDepan();
						op.TampilData(true);
						break;
					case 2:
						op.DeletBelakang();
						op.TampilData(true);
						System.out.println();
						break;
					case 3:
						System.out.print(" Masukkan Angka :");
						x = scan.nextInt();
						op.DeletAngkaDenganNilai(x);
						op.TampilData(true);
						break;
					case 4:
						dataRun2 = Pilihan.Yesorno("Ingin hapus data lagi? ");
						break;
					}
				}
				break;
			case 3:
				programExit();
				break;
			case 4:
				System.out.println("\nProgram Simple Linked List "
						+ "\nDitulis Oleh: Kelompok 4"
						+ "\nYang Beranggota:"
						+ "\n1. Affandi Arrizal"
						+ "\n2. Agustian"
						+ "\n3. Agus Tusilawati"
						+ "\n4. Ana Safira"
						+ "\n5. Nur Su'udiyah"
						+ "\n6. Tri Yogta Rahmadhan  ");
				break;
			}
			ProgramRun = Pilihan.Yesorno("Apakah masih ingin memakai program ? ");
		}
	}
	
}


-# TUGAS 2B #-

import java.util.InputMismatchException;
import java.util.LinkedList;
import java.util.Scanner;

class YesorNo {
	public static boolean Yesorno(String pesan) {
		System.out.println("\n"+ pesan +""
				+ "\nJika Ingin Lanjut Masukkan y"
				+ "\nJika Ingin Berhenti Masukan n");
		
		Scanner sc = new Scanner(System.in);
		String pilihan = sc.next();
		while ( !pilihan.equalsIgnoreCase("Y") && !pilihan.equalsIgnoreCase("n")) {
			System.err.println("Pilihan Anda bukan Y ataupun N ");
			System.out.println("\n" + pesan +"(y/n)");
			pilihan = sc.next();	
		}
		return pilihan.equalsIgnoreCase("y");
	}

}
public class Tugas1b {
	

	private static LinkedList<String> dataStorage = new LinkedList<String> ();


	private static Scanner extracted( ) {
		return new Scanner (System.in);
	}
	private static void displayData1() {
		System.out.println("\ndata dalam List: " + dataStorage);
		System.out.println("Total Data 	: " + dataStorage.size());
	}
	
	private static void tambahdatadiawal() {
		System.out.print("Masukkan Angka Yang Ingin Ditambah ");
		String tempData = extracted().nextLine();
		dataStorage.addFirst(tempData);
		displayData1();
	}
	private static void tambahdatadiakhir() {
		System.out.print("Masukkan Data: ");
		String tempData = extracted().nextLine();
		dataStorage.addLast(tempData);
		displayData1();
	}
	private static void tambahdataditengah() {
		boolean status = true;
		int indexData = 0;
		displayData1();
		while(status) {
			System.out.print("Pada Index Ke Berapa Data Akan Di Ditambahkan : (0-" + (dataStorage.size()-1) + "): ");
			try {
				status  = false;
				indexData = extracted().nextInt();
			}
			catch(InputMismatchException e) {
				System.out.println(" Data Harus Berupa Angka !");
				status = true;
			}
		}
		System.out.print("Data yang ingin disisipkan pada index data ke- "+ indexData +  " adalah: ");
		String tempData = extracted().nextLine();
		dataStorage.add(indexData, tempData);
		displayData1();
	}
	
	private static boolean cariData(String data) {
		return dataStorage.contains(data);
	}
	
	
				
	private static void hapusdatadiawal() {
		dataStorage.removeFirst();
		displayData1();
	}
	
	private static void hapusdatadiakhir() {
		dataStorage.removeLast();
		displayData1();
	}
	private static void hapusdataditengah() {
		boolean status = true;
		int indexData = 0;
		while(status) {
			System.out.print("Pilih Index data yang ingin dihapus: (0-" +(dataStorage.size()- 1 ) + ");");
			try {
				status = false ;
				indexData = extracted().nextInt();	
			}
			catch(InputMismatchException e){
				System.out.println(" Data Harus Berupa Angka !");
				status = true;
			}
		dataStorage.remove(indexData);
		displayData1();
		}
	}
	private static void programExit() {
		System.exit(0);
	}

	public static void main(String[] args) {
		Scanner sc = new Scanner (System.in);
		int x,y;
		boolean ProgramRun = true;
		int pilihan1;
		int pilihan2;
		YesorNo Lanjut  = new YesorNo();
		while(ProgramRun) {
			System.out.println("\n.: PROGRAM MENU :.");
			
			System.out.println(" 1. Tambah Data");
			System.out.println(" 2. Hapus Data");
			System.out.println(" 3. Tentang Program");
			System.out.println(" 4. Program Exit ");
			System.out.println("Tidak Menerima Huruf");
			System.out.println("Masukkan Pilihan Menu [1-4] :");
			pilihan1 = sc.nextInt();
			switch (pilihan1) {
			case 1:
				boolean dataRun = true;
				while(dataRun) {
					System.out.println(" 1. Tambah Data Di Depan");
					System.out.println(" 2. Tambah Data Di Belakang");
					System.out.println(" 3. Tambah Data Di Tengah");
					System.out.println(" 4. Kembali Ke menu utama");
					System.out.println("Tidak Menerima Huruf ");
					System.out.println("Masukkan Pilihan Menu [1-4] :");
					pilihan2 = sc.nextInt();
					switch (pilihan2) {
					case 1:
						tambahdatadiawal();
						break;
					case 2:
						tambahdatadiakhir();
						break;
					case 3:
						tambahdataditengah();
						break;
					case 4:
						dataRun = Lanjut.Yesorno("Anda Ingin Menambah Data Lagi? ");	
					}
				}
				break;
			case 2:
				boolean dataRun2 = true;
				while(dataRun2) {
					System.out.println(" 1. Hapus Data Depan");
					System.out.println(" 2. Hapus Data Tengah");
					System.out.println(" 3. Hapus Data Belakang");
					System.out.println(" 4. Kembali Ke menu utama");
					System.out.println("Tidak Menerima Huruf ");
					System.out.println("Masukkan Pilihan Menu [1-4] :");
					pilihan2 = sc.nextInt();
					switch (pilihan2) {
					case 1:
						hapusdatadiawal();
						System.out.println();
						break;
					case 2:
						hapusdataditengah();
						System.out.println();
						break;
					case 3:
						hapusdatadiakhir();
						break;
					case 4:
						dataRun2 = Lanjut.Yesorno(" Anda Ingin Menghapus Data Lagi? ");		
					}
				}	
				break;
			case 3:
				System.out.println("\nProgramSimple Linked List "
						+ "\nDitulis Oleh: Kelompok 4"
						+ "\nYang Beranggota:"
						+ "\n1. Affandi Arrizal"
						+ "\n2. Agustian"
						+ "\n3. Agus Tusilawati"
						+ "\n4. Ana Safira"
						+ "\n5. Nur Su'udiyah"
						+ "\n6. Tri Yogta Rahmadhan  ");
				break;
			case 4:
				programExit();
				break;
			}	
		}
	}
}
