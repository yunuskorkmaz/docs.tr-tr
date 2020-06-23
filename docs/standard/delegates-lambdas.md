---
title: Temsilciler ve lambda ifadeleri
description: Belirli bir yöntem imzasını belirten bir türü tanımlayan temsilcilerin doğrudan veya başka bir yönteme geçip çağrılabilecek bir tür tanımlar.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 184c9f61fd8456b22e8ecb262c131793160b49b0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244016"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="da273-103">Temsilciler ve lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="da273-103">Delegates and lambdas</span></span>

<span data-ttu-id="da273-104">Temsilciler belirli bir yöntem imzasını belirten bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="da273-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="da273-105">Bu imzayı karşılayan bir Yöntem (statik veya örnek), bu tür bir değişkene atanabilir, daha sonra doğrudan (uygun bağımsız değişkenlerle) veya bağımsız değişken olarak başka bir yönteme geçirilir ve ardından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="da273-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="da273-106">Aşağıdaki örnek, temsilci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da273-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="da273-107">`public delegate string Reverse(string s);`Satır, bu durumda bir dize parametresi alan ve sonra bir dize parametresi döndüren bir yöntem olan belirli bir imzanın temsilci türünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="da273-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="da273-108">`static string ReverseString(string s)`Tanımlı temsilci türüyle tam olarak aynı imzaya sahip olan yöntemi temsilciyi uygular.</span><span class="sxs-lookup"><span data-stu-id="da273-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="da273-109">`Reverse rev = ReverseString;`Satırı, karşılık gelen temsilci türünün bir değişkenine bir yöntem atayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="da273-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="da273-110">`Console.WriteLine(rev("a string"));`Satır, temsilciyi çağırmak için bir temsilci türü değişkeninin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="da273-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="da273-111">Geliştirme sürecini kolaylaştırmak için, .NET, programcıların yeniden kullanılabilen ve yeni türler oluşturmak zorunda olmayan bir temsilci türleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="da273-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="da273-112">Bu türler `Func<>` , `Action<>` ve ' dir `Predicate<>` ve yeni temsilci türleri tanımlamak zorunda kalmadan kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="da273-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="da273-113">Üç tür arasında, kullanılması amaçlanan şekilde yapılacak bazı farklılıklar vardır:</span><span class="sxs-lookup"><span data-stu-id="da273-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="da273-114">`Action<>`Temsilcinin bağımsız değişkenlerini kullanarak bir eylem gerçekleştirmeniz gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da273-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="da273-115">Kapsülleyen Yöntem bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="da273-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="da273-116">`Func<>`genellikle bir dönüşüme sahip olduğunuzda kullanılır, diğer bir deyişle, temsilcinin bağımsız değişkenlerini farklı bir sonuca dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da273-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="da273-117">Tahminler iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="da273-117">Projections are a good example.</span></span> <span data-ttu-id="da273-118">Kapsülleyen yöntemi belirtilen değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="da273-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="da273-119">`Predicate<>`bağımsız değişkenin temsilcinin koşulunu karşılayıp karşılamadığını belirlemeniz gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da273-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="da273-120">Ayrıca bir olarak yazılabilir, bu da `Func<T, bool>` yöntemin bir Boolean değer döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="da273-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="da273-121">Şimdi örneğimizi alıp `Func<>` özel bir tür yerine temsilciyi kullanarak yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da273-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="da273-122">Program tamamen aynı çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="da273-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="da273-123">Bu basit örnek için yöntemin dışında tanımlanmış bir yöntemin olması biraz daha fazla `Main` görünüyor.</span><span class="sxs-lookup"><span data-stu-id="da273-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="da273-124">.NET Framework 2,0 *anonim temsilciler*kavramını ortaya sunmuştur, bu da ek bir tür veya yöntem belirtmeye gerek kalmadan "satır içi" Temsilciler oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da273-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="da273-125">Aşağıdaki örnekte, anonim bir temsilci bir listeyi yalnızca çift sayılarla filtreleyerek konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="da273-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="da273-126">Gördüğünüz gibi, temsilcinin gövdesi, diğer tüm temsilciler gibi yalnızca bir ifade kümesidir.</span><span class="sxs-lookup"><span data-stu-id="da273-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="da273-127">Ancak, ayrı bir tanım olmak yerine, yönteme yönelik Çağrımızda bir _ad_ tanıdık <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="da273-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="da273-128">Ancak, bu yaklaşımda bile, fırladığımız çok fazla kod vardır.</span><span class="sxs-lookup"><span data-stu-id="da273-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="da273-129">Bu, *lambda ifadelerinin* oynatma içine geldiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="da273-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="da273-130">Lambda ifadeleri veya Short için yalnızca "Lambdalar", dil ile tümleşik sorgu (LINQ) temel yapı taşlarından biri olarak C# 3,0 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="da273-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="da273-131">Temsilciler kullanmanın yalnızca daha uygun bir sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="da273-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="da273-132">Bir temsilciye atanmadıkları takdirde, bir imza ve Yöntem gövdesi bildirir, ancak kendi biçimsel kimliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="da273-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="da273-133">Temsilcilerden farklı olarak, doğrudan olay kaydının sağ tarafı olarak veya çeşitli LINQ yan tümceleri ve yöntemleri olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="da273-133">Unlike delegates, they can be directly assigned as the right-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="da273-134">Lambda ifadesi bir temsilci belirtmenin yalnızca başka bir yolu olduğundan, yukarıdaki örneği anonim bir temsilci yerine bir lambda ifadesi kullanacak şekilde yeniden yazamayacak.</span><span class="sxs-lookup"><span data-stu-id="da273-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="da273-135">Yukarıdaki örnekte, kullanılan lambda ifadesi `i => i % 2 == 0` .</span><span class="sxs-lookup"><span data-stu-id="da273-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="da273-136">Ayrıca, temsilcileri kullanmak için kullanışlı bir sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="da273-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="da273-137">Kapakların altında ne olacağı, anonim temsilciyle ilgili olana benzerdir.</span><span class="sxs-lookup"><span data-stu-id="da273-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="da273-138">Daha sonra Lambdalar yalnızca temsilcidir. Bu, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilecekleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="da273-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="da273-139">`+=`Bu bağlamdaki işleç bir [olaya](../csharp/language-reference/keywords/event.md)abone olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da273-139">The `+=` operator in this context is used to subscribe to an [event](../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="da273-140">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="da273-140">For more information, see [How to subscribe to and unsubscribe from events](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="da273-141">Daha fazla okuma ve kaynak</span><span class="sxs-lookup"><span data-stu-id="da273-141">Further reading and resources</span></span>

* [<span data-ttu-id="da273-142">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="da273-142">Delegates</span></span>](../csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="da273-143">Anonim Işlevler</span><span class="sxs-lookup"><span data-stu-id="da273-143">Anonymous Functions</span></span>](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="da273-144">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="da273-144">Lambda expressions</span></span>](../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
