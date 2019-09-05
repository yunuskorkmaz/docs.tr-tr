---
title: 'Nasıl yapılır: Öğelerin koleksiyonunu al (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: fef12745bd608622f071f72049f242405d17ed7d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253415"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="38c16-102">Nasıl yapılır: Öğelerin koleksiyonunu al (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="38c16-102">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="38c16-103">Bu konuda <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38c16-103">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="38c16-104">Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="38c16-104">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38c16-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="38c16-105">Example</span></span>  
 <span data-ttu-id="38c16-106">Bu örnek, `purchaseOrder` öğesinin alt öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="38c16-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="38c16-107">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md)).</span><span class="sxs-lookup"><span data-stu-id="38c16-107">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="38c16-108">Bu örnek aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="38c16-108">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="38c16-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38c16-109">See also</span></span>

- [<span data-ttu-id="38c16-110">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="38c16-110">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
