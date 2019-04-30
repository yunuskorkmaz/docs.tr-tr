---
title: 'Nasıl yapılır: Namespace değiştirmek için tüm XML ağacının (C#)'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 020d072cfb58c90720317734199d241c6892511f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668191"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="b4803-102">Nasıl yapılır: Namespace değiştirmek için tüm XML ağacının (C#)</span><span class="sxs-lookup"><span data-stu-id="b4803-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="b4803-103">Bazen, program aracılığıyla bir öğe veya öznitelik için ad alanı değiştirmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="b4803-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="b4803-104">LINQ to XML bu kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b4803-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="b4803-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> Özelliğini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4803-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="b4803-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> Özelliği ayarlanamaz, ancak öznitelikler kolayca kopyalayabilirsiniz bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>mevcut öznitelikleri kaldırın ve ardından yeni istenen ad alanı olan yeni özellikler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b4803-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="b4803-107">Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="b4803-107">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4803-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4803-108">Example</span></span>  
 <span data-ttu-id="b4803-109">Aşağıdaki kod, iki XML ağaçlarını hiçbir ad alanında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4803-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="b4803-110">Ardından her ağaçları ad alanı değiştirir ve bunları tek bir ağacına birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b4803-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```csharp  
XElement tree1 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XElement tree2 = new XElement("Data",  
    new XElement("Child", "content",  
        new XAttribute("MyAttr", "content")  
    )  
);  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace ad = "http://www.adatum.com";  
// change the namespace of every element and attribute in the first tree  
foreach (XElement el in tree1.DescendantsAndSelf())  
{  
    el.Name = aw.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(aw.GetName(at.Name.LocalName), at.Value));  
}  
// change the namespace of every element and attribute in the second tree  
foreach (XElement el in tree2.DescendantsAndSelf())  
{  
    el.Name = ad.GetName(el.Name.LocalName);  
    List<XAttribute> atList = el.Attributes().ToList();  
    el.Attributes().Remove();  
    foreach (XAttribute at in atList)  
        el.Add(new XAttribute(ad.GetName(at.Name.LocalName), at.Value));  
}  
// add attribute namespaces so that the tree will be serialized with  
// the aw and ad namespace prefixes  
tree1.Add(  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com")  
);  
tree2.Add(  
    new XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com")  
);  
// create a new composite tree  
XElement root = new XElement("Root",  
    tree1,  
    tree2  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b4803-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b4803-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4803-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4803-112">See also</span></span>

- [<span data-ttu-id="b4803-113">(LINQ to XML) XML ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b4803-113">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
