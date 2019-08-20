---
title: Zincirleme sorgularının performansı (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dfd7698d0bdd24a75458a581dfd42c3d21325e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591576"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Zincirleme sorgularının performansı (LINQ to XML) (C#)

LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincir sorgularının ve çok daha karmaşık bir sorgunun gerçekleştirebildiği bir işlemdir.

Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur. Örneğin, aşağıdaki basit kodda `query2` kaynağına sahiptir: `query1`

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

Bu örnek aşağıdaki çıktıyı üretir:

```
4
```

Bu zincirleme sorgu, bağlantılı bir liste ile yineleme ile aynı performans profilini sağlar.

- <xref:System.Xml.Linq.XContainer.Elements%2A> Eksen temelde, bağlantılı bir liste ile yineleme ile aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A>, ertelenmiş yürütme ile bir yineleyici olarak uygulanır. Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş. Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.

- İçinde `query1` <xref:System.Linq.Enumerable.Where%2A> , yantümcesorgununyöntemiçağırmasınısağlar.`where` Bu yöntem ayrıca bir yineleyici olarak uygulanır. Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur. Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır. Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzer.

- ' `query1`De, select yan tümcesi sorgunun <xref:System.Linq.Enumerable.Select%2A> yöntemi çağırmasını sağlar. Bu yöntem, <xref:System.Linq.Enumerable.Where%2A> yöntemiyle aynı performans profiline sahiptir.

- ' `query2`De, `where` yan tümcesi ve `select` `query1`yan tümcesi, ile aynı performans profiline sahiptir.

Bu nedenle yineleme `query2` , diğer bir deyişle, doğrusal saat olan ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır. Karşılık gelen bir Visual Basic örneği aynı performans profiline sahip olabilir.

Yineleyiciler hakkında daha fazla bilgi için bkz. [yield](../../../language-reference/keywords/yield.md).

Sorguları birlikte zincirlemeye yönelik daha ayrıntılı bir öğretici için bkz [. Öğretici: Sorguları birlikte](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)zincirleme.
