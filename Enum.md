### Enum

------



```java
enum Direction {
	NORTH, SOUTH, EAST, WEST;
}

//enum 상수에 개발자 임의 데이터를 심어놓고.. 실제 상수가 대입된 변수에서 그 데이터를 이용하고 싶다.
enum Direction2 {
	//enum 상수는 enum 클래스의 서브 클래스 객체다.. 익명 이너 클래스 객체이다..
	//NORTH 는 Direction2 를 상속받은 익명 클래스의 객체이다..
	//상수에 () 는 결국 상위 클래스의 생성자 호출구문이다.. 상위 클래스에 데이터 받을 생성자 
	//있어야 한다..
	NORTH(100), SOUTH(200), EAST(300), WEST(400);
	

	int price;
	Direction2(int price){
		this.price=price;
	}

}

enum Direction3 {
	NORTH(100){
		@Override
		void printSome() {
			System.out.println("north.. printSome....");
		}
		//enum 클래스에 선언된 함수만 enum 상수에서 구현해야 하는가?
		//enum 상수 임의의 함수를 선언해도 된다.
		//enum 클래스를 상속받은 익명 클래스의 객체이다.. 이용은 상위 타입으로만 이용된다...
		//자체 함수를 얼마든지 선언할수 있지만.. 외부에서는 호출할수 없다..
		//자체 함수라는건 enum 상수 내부에서만 사용하는 함수가 된다..
		void selfFun() {
			System.out.println("north... selfFun....");
		}
	}, SOUTH(200){
		@Override
		void printSome() {
			System.out.println("south.. printSome....");
		}
	}, EAST(300){
		@Override
		void printSome() {
			System.out.println("east.. printSome....");
		}
	}, WEST(400){
		@Override
		void printSome() {
			System.out.println("west.. printSome....");
		}
	};
	

	int price;
	Direction3(int price){
		this.price=price;
	}
	//enum 상수는 enum 클래스 타입으로 이용된다.. 함수를 추가하려면...
	//enum 클래스에 먼저 함수를 선언하고.. enum 상수에서는 그 함수를 구현하는 식으로..
	abstract void printSome();

}

public class Main {
	public static void main(String[] args) {
		Direction d1=Direction.NORTH;
		//name(), ordinal() 모든 emum 상수의 공통 함수들....
		//enum 상수로 함수를 호출하고 있다.==>enum 상수가 객체라는 의미다..
		System.out.println(d1.name()+","+d1.ordinal());
		

		Direction2 d2=Direction2.NORTH;
		System.out.println(d2.name()+","+d2.ordinal()+","+d2.price);
		
		Direction3 d3=Direction3.NORTH;
		System.out.println(d3.price);
		d3.printSome();
	}

}
```

