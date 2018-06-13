---
title: 'Nasıl yapılır: Namespace değiştirmek için tüm XML ağacı (C#)'
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 698d5323d712555cf59714323d2cb13d2ee6a371
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328259"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="8d011-102">Nasıl yapılır: Namespace değiştirmek için tüm XML ağacı (C#)</span><span class="sxs-lookup"><span data-stu-id="8d011-102">How to: Change the Namespace for an Entire XML Tree (C#)</span></span>
<span data-ttu-id="8d011-103">Bazen bir öğe veya öznitelik için ad alanı programlı olarak değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d011-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="8d011-104">LINQ-XML bu kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8d011-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="8d011-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> Özelliği ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8d011-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="8d011-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> Özelliği ayarlanamaz, ancak kolayca öznitelikler kopyalayabilirsiniz bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>varolan öznitelikleri kaldırın ve ardından yeni istenen ad alanında yeni öznitelikler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8d011-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="8d011-107">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="8d011-107">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d011-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d011-108">Example</span></span>  
 <span data-ttu-id="8d011-109">Aşağıdaki kod iki XML ağaçları hiçbir ad alanında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d011-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="8d011-110">Ardından ağaçlarını her ad alanı değiştirir ve tek bir ağacına birleştirir.</span><span class="sxs-lookup"><span data-stu-id="8d011-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
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
  
 <span data-ttu-id="8d011-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="8d011-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d011-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d011-112">See Also</span></span>  
 [<span data-ttu-id="8d011-113">XML ağaçları (LINQ-XML) değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="8d011-113">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
