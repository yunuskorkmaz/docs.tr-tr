---
title: 'Nasıl yapılır: tek bir alt öğe (LINQ to XML) alma (C#)'
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 77ccd56d1d131a740bb90ef4258ef35504f5e3cb
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597887"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="97842-102">Nasıl yapılır: tek bir alt öğe (LINQ to XML) alma (C#)</span><span class="sxs-lookup"><span data-stu-id="97842-102">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="97842-103">Bu konu nasıl tek bir alt öğe, alt öğenin adı verilir alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="97842-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="97842-104">Adı alt öğesi ve bu ada sahip yalnızca bir öğe olduğunu bildiğinizde, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="97842-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="97842-105"><xref:System.Xml.Linq.XContainer.Element%2A> Yöntemi döndürür ilk alt <xref:System.Xml.Linq.XElement> belirtilen <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="97842-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="97842-106">Tek bir alt öğe Visual Basic'te almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanın ve ardından dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi almak oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="97842-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97842-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="97842-107">Example</span></span>  
 <span data-ttu-id="97842-108">Aşağıdaki örnek, kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="97842-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="97842-109">Bu örnek adlı XML ağacı alır `po` ve adlı ilk öğeyi bulan `Comment`.</span><span class="sxs-lookup"><span data-stu-id="97842-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="97842-110">Visual Basic örneği, tek bir öğe almak için dizi dizin oluşturucu gösterimini kullanarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="97842-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="97842-111">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="97842-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="97842-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="97842-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="97842-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="97842-113">Example</span></span>  
 <span data-ttu-id="97842-114">Aşağıdaki örnek, bir ad alanındaki XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="97842-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="97842-115">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="97842-115">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="97842-116">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi bir Namespace,](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="97842-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="97842-117">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="97842-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="97842-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97842-118">See Also</span></span>

- [<span data-ttu-id="97842-119">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="97842-119">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
