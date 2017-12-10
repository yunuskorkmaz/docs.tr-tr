---
title: Temsilciler ve lambdas
description: "Nasıl doğrudan adlı veya başka bir yönteme geçirilen ve olarak adlandırılan belirli yöntem imzası belirtmek Temsilciler, tür tanımlama öğrenin."
keywords: .NET, .NET core
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: c348c36caeaf703a99336f1d2a8f6cdbe5968b99
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="aded9-104">Temsilciler ve lambdas</span><span class="sxs-lookup"><span data-stu-id="aded9-104">Delegates and lambdas</span></span>

<span data-ttu-id="aded9-105">Temsilciler belirli yöntem imzası belirtmek bir türünü tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="aded9-105">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="aded9-106">Bir yöntem (statik veya örnek) karşılayan bu imza Bu tür bir değişkene atanabilir sonra doğrudan (uygun bağımsız değişkenler ile) olarak adlandırılan veya bağımsız değişken olarak kendisi başka bir yönteme geçirilen ve sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="aded9-106">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="aded9-107">Aşağıdaki örnek temsilci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aded9-107">The following example demonstrates delegate use.</span></span>

```csharp
public class Program
{

  public delegate string Reverse(string s);

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Reverse rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

*   <span data-ttu-id="aded9-108">Belirli bir imza bir temsilci türü oluşturuyoruz 4 satırında, bu durumda bir yöntemi, bir dize parametresi alan ve sonra bir dize parametresi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aded9-108">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="aded9-109">6. satırda temsilci uyarlamasını tam aynı imzaya sahip bir yöntem sağlayarak tanımlarız.</span><span class="sxs-lookup"><span data-stu-id="aded9-109">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="aded9-110">13 satırında, uyumlu bir türü yöntemi atandığı `Reverse` temsilci.</span><span class="sxs-lookup"><span data-stu-id="aded9-110">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="aded9-111">Son olarak, 15 satırda bir dize tersine geçirme temsilci biz çağırır.</span><span class="sxs-lookup"><span data-stu-id="aded9-111">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="aded9-112">Geliştirme işlemini kolaylaştırmak için .NET programcıları yeniden kullanmak ve yeni türleri oluşturmak zorunda kalmazsınız temsilci türleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="aded9-112">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="aded9-113">Bunlar `Func<>`, `Action<>` ve `Predicate<>`, ve bunlar içinde çeşitli yerlerde .NET API'lerini gerek kalmadan yeni temsilci türleri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aded9-113">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="aded9-114">Elbette, çoğunlukla kullanılacak demek yolu ile yapmak zorunda kendi imzaları de göreceğiniz gibi üç arasındaki bazı farklar vardır:</span><span class="sxs-lookup"><span data-stu-id="aded9-114">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="aded9-115">`Action<>`Temsilci bağımsız değişkenleri kullanarak bir eylem gerçekleştirmek üzere gereksinimi olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aded9-115">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="aded9-116">`Func<>`genellikle bir dönüşüm taraftan, varsa, kullanılan diğer bir deyişle, temsilci bağımsız farklı bir sonuç dönüştürme gerekir.</span><span class="sxs-lookup"><span data-stu-id="aded9-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="aded9-117">Bu prime örneği projeksiyonlardır.</span><span class="sxs-lookup"><span data-stu-id="aded9-117">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="aded9-118">`Predicate<>`bağımsız değişken temsilci koşulu karşılayan varsa belirlemek üzere gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aded9-118">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="aded9-119">Olarak da yazılabilir bir `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="aded9-119">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="aded9-120">Biz şimdi örneğimizde yukarıdaki alabilir ve kullanarak yeniden `Func<>` temsilci yerine özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="aded9-120">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="aded9-121">Program, tam olarak aynı çalışmaya devam edecek.</span><span class="sxs-lookup"><span data-stu-id="aded9-121">The program will continue running exactly the same.</span></span>

```csharp
public class Program
{

  static string ReverseString(string s)
  {
      return new string(s.Reverse().ToArray());
  }

  static void Main(string[] args)
  {
      Func<string, string> rev = ReverseString;

      Console.WriteLine(rev("a string"));
  }
}
```

<span data-ttu-id="aded9-122">Bu basit örnekte, Main() yönteminin dışında tanımlanmış bir yöntemi olması biraz gereksiz gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="aded9-122">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="aded9-123">.NET Framework 2.0 kavramı sunulan bu nedenle olan **anonim Temsilciler**.</span><span class="sxs-lookup"><span data-stu-id="aded9-123">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="aded9-124">Destek ile herhangi bir ek türü veya yöntemi belirtmek zorunda kalmadan "satır içi" Temsilciler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aded9-124">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="aded9-125">Yalnızca ihtiyaç duyacağınız, temsilci tanımını satır içi.</span><span class="sxs-lookup"><span data-stu-id="aded9-125">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="aded9-126">Örneğin, biz yukarı geçin ve yalnızca çift sayı listesini filtrelemek ve bunları konsola yazdırma için anonim bizim temsilci kullanın alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="aded9-126">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="aded9-127">Vurgulanan satırlar dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="aded9-127">Notice the highlighted lines.</span></span> <span data-ttu-id="aded9-128">Gördüğünüz gibi temsilci gövdesi yalnızca ifadeleri, herhangi bir temsilci kümesidir.</span><span class="sxs-lookup"><span data-stu-id="aded9-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="aded9-129">Ancak bunun yerine ayrı bir tanımı olması, biz bunu ekledik _geçici_ bizim çağrıda `FindAll()` yöntemi `List<T>` türü.</span><span class="sxs-lookup"><span data-stu-id="aded9-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="aded9-130">Ancak, bu yaklaşımda bile yoktur hala biz hemen atabilirsiniz kadar kod.</span><span class="sxs-lookup"><span data-stu-id="aded9-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="aded9-131">Bu yerdir **lambda ifadeleri** oyuna gelir.</span><span class="sxs-lookup"><span data-stu-id="aded9-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="aded9-132">Lambda ifadeleri veya kısaca, yalnızca "Lambda'lar" C# 3.0 sürümünde, temel yapı taşlarını, dil tümleşik sorgu (LINQ) biri olarak ilk kez sunulan.</span><span class="sxs-lookup"><span data-stu-id="aded9-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="aded9-133">Temsilcileri kullanma için yalnızca bir daha kullanışlı sözdizimi oldukları.</span><span class="sxs-lookup"><span data-stu-id="aded9-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="aded9-134">İmza ve yöntem gövdesi bildirme, ancak bir temsilci atamazsanız, kendi resmi kimliğini yok.</span><span class="sxs-lookup"><span data-stu-id="aded9-134">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="aded9-135">Temsilciler, doğrudan taraftaki olay kaydı veya çeşitli LINQ yan tümceleri ve yöntemleri olarak atanabilirler.</span><span class="sxs-lookup"><span data-stu-id="aded9-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="aded9-136">Lambda ifadesi bir temsilci belirtmenin yalnızca başka bir yol olduğundan, biz lambda ifadesi yerine anonim bir temsilci kullanmak için yukarıdaki örnek yeniden yapabiliyor olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aded9-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
public class Program
{

  public static void Main(string[] args)
  {
    List<int> list = new List<int>();

    for (int i = 1; i <= 100; i++)
    {
        list.Add(i);
    }

    List<int> result = list.FindAll(i => i % 2 == 0);

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="aded9-137">Vurgulanan satırlar göz atın, lambda ifadesi gibi nasıl göründüğünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aded9-137">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="aded9-138">Yeniden yalnızca olan bir **çok** perde arkasında olanlar anonim temsilci ile neler için benzer şekilde, kullanma uygun söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="aded9-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="aded9-139">Yeniden Lambda'lar, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilir başka bir deyişle, yalnızca temsilciler olan.</span><span class="sxs-lookup"><span data-stu-id="aded9-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

## <a name="further-reading-and-resources"></a><span data-ttu-id="aded9-140">Daha fazla bilgi ve kaynaklar</span><span class="sxs-lookup"><span data-stu-id="aded9-140">Further reading and resources</span></span>

*   [<span data-ttu-id="aded9-141">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="aded9-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="aded9-142">Anonim İşlevler</span><span class="sxs-lookup"><span data-stu-id="aded9-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="aded9-143">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="aded9-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
