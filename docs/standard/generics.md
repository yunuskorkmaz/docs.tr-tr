---
title: Genel türler (genel türler) genel bakış
description: Genel türlerin, gerçek bir veri türüne uygulamadan tür kullanımı uyumlu veri yapılarını tanımlamanızı sağlayan kod şablonları olarak nasıl davranması gerektiğini öğrenin.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 5f6e84e23b5bcdcb3dcd742823d83728fb43d195
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557950"
---
# <a name="generic-types-overview"></a><span data-ttu-id="d00bd-103">Genel türlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="d00bd-103">Generic types overview</span></span>

<span data-ttu-id="d00bd-104">Geliştiriciler, örtük olarak veya açık olsun, .NET 'te her zaman genel türler kullanır.</span><span class="sxs-lookup"><span data-stu-id="d00bd-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="d00bd-105">.NET ' te LINQ kullandığınızda, ile çalıştığınızı fark muydunuz <xref:System.Collections.Generic.IEnumerable%601> ?</span><span class="sxs-lookup"><span data-stu-id="d00bd-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="d00bd-106">Ya da Entity Framework kullanarak veritabanlarıyla iletişim için "genel deponun" çevrimiçi bir örneğini görüyorsanız, çoğu yöntemin geri döndüğünüzü gördünüz `IQueryable<T>` mi?</span><span class="sxs-lookup"><span data-stu-id="d00bd-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="d00bd-107">**T** 'nin Bu örneklerde ne olduğunu ve neden orada olduğunu merak etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d00bd-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="d00bd-108">İlk olarak .NET Framework 2,0 ' de tanıtılan genel türler temelde, geliştiricilerin gerçek bir veri türüne işlemeden [tür açısından güvenli](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) veri yapıları tanımlamasına olanak sağlayan bir "kod şablonu" dir.</span><span class="sxs-lookup"><span data-stu-id="d00bd-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="d00bd-109">Örneğin,, <xref:System.Collections.Generic.List%601> veya gibi herhangi bir tür ile bildirilebilecek ve kullanılabilen [genel bir koleksiyondur](xref:System.Collections.Generic) `List<int>` `List<string>` `List<Person>` .</span><span class="sxs-lookup"><span data-stu-id="d00bd-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="d00bd-110">Genel türlerin neden yararlı olduğunu anlamak için, genel türleri eklemeden önce ve sonra belirli bir sınıfa göz atalım: <xref:System.Collections.ArrayList> .</span><span class="sxs-lookup"><span data-stu-id="d00bd-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="d00bd-111">.NET Framework 1,0 ' de `ArrayList` öğeler türündedir <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="d00bd-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="d00bd-112">Koleksiyona eklenen herhangi bir öğe sessizce bir öğesine dönüştürüldü `Object` .</span><span class="sxs-lookup"><span data-stu-id="d00bd-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="d00bd-113">Aynı durum, listedeki öğeleri okurken de gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="d00bd-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="d00bd-114">Bu işlem [kutulama ve kutudan](../csharp/programming-guide/types/boxing-and-unboxing.md)çıkarma olarak bilinir ve performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="d00bd-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="d00bd-115">Ancak, performans dışında, derleme zamanında listedeki verilerin türünü belirlemenin bir yolu yoktur ve bu da bazı kırılacak kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d00bd-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="d00bd-116">Genel türler, her liste örneğinin içereceği veri türünü tanımlayarak bu sorunu çözmez.</span><span class="sxs-lookup"><span data-stu-id="d00bd-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="d00bd-117">Örneğin, yalnızca öğesine tamsayılar ekleyebilir `List<int>` ve yalnızca kişileri ekleyebilirsiniz `List<Person>` .</span><span class="sxs-lookup"><span data-stu-id="d00bd-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="d00bd-118">Genel türler çalışma zamanında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d00bd-118">Generics are also available at run time.</span></span> <span data-ttu-id="d00bd-119">Çalışma zamanı, ne tür veri yapısını kullandığınızı bilir ve bunu bellekte daha verimli bir şekilde depolayabilirler.</span><span class="sxs-lookup"><span data-stu-id="d00bd-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="d00bd-120">Aşağıdaki örnek, çalışma zamanında veri yapısı türünü bilmenin verimliliğini gösteren küçük bir programdır:</span><span class="sxs-lookup"><span data-stu-id="d00bd-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

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

<span data-ttu-id="d00bd-121">Bu program aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="d00bd-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="d00bd-122">Burada fark ettiğiniz ilk şey, genel listenin sıralanması genel olmayan listeyi sıralamayla önemli ölçüde daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="d00bd-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="d00bd-123">Ayrıca genel liste türünün farklı olduğunu ([System. Int32]), ancak genel olmayan listenin türü Genelleştirilmiş olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d00bd-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="d00bd-124">Çalışma zamanı genel `List<int>` türünde olduğunu bildiğinden <xref:System.Int32> , liste öğelerini bellekte bir temel alınan tamsayı dizisinde saklayabilir, ancak genel olmayan `ArrayList` her liste öğesini bir nesneye atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d00bd-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="d00bd-125">Bu örnekte gösterildiği gibi, ek yayınlar zaman alır ve liste sıralamasını yavaşlatır.</span><span class="sxs-lookup"><span data-stu-id="d00bd-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="d00bd-126">Çalışma zamanının, genel sitenizin türünü bilmenin daha iyi bir avantajı, daha iyi bir hata ayıklama deneyimidir.</span><span class="sxs-lookup"><span data-stu-id="d00bd-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="d00bd-127">C# dilinde genel bir hata ayıklaması yaparken her bir öğenin veri yapınıza ne tür olduğunu öğrenmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="d00bd-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="d00bd-128">Genel türler olmadan, her öğe ne tür bir fikriniz yoktur.</span><span class="sxs-lookup"><span data-stu-id="d00bd-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="d00bd-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d00bd-129">See also</span></span>

- [<span data-ttu-id="d00bd-130">C# Programlama Kılavuzu-genel türler</span><span class="sxs-lookup"><span data-stu-id="d00bd-130">C# Programming Guide - Generics</span></span>](../csharp/programming-guide/generics/index.md)
