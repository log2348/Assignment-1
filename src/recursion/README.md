


# Assignment-1
๐ญ๐ง Mouse๊ฐ Cheese๋ฅผ ์ฐพ์๊ฐ๋ ํ๋ก๊ทธ๋จ ๊ตฌํ

<br>

## ๐ญ Mouse์ ํ๋ ๋ฐฉ์


<div>
<img src="https://user-images.githubusercontent.com/96460131/190904149-c3aaec2e-593b-42f6-91ea-7ebc01e81391.jpg" width=40% height=40%>

 - Mouse๋ Cheese์ ์์น๋ฅผ ๋ชจ๋ฅธ๋ค๋ ๊ฐ์ 
 - Mouse๋ ์ ๊ทธ๋ฆผ๊ณผ ๊ฐ์ด ์น์ฆ์ ๋๋ฌํ  ๋๊น์ง ๊ณ์ ์ ์งํ๋ฉฐ,
์ขํ์ ๋์ ๋๋ฌํ๋ฉด ๋ฐฉํฅ์ ๋ณ๊ฒฝํ์ฌ ์ ์งํจ

</div>

<br>

## ๐ ํด๋์ค ์ค๋ช

### Mouse

 - Mouse์ ํ๋ ํจ์ํ (recursive function)
 - Mouse๊ฐ Cheese๋ฅผ ๋ง๋๋ฉด ๋์(move)์ด ์ข๋ฃ๋๋๋ก ํจ

		public void move(Cheese cheese, Map map) {

			/**
			 * Mouse์ Cheese์ ์ขํ๊ฐ ๊ฐ์์ง๋ฉด ์ฌ๊ท ํธ์ถ ์ข๋ฃ
			 */
			if (locationX == cheese.getLocationX() && locationY == cheese.getLocationY()) {
				System.out.println("Mouse๊ฐ Cheese๋ฅผ ์ฐพ์์ต๋๋ค !");
				System.out.println(this);
				return;
			}
			
				...
				

			move(cheese, map);

		}





### Cheese

- Mouse๊ฐ ์ฐพ์์ผ ํ๋ Cheese ํด๋์ค
- Mouse์ ๋ง์ฐฌ๊ฐ์ง๋ก, ์์น๋ก์์ ์ขํ๊ฐ์ ๊ฐ์ง


	    @Getter
		@Setter
		public class Cheese {
	
			private int locationX;
			private int locationY;

		}




### Map

- ํ๋ก๊ทธ๋จ์ ์ขํ ๊ณต๊ฐ
- Map ๊ฐ์ฒด ์์ฑ์ ํฌ๊ธฐ ์ง์  (๊ธฐ์ค ์ขํ ์ค์ )

	    @Getter
		public class Map {
			private int x;
			private int y;

			public Map(int x, int y) {
				this.x = x;
				this.y = y;
			}
		}




### Direction
- Mouse์ ๋ฐฉํฅ์ ์ ์ํ ์์ ์งํฉ

	    public enum Direction {
			LEFT, RIGHT
		}




### Main

- main ํจ์ ์คํ
 - Cheese์ ์์น ์ขํ ์๋ ฅ ๋ฐ์ Cheese ๊ฐ์ฒด ์ด๊ธฐํ
 - ์ฌ์ฉ์์ ์๋ ฅ๊ฐ์ ๋ํ validation ์ฒดํฌ


		public class Main {

			public static void main(String[] args) throws IOException {
				Map map = new Map(8, 8);
				Mouse mouse = new Mouse();

				mouse.move(setCheeseLocation(map.getX(), map.getY()), map);
			}

			private static Cheese setCheeseLocation(int mapX, int mapY) throws IOException {
				BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
				Cheese cheese = new Cheese();

				int cheeseX;
				int cheeseY;
				boolean flag = true;

				while (flag) {
				
					...

					if ((cheeseX > mapX || cheeseY > mapY) || (cheeseX < 0 || cheeseY < 0)) {
						System.out.println("Cheese์ ์์น๊ฐ ๋งต์ ๋ฒ์๋ฅผ ๋ฒ์ด๋ฌ์ต๋๋ค.");
					} else {
						cheese.setLocationX(cheeseX);
						cheese.setLocationY(cheeseY);
						flag = false;
					}
				}

				return cheese;
			}

		}



