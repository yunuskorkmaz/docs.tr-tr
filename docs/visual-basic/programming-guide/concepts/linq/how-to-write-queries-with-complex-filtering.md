---
title: 'Nasıl yapılır: karmaşık filtrelemeye sahip sorgular yazma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 41b967e2876be98016b48da5122478f63385c6a8
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834967"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Nasıl yapılır: karmaşık filtrelemeye sahip sorgular yazma (Visual Basic)
Bazen karmaşık filtrelerle LINQ to XML sorguları yazmak isteyebilirsiniz. Örneğin, belirli bir ada ve değere sahip bir alt öğesi olan tüm öğeleri bulmanız gerekebilir. Bu konu, karmaşık filtrelemeye sahip sorgu yazma örneği sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnek, "Shipping" değerine eşit bir `Type` özniteliği ve bir alt `State` öğesi "NY" değerine eşit olan bir alt `Address` öğesine sahip olan `PurchaseOrder` öğelerinin nasıl bulunacağını gösterir. @No__t-0 yan tümcesinde iç içe geçmiş bir sorgu kullanır ve koleksiyonda herhangi bir öğe varsa `Any` işleci `True` ' i döndürür.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 @No__t-0 işleci hakkında daha fazla bilgi için bkz. [nicelik belirteci işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
99505  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında birden fazla satın alma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```console  
99505  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Temel sorgular (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [XML alt eksen özelliği](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML özniteliği eksen özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML değeri özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Projeksiyon Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Nicelik belirteci Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
