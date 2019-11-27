---
title: Düğümlerle Programlama
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 447c462f95536cd40291f9b0d54ab85dcde200db
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346635"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="69cb6-102">Düğümlerle programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69cb6-102">Programming with Nodes (Visual Basic)</span></span>
<span data-ttu-id="69cb6-103">bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştiricilerin genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan programlar yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="69cb6-104">Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri ve açıklamaları işlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="69cb6-105">Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="69cb6-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="69cb6-106">Düğüm ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="69cb6-106">Node Details</span></span>  
 <span data-ttu-id="69cb6-107">Programlama, düğüm düzeyinde çalışan bir programcı 'nin bilmelidir bir dizi ayrıntı vardır.</span><span class="sxs-lookup"><span data-stu-id="69cb6-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="69cb6-108">XDocument 'in alt öğe düğümlerinin üst özelliği null olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="69cb6-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="69cb6-109"><xref:System.Xml.Linq.XObject.Parent%2A> özelliği üst düğümü değil üst <xref:System.Xml.Linq.XElement>içerir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="69cb6-110"><xref:System.Xml.Linq.XDocument> alt düğümlerinin üst <xref:System.Xml.Linq.XElement>yok.</span><span class="sxs-lookup"><span data-stu-id="69cb6-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="69cb6-111">Üst öğesi belgedir, bu nedenle bu düğümlerin <xref:System.Xml.Linq.XObject.Parent%2A> özelliği null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="69cb6-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="69cb6-112">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="69cb6-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-113">This example produces the following output:</span></span>  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="69cb6-114">Bitişik metin düğümleri mümkündür</span><span class="sxs-lookup"><span data-stu-id="69cb6-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="69cb6-115">Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="69cb6-116">Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="69cb6-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="69cb6-117">metin düğümlerini normalleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="69cb6-117">does not normalize text nodes.</span></span> <span data-ttu-id="69cb6-118">Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="69cb6-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="69cb6-119">Ancak, bir <xref:System.Xml.Linq.XText> düğümü yerine bir dize olarak belirtilen içeriği eklerseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dizeyi bitişik bir metin düğümüyle birleştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="69cb6-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="69cb6-120">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-120">The following example demonstrates this:</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="69cb6-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-121">This example produces the following output:</span></span>  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="69cb6-122">Boş metin düğümleri mümkündür</span><span class="sxs-lookup"><span data-stu-id="69cb6-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="69cb6-123">Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="69cb6-124">Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="69cb6-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="69cb6-125">Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.</span><span class="sxs-lookup"><span data-stu-id="69cb6-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="69cb6-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-126">This example produces the following output:</span></span>  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="69cb6-127">Boş bir metin düğümü serileştirme etkiler</span><span class="sxs-lookup"><span data-stu-id="69cb6-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="69cb6-128">Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="69cb6-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="69cb6-129">Bir öğe bir alt düğüm içermiyorsa, bu, kısa etiket sözdizimi ile serileştirilir: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="69cb6-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="69cb6-130">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="69cb6-131">Ad alanları LINQ to XML ağacındaki özniteliklerdir</span><span class="sxs-lookup"><span data-stu-id="69cb6-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="69cb6-132">Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="69cb6-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="69cb6-133">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]' de, ad alanları XML ağacında <xref:System.Xml.Linq.XAttribute> nesneler olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="69cb6-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="69cb6-134">Bir ad alanı bildirimi içeren bir öğe için öznitelikler üzerinde yineleme yaparsanız, ad alanı bildirimini döndürülen koleksiyondaki öğelerden biri olarak görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="69cb6-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="69cb6-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> özelliği bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 <span data-ttu-id="69cb6-136">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-136">This example produces the following output:</span></span>  
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="69cb6-137">XPath eksen yöntemleri, XDocument 'in alt boşluk değerini döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="69cb6-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 <span data-ttu-id="69cb6-138">metin düğümleri yalnızca boşluk içerdiği sürece, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XDocument>alt metin düğümlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-138">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="69cb6-139">Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle <xref:System.Xml.Linq.XContainer.Nodes%2A> eksenini kullanarak bir <xref:System.Xml.Linq.XDocument> alt öğelerinde yineleme yaptığınızda boşluk metin düğümleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="69cb6-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="69cb6-140">Ancak, XPath eksen yöntemlerini kullanarak bir <xref:System.Xml.Linq.XDocument> alt öğelerinde yineleme yaparken boşluk metin düğümleri döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="69cb6-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="69cb6-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-141">This example produces the following output:</span></span>  
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="69cb6-142">XDeclaration nesneleri düğüm değil</span><span class="sxs-lookup"><span data-stu-id="69cb6-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="69cb6-143">Bir <xref:System.Xml.Linq.XDocument>alt düğümleri arasında yineleme yaparken, XML bildirim nesnesini görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="69cb6-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="69cb6-144">Bunun bir alt düğümü değil, belgenin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="69cb6-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="69cb6-145">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="69cb6-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="69cb6-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69cb6-146">See also</span></span>

- [<span data-ttu-id="69cb6-147">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69cb6-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
