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
# <a name="generic-types-overview"></a>Genel türlere genel bakış

Geliştiriciler, örtük olarak veya açık olsun, .NET 'te her zaman genel türler kullanır. .NET ' te LINQ kullandığınızda, ile çalıştığınızı fark muydunuz <xref:System.Collections.Generic.IEnumerable%601> ? Ya da Entity Framework kullanarak veritabanlarıyla iletişim için "genel deponun" çevrimiçi bir örneğini görüyorsanız, çoğu yöntemin geri döndüğünüzü gördünüz `IQueryable<T>` mi? **T** 'nin Bu örneklerde ne olduğunu ve neden orada olduğunu merak etmiş olabilirsiniz.

İlk olarak .NET Framework 2,0 ' de tanıtılan genel türler temelde, geliştiricilerin gerçek bir veri türüne işlemeden [tür açısından güvenli](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) veri yapıları tanımlamasına olanak sağlayan bir "kod şablonu" dir. Örneğin,, <xref:System.Collections.Generic.List%601> veya gibi herhangi bir tür ile bildirilebilecek ve kullanılabilen [genel bir koleksiyondur](xref:System.Collections.Generic) `List<int>` `List<string>` `List<Person>` .

Genel türlerin neden yararlı olduğunu anlamak için, genel türleri eklemeden önce ve sonra belirli bir sınıfa göz atalım: <xref:System.Collections.ArrayList> . .NET Framework 1,0 ' de `ArrayList` öğeler türündedir <xref:System.Object> . Koleksiyona eklenen herhangi bir öğe sessizce bir öğesine dönüştürüldü `Object` . Aynı durum, listedeki öğeleri okurken de gerçekleşir. Bu işlem [kutulama ve kutudan](../csharp/programming-guide/types/boxing-and-unboxing.md)çıkarma olarak bilinir ve performansı etkiler. Ancak, performans dışında, derleme zamanında listedeki verilerin türünü belirlemenin bir yolu yoktur ve bu da bazı kırılacak kod oluşturur. Genel türler, her liste örneğinin içereceği veri türünü tanımlayarak bu sorunu çözmez. Örneğin, yalnızca öğesine tamsayılar ekleyebilir `List<int>` ve yalnızca kişileri ekleyebilirsiniz `List<Person>` .

Genel türler çalışma zamanında da kullanılabilir. Çalışma zamanı, ne tür veri yapısını kullandığınızı bilir ve bunu bellekte daha verimli bir şekilde depolayabilirler.

Aşağıdaki örnek, çalışma zamanında veri yapısı türünü bilmenin verimliliğini gösteren küçük bir programdır:

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

Bu program aşağıdakine benzer bir çıktı üretir:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

Burada fark ettiğiniz ilk şey, genel listenin sıralanması genel olmayan listeyi sıralamayla önemli ölçüde daha hızlıdır. Ayrıca genel liste türünün farklı olduğunu ([System. Int32]), ancak genel olmayan listenin türü Genelleştirilmiş olduğunu fark edebilirsiniz. Çalışma zamanı genel `List<int>` türünde olduğunu bildiğinden <xref:System.Int32> , liste öğelerini bellekte bir temel alınan tamsayı dizisinde saklayabilir, ancak genel olmayan `ArrayList` her liste öğesini bir nesneye atamalısınız. Bu örnekte gösterildiği gibi, ek yayınlar zaman alır ve liste sıralamasını yavaşlatır.

Çalışma zamanının, genel sitenizin türünü bilmenin daha iyi bir avantajı, daha iyi bir hata ayıklama deneyimidir. C# dilinde genel bir hata ayıklaması yaparken her bir öğenin veri yapınıza ne tür olduğunu öğrenmiş olursunuz. Genel türler olmadan, her öğe ne tür bir fikriniz yoktur.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu-genel türler](../csharp/programming-guide/generics/index.md)
