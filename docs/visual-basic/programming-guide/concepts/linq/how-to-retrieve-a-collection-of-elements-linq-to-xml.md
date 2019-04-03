---
title: 'Nasıl yapılır: Öğeleri (LINQ to XML) koleksiyonu alma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
ms.openlocfilehash: 53572ac3c80e012b95527d32da28c8685cd8cfd3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833649"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="a409c-102">Nasıl yapılır: Öğeleri (LINQ to XML) koleksiyonu alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a409c-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a409c-103">Bu konuda gösterilmiştir <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a409c-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="a409c-104">Bu yöntem, öğenin alt öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="a409c-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a409c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a409c-105">Example</span></span>  
 <span data-ttu-id="a409c-106">Bu örnek, alt öğeleri yinelenir `purchaseOrder` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a409c-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="a409c-107">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a409c-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="a409c-108">Bu örnek aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="a409c-108">This example produces the following output.</span></span>  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="a409c-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a409c-109">See also</span></span>

- [<span data-ttu-id="a409c-110">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a409c-110">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
