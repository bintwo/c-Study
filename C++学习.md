#C++学习
##命名空间
	namespace myspace
	{
		int x;
	}
全局变量的特点是：自动初始化	
##cout的用法
	using namespace std||using std::cout
	//第二种用法是使用哪一个就直接引用哪一个 不会造成全局污染       
	int main() {  
		const int *x="assd";  
     	cout<<x;//输出的为"assd"
		cout<<(void*)x;//输出的为地址
	}
cin的用法是获取用户输入，也需要引用命名空间，using std::cin;
  
	intx=0;  
	cin>>x;  
这两种可以和printf进行混着使用  
##引用
	#include<iostream>
	
	
	void change(int &x)
	{
		x = 20;
	}
	
	int main()
	{
		//引用
	
		int x = 0;
		change(x);
		std::cout << x << std::endl;
	
		int y = 1;
		int &w = y;//相当于对于y的引用
	
		system("pause");
		return 0;
	}

*引用的特点  
>1,引用必须初始化  
>2,引用只能初始化的时候赋值，不能在引用中间赋值，在引用中间赋值的话相当于把值直接付给所引用的对象 例如：
	
		int x=0;
		int &w=x;
		int y=10;
		w=y;//此时相当于x=10;	
2021/7/17 15:29:28 
##重载
函数重载的规范：  
 函数名相同，参数的类型或者个数不一样能够形成重载

	#include<iostream>
	
	
	int add(int x, int y)
	{
		return x + y;
	}
	float add(float x, float y)
	{
		return x + y;
	}
	int main()
	{
		//重载
		int x = add(12, 2);
		float q = add(2.f, 3.5f);
		//重载发生必须要参数不一样，只有返回值类型不一样不能构成重载
		std::cout << x<<std::endl;
		std::cout << q << std::endl;
		system("pause");
		return 0;
	}
##参数缺省
在函数中给参数一个默认值，调用的时候可以不用写参数  
**参数的缺省必须在参数列表的结尾**  
**如果要写函数的缺省必须要从参数的最右边开始依次向前**


	#include<iostream>
	
	
	void  add(int x = 0, int y = 10)
	{
		std::cout << x + y << std::endl;
	}
	int main()
	{
		//参数缺省
		add();
		system("pause");
		return 0;
	}

不定参数   需要自己进行了解
##类
类是抽象非具体的  
数据： 也就是变量或者属性  
方法： 也就是函数
以前的数据和方法是分离的  
**类就是数据和方法的共同体 ，struct是数据和数据的共同体**  

	class hero{
		int hp;
		void atk(){

		}
	}
###封装性
**类天然具有封装性，类希望自己的内在细节不被外界掌握，**  
对于一个类来讲 必然有一个暴露出来的方法
    
	#include<iostream>
	using std::cout;
	using std::endl;
	class hero
	{
	public:
		int hp;
		void atk()
		{
	
		}
	};
	
	int main()
	{
		//类
		hero h,h2;
		h = { 10 };
		h2 = h;//可以将一个类赋值给另一个类
		cout << h.hp << endl;
		cout << h2.hp << endl;
		system("pause");
		return 0;
	}
封装性练习：做一个矩形类，能准确地描述矩形的信息，方法能计算矩形的面积

	#include<iostream>
	using std::cout;
	using std::endl;
	class hero
	{
	public:
		int hp;
		void atk()
		{
	
		}
	};
	class Rectangle
	{
	private:
		int x;
		int y;
		float width;
		float height;
	public:
		void setW_H(float _w, float _h)
		{
			width = _w;
			height = _h;
		}
		void getArea()
		{
			cout<< width * height<<endl;
		}
	};
	int main()
	{
		//类
		//hero h,h2;
		//h = { 10 };
		//h2 = h;//可以将一个类赋值给另一个类
		//cout << h.hp << endl;
		//cout << h2.hp << endl;
		Rectangle rect;//实例化类
		rect.setW_H(12, 23.4f);//给类对象赋值
		rect.getArea();//调用方法
		system("pause");
		return 0;
	}
###构造函数

	#include<iostream>
	using std::cout;
	using std::endl;
	class hero
	{
	public:
		int hp;
		void atk()
		{
	
		}
	};
	class Rectangle
	{
	
		
	private:
		int x;
		int y;
		float width;
		float height;
	public:
		//构造函数的重载,可以不带参数
		Rectangle()
		{
			cout << "可以不带参数" << endl;
	
		}
		//参数的缺省
		Rectangle(float _w, float _h = 20)
		{
			width = _w;
			height = _h;
		}
		//构造函数
		/*Rectangle(float _w, float _h)
		{
	
			width = _w;
			height = _h;
	
		}*/
		void setW_H(float _w, float _h)
		{
			width = _w;
			height = _h;
		}
		void getArea()
		{
			cout<< width * height<<endl;
		}
	};
	int main()
	{
		//类
		//hero h,h2;
		//h = { 10 };
		//h2 = h;//可以将一个类赋值给另一个类
		//cout << h.hp << endl;
		//cout << h2.hp << endl;
		Rectangle rect3;
		Rectangle rect(10.0f,20.0f);//实例化类
		//rect.setW_H(12, 23.4f);//给类对象赋值
		rect.getArea();//调用方法
		Rectangle rect1(20);
		rect1.getArea();
		system("pause");
		return 0;
	}
###析构函数
类的消亡的时候调用的函数

	 ~Rectangle()
		{
	
		}
当在类内部进行开辟空间的时候需要进行释放空间，这时候就要用到析构函数

	#include<iostream>
	using std::cout;
	using std::endl;
	class hero
	{
	public:
		int hp;
		void atk()
		{
	
		}
	};
	class Rectangle
	{
	
		
	private:
		int x;
		int y;
		float width;
		float height;
		char *p;
	public:
		//构造函数的重载,可以不带参数
		Rectangle()
		{
			cout << "可以不带参数" << endl;
			p =(char*) malloc(sizeof("动态开辟空间"));
			memcpy(p, "动态开辟空间", sizeof("动态开辟空间"));
			cout << "开辟的空间=" << p << endl;
	
		}
		
		 ~Rectangle()
		{
			 if (p)
			 {
				 cout << "释放开辟的空间" << endl;
				 free(p);
				 p = NULL;
			 }
	
		}
		void setW_H(float _w, float _h)
		{
			width = _w;
			height = _h;
		}
		void release()
		{
			
		}
		void getArea()
		{
			cout<< width * height<<endl;
		}
	};
	int main()
	{
		//类
		//hero h,h2;
		//h = { 10 };
		//h2 = h;//可以将一个类赋值给另一个类
		//cout << h.hp << endl;
		//cout << h2.hp << endl;
		
		{
			Rectangle rect3;
		}
		
		system("pause");
		return 0;
	}
##动态空间
类内的函数不占用空间  
动态开辟动态空间的方法  new 关键字  

	#include<iostream>
	using std::cout;
	using std::endl;
	class  Man
	{
	public:
		int age;
		//构造函数
		Man()
		{
			cout << "构造函数被调用" << endl;
		}
		//析构函数
		~Man()
		{
			cout << "析构函数被调用" << endl;
		}
		void getage()
		{
			cout << age << endl;
	
		}
	
	};
	
	int main()
	{
		//c++中动态空间
		//Man *man = (Man*)malloc(sizeof(Man));//使用malloc对类对象进行初始化在复杂的对象中会造成不稳定，因此产生了new
	
		//man->age = 10;
	//1,Man *man = new Man();
		//man->age = 20;
		//man->getage();
	//2.
		//new  Man();//此时开辟空间了，是一个匿名类对象。。但是没有办法进行调用对象造成了内存的泄露
	//3.
		//{
		//	Man *man = new Man();//new对象的析构函数不能自动被调用，需要进行手动释放内存
		//	delete man;
		//}
	//4.当对象是数组对象的时候
		//{
		//	Man man[10];//此时产生了十个自动变量，会调用十次构造函数，程序结束时候自动释放，调用十次析构函数
	
		//}
	//5,对象为指针对象数组的时候
		{
			//Man *man[10];//此时没有产生对象，此时p是存了10个指针变量的容器，和对象没有关系，这时候没有任何对象产生
			Man *man = new Man[10];//此时产生了10个对象，这是在堆空间上开辟的空间，所以要进行手动的释放  那需要进行怎么样的手动释放
			delete[] man;
		}
		
		//cout << sizeof(Man) << endl;
	
		system("pause");
		return 0;
	}
##拷贝构造函数
##内联函数
将一个函数的调用过程简化成没有函数调用过程

	inline void text();
缺点：有额外的内存开销  
优点：比较快  
一旦我们的函数声明和实现不在一起，就不能使用内联函数,这时候需要把实现也放在.h中

	inline void text(){cout<<x<<endl;}
##友元函数
打破类的封装  

	friend 关键字
友元函数不是成员函数，但是友元函数可以用类里面的所有数据   
里面没有this变量  
可以是另一个类得成员函数  
**友元类：该友元类内的所有成员函数都是友元函数**  
友元的性质：1，单向性；2，不传递性；3，没有继承
## 函数递归调用
在函数内部进行函数的层层调用  
大部分的函数递归可以用循环解决   
大部分的循环也可以用函数的递归解决  
大量的函数递归会造成函数栈溢出，      以及内存的使用过大
##常量成员
##运算符重载
**c++将类对象作为参数时候加“&”符号的作用：  
这个是引用符号，如果不加，传入的是实参的一个拷贝，修改那个拷贝不会影响到传入的对象；加入后传入的是实参自己，修改的话会影响到自己**

	operator + ()
	{
	}
 一般情况下把运算符重载的函数写成友元函数  
下列运算符不能被重载  
.---------成员访问运算符  
.* -------成员指针访问运算符 
::--------域运算符  
sizeof----长度运算符  
?:--------条件运算符

###仿函数
运算符重载的结果（）


练习：使用数组的形式完成链表的数据访问

##继承
##继承中的构造与析构
二义性  
##虚继承和多继承
**多继承：**一个类有多个基类来源  
虚继承：virtual
##多态
静态多态：函数重载  
动态多态：出现三个前提：1，类内部；2，要有继承关系；3，基类类型描述派生类实例对象  
将基类中函数写成虚函数  
虚函数表
##抽象类
不完整的类 没有实现  也叫作虚基类

	class TextClass
	{
		public:
		virtual void text()=0;纯虚函数	
	} 
抽象类不能产生实例对象  
抽象基类强制要求派生类实现某些关键的方法

	