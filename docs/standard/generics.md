---
title: Genel türler (genel türler) genel bakış
description: Taahhüt vermek zorunda kalmadan bir gerçek veri türü için tür açısından güvenli veri yapıları tanımlamanızı sağlayan kod şablonları nasıl genel türler gören öğrenin.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 1d1899d482738bc6cc9f638b6a74eab8d4ca70c1
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121187"
---
# <a name="generic-types-overview"></a>Genel türler genel bakış

Geliştiriciler genel türler, her zaman açık veya örtük olarak olup olmadığını,. NET'te kullanın. . NET'te LINQ kullandığınızda, hiç olmadığı kadar birlikte çalıştığınız fark ettiniz <xref:System.Collections.Generic.IEnumerable%601>? Veya, Entity Framework kullanan veritabanlarına konuşmak için hiç olmadığı kadar çevrimiçi bir örneği, bir "Genel deponun" gördüğünüz, pek çok yöntem Iqueryable dönüş gördünüz mü<T>? Hangi merak etmiş **T** Bu örnekler ve burada neden olduğu yer.

İlk .NET Framework 2.0 sürümünde sunulan **genel türler** aslında bir "code"şablonu"olan tanımlamak geliştiricilerinin sağlayan [tür kullanımı uyumlu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) olmadan yürüten bir gerçek veri türü için veri yapıları. Örneğin, <xref:System.Collections.Generic.List%601> olduğu bir [genel koleksiyon](xref:System.Collections.Generic) , bildirilebileceği ve herhangi bir türü ile gibi kullanılan `List<int>`, `List<string>`, veya `List<Person>`.

Genel türler neden yararlıdır anlamak için bir özel bir sınıf önce ve genel türler ekledikten sonra bakalım: <xref:System.Collections.ArrayList>. .NET Framework 1. 0'da, `ArrayList` öğe türü olan <xref:System.Object>. Bu geliyordu eklenen herhangi bir öğenin içine sessiz bir şekilde dönüştürülmüş bir `Object`. Aynı öğeler listeden okurken gerçekleşir. Bu işlem olarak bilinir [kutulama ve kutudan çıkarma](../csharp/programming-guide/types/boxing-and-unboxing.md), ve performansı etkiler. Birden çok, ancak derleme zamanında listesinde veri türünü belirlemek için hiçbir yolu yoktur. Bu, bazı kırılgan kodunu sağlar. Genel türler, her bir örneğin listesinin içereceği veri türünü tanımlayarak bu sorunu çözer. Örneğin, yalnızca tam sayılar ekleyebilirsiniz `List<int>` ve yalnızca kişilere ekleyin `List<Person>`.

Genel türler, ayrıca çalışma zamanında kullanılabilir. Başka bir deyişle, çalışma zamanının hangi türde veri yapısı, kullanmakta olduğunuz ve bellekte daha verimli bir şekilde depolayabilirsiniz bilir.

Aşağıdaki örnek veri olduğunu bilmesinin etkinliğini gösteren küçük bir program, yapı zamanında türü:

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

Bu program, aşağıdakine benzer bir çıktı üretir:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

İşte bu genel listeyi sıralamaya dikkat edin ilk şey, genel olmayan listenin sıralama daha önemli ölçüde daha hızlı. Genel olmayan listesi türünü genelleştirilmiş ise tür genel liste için farklı ([]),: System.Int32 olduğunu fark edebilirsiniz. Çalışma zamanı genel bildiğinden `List<int>` türünde <xref:System.Int32>, liste öğelerini genel olmayan sırasında bellekte temel alınan bir tamsayı dizisi olarak depolayabilir `ArrayList` her liste öğesinde bir nesneye dönüştürmek vardır. Bu örnekte gösterildiği gibi ek yayınları zaman ayırıp listesi sıralama aşağı yavaş.

Ek bir avantajı, genel tür bilerek çalışma zamanının daha iyi hata ayıklama bir deneyimdir. Genel C# hata ayıklama işlemi yaparken, her öğe türünü data yapınız bildirin. Genel türler hiçbir fikriniz her öğe türüne sahip.

## <a name="see-also"></a>Ayrıca bkz.

- [C# genel türlere giriş](https://msdn.microsoft.com/library/ms379564.aspx)
- [C# programlama kılavuzu - genel türler](../../docs/csharp/programming-guide/generics/index.md)
