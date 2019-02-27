---
title: Genel türler (genel türler) genel bakış
description: Taahhüt vermek zorunda kalmadan bir gerçek veri türü için tür açısından güvenli veri yapıları tanımlamanızı sağlayan kod şablonları nasıl genel türler gören öğrenin.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 991e3800e1302843db0dc1c57ed3a7e4becd298e
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835297"
---
# <a name="generic-types-overview"></a><span data-ttu-id="66443-103">Genel türler genel bakış</span><span class="sxs-lookup"><span data-stu-id="66443-103">Generic types overview</span></span>

<span data-ttu-id="66443-104">Geliştiriciler genel türler, her zaman açık veya örtük olarak olup olmadığını,. NET'te kullanın.</span><span class="sxs-lookup"><span data-stu-id="66443-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="66443-105">. NET'te LINQ kullandığınızda, hiç olmadığı kadar birlikte çalıştığınız fark ettiniz <xref:System.Collections.Generic.IEnumerable%601>?</span><span class="sxs-lookup"><span data-stu-id="66443-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="66443-106">Veya, Entity Framework kullanan veritabanlarına konuşmak için hiç olmadığı kadar çevrimiçi bir örneği, bir "Genel deponun" gördüğünüz, pek çok yöntem Iqueryable dönüş gördünüz mü<T>?</span><span class="sxs-lookup"><span data-stu-id="66443-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="66443-107">Hangi merak etmiş **T** Bu örnekler ve burada neden olduğu yer.</span><span class="sxs-lookup"><span data-stu-id="66443-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="66443-108">İlk .NET Framework 2.0 sürümünde sunulan **genel türler** aslında bir "code"şablonu"olan tanımlamak geliştiricilerinin sağlayan [tür kullanımı uyumlu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) olmadan yürüten bir gerçek veri türü için veri yapıları.</span><span class="sxs-lookup"><span data-stu-id="66443-108">First introduced in the .NET Framework 2.0, **generics** are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="66443-109">Örneğin, <xref:System.Collections.Generic.List%601> olduğu bir [genel koleksiyon](xref:System.Collections.Generic) , bildirilebileceği ve herhangi bir türü ile gibi kullanılan `List<int>`, `List<string>`, veya `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="66443-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="66443-110">Genel türler neden yararlıdır anlamak için bir özel bir sınıf önce ve genel türler ekledikten sonra bakalım: <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="66443-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="66443-111">.NET Framework 1. 0'da, `ArrayList` öğe türü olan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="66443-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="66443-112">Bu geliyordu eklenen herhangi bir öğenin içine sessiz bir şekilde dönüştürülmüş bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="66443-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="66443-113">Aynı öğeler listeden okurken gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="66443-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="66443-114">Bu işlem olarak bilinir [kutulama ve kutudan çıkarma](../csharp/programming-guide/types/boxing-and-unboxing.md), ve performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="66443-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="66443-115">Birden çok, ancak derleme zamanında listesinde veri türünü belirlemek için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="66443-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="66443-116">Bu, bazı kırılgan kodunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="66443-116">This makes for some fragile code.</span></span> <span data-ttu-id="66443-117">Genel türler, her bir örneğin listesinin içereceği veri türünü tanımlayarak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="66443-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="66443-118">Örneğin, yalnızca tam sayılar ekleyebilirsiniz `List<int>` ve yalnızca kişilere ekleyin `List<Person>`.</span><span class="sxs-lookup"><span data-stu-id="66443-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="66443-119">Genel türler, ayrıca çalışma zamanında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="66443-119">Generics are also available at runtime.</span></span> <span data-ttu-id="66443-120">Başka bir deyişle, çalışma zamanının hangi türde veri yapısı, kullanmakta olduğunuz ve bellekte daha verimli bir şekilde depolayabilirsiniz bilir.</span><span class="sxs-lookup"><span data-stu-id="66443-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="66443-121">Aşağıdaki örnek veri olduğunu bilmesinin etkinliğini gösteren küçük bir program, yapı zamanında türü:</span><span class="sxs-lookup"><span data-stu-id="66443-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="66443-122">Bu program, aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="66443-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="66443-123">İşte bu genel listeyi sıralamaya dikkat edin ilk şey, genel olmayan listenin sıralama daha önemli ölçüde daha hızlı.</span><span class="sxs-lookup"><span data-stu-id="66443-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="66443-124">Genel olmayan listesi türünü genelleştirilmiş ise tür genel liste için farklı ([]),: System.Int32 olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66443-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="66443-125">Çalışma zamanı genel bildiğinden `List<int>` türünde <xref:System.Int32>, liste öğelerini genel olmayan sırasında bellekte temel alınan bir tamsayı dizisi olarak depolayabilir `ArrayList` her liste öğesinde bir nesneye dönüştürmek vardır.</span><span class="sxs-lookup"><span data-stu-id="66443-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="66443-126">Bu örnekte gösterildiği gibi ek yayınları zaman ayırıp listesi sıralama aşağı yavaş.</span><span class="sxs-lookup"><span data-stu-id="66443-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="66443-127">Ek bir avantajı, genel tür bilerek çalışma zamanının daha iyi hata ayıklama bir deneyimdir.</span><span class="sxs-lookup"><span data-stu-id="66443-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="66443-128">Genel C# hata ayıklama işlemi yaparken, her öğe türünü data yapınız bildirin.</span><span class="sxs-lookup"><span data-stu-id="66443-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="66443-129">Genel türler hiçbir fikriniz her öğe türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="66443-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="66443-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66443-130">See also</span></span>

- [<span data-ttu-id="66443-131">C# programlama kılavuzu - genel türler</span><span class="sxs-lookup"><span data-stu-id="66443-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
