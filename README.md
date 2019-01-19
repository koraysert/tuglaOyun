# tuglaOyun
package tuglaOyunu.base;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Runner {
	static Scanner sc = new Scanner(System.in);
	static String girilen = "";
	static List<String> t = new ArrayList<String>();

	long start = System.currentTimeMillis();

	static int x, y, sayac = 0;
	static int puan = 10;

	public static void main(String[] args) {
		baslangic();

	}

	public static void getir() {
		System.out.println("0-9 arası bir atış noktası seçin");
		girilen = sc.next();

	}

	public static void baslangic() {
		t.clear();
		sayac = 0;
		puan = 10;
		x = (int) (Math.random() * 10);
		y = (int) (Math.random() * 10) + 90;

		for (int i = 0; i < 100; i++) {
			t.add("*");

		}
		getir();
		t.set(x, "X");
		t.set(y, "Ü");
		
		yenile();
		oyun();
	}

	public static void yenile() {
	
		for (int i = 0; i < 100; i++) {
			if (i % 10 == 0 && i != 0) {
				System.out.println();
			}
			System.out.print(t.get(i) + "   ");
		}
		System.out.println();
	}

	public static void oyun() {

		while (girilen != "") {
			sayac++;
			puan--;
			if (girilen.length() == 1 && girilen.matches("[0-9]+")) {
				if (x < 90 && y % 10 != x % 10) {
					t.set(x + 10, "X");
					t.set(x, "*");
					x = x + 10;
					if (Integer.parseInt(girilen) + 90 != y) {
						t.set(Integer.parseInt(girilen) + 90, "Ü");
						t.set(y, "*");
						y = Integer.parseInt(girilen) + 90;
					}
					yenile();

				} else {
					System.out.println("oyun bitti puan. " + puan);
					baslangic();
				}
			} else {
				System.out.println("hatalı giriş");
			}

			try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
			try {if (sayac % 2 == 0) {
				girilen = Math.abs((Integer.parseInt(girilen) - sayac) % 10) + "";
			} else {
				girilen = (Integer.parseInt(girilen) + sayac) % 10 + "";
				
			}}catch(Exception e) {break;}
			

		}
	}


}
