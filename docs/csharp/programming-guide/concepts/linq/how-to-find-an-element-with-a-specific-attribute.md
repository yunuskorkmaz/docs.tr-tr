---
title: Belirli bir özniteliğe (C#) sahip bir öğe yi bulma
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 106885b8658c493caab3101e6b4ce921589076eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141156"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="b21df-102">Belirli bir özniteliğe (C#) sahip bir öğe yi bulma</span><span class="sxs-lookup"><span data-stu-id="b21df-102">How to find an element with a specific attribute (C#)</span></span>
<span data-ttu-id="b21df-103">Bu konu, belirli bir değere sahip bir özniteliğe sahip bir öğeyi nasıl bulacağımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b21df-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b21df-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b21df-104">Example</span></span>  
 <span data-ttu-id="b21df-105">Örnek, "Faturalama" `Address` değeri olan `Type` bir özniteliği olan öğeyi nasıl bulabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b21df-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="b21df-106">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Tipik SatınAlma Siparişi (LINQ-XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="b21df-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="b21df-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b21df-107">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="b21df-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b21df-108">Example</span></span>  
 <span data-ttu-id="b21df-109">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b21df-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="b21df-110">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b21df-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b21df-111">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Tipik Satın Alma Siparişi.](./sample-xml-file-typical-purchase-order-in-a-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="b21df-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="b21df-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b21df-112">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b21df-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b21df-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="b21df-114">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="b21df-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b21df-115">Projeksiyon İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b21df-115">Projection Operations (C#)</span></span>](./projection-operations.md)
