---
title: Genel türler (genel bilgiler) genel bakış
description: Genel olarak, gerçek bir veri türüne bağlanmadan tür güvenliğine uygun veri yapılarını tanımlamanıza olanak tanıyan kod şablonları olarak nasıl davrandığını öğrenin.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: f51d69088b0d5c798f3aa3a6c1f5b62b3ea81d39
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635279"
---
# <a name="generic-types-overview"></a><span data-ttu-id="31025-103">Genel türlere genel bakış</span><span class="sxs-lookup"><span data-stu-id="31025-103">Generic types overview</span></span>

<span data-ttu-id="31025-104">Geliştiriciler genel jenerikleri .NET'te her zaman, ister örtülü ister açık olarak kullanırlar.</span><span class="sxs-lookup"><span data-stu-id="31025-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="31025-105">.NET'te LINQ kullandığınızda, birlikte <xref:System.Collections.Generic.IEnumerable%601>çalıştığınızı fark ettin mi?</span><span class="sxs-lookup"><span data-stu-id="31025-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="31025-106">Ya da Varlık Çerçevesi'ni kullanarak veritabanlarıyla konuşmak için "genel depo" içeren çevrimiçi bir örnek `IQueryable<T>`gördüyseniz, çoğu yöntemin geri döndüğünü gördünüz mü?</span><span class="sxs-lookup"><span data-stu-id="31025-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="31025-107">Bu örneklerde **T'nin** ne olduğunu ve neden orada olduğunu merak etmiş olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31025-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="31025-108">İlk olarak .NET Framework 2.0'da tanıtılan genel bilgiler, geliştiricilerin gerçek bir veri türüne bağlanmadan [tür egelenebilir](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) veri yapılarını tanımlamasına olanak tanıyan bir "kod şablonu"dur.</span><span class="sxs-lookup"><span data-stu-id="31025-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="31025-109"><xref:System.Collections.Generic.List%601> Örneğin, beyan edilebilen ve herhangi bir türle kullanılabilen `List<string>`genel `List<Person>`bir [koleksiyondur,](xref:System.Collections.Generic) `List<int>`örneğin , , veya .</span><span class="sxs-lookup"><span data-stu-id="31025-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="31025-110">Jeneriklerin neden yararlı olduğunu anlamak için, jenerik eklemeden önce ve <xref:System.Collections.ArrayList>sonra belirli bir sınıfa göz atalım: .</span><span class="sxs-lookup"><span data-stu-id="31025-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="31025-111">.NET Framework 1.0'da `ArrayList` elemanlar türdedir. <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="31025-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="31025-112">Koleksiyona eklenen herhangi bir öğe sessizce `Object`bir .</span><span class="sxs-lookup"><span data-stu-id="31025-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="31025-113">Aynı listedeki öğeleri okurken de olur.</span><span class="sxs-lookup"><span data-stu-id="31025-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="31025-114">Bu [işlem, kutulama ve unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)olarak bilinir ve performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="31025-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="31025-115">Ancak performans dışında, derleme zamanında listedeki veri türünü belirlemenin bir yolu yoktur, bu da bazı kırılgan kodlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="31025-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="31025-116">Genel ler, listenin her örneğinin içereceği veri türünü tanımlayarak bu sorunu çözer.</span><span class="sxs-lookup"><span data-stu-id="31025-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="31025-117">Örneğin, yalnızca sensager ekleyebilir `List<int>` ve yalnızca `List<Person>`Kişiler'e ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31025-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="31025-118">Jenerikler çalışma zamanında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31025-118">Generics are also available at run time.</span></span> <span data-ttu-id="31025-119">Çalışma zamanı, ne tür bir veri yapısı kullandığınızı bilir ve bellekte daha verimli bir şekilde depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="31025-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="31025-120">Aşağıdaki örnek, çalışma zamanında veri yapısı türünü bilmenin verimliliğini gösteren küçük bir programdır:</span><span class="sxs-lookup"><span data-stu-id="31025-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

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

<span data-ttu-id="31025-121">Bu program aşağıdakilere benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="31025-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="31025-122">Burada fark edebilirsiniz ilk şey, genel liste sıralama önemli ölçüde genel olmayan liste sıralama daha hızlı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="31025-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="31025-123">Ayrıca, genel liste için yazın farklı olduğunu da fark edebilirsiniz ([System.Int32]), genel olmayan liste için tür genelleştirilmiş ise.</span><span class="sxs-lookup"><span data-stu-id="31025-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="31025-124">Çalışma zamanı genel in `List<int>` türünün <xref:System.Int32>genel olduğunu bildiğinden, liste öğelerini bellekte altta yatan bir `ArrayList` arayıcı dizisinde depolayabilirken, genel olmayan ların her liste öğesini bir nesneye dökmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="31025-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="31025-125">Bu örnekte de görüldüğü gibi, ekstra dökümler zaman alır ve liste sıralamasını yavaşlatıyor.</span><span class="sxs-lookup"><span data-stu-id="31025-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="31025-126">Genel ürününüzün türünü bilmenin çalışma zamanının ek bir avantajı da daha iyi bir hata ayıklama deneyimidir.</span><span class="sxs-lookup"><span data-stu-id="31025-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="31025-127">C#'da bir genel hata ayıklama yaparken, veri yapınızda her öğenin türünde olduğunu bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31025-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="31025-128">Jenerik olmadan, her öğenin türü hakkında hiçbir fikriniz olmazdı.</span><span class="sxs-lookup"><span data-stu-id="31025-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="31025-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31025-129">See also</span></span>

- [<span data-ttu-id="31025-130">C# Programlama Kılavuzu - Genel</span><span class="sxs-lookup"><span data-stu-id="31025-130">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
