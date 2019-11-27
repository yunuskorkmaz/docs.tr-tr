---
title: 'Nasıl yapılır: öğelerin koleksiyonunu alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 592ef68206df59bc848644d0a62bf0efdb10609e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347592"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>Nasıl yapılır: öğelerin koleksiyonunu alma (LINQ to XML) (Visual Basic)
Bu konuda <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi gösterilmektedir. Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `purchaseOrder` öğesinin alt öğeleri boyunca yinelenir.  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir.  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
