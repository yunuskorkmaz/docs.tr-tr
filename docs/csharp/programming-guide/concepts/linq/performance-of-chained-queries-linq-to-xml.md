---
title: Performans zincirleme sorgu (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Performans zincirleme sorgu (LINQ-XML) (C#)
LINQ (ve LINQ-XML) en önemli avantajları zincirleme sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirebilirsiniz biridir.  
  
 Başka bir sorgu, kaynağı olarak kullanan bir sorgu bir zincirleme sorgudur. Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
4  
```  
  
 Bu zincirleme sorgu bağlantılı listesini yineleme olarak aynı performans profili sağlar.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Eksen bağlantılı listesini yineleme olarak temelde aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A> Ertelenmiş yürütme ile yineleyici olarak uygulanır. Bu, bazı iş Ayrıca bağlantılı liste yineleme yapma gibi yineleyici nesne ayırma ve yürütme durumu izlemek için yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından saat ve her yinelemede yapılır iş yapılan iş. Kurulum çalışması küçük, sabit bir tutar iş ve her yinelemede çalışmanın kaynak koleksiyondaki öğe sayısını doğru orantılıdır.  
  
-   İçinde `query1`, `where` yan tümcesi neden çağırmak sorgu <xref:System.Linq.Enumerable.Where%2A> yöntemi. Bu yöntem aynı zamanda yineleyici uygulanır. Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum başvurur temsilci başlatmasını oluşur. Her bir yineleme, koşul yürütmek için temsilci çağrılır. Kurulum çalışması ve her yinelemede çalışmanın benzer çalışmanın eksen yineleme oluştu.  
  
-   İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi. Bu yöntem olarak aynı performans profiline sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.  
  
-   İçinde `query2`, her iki `where` yan tümcesi ve `select` yan tümcesi bulunan aynı performans profili olarak `query1`.  
  
 Üzerinden yineleme `query2` ilk kaynağındaki öğelerin sayısı orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman bu nedenle olur. Karşılık gelen bir Visual Basic örnek aynı performans profili olması.  
  
 Yineleyiciler hakkında daha fazla bilgi için bkz: [verim](../../../../csharp/language-reference/keywords/yield.md).  
  
 Sorguları birlikte zincirleme üzerinde daha ayrıntılı öğretici için bkz [Öğreticisi: sorguları birlikte zincirleme](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
