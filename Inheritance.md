```java
class Person {
	private String name;
	private int age;
	
	static {
		System.out.println("super static");
	}
	{
		System.out.println("super object");
	}
	public Person(String name, int age) {
		System.out.println("super constructor....");
		this.name=name;
		this.age=age;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public int getAge() {
		return age;
	}
	public void setAge(int age) {
		this.age = age;
	}
	//데이터를 가지는 클래스는 디버깅의 편의성을 위해서.. toString() 함수를 오버라이드 받아 작성
	//sysout(obj) 하면 obj 의 toString() 함수가 자동으로 호출되는데..toString() 은 
	//Object 의 함수이고.. 객체의 레퍼런스 정보가 출력된다.. 데이터 적으로 의미없다..
	//sysout(obj) 에 의해 데이터가 출력되게.. toString() 을 오버라이드 받아 작성해 놓는다.
	@Override
	public String toString() {
		return "name:"+name+", age: "+age;
	}
}

class Professor extends Person {
	private String subject;
	static {
		System.out.println("sub static");
	}
	{
		System.out.println("sub object");
	}
	public Professor(String name, int age, String subject) {
		super(name, age);
		this.subject=subject;
		System.out.println("sub constructor...");
	}
	public String getSubject() {
		return subject;
	}
	public void setSubject(String subject) {
		this.subject = subject;
	}
	@Override
	public String toString() {
		return super.toString()+", subject : "+subject;
	}
}


public class Main {
	public static void main(String[] args) {
		Professor obj=new Professor("kim", 30, "java");
		System.out.println(obj);
	}
}

```

