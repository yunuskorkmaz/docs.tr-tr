---
title: 'Nasıl yapılır: Öğe Koleksiyonu Alma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 13aa9ce10df1e23ba5191b523db0272aa52ea581
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397875"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>Nasıl yapılır: öğelerin koleksiyonunu alma (LINQ to XML) (Visual Basic)
Bu konuda yöntemi gösterilmektedir <xref:System.Xml.Linq.XContainer.Elements%2A> . Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, öğesinin alt öğeleri boyunca yinelenir `purchaseOrder` .  
  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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

- [LINQ to XML eksenleri (Visual Basic)](linq-to-xml-axes.md)
