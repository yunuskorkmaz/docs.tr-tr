---
title: Zincirlenmiş Sorguların Performansı (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 15cb9f94a49600c221b0cbb246743a79e9a5297b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353130"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Zincirleme sorgularının performansı (LINQ to XML) (Visual Basic)

LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincir sorgularının ve çok daha karmaşık bir sorgunun gerçekleştirebildiği bir işlemdir.

Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur. Örneğin, aşağıdaki basit kodda, `query1` kaynağı olarak `query2`:

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

Bu örnek aşağıdaki çıktıyı üretir:

```console
4
```

Bu zincirleme sorgu, bağlantılı bir liste ile yineleme ile aynı performans profilini sağlar.

- <xref:System.Xml.Linq.XContainer.Elements%2A> eksen temelde, bağlantılı bir liste ile yineleme ile aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A>, ertelenmiş yürütme ile bir yineleyici olarak uygulanır. Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş. Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.

- `query1`, `Where` yan tümcesi sorgunun <xref:System.Linq.Enumerable.Where%2A> yöntemini çağırmasını sağlar. Bu yöntem ayrıca bir yineleyici olarak uygulanır. Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur. Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır. Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzer.

- `query1`, select yan tümcesi sorgunun <xref:System.Linq.Enumerable.Select%2A> metodunu çağırmasını sağlar. Bu yöntemin <xref:System.Linq.Enumerable.Where%2A> yöntemiyle aynı performans profili vardır.

- `query2`, hem `Where` yan tümcesi hem de `Select` yan tümcesi `query1`ile aynı performans profiline sahiptir.

 `query2` yoluyla yineleme, diğer bir deyişle, doğrusal zaman içinde ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
