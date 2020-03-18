---
title: Genel türler (genel bilgiler) genel bakış
description: Genel olarak, gerçek bir veri türüne bağlanmadan tür güvenliğine uygun veri yapılarını tanımlamanıza olanak tanıyan kod şablonları olarak nasıl davrandığını öğrenin.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 3c1181f5be717f328ae906c6009fc8a34b904c89
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61923857"
---
# <a name="generic-types-overview"></a>Genel türlere genel bakış

Geliştiriciler genel jenerikleri .NET'te her zaman, ister örtülü ister açık olarak kullanırlar. .NET'te LINQ kullandığınızda, birlikte <xref:System.Collections.Generic.IEnumerable%601>çalıştığınızı fark ettin mi? Ya da varlık framework kullanarak veritabanları konuşmak için bir "genel depo" bir online örnek gördüm, çoğu yöntem\<iQueryable T> dönmek gördünüz mü? Bu örneklerde **T'nin** ne olduğunu ve neden orada olduğunu merak etmiş olabilirsiniz.

İlk olarak .NET Framework 2.0'da tanıtılan **genel** bilgiler, geliştiricilerin gerçek bir veri türüne bağlanmadan [tür egelenebilir](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) veri yapılarını tanımlamasına olanak tanıyan bir "kod şablonu"dur. <xref:System.Collections.Generic.List%601> Örneğin, beyan edilebilen ve herhangi bir türle kullanılabilen `List<string>`genel `List<Person>`bir [koleksiyondur,](xref:System.Collections.Generic) `List<int>`örneğin , , veya .

Jeneriklerin neden yararlı olduğunu anlamak için, jenerik eklemeden önce ve <xref:System.Collections.ArrayList>sonra belirli bir sınıfa göz atalım: . .NET Framework 1.0'da `ArrayList` elemanlar türdedir. <xref:System.Object> Bu, eklenen herhangi bir öğenin sessizce bir `Object`. Aynı listedeki öğeleri okurken de olur. Bu [işlem, kutulama ve unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)olarak bilinir ve performansı etkiler. Ancak bundan daha fazlası, derleme zamanında listedeki veri türünü belirlemenin bir yolu yoktur. Bu bazı kırılgan kod için yapar. Genel ler, listenin her örneğinin içereceği veri türünü tanımlayarak bu sorunu çözer. Örneğin, yalnızca sensager ekleyebilir `List<int>` ve yalnızca `List<Person>`Kişiler'e ekleyebilirsiniz.

Jenerikler çalışma zamanında da kullanılabilir. Bu, çalışma zamanının ne tür bir veri yapısı kullandığınızı bildiği ve bellekte daha verimli bir şekilde depolayabildiği anlamına gelir.

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

Bu program aşağıdakilere benzer çıktı üretir:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

Burada fark edebilirsiniz ilk şey, genel liste sıralama önemli ölçüde genel olmayan liste sıralama daha hızlı olmasıdır. Ayrıca, genel liste için yazın farklı olduğunu da fark edebilirsiniz ([System.Int32]), genel olmayan liste için tür genelleştirilmiş ise. Çalışma zamanı genel in `List<int>` türünün <xref:System.Int32>genel olduğunu bildiğinden, genel `ArrayList` olmayan her liste öğesini bir nesneye dökmek zorunda iken liste öğelerini bellekte altta yatan bir sonraki seger dizisinde depolayabilir. Bu örnekte de görüldüğü gibi, ekstra dökümler zaman alır ve liste sıralamasını yavaşlatıyor.

Genel ürününüzün türünü bilmenin çalışma zamanının ek bir avantajı da daha iyi bir hata ayıklama deneyimidir. C#'da bir genel hata ayıklama yaparken, veri yapınızda her öğenin türünde olduğunu bilirsiniz. Jenerik olmadan, her öğenin türü hakkında hiçbir fikriniz olmazdı.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu - Genel](../../docs/csharp/programming-guide/generics/index.md)
