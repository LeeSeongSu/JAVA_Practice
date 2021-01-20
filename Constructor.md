### Constructor

------

```java
class Member {
	String name;
	int age;
	

	static {
		System.out.println("static.......");
	}
	
	{
		System.out.println("object.......");
	}
	
	public Member() {
		System.out.println("Member() ......");
	}
	public Member(String name) {
		this();
		this.name=name;
		System.out.println("Member(String name).....");
	}
	public Member(String name, int age) {
		this(name);
		this.age=age;
		System.out.println("Member(String name, int age)......");
	}

}


public class Main {
	public static void main(String[] args) {
		Member obj1=new Member();
		System.out.println(obj1.name+","+obj1.age);
		

		Member obj2=new Member("kim");
		System.out.println(obj2.name+","+obj2.age);
		
		Member obj3=new Member("kim",20);
		System.out.println(obj3.name+","+obj3.age);
		
	}

}
```

