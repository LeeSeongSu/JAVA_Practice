```java
//singleton.... 클래스 작성자가.. 자신의 클래스의 객체가 하나만 생성되서 이용되게 강제...
class SingleTon {
	int data;
	static SingleTon instance;
	private SingleTon() {}
	//외부에서 객체가 필요한 순간 직접 생성하지 말고 이 함수를 호출해서 .. 이곳에서 리턴하는 
	//객체를 이용하라..
	public static SingleTon getInstance() {
		if(instance == null) {
			instance = new SingleTon();
		}
		return instance;
	}
}

public class Main {
	public static void main(String[] args) {
		SingleTon obj1 = SingleTon.getInstance();
		obj1.data=10;
		SingleTon obj2 = SingleTon.getInstance();
		obj2.data=20;
		System.out.println(obj1.data);
		System.out.println(obj2.data);
	}
}

```

