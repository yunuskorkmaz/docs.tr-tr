---
title: Temsilciler ve lambda ifadeleri
description: Temsilcilerin, doğrudan çağrılabilen veya başka bir yönteme geçirilebilen ya da çağrılan belirli bir yöntem imzasını belirten bir türü nasıl tanımladığını öğrenin.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 0abcc73e31eab89c422513acf778bc8bd092e788
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345546"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="abd2b-103">Temsilciler ve lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="abd2b-103">Delegates and lambdas</span></span>

<span data-ttu-id="abd2b-104">Temsilciler, belirli bir yöntem imzasını belirten bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="abd2b-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="abd2b-105">Bu imzayı karşılayan bir Yöntem (statik veya örnek), bu tür bir değişkene atanabilir, daha sonra doğrudan (uygun bağımsız değişkenlerle) veya bağımsız değişken olarak başka bir yönteme geçirilir ve ardından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="abd2b-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="abd2b-106">Aşağıdaki örnek, temsilci kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="abd2b-107">`public delegate string Reverse(string s);` satırı belirli bir imzanın temsilci türünü oluşturur, bu durumda bir dize parametresi alan ve sonra bir dize parametresi döndüren bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="abd2b-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="abd2b-108">Tanımlı temsilci türüyle tam olarak aynı imzaya sahip `static string ReverseString(string s)` yöntemi, temsilciyi uygular.</span><span class="sxs-lookup"><span data-stu-id="abd2b-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="abd2b-109">`Reverse rev = ReverseString;` satırı, karşılık gelen temsilci türünün bir değişkenine bir yöntem atayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="abd2b-110">`Console.WriteLine(rev("a string"));` satırı, temsilciyi çağırmak için bir temsilci türü değişkeninin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="abd2b-111">Geliştirme sürecini kolaylaştırmak için, .NET, programcıların yeniden kullanılabilen ve yeni türler oluşturmak zorunda olmayan bir temsilci türleri kümesi içerir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="abd2b-112">Bunlar `Func<>`, `Action<>` ve `Predicate<>`ve yeni temsilci türleri tanımlamaya gerek kalmadan .NET API 'Lerinde çeşitli yerlerde kullanılabilirler.</span><span class="sxs-lookup"><span data-stu-id="abd2b-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="abd2b-113">Kuşkusuz, her ikisi arasında, genellikle kullanılması amaçlanan gibi olması gereken üç farklı bir farklılık vardır:</span><span class="sxs-lookup"><span data-stu-id="abd2b-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="abd2b-114">`Action<>`, temsilcinin bağımsız değişkenlerini kullanarak bir eylem gerçekleştirmeniz gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abd2b-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
* <span data-ttu-id="abd2b-115">`Func<>`, genellikle bir dönüşüme sahip olduğunuzda kullanılır, diğer bir deyişle, temsilcinin bağımsız değişkenlerini farklı bir sonuca dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="abd2b-116">Tahminler bunun ana örneğidir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-116">Projections are a prime example of this.</span></span>
* <span data-ttu-id="abd2b-117">`Predicate<>`, bağımsız değişkenin temsilci koşulunu karşılayıp karşılamadığını belirlemeniz gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abd2b-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="abd2b-118">Ayrıca, bir `Func<T, bool>`olarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="abd2b-119">Şimdi örneğimizi alıp özel bir tür yerine `Func<>` temsilcisini kullanarak yeniden yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abd2b-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="abd2b-120">Program tamamen aynı çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-120">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="abd2b-121">Bu basit örnek için `Main` yöntemi dışında tanımlanan bir yöntemin olması biraz daha fazla görünüyor.</span><span class="sxs-lookup"><span data-stu-id="abd2b-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="abd2b-122">Bunun nedeni 2,0 .NET Framework **anonim temsilciler**kavramını sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="abd2b-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="abd2b-123">Desteğiyle, ek bir tür veya yöntem belirtmek zorunda kalmadan "satır içi" Temsilciler oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abd2b-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="abd2b-124">İhtiyaç duyduğunuz temsilcinin tanımını yalnızca satır içi olarak alırsınız.</span><span class="sxs-lookup"><span data-stu-id="abd2b-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="abd2b-125">Bir örnek için, bu anahtarı değiştirmek ve anonim temsilcimizi kullanarak tek hatta sayıların bir listesini filtreleyeceğiz ve ardından konsola yazdıracağız.</span><span class="sxs-lookup"><span data-stu-id="abd2b-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

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

<span data-ttu-id="abd2b-126">Gördüğünüz gibi, temsilcinin gövdesi, diğer tüm temsilciler gibi yalnızca bir ifade kümesidir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="abd2b-127">Ancak, ayrı bir tanım olmak yerine, <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metoduna yapılan Çağrımızda BT _geçici_ olarak tanıtıldık.</span><span class="sxs-lookup"><span data-stu-id="abd2b-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="abd2b-128">Ancak, bu yaklaşımda bile, fırladığımız çok fazla kod vardır.</span><span class="sxs-lookup"><span data-stu-id="abd2b-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="abd2b-129">Bu, **lambda ifadelerinin** oynatma içine geldiği yerdir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="abd2b-130">Lambda ifadeleri veya Short için yalnızca "Lambdalar", dil ile tümleşik sorgu C# (LINQ) temel yapı taşlarından biri olarak 3,0 ' de ilk sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="abd2b-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="abd2b-131">Temsilciler kullanmanın yalnızca daha uygun bir sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="abd2b-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="abd2b-132">Bir temsilciye atanmadıkları takdirde, bir imza ve Yöntem gövdesi bildirir, ancak kendi biçimsel kimliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="abd2b-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="abd2b-133">Temsilcilerden farklı olarak, doğrudan olay kaydının sol tarafı olarak veya çeşitli LINQ yan tümceleri ve yöntemleri olarak atanabilir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="abd2b-134">Lambda ifadesi bir temsilci belirtmenin yalnızca başka bir yolu olduğundan, yukarıdaki örneği anonim bir temsilci yerine bir lambda ifadesi kullanacak şekilde yeniden yazamayacak.</span><span class="sxs-lookup"><span data-stu-id="abd2b-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="abd2b-135">Yukarıdaki örnekte, kullanılan lambda ifadesi `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="abd2b-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="abd2b-136">Bu, temsilcileri kullanmak için **oldukça** kullanışlı bir sözdizimidir, bu nedenle, kapsamaları altında olduğu gibi, anonim temsilciyle ne gibi bir durumla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="abd2b-137">Daha sonra Lambdalar yalnızca temsilcidir. Bu, aşağıdaki kod parçacığında gösterildiği gibi herhangi bir sorun olmadan bir olay işleyicisi olarak kullanılabilecekleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="abd2b-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="abd2b-138">Bu bağlamdaki `+=` işleci bir [olaya](../../docs/csharp/language-reference/keywords/event.md)abone olmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abd2b-138">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="abd2b-139">Daha fazla bilgi için bkz. [olaylara abone olma ve olayları kaldırma](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="abd2b-139">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="abd2b-140">Daha fazla okuma ve kaynak</span><span class="sxs-lookup"><span data-stu-id="abd2b-140">Further reading and resources</span></span>

* [<span data-ttu-id="abd2b-141">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="abd2b-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="abd2b-142">Anonim İşlevler</span><span class="sxs-lookup"><span data-stu-id="abd2b-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="abd2b-143">Lambda ifadeleri</span><span class="sxs-lookup"><span data-stu-id="abd2b-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
