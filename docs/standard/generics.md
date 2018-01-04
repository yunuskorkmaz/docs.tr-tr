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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f36bae495631db68afb1404398cbf43e890d4f33
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="generic-types-generics-overview"></a>Genel türleri (genel türler) genel bakış

Genel türler her zaman C# ' ta örtük veya açık olarak olup olmadığını kullanırız. LINQ C# ' ta kullandığınızda, size herhangi bir zamanda IEnumerable çalıştığınız fark ettiniz<T>? Veya veritabanlarını Entity Framework kullanarak Konuşmayı için "Genel repository" çevrimiçi bir örneği'ni şimdiye kadar görürseniz, çoğu yöntemleri Iqueryable döndürür gördünüz mü<T>? Hangi hiç merak ettiniz **T** Bu örnekler ve neden var olduğunu?

.NET Framework 2.0, C# dili ve ortak dil çalışma zamanı (CLR) söz konusu değişiklikler genel türler için ilk kez kullanıma sunuldu. **Genel türler** aslında bir "kod şablonu" olan tanımlamak geliştiricilere sağlayan [tür kullanımı uyumlu](https://msdn.microsoft.com/library/hbzz1a9a.aspx) gerçek veri türü için yürüten olmadan veri yapılarını. Örneğin, `List<T>` olan bir [genel koleksiyon](xref:System.Collections.Generic) , kullanılabilir bildirilen ve herhangi bir türü ile kullanılan: `List<int>`, `List<string>`, `List<Person>`vb.

Bu nedenle, noktası nedir? Genel türler neden yararlıdır? Bu anlamak için kimliğinizi önce ve genel türler ekledikten sonra belirli bir sınıf göz atın gerekiyor. Bakalım `ArrayList`. C# 1.0, `ArrayList` öğe türü olan `object`. Bu eklenmiş olan herhangi bir öğe içine sessizce dönüştürüldü geliyordu bir `object`; aynı şey öğeleri listeden okuma (Bu işlem olarak bilinir [kutulama](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) ve sırasıyla kutudan çıkarma). Kutulama ve kutudan çıkarma performansını etkiler. Birden fazla ancak gerçek tür listesinde veri nedir derleme zamanında bildirmek için yolu yoktur. Bu, bazı kırılacak kodunu hale getirir. Genel türler listesinin her örneğin içereceği veri türünü ek bilgileri sağlayarak bu sorunu çözün. Basitçe, tamsayılara yalnızca ekleyebilirsiniz `List<int>` ve yalnızca kişilere Ekle `List<Person>`, vb.

Genel türler kullanılabilir ayrıca çalışma zamanında veya **reified**. Başka bir deyişle, çalışma zamanı ne tür bir veri yapısı, kullanmakta olduğunuz ve bellekte daha verimli bir şekilde depolayabilir bilir.

Veri bilmesinin verimlilik gösterilmiştir küçük bir program İşte yapı çalışma zamanında tür:

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

Bu program şu çıkışı üretir:

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

İşte bu genel listenin sıralama fark ilk şey için genel olmayan listesi önemli ölçüde daha hızlıdır. Genel olmayan liste türü genelleştirilmiş oysa türü genel listesi için ayrı ([System.Int32]) olduğuna dikkat edin de. Çalışma zamanı genel bildiği için `List<int>` olan int türünde, bu liste öğelerini genel olmayan bellek temel alınan bir tamsayı dizide depolayabilirsiniz `ArrayList` bir nesne dizisinin bellekte depolanır gibi bir nesne olarak her liste öğesi yayınlanamıyor sahiptir. Bu örnek ile gösterildiği gibi ek nesnesiyle sürebilir ve listesi sıralama aşağı yavaş.

Son yararlı, genel türde bilerek çalışma zamanı hakkında daha iyi hata ayıklama deneyimini şeydir. C# genel ayıklarken her öğe, veri yapısında türünü bilmeniz. Genel türler, hiçbir fikir her öğenin ne tür gerekir.

## <a name="further-reading-and-resources"></a>Daha fazla bilgi ve kaynaklar

*   [C# genel türlere giriş](https://msdn.microsoft.com/library/ms379564.aspx)
*   [C# programlama kılavuzu - genel türler](../../docs/csharp/programming-guide/generics/index.md)
