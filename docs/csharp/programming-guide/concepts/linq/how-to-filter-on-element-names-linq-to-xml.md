---
title: 'Nasıl yapılır: öğe adlarını (LINQ to XML) filtreleme (C#)'
ms.date: 07/20/2015
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: df3a2fb7de888dfc2bc93520c16a52b594047fb3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563839"
---
# <a name="how-to-filter-on-element-names-linq-to-xml-c"></a><span data-ttu-id="eeeb4-102">Nasıl yapılır: öğe adlarını (LINQ to XML) filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="eeeb4-102">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>
<span data-ttu-id="eeeb4-103">Çağırdığınızda döndüren yöntemler birini <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement>, öğeyi adına göre filtre uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeeb4-103">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eeeb4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="eeeb4-104">Example</span></span>  
 <span data-ttu-id="eeeb4-105">Bu örnek yalnızca belirtilen ada sahip alt öğeleri içerecek şekilde filtrelenmiş bir alt koleksiyonunu alır.</span><span class="sxs-lookup"><span data-stu-id="eeeb4-105">This example retrieves a collection of descendants that is filtered to contain only descendants with the specified name.</span></span>  
  
 <span data-ttu-id="eeeb4-106">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="eeeb4-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants("ProductName")  
    select el;  
foreach(XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string) prdName);  
```  
  
 <span data-ttu-id="eeeb4-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="eeeb4-107">This code produces the following output:</span></span>  
  
```  
ProductName:Lawnmower  
ProductName:Baby Monitor  
```  
  
 <span data-ttu-id="eeeb4-108">Döndüren yöntemler <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Xml.Linq.XElement> koleksiyonları aynı deseni takip edin.</span><span class="sxs-lookup"><span data-stu-id="eeeb4-108">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="eeeb4-109">Bunların imzalarını benzer <xref:System.Xml.Linq.XContainer.Elements%2A> ve <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span><span class="sxs-lookup"><span data-stu-id="eeeb4-109">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="eeeb4-110">Benzer yöntem imzaları olan yöntemlerinin tam listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="eeeb4-110">The following is the complete list of methods that have similar method signatures:</span></span>  
  
-   <xref:System.Xml.Linq.XNode.Ancestors%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
  
-   <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>  
  
-   <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>  
  
## <a name="example"></a><span data-ttu-id="eeeb4-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="eeeb4-111">Example</span></span>  
 <span data-ttu-id="eeeb4-112">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="eeeb4-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="eeeb4-113">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="eeeb4-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="eeeb4-114">Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: tipik satın alma siparişi bir Namespace,](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="eeeb4-114">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
IEnumerable<XElement> items =  
    from el in po.Descendants(aw + "ProductName")  
    select el;  
foreach (XElement prdName in items)  
    Console.WriteLine(prdName.Name + ":" + (string)prdName);  
```  
  
 <span data-ttu-id="eeeb4-115">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="eeeb4-115">This code produces the following output:</span></span>  
  
```  
{http://www.adventure-works.com}ProductName:Lawnmower  
{http://www.adventure-works.com}ProductName:Baby Monitor  
```  
  
## <a name="see-also"></a><span data-ttu-id="eeeb4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eeeb4-116">See Also</span></span>

- [<span data-ttu-id="eeeb4-117">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="eeeb4-117">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
