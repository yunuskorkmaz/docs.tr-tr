---
title: "Dönüştürme veri türleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5fb0e9dfb0f1fb882116449757ed0f0bf9029b39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-data-types-visual-basic"></a>Dönüştürme veri türleri (Visual Basic)
Dönüştürme yöntemleri giriş nesnelerin türünü değiştirin.  
  
 LINQ sorgularını dönüştürme işlemlerinde çeşitli uygulamalar yararlı olur. Bazı örnekler şunlardır:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Yöntemi, bir türün özel bir standart sorgu işleci uyarlamasını gizlemek için kullanılabilir.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Yöntemi, LINQ sorgusu için koleksiyonları parametresiz etkinleştirmek için kullanılabilir.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, Ve <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> yöntemleri, sorgu numaralandırılan kadar yerine onu ertelemeyi hemen sorgu yürütme zorlamak için kullanılabilir.  
  
## <a name="methods"></a>Yöntemler  
 Aşağıdaki tabloda veri türü dönüşümleri gerçekleştirmek standart sorgu işleci yöntemlerini listeler.  
  
 Bu tabloda, adları "As" başlayın dönüştürme yöntemleri kaynak koleksiyonu statik türünü değiştirme ancak bunu numaralandırmak değil. "Kaynak toplamasını ve öğeleri karşılık gelen koleksiyona koymak için" ile adları başlayan yöntemleri yazın.  
  
|Yöntem adı|Açıklama|Visual Basic sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|Olarak yazılan giriş döndürür <xref:System.Collections.Generic.IEnumerable%601>.|Yok.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|(Genel) dönüştürür <xref:System.Collections.IEnumerable> (Genel) <xref:System.Linq.IQueryable>.|Yok.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Cast|Belirtilen tür için bir koleksiyonun öğelerini çevirir.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Değerleri yeteneklerini bir belirtilen türe göre filtreler.|Yok.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Bir koleksiyonu bir diziye dönüştürür. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|Todictionary öğesini|Öğeler haline getirir bir <xref:System.Collections.Generic.Dictionary%602> bir anahtar Seçici işlevine bağlı. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|ToList|Bir koleksiyona dönüştüren bir <xref:System.Collections.Generic.List%601>. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Öğeler haline getirir bir <xref:System.Linq.Lookup%602> (bir-çok sözlük) dayalı bir anahtar Seçici işlevdir. Bu yöntem, sorgu yürütme zorlar.|Yok.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Sorgu ifade sözdizimi örneği  
 Aşağıdaki kod örneğinde `From As` yan tümcesi yalnızca alt üzerinde kullanılabilir üyesi erişmeden önce alt türüne yayınlanamıyor.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
