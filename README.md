package yilanOyunu.base;

public class Runner {
	public static void main(String[] args) throws InterruptedException  {
		YilanOyunu2 yo = new YilanOyunu2();
		yo.baslangic();
		// w=119a=97s=115d=100
		//long start = System.currentTimeMillis();
		yo.getir();
		while (yo.girilen != "") {// System.out.println(yo.ascii(yo.girilen));yo.getir();
			
		        yo.oyun(yo.girilen);
		        
		       // Thread.sleep(1000);
		        
			if (yo.girilen != "") {
				yo.getir();
			
			
			}

		}
	}

}


import java.util.Scanner;

public class YilanOyunu {
	Scanner scn = new Scanner(System.in);
	String[][] c = new String[10][10];
	String[][] tuzaklarveyemler = new String[10][10];
	String girilen;
	int x = 0;
	int y = 0;
	int z = 0;
	int t = 0;
	int zson = 0;
	int tson = 0;
	int boy = 0;
	int çarpma = 0;
	int puan = 0;
//	int a2 = 0;
//	int b = 0;
//	String ab = "";

	public void getir() {
		System.out.println(
				"@ başlangıç noktasıdır, ilerlemek için w a s d + enter kullanın, z + enter ile oyundan çıkabilirsiniz");
		girilen = scn.next();
	}

	public void baslangic() {

		// for(int i =0;i<10;i++) {for(int j=0;j<10;j++)
		// {c[i][j]=i+""+j;System.out.print(c[i][j]+" ");}System.out.println();}

		for (int i = 0; i < 10; i++) {
			x = (int) (Math.random() * 10);
			y = (int) (Math.random() * 10);
			z = (int) (Math.random() * 10);
			t = (int) (Math.random() * 10);

			if (tuzaklarveyemler[x][y] == null && tuzaklarveyemler[z][t] == null) {
				tuzaklarveyemler[x][y] = "X";
				tuzaklarveyemler[z][t] = "O";
			} else {
				i = i - 1;
			}

			if (i == 9) {
				zson = x;
				tson = y;
			}
		}

		for (int i = 0; i < 10; i++) {
			for (int j = 0; j < 10; j++) {
				if (tuzaklarveyemler[i][j] == null) {
					c[i][j] = "*";
				} else {
					c[i][j] = tuzaklarveyemler[i][j];
				}
				c[zson][tson] = "@";
				// c[zson][tson-1] = "O";
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
//		ab = ilkindex();
//		a2 = Integer.parseInt(ab.toCharArray()[0] + "");
//		b = Integer.parseInt(ab.toCharArray()[1] + "");
		if (ascii(s) == 119) {
			if (x != 0) {

				if (!c[x - 1][y].equals("X")) {
					x = x - 1;
					if (c[x][y].equals("O")) {
						c[x][y] = ("*");
						boy++;
						puan++;

						try {
							for (int i = 0; i < 10; i++) {
								if (c[i][y].equals("@")) {
									c[i][y] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x + i][y].equals("*")) {
									c[x + i][y] = "@";
								}
							}
							// c[x+boy][y] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != y) {
									if (c[x + 1][i].equals("@")) {
										c[x + 1][i] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

						yenile();

					} else if (c[x][y].equals("*")) {

						try {
							for (int i = 0; i < 10; i++) {
								if (c[i][y].equals("@")) {
									c[i][y] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x + i][y].equals("*")) {
									c[x + i][y] = "@";
								}
							}
							// c[x+boy][y] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != y) {
									if (c[x + 1][i].equals("@")) {
										c[x + 1][i] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

						// x = x - 1;

//						c[a2 - 1][y] = "O";
//						c[a2][b] = "*";
//						x = x - 1;
						yenile();

					}
				} else {

					çarpma++;
					System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));
				}

			} else {

				çarpma++;
				System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));

			}

		} else if (ascii(s) == 115) {
			if (x != 9) {
				if (!c[x + 1][y].equals("X")) {
					x = x + 1;
					if (c[x][y].equals("O")) {
						c[x][y] = ("*");
						boy++;
						puan++;

						try {
							for (int i = 0; i < 10; i++) {
								if (c[i][y].equals("@")) {
									c[i][y] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x - i][y].equals("*")) {
									c[x - i][y] = "@";
								}
							}
							// c[x-1-boy][y] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != y) {
									if (c[x - 1][i].equals("@")) {
										c[x - 1][i] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

						yenile();

					} else if (c[x][y].equals("*")) {

						try {
							for (int i = 0; i < 10; i++) {
								if (c[i][y].equals("@")) {
									c[i][y] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x - i][y].equals("*")) {
									c[x - i][y] = "@";
								}
							}
							// c[x-1-boy][y] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != y) {
									if (c[x - 1][i].equals("@")) {
										c[x - 1][i] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

//						c[a2][b] = "*";
//						x = x + 1;
						yenile();

					}
				} else {

					çarpma++;
					System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));
				}

			} else {

				çarpma++;
				System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));

			}
		} else if (ascii(s) == 97) {
			if (y != 0) {
				if (!c[x][y - 1].equals("X")) {
					y = y - 1;
					if (c[x][y].equals("O")) {
						c[x][y] = ("*");
						boy++;
						puan++;

						try {
							for (int i = 0; i < 10; i++) {
								if (c[x][i].equals("@")) {
									c[x][i] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x][y + i].equals("*")) {
									c[x][y + i] = "@";
								}
							}
							// c[x][y+1+boy] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != x) {
									if (c[i][y + 1].equals("@")) {
										c[i][y + 1] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

						yenile();

					} else if (c[x][y].equals("*")) {

						try {
							for (int i = 0; i < 10; i++) {
								if (c[x][i].equals("@")) {
									c[x][i] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x][y + i].equals("*")) {
									c[x][y + i] = "@";
								}
							}
							// c[x][y+1+boy] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != x) {
									if (c[i][y + 1].equals("@")) {
										c[i][y + 1] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

//						c[x][b - 1] = "O";
//						c[a2][b] = "*";
//						y = y - 1;
						yenile();

					}
				} else {

					çarpma++;
					System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));
				}

			} else {

				çarpma++;
				System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));

			}
		} else if (ascii(s) == 100) {
			if (y != 9) {
				if (!c[x][y + 1].equals("X")) {
					y = y + 1;
					if (c[x][y].equals("O")) {
						c[x][y] = ("*");
						boy++;
						puan++;

						try {
							for (int i = 0; i < 10; i++) {
								if (c[x][i].equals("@")) {
									c[x][i] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x][y - i].equals("*")) {
									c[x][y - i] = "@";
								}
							}
							// c[x][y-1-boy] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != x) {
									if (c[i][y - 1].equals("@")) {
										c[i][y - 1] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

						yenile();

					} else if (c[x][y].equals("*")) {
						try {
							for (int i = 0; i < 10; i++) {
								if (c[x][i].equals("@")) {
									c[x][i] = "*";
								}
							}
							for (int i = 0; i <= boy; i++) {
								if (c[x][y - i].equals("*")) {
									c[x][y - i] = "@";
								}
							}
							// c[x][y-1-boy] = "*";
						} catch (Exception e) {
						}
						try {
							for (int i = 0; i < 10; i++) {
								if (i != x) {
									if (c[i][y - 1].equals("@")) {
										c[i][y - 1] = "*";
									}
								}
							}
						} catch (Exception e) {
						}

//						c[x][b + 1] = "O";
//						c[a2][b] = "*";
//						y = y + 1;
						yenile();

					}
				} else {

					çarpma++;
					System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));
				}

			} else {
				çarpma++;
				System.out.println("çarptınız yön değiştiriniz kalan hakkınız: " + (3 - çarpma));

			}
		} else {

			if (ascii(s) == 122) {
				girilen = "";
			}
		}
		if (çarpma == 3 || puan == 10) {

			System.out.println("oyun bitti puan: 10 üzerinde " + puan);
			girilen = "";
		}
	}

	public void yenile() {

		for (int i = 0; i < 10; i++) {
			for (int j = 0; j < 10; j++) {
				// if(c[i][j].equals("O")) {c[i][j]="*";}
				System.out.print(c[i][j] + "    ");
			}
			System.out.println();
		}

	}

//	public String ilkindex() {
//		int sayaç = 0;
//	String ij="";
//		for(int i =0;i<10;i++) {if(sayaç==0) {for(int j=0;j<10;j++){if(c[i][j].equals("O")&&sayaç==0) {sayaç++;ij=i+""+j;}}}}
//		
//		return ij;
//
//		
//	}
}
