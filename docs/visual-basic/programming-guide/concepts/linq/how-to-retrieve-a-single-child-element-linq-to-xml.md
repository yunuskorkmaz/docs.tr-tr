---
title: "Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 580315fda6ef6f1919f7f2aabc0cf3604a5c4337
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (Visual Basic)
Bu konuda, tek bir alt öğe, alt öğe adı verilen almak açıklanmaktadır. Adı alt öğe ve bu ada sahip olan yalnızca bir öğe olduğunu bildiğiniz durumlarda bir koleksiyon yerine yalnızca tek bir öğede almak kullanışlı olabilir.  
  
 <xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> belirtilen <xref:System.Xml.Linq.XName>.  
  
 Tek bir alt öğe Visual Basic'te almak istiyorsanız, bir ortak XML özelliğini kullanın ve ardından dizinin dizin oluşturucu gösterimini kullanarak ilk öğe almak için bir yaklaşımdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanımını gösteren <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi. Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğe bulur `Comment`.  
  
 Visual Basic örnek, tek bir öğe almak için dizi dizin oluşturucu gösterimini kullanarak gösterir.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: tipik satın alma siparişi (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanı içinde XML için aynı kodu gösterir. Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: bir Namespace tipik satınalma siparişi](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
