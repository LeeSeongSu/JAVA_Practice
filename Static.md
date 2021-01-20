## STATIC



```java
class Count {
	public static int totalCount;
	int count;
	static void some1() {
		totalCount++;
//		count++;//static 함수에서 object member 이용 불가.
		//메모리 할당 순서때문이다.. 항상 static member가 먼저 메모리 할당되고..
		//객체 생성 전에 이용될수 있기 때문이다...
	}
	void some2() {
		totalCount++;//이 함수가 호출되었다는건 객체가 생성되었다는 거고..
		//객체 생성이 완료되었다는건 클래스 인지에 의해 class member 가 이미 메모리에 올라왔다
		count++;
	}
}

public class Main {
	public static void main(String[] args) {
		Count c1=new Count();
		Count c2=new Count();
		

		c1.count++;
		c2.count++;
		//static member 들은 클래스명 접근 가능, 객체명 접근 가능..
		//권장사항은 클래스명으로 접근하기를...
		c1.totalCount++;
		Count.totalCount++;
		c2.totalCount++;
		
		System.out.println(Count.totalCount+","+c1.count);
		System.out.println(c2.totalCount+","+c2.count);
	}

}
```

