---
title: Tüm XML ağacının (C#) ad alanını değiştirme
ms.date: 07/20/2015
ms.assetid: 1584ff3b-c77d-4241-ab62-80adfb7bfc1b
ms.openlocfilehash: 6462cbb5001682b6a464c1446f8ae6de3c5669d1
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141516"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-c"></a><span data-ttu-id="a3f6b-102">Tüm XML ağacının (C#) ad alanını değiştirme</span><span class="sxs-lookup"><span data-stu-id="a3f6b-102">How to change the namespace for an entire XML tree (C#)</span></span>
<span data-ttu-id="a3f6b-103">Bazen bir öğe veya öznitelik için ad alanını programlı olarak değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a3f6b-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="a3f6b-104">LINQ to XML bu kadar kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="a3f6b-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="a3f6b-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> özelliği ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a3f6b-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="a3f6b-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> özelliği ayarlanamaz, ancak öznitelikleri kolayca bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>kopyalayabilir, var olan öznitelikleri kaldırabilir ve ardından yeni istenen ad alanındaki yeni öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a3f6b-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="a3f6b-107">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a3f6b-107">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3f6b-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3f6b-108">Example</span></span>  
 <span data-ttu-id="a3f6b-109">Aşağıdaki kod, ad alanı olmadan iki XML ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a3f6b-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="a3f6b-110">Daha sonra ağaçların her birinin ad alanını değiştirir ve bunları tek bir ağaçta birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a3f6b-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
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
  
 <span data-ttu-id="a3f6b-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a3f6b-111">This example produces the following output:</span></span>  
  
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
