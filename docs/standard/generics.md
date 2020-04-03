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
# <a name="generic-types-overview"></a>Genel türlere genel bakış

Geliştiriciler genel jenerikleri .NET'te her zaman, ister örtülü ister açık olarak kullanırlar. .NET'te LINQ kullandığınızda, birlikte <xref:System.Collections.Generic.IEnumerable%601>çalıştığınızı fark ettin mi? Ya da Varlık Çerçevesi'ni kullanarak veritabanlarıyla konuşmak için "genel depo" içeren çevrimiçi bir örnek `IQueryable<T>`gördüyseniz, çoğu yöntemin geri döndüğünü gördünüz mü? Bu örneklerde **T'nin** ne olduğunu ve neden orada olduğunu merak etmiş olabilirsiniz.

İlk olarak .NET Framework 2.0'da tanıtılan genel bilgiler, geliştiricilerin gerçek bir veri türüne bağlanmadan [tür egelenebilir](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) veri yapılarını tanımlamasına olanak tanıyan bir "kod şablonu"dur. <xref:System.Collections.Generic.List%601> Örneğin, beyan edilebilen ve herhangi bir türle kullanılabilen `List<string>`genel `List<Person>`bir [koleksiyondur,](xref:System.Collections.Generic) `List<int>`örneğin , , veya .

Jeneriklerin neden yararlı olduğunu anlamak için, jenerik eklemeden önce ve <xref:System.Collections.ArrayList>sonra belirli bir sınıfa göz atalım: . .NET Framework 1.0'da `ArrayList` elemanlar türdedir. <xref:System.Object> Koleksiyona eklenen herhangi bir öğe sessizce `Object`bir . Aynı listedeki öğeleri okurken de olur. Bu [işlem, kutulama ve unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)olarak bilinir ve performansı etkiler. Ancak performans dışında, derleme zamanında listedeki veri türünü belirlemenin bir yolu yoktur, bu da bazı kırılgan kodlar sağlar. Genel ler, listenin her örneğinin içereceği veri türünü tanımlayarak bu sorunu çözer. Örneğin, yalnızca sensager ekleyebilir `List<int>` ve yalnızca `List<Person>`Kişiler'e ekleyebilirsiniz.

Jenerikler çalışma zamanında da kullanılabilir. Çalışma zamanı, ne tür bir veri yapısı kullandığınızı bilir ve bellekte daha verimli bir şekilde depolayabilir.

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

Burada fark edebilirsiniz ilk şey, genel liste sıralama önemli ölçüde genel olmayan liste sıralama daha hızlı olmasıdır. Ayrıca, genel liste için yazın farklı olduğunu da fark edebilirsiniz ([System.Int32]), genel olmayan liste için tür genelleştirilmiş ise. Çalışma zamanı genel in `List<int>` türünün <xref:System.Int32>genel olduğunu bildiğinden, liste öğelerini bellekte altta yatan bir `ArrayList` arayıcı dizisinde depolayabilirken, genel olmayan ların her liste öğesini bir nesneye dökmesi gerekir. Bu örnekte de görüldüğü gibi, ekstra dökümler zaman alır ve liste sıralamasını yavaşlatıyor.

Genel ürününüzün türünü bilmenin çalışma zamanının ek bir avantajı da daha iyi bir hata ayıklama deneyimidir. C#'da bir genel hata ayıklama yaparken, veri yapınızda her öğenin türünde olduğunu bilirsiniz. Jenerik olmadan, her öğenin türü hakkında hiçbir fikriniz olmazdı.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu - Genel](../../docs/csharp/programming-guide/generics/index.md)
