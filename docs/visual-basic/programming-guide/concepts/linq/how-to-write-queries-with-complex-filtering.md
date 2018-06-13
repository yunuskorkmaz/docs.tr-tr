---
title: 'Nasıl yapılır: karmaşık (Visual Basic) filtresiyle sorguları yazma'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 500cd9cdc62252eff3addc26006c4ce815ae1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645869"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>Nasıl yapılır: karmaşık (Visual Basic) filtresiyle sorguları yazma
Bazen LINQ XML sorguları karmaşık filtrelerle yazmak istiyorum. Örneğin, bir özel ad ve değer olan bir alt öğesi olan tüm öğeleri bulmak olabilir. Bu konuda, karmaşık filtreleme ile bir sorgu yazma bir örnek verir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte tüm bulmayı gösteren `PurchaseOrder` olan bir alt öğenin `Address` sahip öğe bir `Type` özniteliği "Aktarma" ve bir alt eşit `State` öğesi "NY" eşit. İç içe bir sorgu kullanır `Where` yan tümcesi ve `Any` operatörü döndürür `True` koleksiyonu herhangi bir öğe varsa.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: birden çok satınalma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Hakkında daha fazla bilgi için `Any` işleci, bkz: [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
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
 Aşağıdaki örnek bir ad alanı XML aynı sorgu gösterir. Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace içinde birden çok satınalma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [Temel sorgu (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [XML Alt Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML Özniteliği Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)  
 [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Projeksiyon işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
 [Niceleyici işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
