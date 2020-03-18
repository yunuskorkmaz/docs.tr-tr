---
title: Tek bir alt öğe (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347470"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a><span data-ttu-id="9d293-102">Tek bir alt öğe (LINQ - XML) (C#) nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="9d293-102">How to retrieve a single child element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9d293-103">Bu konu, alt öğenin adı verilen tek bir alt öğenin nasıl alınır açıklar.</span><span class="sxs-lookup"><span data-stu-id="9d293-103">This topic explains how to retrieve a single child element, given the name of the child element.</span></span> <span data-ttu-id="9d293-104">Alt öğenin adını biliyorsanız ve bu ada sahip tek bir öğe varsa, koleksiyon yerine yalnızca bir öğeyi almak uygun olabilir.</span><span class="sxs-lookup"><span data-stu-id="9d293-104">When you know the name of the child element and that there is only one element that has this name, it can be convenient to retrieve just one element, instead of a collection.</span></span>  
  
 <span data-ttu-id="9d293-105">Yöntem <xref:System.Xml.Linq.XContainer.Element%2A> belirtilen ile <xref:System.Xml.Linq.XElement> ilk alt <xref:System.Xml.Linq.XName>döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d293-105">The <xref:System.Xml.Linq.XContainer.Element%2A> method returns the first child <xref:System.Xml.Linq.XElement> with the specified <xref:System.Xml.Linq.XName>.</span></span>  
  
 <span data-ttu-id="9d293-106">Visual Basic'te tek bir alt öğe almak istiyorsanız, sık karşılaşılan bir yaklaşım XML özelliğini kullanmak ve ardından dizi dizileyici gösterimini kullanarak ilk öğeyi almaktır.</span><span class="sxs-lookup"><span data-stu-id="9d293-106">If you want to retrieve a single child element in Visual Basic, a common approach is to use the XML property, and then retrieve the first element using array indexer notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d293-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d293-107">Example</span></span>  
 <span data-ttu-id="9d293-108">Aşağıdaki örnek yöntemin <xref:System.Xml.Linq.XContainer.Element%2A> kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9d293-108">The following example demonstrates the use of the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="9d293-109">Bu örnek, XML `po` ağacı adlı alır `Comment`ve adlı ilk öğeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="9d293-109">This example takes the XML tree named `po` and finds the first element named `Comment`.</span></span>  
  
 <span data-ttu-id="9d293-110">Visual Basic örneği, tek bir öğeyi almak için dizi dizinleyici gösterimini kullanırken gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d293-110">The Visual Basic example shows using array indexer notation to retrieve a single element.</span></span>  
  
 <span data-ttu-id="9d293-111">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="9d293-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="9d293-112">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9d293-112">This example produces the following output:</span></span>  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a><span data-ttu-id="9d293-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d293-113">Example</span></span>  
 <span data-ttu-id="9d293-114">Aşağıdaki örnek, xml için bir ad alanında aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d293-114">The following example shows the same code for XML that is in a namespace.</span></span> <span data-ttu-id="9d293-115">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9d293-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="9d293-116">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Tipik Satın Alma Siparişi.](./sample-xml-file-typical-purchase-order-in-a-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="9d293-116">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="9d293-117">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9d293-117">This example produces the following output:</span></span>  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d293-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d293-118">See also</span></span>

- [<span data-ttu-id="9d293-119">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="9d293-119">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
