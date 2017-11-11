using System;

namespace ConsoleApplication1
{



	// обобщенный класс


	//Когда для класса MyObj указывается аргумент типа, например int или string, 
    //то создается так называемый в C# закрыто сконструированный тип. В частности, 
    //MyObj<int> является закрыто сконструированным типом. Ведь, по существу, такой обобщенный тип, 
    //как MyObj<T>, является абстракцией. И только после того, как будет сконструирован конкретный вариант, 
    //например MyObj<int>, создается конкретный тип. А конструкция, подобная MyObj<T>, называется в C# 
    //открыто сконструированным типом, поскольку в ней указывается параметр типа Т, но не такой конкретный тип, как int.

//В C# чаще определяются такие понятия, как открытый и закрытый типы. Открытым типом считается такой 
    //параметр типа или любой обобщенный тип, для которого аргумент типа является параметром типа или
    //же включает его в себя. А любой тип, не относящийся к открытому, считается закрытым. Сконструированным 
    //типом считается такой обобщенный тип, для которого предоставлены все аргументы типов. Если все эти 
    //аргументы относятся к закрытым типам, то такой тип считается закрыто сконструированным. А если один 
    //или несколько аргументов типа относятся к открытым типам, то такой тип считается открыто сконструированным.

//И еще один момент.В связи с изложенным выше возникает следующий резонный вопрос: если аналогичные
    //функциональные возможности обобщенного класса MyObj можно получить и без обобщений, просто указав 
    //объект как тип данных и выполнив надлежащее приведение типов, то какая польза от того, что класс
    //MyObj делается обобщенным? Ответ на этот вопрос заключается в том, что обобщения автоматически 
    //обеспечивают типовую безопасность всех операций, затрагивающих класс MyObj.В ходе выполнения этих 
    //операций обобщения исключают необходимость обращаться к приведению типов и проверять соответствие типов в коде вручную.

	// Создадим обобщенный класс имеющий параметр типа T
	class MyObj<T>
	{
		T obj;

		public MyObj(T obj)
		{
			this.obj = obj;
		}

		public void objectType()
		{
			Console.WriteLine("Тип объекта: " + typeof(T));
		}
	}

	// Обобщенный класс с несколькими параметрами
	class MyObjects<T, V, E>
	{
		T obj1;
		V obj2;
		E obj3;

		public MyObjects(T obj1, V obj2, E obj3)
		{
			this.obj1 = obj1;
			this.obj2 = obj2;
			this.obj3 = obj3;
		}

		public void objectsType()
		{
			Console.WriteLine("\nТип объекта 1: " + typeof(T) +
				"\nТип объекта 2: " + typeof(V) +
				"\nТип объекта 3: " + typeof(E));
		}
	}


	//обобщенный интерфейс

	//Помимо обобщенных классов и методов, в C# допускаются обобщенные интерфейсы.
	//Такие интерфейсы указываются аналогично обобщенным классам. Применяя обобщения,
	//можно определять интерфейсы, объявляющие методы с обобщенными параметрами. 

	// Объявляем обобщенный интерфейс
	public interface ISort<T> 
        where T : struct
    {
        void ReWrite();
    }

    // Реализуем интерфейс в классе MyObje
    class MyObje<T> : ISort<T> where T : struct
    {
        public int longOb { get; set; }
        T[] myarr;

        public MyObje(int i)
        {
            longOb = i;
        }

        public MyObje(int i, T[] arr)
        {
            longOb = i;
            myarr = new T[i];
            for (int j = 0; j < arr.Length; j++)
                myarr[j] = arr[j];
        }

        public void ReWrite()
        {
            Console.WriteLine("Тип: {0}",typeof(T));
            Console.WriteLine("Массив объектов: ");
            foreach (T t in myarr)
                Console.Write("{0}\t",t);
            Console.WriteLine("\n");
        }
    }

    class Program
    {
		//исключения
		static void Del(int x, int y)
		{
			try
			{
				int result = x / y;
			}
			catch (DivideByZeroException)
			{
				Console.WriteLine("Деление на ноль!");
			}
			// Данный блок будет всегда выполняться
			finally
			{
				Console.WriteLine("Конец программы");
			}
		}
        static void Main()
        {
            //обобщенный интерфейс
            byte[] MyArrByte = new byte[5] {4, 5, 18, 56, 8};
            MyObje<byte> ByteConst = new MyObje<byte>(MyArrByte.Length,MyArrByte);
            ByteConst.ReWrite();

            float[] MyArrFloat = new float[8] { 12.0f, 1f, 3.4f, 2.8f, -334.7f, -2f, 7.89f, 0 };
            MyObje<float> FloatConst = new MyObje<float>(MyArrFloat.Length, MyArrFloat);
            FloatConst.ReWrite();


           // обобщенный класс
			// Создадим экземпляр обобщенного класса типа int
			MyObj<int> obj1 = new MyObj<int>(25);
			obj1.objectType();

			MyObjects<string, byte, decimal> obj2 = new MyObjects<string, byte, decimal>("Alex", 26, 12.333m);
			obj2.objectsType();


				//исключения
				Del(5, 0);


			//ограничения обобобщения 


			Account<int> acc1 = new Account<int>(1857) { Sum = 4500 };
			Account<int> acc2 = new Account<int>(3453) { Sum = 5000 };

			Transaction<Account<int>> transaction1 = new Transaction<Account<int>>
			{
				FromAccount = acc1,
				ToAccount = acc2,
				Sum = 6900
			};
			transaction1.Execute();

			Console.Read();
        }
    }

	//ограничения на обобобщения 

	class Account<T>
	{
		public T Id { get; private set; } // номер счета
		public int Sum { get; set; }
		public Account(T _id)
		{
			Id = _id;
		}
	}
	class Transaction<T> where T : Account<int>
	{
		public T FromAccount { get; set; }  // с какого счета перевод
		public T ToAccount { get; set; }    // на какой счет перевод
		public int Sum { get; set; }        // сумма перевода

		public void Execute()
		{
			if (FromAccount.Sum > Sum)
			{
				FromAccount.Sum -= Sum;
				ToAccount.Sum += Sum;
				Console.WriteLine($"Счет {FromAccount.Id}: {FromAccount.Sum}$ \nСчет {ToAccount.Id}: {ToAccount.Sum}$");
			}
			else
			{
				Console.WriteLine($"Недостаточно денег на счете {FromAccount.Id}");
			}
		}
	}
}

//С помощью универсальных параметров мы можем типизровать обобщенные классы любым типом.
//Однако иногда возникает необходимость конкретизировать тип. Например, у нас есть
//следующий класс Account, который представляет банковский счет:

//class Account
//{
//	public int Id { get; private set; } // номер счета
//	public int Sum { get; set; }
//	public Account(int _id)
//	{
//		Id = _id;
//	}
//}
//Для перевода средств с одного счета на другой мы можем определить класс Transaction, 
//который для выполнения всех операций будет использовать объекты класса Account.
//Но у класса Account может быть много наследников: DepositAccount (депозитный счет), 
//DemandAccount (счет до востребования) и т.д.И мы не можем знать, какие именно типы
//счетов будут использоваться в классе Transaction.Возможно, транзации будут проводиться только
//между счетами до востребования. И в этом случае в качестве универсального параметра можно установить тип Account:

//class Transaction<T> where T : Account
//{
//	public T FromAccount { get; set; }  // с какого счета перевод
//	public T ToAccount { get; set; }    // на какой счет перевод
//	public int Sum { get; set; }        // сумма перевода

//	public void Execute()
//	{
//		if (FromAccount.Sum > Sum)
//		{
//			FromAccount.Sum -= Sum;
//			ToAccount.Sum += Sum;
//			Console.WriteLine($"Счет {FromAccount.Id}: {FromAccount.Sum}$ \nСчет {ToAccount.Id}: {ToAccount.Sum}$");
//		}
//		else
//		{
//			Console.WriteLine($"Недостаточно денег на счете {FromAccount.Id}");
//		}
//	}
//}
//С помощью выражения where T : Account мы указываем, что используемый тип T обязательно 
//должен быть классом Account или его наследником.Благодаря подобному ограничению мы 
//можем использовать внутри класса Transaction все объекты типа T именно как объекты 
//Account и соответственно обращаться к их свойствам и методам.
//Теперь применим класс Transaction в программе:

//class Program
//{
//	static void Main(string[] args)
//	{
//		Account acc1 = new Account(1857) { Sum = 4500 };
//		Account acc2 = new Account(3453) { Sum = 5000 };
//		Transaction<Account> transaction1 = new Transaction<Account>
//		{
//			FromAccount = acc1,
//			ToAccount = acc2,
//			Sum = 6900
//		};
//		transaction1.Execute();

//		Console.ReadLine();
//	}
//}
//Следует учитывать, что только один класс может использоваться в качестве ограничения.
//В качестве ограничения также может выступать и обобщенный класс:

//class Program
//{
//	private static void Main(string[] args)
//	{
//		Account<int> acc1 = new Account<int>(1857) { Sum = 4500 };
//		Account<int> acc2 = new Account<int>(3453) { Sum = 5000 };

//		Transaction<Account<int>> transaction1 = new Transaction<Account<int>>
//		{
//			FromAccount = acc1,
//			ToAccount = acc2,
//			Sum = 6900
//		};
//		transaction1.Execute();

//		Console.Read();
//	}
//}
//class Account<T>
//{
//	public T Id { get; private set; } // номер счета
//	public int Sum { get; set; }
//	public Account(T _id)
//	{
//		Id = _id;
//	}
//}
//class Transaction<T> where T : Account<int>
//{
//	public T FromAccount { get; set; }  // с какого счета перевод
//	public T ToAccount { get; set; }    // на какой счет перевод
//	public int Sum { get; set; }        // сумма перевода

//	public void Execute()
//	{
//		if (FromAccount.Sum > Sum)
//		{
//			FromAccount.Sum -= Sum;
//			ToAccount.Sum += Sum;
//			Console.WriteLine($"Счет {FromAccount.Id}: {FromAccount.Sum}$ \nСчет {ToAccount.Id}: {ToAccount.Sum}$");
//		}
//		else
//		{
//			Console.WriteLine($"Недостаточно денег на счете {FromAccount.Id}");
//		}
//	}
//}
//В данном случае класс Transaction типизирован классом Account<int>.Класс Account 
//же может быть типизирован абсолютно любым типом. Однако класс Transaction может 
//использовать только объекты класса Account<int> или его наследников. 
