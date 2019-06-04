---
title: Performans zincirleme sorgu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 1301a8142ab1a8f793dc30f37c50aa45c2cd9a2a
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484118"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Performans zincirleme sorgu (LINQ to XML) (C#)
LINQ (ve LINQ to XML) en önemli avantajlarından biri, zincir sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirilebiliyor olmasıdır.  
  
 Zincirleme bir sorgu, kaynağı olarak başka bir sorgu kullanan bir sorgudur. Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:  
  
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
  
 Bu Zincirli sorgu ile bağlantılı bir liste yineleme aynı performans profili sağlar.  
  
- <xref:System.Xml.Linq.XContainer.Elements%2A> Eksen sahip bir bağlantılı listede yineleme olarak temelde aynı performans. <xref:System.Xml.Linq.XContainer.Elements%2A> Ertelenmiş yürütme ile bir yineleyici olarak uygulanır. Bu, bazı iş Ayrıca bağlantılı liste yineleme gibi yineleyici nesnesinden ayırma ve yürütme durumunu izlemek için yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından zamanda ve her yinelemede bitti iş bitti iş. İş küçük, sabit bir miktarda Kurulum çalışmadır ve her yineleme sırasında çalışmanın kaynak koleksiyondaki öğe sayısı ile orantılıdır.  
  
- İçinde `query1`, `where` çağırmak sorgu yan tümcesi neden <xref:System.Linq.Enumerable.Where%2A> yöntemi. Bu yöntem aynı zamanda bir yineleyici uygulanır. Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum Bakacağınız temsilci örnekleme oluşur. Her yineleme ile koşul yürütmek için temsilci çağrılır. Kurulum çalışması ve her yineleme sırasında çalışmanın benzer çalışmanın eksen yineleme sırasında.  
  
- İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi. Bu yöntem aynı performans profili sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.  
  
- İçinde `query2`hem `where` yan tümcesi ve `select` yan tümcesine sahip olarak aynı performans profili `query1`.  
  
 Üzerinden yineleme `query2` ilk kaynak öğe sayısını orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman, bu nedenle olur. Karşılık gelen bir Visual Basic örneği aynı performans profili gerekir.  
  
 Yineleyiciler hakkında daha fazla bilgi için bkz. [yield](../../../../csharp/language-reference/keywords/yield.md).  
  
 Daha ayrıntılı bir eğitim sorguları birbirine zincirleme hakkında bilgi için bkz [Öğreticisi: Sorguları birbirine zincirleme](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
