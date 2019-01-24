---
title: 'Nasıl yapılır: (Visual Basic) karmaşık filtreleme ile sorgu yazma'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 9636e67b32107378a46c00338cb4c2bea20fc1d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646691"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Nasıl yapılır: (Visual Basic) karmaşık filtreleme ile sorgu yazma
Bazen karmaşık filtrelerle XML sorgularında LINQ yazmak istersiniz. Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri Bul gerekebilir. Bu konu, karmaşık filtreleme ile sorgu yazma örneği sağlar.  
  
## <a name="example"></a>Örnek  
 Bu örnekte tüm bulmayı gösteren `PurchaseOrder` alt olan öğeler `Address` sahip öğe bir `Type` özniteliği "Gönderim" hem de bir alt gruba eşit `State` öğesi "NY için" eşit. İç içe bir sorgu kullanan `Where` yan tümcesi ve `Any` işleci döndürür `True` koleksiyonu herhangi bir öğe varsa.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Birden fazla satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Hakkında daha fazla bilgi için `Any` işleci bkz [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
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
  
```  
99505  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace, birden fazla satın alma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
```  
99505  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Temel sorgular (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [XML Alt Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Özniteliği Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Projeksiyon işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
