---
title: Temsilciler ve lambda ifadeleri
description: Nasıl doğrudan veya başka bir yönteme ve adlı bir özel yöntem imzası belirtmek Temsilciler, tür tanımlama hakkında bilgi edinin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: e392f6b2e57bebf1ab916bc6142aebbc8f341db2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615311"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="539fd-103">Temsilciler ve lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="539fd-103">Delegates and lambdas</span></span>

<span data-ttu-id="539fd-104">Temsilciler belirli yöntem imzası belirtmek tanımlayan bir tür.</span><span class="sxs-lookup"><span data-stu-id="539fd-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="539fd-105">Bir yöntem (statik veya örnek) Bu imza Bu türden bir değişkene atanabilir sonra doğrudan (uygun bağımsız değişkenlerle) olarak adlandırılan veya bağımsız değişken olarak kendisini başka bir yönteme geçirilen ve ardından adlı karşılar.</span><span class="sxs-lookup"><span data-stu-id="539fd-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="539fd-106">Aşağıdaki örnekte, temsilci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="539fd-106">The following example demonstrates delegate use.</span></span>

```csharp
using System;
using System.Linq;

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

* <span data-ttu-id="539fd-107">`public delegate string Reverse(string s);` Satırı bu durumda bir temsilci türü belirli imzası, bir dize parametresi alan ve sonra bir dize parametresi döndüren bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="539fd-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="539fd-108">`static string ReverseString(string s)` Tanımlı temsilci türüyle tam aynı imzaya sahip yöntemi temsilci uygular.</span><span class="sxs-lookup"><span data-stu-id="539fd-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="539fd-109">`Reverse rev = ReverseString;` Satır gösterir bir yöntemi karşılık gelen temsilci türünün bir değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="539fd-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="539fd-110">`Console.WriteLine(rev("a string"));` Satırı bir temsilci türünde bir değişken temsilci çağırmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="539fd-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="539fd-111">Geliştirme işlemi kolaylaştırmak için .NET programcıları yeniden ve yeni türler oluşturmak için olmaması temsilci türleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="539fd-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="539fd-112">Bunlar `Func<>`, `Action<>` ve `Predicate<>`, ve bunlar gerek kalmadan .NET API'lerini çeşitli yerlerde yeni temsilci türleri tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="539fd-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="539fd-113">Elbette, kullanılacak düşünülen işlemleriyle yapmak için çoğunlukla sahip imzaları içindeki göreceğiniz gibi üç arasında bazı farklar vardır:</span><span class="sxs-lookup"><span data-stu-id="539fd-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="539fd-114">`Action<>` temsilcinin bağımsız değişkenleri kullanarak bir eylem gerçekleştirmek için ihtiyaç olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="539fd-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
* <span data-ttu-id="539fd-115">`Func<>` genellikle bir dönüştürme taraftan, varsa, kullanılan diğer bir deyişle, temsilcinin bağımsız değişkenleri farklı bir sonuç biçimine dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="539fd-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="539fd-116">Tahminler, bu birinci bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="539fd-116">Projections are a prime example of this.</span></span>
* <span data-ttu-id="539fd-117">`Predicate<>` bağımsız değişken, temsilci koşulu karşılayıp karşılamadığını belirlemek gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="539fd-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="539fd-118">Olarak da yazılabilir bir `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="539fd-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="539fd-119">Biz artık yukarıdaki örneğimizde alabilir ve kullanarak yeniden `Func<>` temsilci yerine özel bir tür.</span><span class="sxs-lookup"><span data-stu-id="539fd-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="539fd-120">Program, tam olarak aynı çalışmaya devam edecek.</span><span class="sxs-lookup"><span data-stu-id="539fd-120">The program will continue running exactly the same.</span></span>

```csharp
using System;
using System.Linq;

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

<span data-ttu-id="539fd-121">Bu basit örnekte, olması dışında tanımlanmış bir yöntem `Main` yöntemi biraz gereksiz görünüyor.</span><span class="sxs-lookup"><span data-stu-id="539fd-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="539fd-122">.NET Framework 2.0 sunulan kavramı, bu nedenle olan **anonim Temsilciler**.</span><span class="sxs-lookup"><span data-stu-id="539fd-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="539fd-123">Destek ile herhangi bir ek türü veya yöntemini belirtmek zorunda kalmadan "satır içi" temsilci oluşturmak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="539fd-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="539fd-124">Yalnızca satır gerek duyduğunuz, temsilci tanımı.</span><span class="sxs-lookup"><span data-stu-id="539fd-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="539fd-125">Örneğin, yedekleme geçin ve yalnızca çift sayıların bir listeyi filtreleyin ve ardından bunları konsola yazdırır bizim anonim temsilci kullanmak için kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="539fd-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
using System;
using System.Collections.Generic;

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
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="539fd-126">Gördüğünüz gibi temsilci yalnızca bir dizi ifadeleri, herhangi bir temsilci gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="539fd-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="539fd-127">Ancak bunun yerine ayrı bir tanımı olan, onu tanıttık _geçici_ bizim çağrıda <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="539fd-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="539fd-128">Ancak, bile bu yaklaşımda, yine de biz hemen oluşturabilecek kadar kodu yok.</span><span class="sxs-lookup"><span data-stu-id="539fd-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="539fd-129">Burada **lambda ifadeleri** oyuna gelir.</span><span class="sxs-lookup"><span data-stu-id="539fd-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="539fd-130">Lambda ifadeleri veya kısaca, yalnızca "lambdalar" de kullanıma sunulmuştur ilk C# 3.0, temel yapı taşlarını, dil tümleşik sorgu (LINQ) biri olarak.</span><span class="sxs-lookup"><span data-stu-id="539fd-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="539fd-131">Temsilcileri kullanma için yalnızca bir daha kullanışlı söz dizimi değildirler.</span><span class="sxs-lookup"><span data-stu-id="539fd-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="539fd-132">Bir imza ve bir yöntem gövdesi bildirmek, ancak bir temsilciye atanmış oldukları sürece, kendi, biçimsel bir kimlik yok.</span><span class="sxs-lookup"><span data-stu-id="539fd-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="539fd-133">Temsilciler, bunlar doğrudan sol tarafı olay kaydı veya çeşitli LINQ yan tümceleri ve yöntemler olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="539fd-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="539fd-134">Bir lambda ifadesi bir temsilci belirtmenin başka bir yol olduğundan, biz bir anonim temsilci yerine bir lambda ifadesi kullanmak için yukarıdaki örnek yeniden mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="539fd-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
using System;
using System.Collections.Generic;

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

<span data-ttu-id="539fd-135">Önceki örnekte kullanılan lambda ifadesidir `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="539fd-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="539fd-136">Yeniden yalnızca olduğu bir **çok** ne olacağını perde anonim temsilci ile neler için benzer şekilde, temsilciler kullanılarak için kullanışlı bir söz dizimi.</span><span class="sxs-lookup"><span data-stu-id="539fd-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="539fd-137">Yine, lambda ifadeleri, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilir anlamına gelir yalnızca temsilcileri.</span><span class="sxs-lookup"><span data-stu-id="539fd-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="539fd-138">`+=` İşleci bu bağlamda abone olmak için kullanılan bir [olay](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="539fd-138">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="539fd-139">Daha fazla bilgi için [nasıl yapılır: Abone olma ve aboneliği olaylardan](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="539fd-139">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="539fd-140">Daha fazla bilgi ve kaynaklar</span><span class="sxs-lookup"><span data-stu-id="539fd-140">Further reading and resources</span></span>

* [<span data-ttu-id="539fd-141">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="539fd-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="539fd-142">Anonim İşlevler</span><span class="sxs-lookup"><span data-stu-id="539fd-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="539fd-143">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="539fd-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
