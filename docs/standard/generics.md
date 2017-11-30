---
title: "Genel türleri (genel türler) genel bakış"
description: "Tür kullanımı uyumlu veri yapılarını gerçek veri türü için kaydetmeden tanımlamanıza izin kodu şablonları nasıl genel türler görür öğrenin."
keywords: .NET, .NET core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: 08b8de2fe17a0032a1c1180667f39b1d6ce0feb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="generic-types-generics-overview"></a><span data-ttu-id="d1b64-104">Genel türleri (genel türler) genel bakış</span><span class="sxs-lookup"><span data-stu-id="d1b64-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="d1b64-105">Genel türler her zaman C# ' ta örtük veya açık olarak olup olmadığını kullanırız.</span><span class="sxs-lookup"><span data-stu-id="d1b64-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="d1b64-106">LINQ C# ' ta kullandığınızda, size herhangi bir zamanda IEnumerable çalıştığınız fark ettiniz<T>?</span><span class="sxs-lookup"><span data-stu-id="d1b64-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="d1b64-107">Veya veritabanlarını Entity Framework kullanarak Konuşmayı için "Genel repository" çevrimiçi bir örneği'ni şimdiye kadar görürseniz, çoğu yöntemleri Iqueryable döndürür gördünüz mü<T>?</span><span class="sxs-lookup"><span data-stu-id="d1b64-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="d1b64-108">Hangi hiç merak ettiniz **T** Bu örnekler ve neden var olduğunu?</span><span class="sxs-lookup"><span data-stu-id="d1b64-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="d1b64-109">.NET Framework 2.0, C# dili ve ortak dil çalışma zamanı (CLR) söz konusu değişiklikler genel türler için ilk kez kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="d1b64-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="d1b64-110">**Genel türler** aslında bir "kod şablonu" olan tanımlamak geliştiricilere sağlayan [tür kullanımı uyumlu](https://msdn.microsoft.com/library/hbzz1a9a.aspx) gerçek veri türü için yürüten olmadan veri yapılarını.</span><span class="sxs-lookup"><span data-stu-id="d1b64-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="d1b64-111">Örneğin, `List<T>` olan bir [genel koleksiyon](xref:System.Collections.Generic) , kullanılabilir bildirilen ve herhangi bir türü ile kullanılan: `List<int>`, `List<string>`, `List<Person>`vb.</span><span class="sxs-lookup"><span data-stu-id="d1b64-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="d1b64-112">Bu nedenle, noktası nedir?</span><span class="sxs-lookup"><span data-stu-id="d1b64-112">So, what’s the point?</span></span> <span data-ttu-id="d1b64-113">Genel türler neden yararlıdır?</span><span class="sxs-lookup"><span data-stu-id="d1b64-113">Why are generics useful?</span></span> <span data-ttu-id="d1b64-114">Bu anlamak için kimliğinizi önce ve genel türler ekledikten sonra belirli bir sınıf göz atın gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="d1b64-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="d1b64-115">Bakalım `ArrayList`.</span><span class="sxs-lookup"><span data-stu-id="d1b64-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="d1b64-116">C# 1.0, `ArrayList` öğe türü olan `object`.</span><span class="sxs-lookup"><span data-stu-id="d1b64-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="d1b64-117">Bu eklenmiş olan herhangi bir öğe içine sessizce dönüştürüldü geliyordu bir `object`; aynı şey öğeleri listeden okuma (Bu işlem olarak bilinir [kutulama](https://msdn.microsoft.com/library/yz2be5wk.aspx) ve sırasıyla kutudan çıkarma).</span><span class="sxs-lookup"><span data-stu-id="d1b64-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) and unboxing respectively).</span></span> <span data-ttu-id="d1b64-118">Kutulama ve kutudan çıkarma performansını etkiler.</span><span class="sxs-lookup"><span data-stu-id="d1b64-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="d1b64-119">Birden fazla ancak gerçek tür listesinde veri nedir derleme zamanında bildirmek için yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="d1b64-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="d1b64-120">Bu, bazı kırılacak kodunu hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d1b64-120">This makes for some fragile code.</span></span> <span data-ttu-id="d1b64-121">Genel türler listesinin her örneğin içereceği veri türünü ek bilgileri sağlayarak bu sorunu çözün.</span><span class="sxs-lookup"><span data-stu-id="d1b64-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="d1b64-122">Basitçe, tamsayılara yalnızca ekleyebilirsiniz `List<int>` ve yalnızca kişilere Ekle `List<Person>`, vb.</span><span class="sxs-lookup"><span data-stu-id="d1b64-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="d1b64-123">Genel türler kullanılabilir ayrıca çalışma zamanında veya **reified**.</span><span class="sxs-lookup"><span data-stu-id="d1b64-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="d1b64-124">Başka bir deyişle, çalışma zamanı ne tür bir veri yapısı, kullanmakta olduğunuz ve bellekte daha verimli bir şekilde depolayabilir bilir.</span><span class="sxs-lookup"><span data-stu-id="d1b64-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="d1b64-125">Veri bilmesinin verimlilik gösterilmiştir küçük bir program İşte yapı çalışma zamanında tür:</span><span class="sxs-lookup"><span data-stu-id="d1b64-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="d1b64-126">Bu program şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="d1b64-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="d1b64-127">İşte bu genel listenin sıralama fark ilk şey için genel olmayan listesi önemli ölçüde daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="d1b64-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="d1b64-128">Genel olmayan liste türü genelleştirilmiş oysa türü genel listesi için ayrı ([System.Int32]) olduğuna dikkat edin de.</span><span class="sxs-lookup"><span data-stu-id="d1b64-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="d1b64-129">Çalışma zamanı genel bildiği için `List<int>` olan int türünde, bu liste öğelerini genel olmayan bellek temel alınan bir tamsayı dizide depolayabilirsiniz `ArrayList` bir nesne dizisinin bellekte depolanır gibi bir nesne olarak her liste öğesi yayınlanamıyor sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d1b64-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="d1b64-130">Bu örnek ile gösterildiği gibi ek nesnesiyle sürebilir ve listesi sıralama aşağı yavaş.</span><span class="sxs-lookup"><span data-stu-id="d1b64-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="d1b64-131">Son yararlı, genel türde bilerek çalışma zamanı hakkında daha iyi hata ayıklama deneyimini şeydir.</span><span class="sxs-lookup"><span data-stu-id="d1b64-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="d1b64-132">C# genel ayıklarken her öğe, veri yapısında türünü bilmeniz.</span><span class="sxs-lookup"><span data-stu-id="d1b64-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="d1b64-133">Genel türler, hiçbir fikir her öğenin ne tür gerekir.</span><span class="sxs-lookup"><span data-stu-id="d1b64-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="d1b64-134">Daha fazla bilgi ve kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d1b64-134">Further reading and resources</span></span>

*   [<span data-ttu-id="d1b64-135">C# genel türlere giriş</span><span class="sxs-lookup"><span data-stu-id="d1b64-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="d1b64-136">C# programlama kılavuzu - genel türler</span><span class="sxs-lookup"><span data-stu-id="d1b64-136">C# Programming Guide - Generics</span></span>](https://msdn.microsoft.com/library/512aeb7t.aspx)
