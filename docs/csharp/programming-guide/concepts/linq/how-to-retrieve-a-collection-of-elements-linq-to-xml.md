---
title: Öğelerin koleksiyonunu alma (LINQ to XML) (C#)
description: C# içindeki Elements yöntemi bir öğenin alt öğelerinin bir koleksiyonunu alır. Bu LINQ to XML örnek, bir öğenin alt öğeleri üzerinden yinelenir.
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103352"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a><span data-ttu-id="a12c9-104">Öğelerin koleksiyonunu alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a12c9-104">How to retrieve a collection of elements (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a12c9-105">Bu konuda yöntemi gösterilmektedir <xref:System.Xml.Linq.XContainer.Elements%2A> .</span><span class="sxs-lookup"><span data-stu-id="a12c9-105">This topic demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="a12c9-106">Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="a12c9-106">This method retrieves a collection of the child elements of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a12c9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a12c9-107">Example</span></span>  
 <span data-ttu-id="a12c9-108">Bu örnek, öğesinin alt öğeleri boyunca yinelenir `purchaseOrder` .</span><span class="sxs-lookup"><span data-stu-id="a12c9-108">This example iterates through the child elements of the `purchaseOrder` element.</span></span>  
  
 <span data-ttu-id="a12c9-109">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="a12c9-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 <span data-ttu-id="a12c9-110">Bu örnek aşağıdaki çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="a12c9-110">This example produces the following output.</span></span>  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a><span data-ttu-id="a12c9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a12c9-111">See also</span></span>

- [<span data-ttu-id="a12c9-112">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="a12c9-112">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
