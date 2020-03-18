---
title: Zincirli Sorguların Performansı (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253117"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Zincirli Sorguların Performansı (LINQ - XML) (C#)

LINQ'un (ve LINQ'dan XML'e) en önemli avantajlarından biri, zincirli sorguların yanı sıra tek bir daha büyük, daha karmaşık sorguyu gerçekleştirebiliyor olmasıdır.

Zincirlenmiş sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur. Örneğin, aşağıdaki basit kod, `query2` `query1` kaynağı olarak vardır:

```csharp
XElement root = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    new XElement("Child", 3),
    new XElement("Child", 4)
);

var query1 = from x in root.Elements("Child")
             where (int)x >= 3
             select x;

var query2 = from e in query1
             where (int)e % 2 == 0
             select e;

foreach (var i in query2)
    Console.WriteLine("{0}", (int)i);
```

Bu örnek, aşağıdaki çıktıyı üretir:

```output
4
```

Bu zincirleme sorgu, bağlantılı bir liste üzerinden yinelenen aynı performans profilini sağlar.

- Eksen, <xref:System.Xml.Linq.XContainer.Elements%2A> bağlantılı bir liste boyunca yinelenmeyle temelde aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A>ertelenmiş yürütme ile bir yineleyici olarak uygulanır. Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı liste yi yinelemeye ek olarak bazı işler yaptığı anlamına gelir. Bu çalışma iki kategoriye ayrılabilir: yineleyicinin ayarlandığı anda yapılan iş ve her yineleme sırasında yapılan iş. Kurulum çalışması küçük, sabit bir çalışma miktarıdır ve her yineleme sırasında yapılan iş kaynak koleksiyonundaki madde sayısıyla orantılıdır.

- In `query1`, `where` yan tümcesi <xref:System.Linq.Enumerable.Where%2A> sorgu yöntemi aramak için neden olur. Bu yöntem aynı zamanda bir yineleyici olarak da uygulanır. Kurulum çalışması, lambda ifadesine başvurulacak temsilcinin yanı sıra bir yineleyici için normal kurulumun anlık olarak düzenlenmesinden oluşur. Her yinelemede, temsilci yüklemi yürütmek için çağrılır. Kurulum çalışması ve her yineleme sırasında yapılan iş, eksen üzerinden yineleme yaparken yapılan işe benzer.

- 'de, `query1`select yan tümcesi sorgunun yöntemi ni aramasına <xref:System.Linq.Enumerable.Select%2A> neden olur. Bu yöntem, yöntemle aynı <xref:System.Linq.Enumerable.Where%2A> performans profiline sahiptir.

- In `query2`, `where` hem yan `select` tümcesi hem `query1`de yan tümcesi aynı performans profiline sahiptir.

Bu nedenle yineleme, ilk sorgunun kaynağındaki madde sayısıyla, başka bir deyişle doğrusal zamanla doğrusal olarak doğrusal olarak `query2` orantılıdır. İlgili Visual Basic örneği aynı performans profiline sahip olur.

Yineleyiciler hakkında daha fazla bilgi için [bkz.](../../../language-reference/keywords/yield.md)

Sorguları birbirine zincirleme konusunda daha ayrıntılı bir öğretici için [Bkz. Öğretici: Sorguları Birlikte Zincirleme.](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
