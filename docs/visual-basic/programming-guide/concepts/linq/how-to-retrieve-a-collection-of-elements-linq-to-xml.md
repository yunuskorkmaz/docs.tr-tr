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
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a><span data-ttu-id="fbfac-102">Nasıl yapılır: öğelerin koleksiyonunu alma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbfac-102">How to: Retrieve a Collection of Elements (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="fbfac-103">Bu konuda yöntemi gösterilmektedir <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="fbfac-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="fbfac-104">Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="fbfac-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbfac-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fbfac-105">Example</span></span>  
 <span data-ttu-id="fbfac-106">Bu örnek, öğesinin alt öğeleri boyunca yinelenir `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="fbfac-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="fbfac-107">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="fbfac-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="fbfac-108">Bu örnek aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="fbfac-108">This example produces the following output.</span></span>  
  
```console  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="fbfac-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbfac-109">See also</span></span>

- [<span data-ttu-id="fbfac-110">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbfac-110">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
