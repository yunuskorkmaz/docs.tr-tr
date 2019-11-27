---
title: Veri Türlerini Dönüştürme
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: 25d21954f0bb7555f1f5666f83fb37f4f73e2a60
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354254"
---
# <a name="converting-data-types-visual-basic"></a>Veri türlerini dönüştürme (Visual Basic)

Dönüştürme yöntemleri giriş nesnelerinin türünü değiştirir.

 LINQ sorgularındaki dönüştürme işlemleri çeşitli uygulamalarda yararlıdır. Aşağıda bazı örnekler verilmiştir:

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> yöntemi, bir türün standart sorgu işlecinin özel uygulamasını gizlemek için kullanılabilir.

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> yöntemi, LINQ sorgulaması için parametreli olmayan koleksiyonları etkinleştirmek üzere kullanılabilir.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılana kadar, sorgu yürütmeye zorlamak yerine hemen bu işlemi yapmak için kullanılabilir.

## <a name="methods"></a>Yöntemler

Aşağıdaki tabloda, veri türü dönüştürmeleri gerçekleştiren standart sorgu işleci yöntemleri listelenmektedir.

Bu tablodaki, adları "as" ile başlayan dönüştürme yöntemleri, kaynak koleksiyonun statik türünü değiştirir ancak onu numaralandırmaz. Adları "to" ile başlayan Yöntemler, kaynak koleksiyonu numaralandırır ve öğeleri karşılık gelen koleksiyon türüne koyar.

|Yöntem adı|Açıklama|Sorgu Ifadesi söz dizimini Visual Basic|Daha Fazla Bilgi|
|-----------------|-----------------|------------------------------------------|----------------------|
|Asılabilir|<xref:System.Collections.Generic.IEnumerable%601>olarak yazılan girişi döndürür.|Geçerli değildir.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Bir (genel) <xref:System.Collections.IEnumerable> bir (genel) <xref:System.Linq.IQueryable>dönüştürür.|Geçerli değildir.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Cast|Bir koleksiyonun öğelerini belirtilen bir türe yayınlar.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|OfType|Değerleri, belirli bir türe atama becerisine bağlı olarak filtreler.|Geçerli değildir.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray|Bir koleksiyonu bir diziye dönüştürür. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Öğeleri bir anahtar Seçici işlevine göre <xref:System.Collections.Generic.Dictionary%602> koyar. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList|Bir koleksiyonu bir <xref:System.Collections.Generic.List%601>dönüştürür. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Öğeleri bir anahtar Seçici işlevine göre bir <xref:System.Linq.Lookup%602> (bire çok sözlüğüne) koyar. Bu yöntem sorgu yürütmeyi zorlar.|Geçerli değildir.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

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
