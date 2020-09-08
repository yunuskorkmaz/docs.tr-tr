---
title: Zincirleme sorgularının performansı-LINQ to XML
description: Zincirleme sorguları ve tek bir daha karmaşık sorgu hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: c1dae1eaf008a1f17c6884ef6b8e67d042719ad9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553093"
---
# <a name="performance-of-chained-queries-linq-to-xml"></a>Zincirleme sorguların performansı (LINQ to XML)

LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincirlenmiş sorguların yanı sıra zincirleme sorgulardan daha büyük ve daha karmaşık tek bir sorgu gerçekleştirebildiği bir işlemdir.

Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur. Örneğin, aşağıdaki basit kodda `query2` `query1` kaynağına sahiptir:

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

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
4
```

Bu zincirleme sorgu, bağlantılı bir liste ile yineleme ile aynı performans profilini sağlar.

- <xref:System.Xml.Linq.XContainer.Elements%2A>Eksen temelde, bağlantılı bir liste ile yineleme ile aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A> , ertelenmiş yürütme ile bir yineleyici olarak uygulanır. Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş. Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.
- `query1`' De, `where` yan tümce ( `Where` Visual Basic) sorgunun yöntemi çağırmasını sağlar <xref:System.Linq.Enumerable.Where%2A> . Bu yöntem ayrıca bir yineleyici olarak uygulanır. Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur. Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır. Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzerdir.
- `query1`' De, select yan tümcesi sorgunun yöntemi çağırmasını sağlar <xref:System.Linq.Enumerable.Select%2A> . Bu yöntem, yöntemiyle aynı performans profiline sahiptir <xref:System.Linq.Enumerable.Where%2A> .
- ' De `query2` , `where` yan tümcesinin ( `Where` Visual Basic) ve `select` yan tümcesindeki ' de ile aynı performans profili vardır `query1` .

`query2`Bu nedenle yineleme, diğer bir deyişle, doğrusal saat olan ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır.

Yineleyiciler hakkında daha fazla bilgi için bkz. [yield](../../csharp/language-reference/keywords/yield.md).

Sorguları birlikte zincirlemeye yönelik daha ayrıntılı bir öğretici için bkz. [öğretici: birlikte zinciri sorguları (C#)](chain-queries-example.md).
