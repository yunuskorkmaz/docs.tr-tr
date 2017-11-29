---
title: "Nasıl yapılır: bir tüm XML ağacı (Visual Basic) Namespace değiştirme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c5ee83840f9d8b4105e7af53008a329dfde37d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a><span data-ttu-id="4f598-102">Nasıl yapılır: bir tüm XML ağacı (Visual Basic) Namespace değiştirme</span><span class="sxs-lookup"><span data-stu-id="4f598-102">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>
<span data-ttu-id="4f598-103">Bazen bir öğe veya öznitelik için ad alanı programlı olarak değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4f598-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="4f598-104">LINQ-XML bu kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="4f598-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="4f598-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> Özelliği ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="4f598-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="4f598-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> Özelliği ayarlanamaz, ancak kolayca öznitelikler kopyalayabilirsiniz bir <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>varolan öznitelikleri kaldırın ve ardından yeni istenen ad alanında yeni öznitelikler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4f598-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="4f598-107">Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="4f598-107">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f598-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f598-108">Example</span></span>  
 <span data-ttu-id="4f598-109">Aşağıdaki kod iki XML ağaçları hiçbir ad alanında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f598-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="4f598-110">Ardından ağaçlarını her ad alanı değiştirir ve tek bir ağacına birleştirir.</span><span class="sxs-lookup"><span data-stu-id="4f598-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="4f598-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="4f598-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4f598-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f598-112">See Also</span></span>  
 [<span data-ttu-id="4f598-113">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f598-113">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
