---
title: 'Nasıl yapılır: Belirli bir özniteliğe sahip öğeyi bulma (C#)'
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 7ec6240bf399058ca94cc52c66e6029f924fcd29
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485564"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="7d32c-102">Nasıl yapılır: Belirli bir özniteliğe sahip öğeyi bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="7d32c-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="7d32c-103">Bu konuda, belirli bir değere sahip bir özniteliği olan bir öğeyi bulmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7d32c-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d32c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d32c-104">Example</span></span>  
 <span data-ttu-id="7d32c-105">Bu örnek nasıl bulunacağını gösterir `Address` sahip öğe bir `Type` "Billing" değerine sahip öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7d32c-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="7d32c-106">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="7d32c-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="7d32c-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7d32c-107">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7d32c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d32c-108">Example</span></span>  
 <span data-ttu-id="7d32c-109">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d32c-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="7d32c-110">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7d32c-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7d32c-111">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace, tipik satın alma siparişi](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="7d32c-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="7d32c-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7d32c-112">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d32c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d32c-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="7d32c-114">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="7d32c-114">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7d32c-115">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="7d32c-115">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
