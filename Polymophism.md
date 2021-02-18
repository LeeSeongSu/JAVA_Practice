```java
class Employee {
	String name;
	int salary=1000;
	
	//폴리모피즘의 기본은 하위 객체가 상위 타입으로 이용된다는 거다..
	//그런데 실제 호출시 하위에 정의한 함수가 호출되게 하자는 기법..
	//==>상위 타입으로 객체가 이용됨으로 상위에는 함수가 선언되어 있어야 한다..
	//설계적인 측면에서 객체가 특정 행위가 있음을 설계하지만.. 구체적인 내용 구현은 하위에서 
	//해야 하는 경우에는...==>추상함수로 선언...
	//==>하위에서 재정의할수도 있지만.. 공통 코드도 있다...==>구현 함수로 선언..
	public int calcBonus() {
		System.out.println("Employee 보너스 = 기본급 * 12");
		return salary * 12;
	}
}

class Salesman extends Employee {
	//폴리모피즘은 .. 하위에서 상위 함수 오버라이드...
	@Override
	public int calcBonus() {
		System.out.println("Salesman 보너스 = 기본급 * 12 * 4");
		return salary * 12 * 4;
	}
}

class Consultant extends Employee {
	@Override
	public int calcBonus() {
		System.out.println("consultant 보너스 = 기본급 * 12 * 2");
		return salary * 12 * 2;
	}
}

public class Main {
	public static void calcBonus(Employee e) {
		//이 함수에서는 상위 클래스의 함수를 호출했다...
		//==>그래서 상위에도 함수가 선언되어야..
		//==>실제 실행은 런타임시 대입되는 하위 객체의 함수가 호출.. 동적 바인딩...
		System.out.println(e.calcBonus());
	}
	
	public static void main(String[] args) {
		calcBonus(new Employee());
		calcBonus(new Salesman());
		calcBonus(new Consultant());
	}
}

```

