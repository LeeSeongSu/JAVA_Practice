```java
//oop 에서 클래스를 생성할때 직접 생성하지 않고 누군가가 생성해서 넘겨주는것을 받아서 이용하는...
//gof design pattern 의 builder pattern/ factory pattern
//둘다 클래스를 직접 생성하지 않고.. 누군가가 대행 생성해준다는 개념...
//==>factory pattern : 객체 생성 결합을 없애서.. 프로그램의 유지보수성을 좋게 하기 위해서..
//유지보수성을 결정하는 인자는 많다.. 그중 가장 큰 인자는 결합도이다.. 결합도중에 가장 큰것은
//객체 생성 결합이다..
//new B(); 이렇게 생성했다면..이 코드가 작성되어 있는 곳과.. B 클래스가 결합되어서..
//B 클래스에서 C 클래스로 바꿔야 한다면.. 결합된 코드 모두를 수정해버려야 하는...
//그런데 내가 생성하지 않고 누군가가 대신 생성해서 넘겨준다면.. 나는 그 클래스와 결합되지 않는다..

//런타임 로그...클래스...
//DBLog .. new DBLog() 생성...
//DB 부하 문제로.. 팀에서 의사결정으로 FileLog 로 교체하기로.. 로그남긴 모든 코드가 수정..
//factory  pattern 을 적용해서 설계되었담..
//Log <- DBLog
//factory가 DBLog 객체 생성해서 넘겨주면 이용하는 곳에서 Log 타입으로 받아서 이용하고 있다면
//FileLog 로 교체한다면.. factory만 수정하면 된다..

//==>Builder pattern... 객체 생성 작업이 복잡하다.. 대행자를 두자는 개념...
//Dialog 객체를 이용해야 하는데.. 클래스는 하나인데.. 조건에 따라.. alert, datepicker,
//timepicker, icon ?, button 1?, 2?, 3?.....
//그 복잡함을 누군가에게 위임시키자...

//이 클래스의 객체를 생성해서 이용해야 하는데.. 대생자를 두겠다는 가정....
class Dialog {
	int data;
	private Dialog() {}
	//객체 생성 대행자(Builder)를 외부 클래스로 만들어도 되지만..
	//일반적으로 생성 대상이 되는 클래스의 이너 클래스로 많이 만든다..
	static class Builder {
		Dialog create() {
			return new Dialog();
		}
	}
}

public class Main {
	public static void main(String[] args) {
		Dialog.Builder builder = new Dialog.Builder();
		
		Dialog obj1=builder.create();
		obj1.data=10;
		Dialog obj2=builder.create();
		obj2.data=20;
		System.out.println(obj1.data+","+obj2.data);
	}
}

```

