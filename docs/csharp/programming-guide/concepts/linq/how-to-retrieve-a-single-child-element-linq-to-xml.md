---
title: Tek bir alt öğe alma (LINQ to XML) (C#)
description: Tek bir alt öğeyi ada göre almak için LINQ to XML nasıl kullanacağınızı öğrenin. Bu C# örneğinde, öğe yöntemi belirtilen ilk alt öğeyi döndürür.
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: c3a044f30cf2e411bdff52586c7a370b626f41bc
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103283"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="c8f3a-104">Tek bir alt öğe alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c8f3a-104">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c8f3a-105">Bu konu, alt öğenin adı verildiğinde tek bir alt öğenin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c8f3a-105">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="c8f3a-106">Alt öğenin adını bildiğiniz ve bu ada sahip yalnızca bir öğe olduğunda, bir koleksiyon yerine yalnızca bir öğe almak kullanışlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8f3a-106">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="c8f3a-107"><xref:System.Xml.Linq.XContainer.Element%2A>Yöntemi, belirtilen ilk alt öğesini döndürür <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="c8f3a-107">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="c8f3a-108">Visual Basic tek bir alt öğe almak istiyorsanız, yaygın bir yaklaşım XML özelliğini kullanmak ve sonra dizi dizin oluşturucu gösterimini kullanarak ilk öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="c8f3a-108">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8f3a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8f3a-109">Example</span></span>  
 <span data-ttu-id="c8f3a-110">Aşağıdaki örnek yönteminin kullanımını gösterir <xref:System.Xml.Linq.XContainer.Element%2A> .</span><span class="sxs-lookup"><span data-stu-id="c8f3a-110">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="c8f3a-111">Bu örnek adlı XML ağacını alır `po` ve adlı ilk öğeyi bulur `Comment` .</span><span class="sxs-lookup"><span data-stu-id="c8f3a-111">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="c8f3a-112">Visual Basic örnek, tek bir öğeyi almak için dizi dizin oluşturucu gösterimini kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f3a-112">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="c8f3a-113">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: tipik satın alma siparişi (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="c8f3a-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="c8f3a-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c8f3a-114">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="c8f3a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8f3a-115">Example</span></span>  
 <span data-ttu-id="c8f3a-116">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8f3a-116">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="c8f3a-117">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c8f3a-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c8f3a-118">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: bir ad alanında tipik satın alma siparişi](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c8f3a-118">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="c8f3a-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c8f3a-119">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8f3a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8f3a-120">See also</span></span>

- [<span data-ttu-id="c8f3a-121">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="c8f3a-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
