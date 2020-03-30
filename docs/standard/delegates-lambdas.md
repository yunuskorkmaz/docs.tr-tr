---
title: Temsilciler ve lambda ifadeleri
description: Temsilcilerin, doğrudan çağrılabilen veya başka bir yönteme geçirilebilen ve çağrılan belirli bir yöntem imzasını belirten bir türü nasıl tanımladığını öğrenin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 34bfa4c6007ec771f784e927675f4e24d52e194f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391240"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="2399e-103">Temsilciler ve lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2399e-103">Delegates and lambdas</span></span>

<span data-ttu-id="2399e-104">Temsilciler, belirli bir yöntem imzasını belirten bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2399e-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="2399e-105">Bu imzayı karşılayan bir yöntem (statik veya örnek) bu tür bir değişkene atanabilir, sonra doğrudan (uygun bağımsız değişkenlerle) çağrılabilir veya bağımsız değişkenin kendisi olarak başka bir yönteme aktarılabilir ve sonra çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="2399e-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="2399e-106">Aşağıdaki örnek, temsilci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2399e-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="2399e-107">Satır `public delegate string Reverse(string s);` belirli bir imza bir temsilci türü oluşturur, bu durumda bir dize parametresi alır ve sonra bir dize parametresi döndürür bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="2399e-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="2399e-108">`static string ReverseString(string s)` Tanımlanan temsilci türüyle aynı imzaya sahip yöntem, temsilciyi uygular.</span><span class="sxs-lookup"><span data-stu-id="2399e-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="2399e-109">Satır, `Reverse rev = ReverseString;` ilgili temsilci türünden bir değişkene bir yöntem atayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2399e-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="2399e-110">Satır, `Console.WriteLine(rev("a string"));` temsilciyi çağırmak için temsilci türünden bir değişkenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2399e-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="2399e-111">Geliştirme işlemini kolaylaştırmak için .NET, programcıların yeniden kullanabileceği ve yeni türler oluşturması gerekmeyen bir dizi temsilci türü içerir.</span><span class="sxs-lookup"><span data-stu-id="2399e-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="2399e-112">Bunlar `Func<>` `Action<>` ,ve `Predicate<>`,, yeni temsilci türlerini tanımlamaya gerek kalmadan .NET API'leri boyunca çeşitli yerlerde kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="2399e-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="2399e-113">Tabii ki, çoğunlukla kullanılmak üzere olması gerekiyordu yolu ile ilgisi var onların imzaları göreceğiniz gibi üç arasında bazı farklılıklar vardır:</span><span class="sxs-lookup"><span data-stu-id="2399e-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="2399e-114">`Action<>`temsilcinin bağımsız değişkenlerini kullanarak bir eylem gerçekleştirmeye ihtiyaç duyulduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2399e-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="2399e-115">Kapsüllediği yöntem bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="2399e-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="2399e-116">`Func<>`genellikle elinizde bir dönüşüm olduğunda, yani temsilcinin bağımsız değişkenlerini farklı bir sonuca dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2399e-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="2399e-117">Projeksiyonlar bunun en önemli örneklerindendir.</span><span class="sxs-lookup"><span data-stu-id="2399e-117">Projections are a prime example of this.</span></span> <span data-ttu-id="2399e-118">Kapsülletiyi kapaya saran yöntem belirli bir değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="2399e-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="2399e-119">`Predicate<>`bağımsız değişkenin temsilcinin durumunu karşılar mı belirlemeniz gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2399e-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="2399e-120">Aynı zamanda bir `Func<T, bool>`, yöntem bir boolean değeri döndürür anlamına gelir olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="2399e-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="2399e-121">Şimdi yukarıdaki örneği alabilir ve özel bir `Func<>` tür yerine temsilci kullanarak yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2399e-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="2399e-122">Program tam olarak aynı çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="2399e-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="2399e-123">Bu basit örnek için, `Main` yöntem dışında tanımlanan bir yöntem olması biraz gereksiz görünüyor.</span><span class="sxs-lookup"><span data-stu-id="2399e-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="2399e-124">Bu nedenle .NET Framework 2.0 **anonim delegeler**kavramını tanıttı.</span><span class="sxs-lookup"><span data-stu-id="2399e-124">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="2399e-125">Onların desteği ile herhangi bir ek tür veya yöntem belirtmenize gerek kalmadan "satır" temsilcileri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2399e-125">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="2399e-126">Yalnızca gerektiğinde temsilcinin tanımını satır alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2399e-126">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="2399e-127">Örneğin, değiştirip anonim temsilcimizi kullanarak yalnızca çift sayıların listesini filtreleyip konsola yazdıracağız.</span><span class="sxs-lookup"><span data-stu-id="2399e-127">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

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

<span data-ttu-id="2399e-128">Gördüğünüz gibi, temsilcinin gövdesi diğer temsilciler gibi yalnızca bir dizi ifadedir.</span><span class="sxs-lookup"><span data-stu-id="2399e-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="2399e-129">Ama bunun ayrı bir tanım olması yerine, _ad hoc_ <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> bu yönteme yaptığımız çağrıda geçici olarak tanıttık.</span><span class="sxs-lookup"><span data-stu-id="2399e-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2399e-130">Ancak, bu yaklaşım bile, hala biz atabilir çok kod var.</span><span class="sxs-lookup"><span data-stu-id="2399e-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="2399e-131">Lambda **ifadeleri** burada devreye giriyor.</span><span class="sxs-lookup"><span data-stu-id="2399e-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="2399e-132">Lambda ifadeler, ya da kısaca sadece "lambdas", C # 3.0 ilk tanıtıldı, Dil Entegre Sorgu (LINQ) temel yapı taşlarından biri olarak.</span><span class="sxs-lookup"><span data-stu-id="2399e-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="2399e-133">Onlar sadece temsilcileri kullanmak için daha uygun bir sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="2399e-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="2399e-134">Bir imza ve yöntem gövdesi beyan ederler, ancak bir temsilciye atanmadıkça kendilerine ait resmi bir kimlikleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="2399e-134">They declare a signature and a method body, but don’t have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="2399e-135">Temsilcilerin aksine, doğrudan olay kaydının sol tarafı olarak veya çeşitli LINQ yan tümceleri ve yöntemleri yle atanabilirler.</span><span class="sxs-lookup"><span data-stu-id="2399e-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="2399e-136">Lambda ifadesi bir temsilci belirtmenin başka bir yolu olduğundan, yukarıdaki örneği anonim bir temsilci yerine lambda ifadesini kullanmak için yeniden yazabilmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="2399e-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="2399e-137">Önceki örnekte kullanılan lambda ifadesidir. `i => i % 2 == 0`</span><span class="sxs-lookup"><span data-stu-id="2399e-137">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="2399e-138">Yine, bu delegeleri kullanmak için **sadece çok** uygun bir sözdizimi, bu nedenle kapakları altında ne olur anonim temsilci ile ne benzer.</span><span class="sxs-lookup"><span data-stu-id="2399e-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="2399e-139">Yine, lambdas sadece delegeler, hangi herhangi bir sorun olmadan bir olay işleyiciolarak kullanılabilir anlamına gelir, aşağıdaki kod snippet gösterdiği gibi.</span><span class="sxs-lookup"><span data-stu-id="2399e-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="2399e-140">Bu `+=` bağlamda işleç bir [olaya](../../docs/csharp/language-reference/keywords/event.md)abone olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2399e-140">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="2399e-141">Daha fazla bilgi için [olaylara nasıl abone olunur ve bu etkinliklerden aboneliğinizi iptal edebilirsiniz.](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="2399e-141">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="2399e-142">Daha fazla okuma ve kaynaklar</span><span class="sxs-lookup"><span data-stu-id="2399e-142">Further reading and resources</span></span>

* [<span data-ttu-id="2399e-143">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="2399e-143">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="2399e-144">Anonim Fonksiyonlar</span><span class="sxs-lookup"><span data-stu-id="2399e-144">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="2399e-145">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="2399e-145">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
