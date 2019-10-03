---
title: Zincirleme sorgularının performansı (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 69ed09addb50ac45e7b46cd0322d4df076b5875b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834960"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Zincirleme sorgularının performansı (LINQ to XML) (Visual Basic)

LINQ 'in (ve LINQ to XML) en önemli avantajlarından biri, zincir sorgularının ve çok daha karmaşık bir sorgunun gerçekleştirebildiği bir işlemdir.

Zincirleme sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur. Örneğin, aşağıdaki basit kodda `query2`, kaynağı olarak `query1` ' dir:

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

- @No__t-0 ekseni temelde bağlı bir liste ile yineleme ile aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A>, ertelenmiş yürütme ile bir yineleyici olarak uygulanır. Bu, yineleyici nesnesini ayırma ve yürütme durumunu izleme gibi bağlantılı listede yineleme yapmak için ek olarak bir iş yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyicinin ayarlandığı sırada gerçekleştirilen iş ve her yineleme sırasında gerçekleştirilen iş. Kurulum işi küçük, sabit bir iş miktarı ve her yineleme sırasında yapılan iş, kaynak koleksiyondaki öğelerin sayısıyla orantılıdır.

- @No__t-0 ' da `Where` yan tümcesi sorgunun <xref:System.Linq.Enumerable.Where%2A> metodunu çağırmasını sağlar. Bu yöntem ayrıca bir yineleyici olarak uygulanır. Kurulum işi, lambda ifadesine başvuracak temsilciyi örnekledikten ve bir yineleyici için normal kuruluma oluşur. Her yinelemeyle, bu temsilci, koşulu yürütmek için çağırılır. Kurulum işi ve her yineleme sırasında yapılan iş, eksen boyunca yineleme sırasında yapılan işe benzer.

- @No__t-0 ' da, select yan tümcesi sorgunun <xref:System.Linq.Enumerable.Select%2A> metodunu çağırmasını sağlar. Bu yöntemin <xref:System.Linq.Enumerable.Where%2A> yöntemiyle aynı performans profili vardır.

- @No__t-0 ' da, hem `Where` yan tümcesi hem de `Select` yan tümcesi `query1` ' teki aynı performans profiline sahiptir.

 @No__t-0 ile yineleme, diğer bir deyişle, doğrusal bir süre içinde ilk sorgunun kaynağındaki öğe sayısıyla doğrudan orantılıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [Performans (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
