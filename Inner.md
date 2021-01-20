### Inner

------

```java
class Super {
	void superFun() {
		System.out.println("Super... Fun....");
	}
}

class OuterClass {
	int outerData=10;
	class InnerClass {
		int innerData=20;
		void innerFun() {
			outerData++;//object member 로 이용되는 클래스임으로 자신의 클래스가 이용되는
			//시점이면 outer 클래스의 멤버가 모두 메모리에 올라와 있기 때문에...
			System.out.println("InnerClass : "+outerData+","+innerData);
		}
	}
	static class StaticInnerClass {
		void innerFun() {
//			outerData++;//error..static member 이다.. 이 클래스 이용시.. outer 의 
			//멤버가 메모리에 올라오지 않을수 있다.
			System.out.println("StaticInnerClass.....");
		}
	}
}

public class Main{
	public static void main(String[] args) {
		OuterClass obj1=new OuterClass();
		OuterClass.InnerClass innerObj=obj1.new InnerClass();
		innerObj.innerFun();
		

		OuterClass.StaticInnerClass innerObj2=new OuterClass.StaticInnerClass();
		innerObj2.innerFun();
		
		Super superObj=new Super();
		superObj.superFun();
		
		//Super 를 상속받은 익명 클래스를 선언하고.. 선언과 동시에 생성..
		//실제 생성된 객체는 Super 객체가 아니라.. 익명 클래스의 객체가 생성된거다..
		//이름은 없지만 하위 클래스가 상위 타입으로는 선언될수 있어서.. 
		//익명 클래스의 객체를 생성하고 상위 타입으로 이용하는 것...
		Super superObj2=new Super() {
			void superFun() {
				System.out.println("anonymous class fun....");
			}
		};
		superObj2.superFun();
	}

}
```

