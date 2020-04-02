---
title: Genel türler (genel bilgiler) genel bakış
description: Genel olarak, gerçek bir veri türüne bağlanmadan tür güvenliğine uygun veri yapılarını tanımlamanıza olanak tanıyan kod şablonları olarak nasıl davrandığını öğrenin.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 0188e620a45462e7cc31391406ade9d57b1b0220
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588475"
---
# <a name="generic-types-overview"></a><span data-ttu-id="8749d-103">Genel türlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="8749d-103">Generic types overview</span></span>

<span data-ttu-id="8749d-104">Geliştiriciler genel jenerikleri .NET'te her zaman, ister örtülü ister açık olarak kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="8749d-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="8749d-105">.NET'te LINQ kullandığınızda, birlikte <xref:System.Collections.Generic.IEnumerable%601>çalıştığınızı fark ettin mi?</span><span class="sxs-lookup"><span data-stu-id="8749d-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="8749d-106">Ya da Varlık Çerçevesi'ni kullanarak veritabanlarıyla konuşmak için "genel depo" içeren çevrimiçi bir örnek `IQueryable<T>`gördüyseniz, çoğu yöntemin geri döndüğünü gördünüz mü?</span><span class="sxs-lookup"><span data-stu-id="8749d-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="8749d-107">Bu örneklerde **T'nin** ne olduğunu ve neden orada olduğunu merak etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8749d-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="8749d-108">İlk olarak .NET Framework 2.0'da tanıtılan genel bilgiler, geliştiricilerin gerçek bir veri türüne bağlanmadan [tür egelenebilir](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) veri yapılarını tanımlamasına olanak tanıyan bir "kod şablonu"dur.</span><span class="sxs-lookup"><span data-stu-id="8749d-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="8749d-109"><xref:System.Collections.Generic.List%601> Örneğin, beyan edilebilen ve herhangi bir türle kullanılabilen `List<string>`genel `List<Person>`bir [koleksiyondur,](xref:System.Collections.Generic) `List<int>`örneğin , , veya .</span><span class="sxs-lookup"><span data-stu-id="8749d-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="8749d-110">Jeneriklerin neden yararlı olduğunu anlamak için, jenerik eklemeden önce ve <xref:System.Collections.ArrayList>sonra belirli bir sınıfa göz atalım: .</span><span class="sxs-lookup"><span data-stu-id="8749d-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="8749d-111">.NET Framework 1.0'da `ArrayList` elemanlar türdedir. <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="8749d-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="8749d-112">Bu, eklenen herhangi bir öğenin sessizce bir `Object`.</span><span class="sxs-lookup"><span data-stu-id="8749d-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="8749d-113">Aynı listedeki öğeleri okurken de olur.</span><span class="sxs-lookup"><span data-stu-id="8749d-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="8749d-114">Bu [işlem, kutulama ve unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)olarak bilinir ve performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="8749d-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="8749d-115">Ancak bundan daha fazlası, derleme zamanında listedeki veri türünü belirlemenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="8749d-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="8749d-116">Bu bazı kırılgan kod için yapar.</span><span class="sxs-lookup"><span data-stu-id="8749d-116">This makes for some fragile code.</span></span> <span data-ttu-id="8749d-117">Genel ler, listenin her örneğinin içereceği veri türünü tanımlayarak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="8749d-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="8749d-118">Örneğin, yalnızca sensager ekleyebilir `List<int>` ve yalnızca `List<Person>`Kişiler'e ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8749d-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="8749d-119">Jenerikler çalışma zamanında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8749d-119">Generics are also available at run time.</span></span> <span data-ttu-id="8749d-120">Bu, çalışma zamanının ne tür bir veri yapısı kullandığınızı bildiği ve bellekte daha verimli bir şekilde depolayabildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8749d-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="8749d-121">Aşağıdaki örnek, çalışma zamanında veri yapısı türünü bilmenin verimliliğini gösteren küçük bir programdır:</span><span class="sxs-lookup"><span data-stu-id="8749d-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

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

<span data-ttu-id="8749d-122">Bu program aşağıdakilere benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="8749d-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="8749d-123">Burada fark edebilirsiniz ilk şey, genel liste sıralama önemli ölçüde genel olmayan liste sıralama daha hızlı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8749d-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="8749d-124">Ayrıca, genel liste için yazın farklı olduğunu da fark edebilirsiniz ([System.Int32]), genel olmayan liste için tür genelleştirilmiş ise.</span><span class="sxs-lookup"><span data-stu-id="8749d-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="8749d-125">Çalışma zamanı genel in `List<int>` türünün <xref:System.Int32>genel olduğunu bildiğinden, liste öğelerini bellekte altta yatan bir `ArrayList` arayıcı dizisinde depolayabilirken, genel olmayan ların her liste öğesini bir nesneye dökmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8749d-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="8749d-126">Bu örnekte de görüldüğü gibi, ekstra dökümler zaman alır ve liste sıralamasını yavaşlatıyor.</span><span class="sxs-lookup"><span data-stu-id="8749d-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="8749d-127">Genel ürününüzün türünü bilmenin çalışma zamanının ek bir avantajı da daha iyi bir hata ayıklama deneyimidir.</span><span class="sxs-lookup"><span data-stu-id="8749d-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="8749d-128">C#'da bir genel hata ayıklama yaparken, veri yapınızda her öğenin türünde olduğunu bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8749d-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="8749d-129">Jenerik olmadan, her öğenin türü hakkında hiçbir fikriniz olmazdı.</span><span class="sxs-lookup"><span data-stu-id="8749d-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="8749d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8749d-130">See also</span></span>

- [<span data-ttu-id="8749d-131">C# Programlama Kılavuzu - Genel</span><span class="sxs-lookup"><span data-stu-id="8749d-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
