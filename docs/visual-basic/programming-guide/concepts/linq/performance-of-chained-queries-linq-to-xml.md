---
title: Zincirleme sorgu (LINQ-XML) performansını (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: d390fc0e45967cd98697320eb6f61a51cb1c19da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645713"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Zincirleme sorgu (LINQ-XML) performansını (Visual Basic)
LINQ (ve LINQ-XML) en önemli avantajları zincirleme sorguları yanı sıra tek bir büyük, daha karmaşık sorgu gerçekleştirebilirsiniz biridir.  
  
 Başka bir sorgu, kaynağı olarak kullanan bir sorgu bir zincirleme sorgudur. Örneğin, aşağıdaki kodda basit, `query2` sahip `query1` kaynağı olarak:  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
4  
```  
  
 Bu zincirleme sorgu bağlantılı listesini yineleme olarak aynı performans profili sağlar.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Eksen bağlantılı listesini yineleme olarak temelde aynı performansa sahiptir. <xref:System.Xml.Linq.XContainer.Elements%2A> Ertelenmiş yürütme ile yineleyici olarak uygulanır. Bu, bazı iş Ayrıca bağlantılı liste yineleme yapma gibi yineleyici nesne ayırma ve yürütme durumu izlemek için yaptığı anlamına gelir. Bu iş iki kategoriye ayrılabilir: yineleyici ayarlandığından saat ve her yinelemede yapılır iş yapılan iş. Kurulum çalışması küçük, sabit bir tutar iş ve her yinelemede çalışmanın kaynak koleksiyondaki öğe sayısını doğru orantılıdır.  
  
-   İçinde `query1`, `Where` yan tümcesi neden çağırmak sorgu <xref:System.Linq.Enumerable.Where%2A> yöntemi. Bu yöntem aynı zamanda yineleyici uygulanır. Kurulum çalışması için bir yineleyici lambda ifadesi yanı sıra, normal kurulum başvurur temsilci başlatmasını oluşur. Her bir yineleme, koşul yürütmek için temsilci çağrılır. Kurulum çalışması ve her yinelemede çalışmanın benzer çalışmanın eksen yineleme oluştu.  
  
-   İçinde `query1`, select yan tümcesi çağırmak sorgu neden <xref:System.Linq.Enumerable.Select%2A> yöntemi. Bu yöntem olarak aynı performans profiline sahip <xref:System.Linq.Enumerable.Where%2A> yöntemi.  
  
-   İçinde `query2`, her iki `Where` yan tümcesi ve `Select` yan tümcesi bulunan aynı performans profili olarak `query1`.  
  
 Üzerinden yineleme `query2` ilk kaynağındaki öğelerin sayısı orantılı sorgu doğrudan, diğer bir deyişle, doğrusal zaman bu nedenle olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
