---
title: Veri türlerini dönüştürme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 4d0658983b5873c635d1926444293b0ddf5b0a87
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835181"
---
# <a name="converting-data-types-visual-basic"></a>Veri türlerini dönüştürme (Visual Basic)
Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.  
  
 LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır. Aşağıda bazı örnekler verilmiştir:
  
- @No__t-0 yöntemi, bir türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.  
  
- @No__t-0 yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.  
  
- @No__t-0, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen kullanılabilir.  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.  
  
 Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz. Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.  
  
|Yöntem adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha fazla bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Asılabilir|@No__t-0 olarak yazılan girişi döndürür.|Yok.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Bir (genel) <xref:System.Collections.IEnumerable> ' a (genel) <xref:System.Linq.IQueryable> dönüştürür.|Yok.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Cast|Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.|Yok.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Bir koleksiyonu bir diziye dönüştürür. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Öğeleri bir anahtar Seçici işlevine göre <xref:System.Collections.Generic.Dictionary%602> ' a koyar. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|Bir koleksiyonu bir @no__t dönüştürür-0. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Öğeleri bir anahtar Seçici işlevine göre <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) öğesine koyar. Bu yöntem sorgu yürütmeyi zorlar.|Yok.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu Ifadesi söz dizimi örneği  
 Aşağıdaki kod örneği, yalnızca alt tür üzerinde kullanılabilir olan bir üyeye erişmeden önce bir türü bir alt türe dönüştürmek için `From As` yan tümcesini kullanır.  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq>
- [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [From Yan Tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
