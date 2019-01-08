# SnakeGamepackage yilanOyunu.base;

import java.util.Scanner;

public class YilanOyunu {
	Scanner scn = new Scanner(System.in);
	String[][] c = new String[10][10];
	String[][] tuzaklar = new String[10][10];
	String girilen;
	int x = 0;
	int y = 0;
	int xson = 0;
	int yson = 0;
	int w = 0;
	int a = 0;
	int s2 = 0;
	int d = 0;
	int puan = 90;

	public void getir() {
		System.out.println(
				"Q başlangıç noktasıdır, ilerlemek için w a s d + enter kullanın, z + enter ile oyundan çıkabilirsiniz");
		girilen = scn.next();
	}

	public void baslangic() {

		for (int i = 0; i < 11; i++) {
			x = (int) (Math.random() * 10);
			y = (int) (Math.random() * 10);

			if (tuzaklar[x][y] == null) {
				tuzaklar[x][y] = "O";
			} else {
				i = i - 1;
			}
			if (i == 10) {
				xson = x;
				yson = y;
			}
		}

		for (int i = 0; i < 10; i++) {
			for (int j = 0; j < 10; j++) {
				if (tuzaklar[i][j] == null) {
					c[i][j] = "X";
				} else {
					c[i][j] = tuzaklar[i][j];
				}
				c[xson][yson] = "Q";
				System.out.print(c[i][j] + "    ");
			}
			System.out.println();
		}
		// x=0;y=0;
	}

	public int ascii(String s) {
		return (int) s.toCharArray()[0];
	}

	public void oyun(String s) {
		if (ascii(s) == 119) {
			if (x != 0) {
				if (c[x - 1][y] != "O") {
					c[x - 1][y] = "Q";
					c[x][y] = "O";
					x = x - 1;
					yenile();
					w++;

				} else {
					System.out.println("çarptınız yön değiştiriniz");
					w = 0;

				}
			} else {
				System.out.println("çarptınız yön değiştiriniz");
				w = 0;

			}
		} else if (ascii(s) == 115) {
			if (x != 9) {
				if (c[x + 1][y] != "O") {
					c[x + 1][y] = "Q";
					c[x][y] = "O";
					x = x + 1;
					yenile();
					s2++;
				} else {
					System.out.println("çarptınız yön değiştiriniz");
					s2 = 0;
				}
			} else {
				System.out.println("çarptınız yön değiştiriniz");
				s2 = 0;
			}
		} else if (ascii(s) == 97) {
			if (y != 0) {
				if (c[x][y - 1] != "O") {
					c[x][y - 1] = "Q";
					c[x][y] = "O";
					y = y - 1;
					yenile();
					a++;
				} else {
					System.out.println("çarptınız yön değiştiriniz");
					a = 0;
				}
			} else {
				System.out.println("çarptınız yön değiştiriniz");
				a = 0;
			}
		} else if (ascii(s) == 100) {
			if (y != 9) {
				if (c[x][y + 1] != "O") {
					c[x][y + 1] = "Q";
					c[x][y] = "O";
					y = y + 1;
					yenile();
					d++;
				} else {
					System.out.println("çarptınız yön değiştiriniz");
					d = 0;
				}
			} else {
				System.out.println("çarptınız yön değiştiriniz");
				d = 0;
			}
		} else {
			// System.out.println("Q başlangıç noktasıdır, ilerlemek için w a s d + enter kullanın, z + enter ile oyundan çıkabilirsiniz");
			if (ascii(s) == 122) {
				girilen = "";
			}
		}
		if ((w + a + s2 + d) == 0) {
			for (int i = 0; i < 10; i++) {
				for (int j = 0; j < 10; j++) {
					if (c[i][j].equals("X")) {
						puan--;

					}
				}

			}
			System.out.println("yön kalmadı, oyun bitti puan: " + puan);
			girilen = "";
		}
	}

	public void yenile() {
		for (int i = 0; i < 10; i++) {
			for (int j = 0; j < 10; j++) {
				System.out.print(c[i][j] + "    ");
			}
			System.out.println();
		}
	}

}
