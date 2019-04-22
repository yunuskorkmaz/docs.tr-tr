---
title: (Visual Basic) düğümlerle programlama
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: ed7f460b441a5973c33841f1f53ce4679b627071
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817116"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="bc683-102">(Visual Basic) düğümlerle programlama</span><span class="sxs-lookup"><span data-stu-id="bc683-102">Programming with Nodes (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="bc683-103">öğeler ve öznitelikler daha hassas bir düzeyde ayrıntı çalışan programları yazmak bir XML Düzenleyicisi, bir dönüştürme sistemi veya bir rapor yazıcı gibi programlar genellikle yazmanız gereken geliştiriciler gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc683-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="bc683-104">Bunlar genellikle metin düğümleri, işleme yönergeleri ve açıklamaları düzenleme düğüm düzeyinde çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bc683-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="bc683-105">Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc683-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="bc683-106">Düğüm ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="bc683-106">Node Details</span></span>  
 <span data-ttu-id="bc683-107">Bir dizi düğümü düzeyinde çalışan Programcı bilmeniz gereken programlama ayrıntılarını vardır.</span><span class="sxs-lookup"><span data-stu-id="bc683-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="bc683-108">Üst özellik, alt düğümleri, XDocument Null olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="bc683-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="bc683-109"><xref:System.Xml.Linq.XObject.Parent%2A> Özelliği içeren üst <xref:System.Xml.Linq.XElement>, üst düğümü değil.</span><span class="sxs-lookup"><span data-stu-id="bc683-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="bc683-110">Alt düğümleri <xref:System.Xml.Linq.XDocument> üst sahip <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="bc683-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bc683-111">Üst belge olduğu şekilde <xref:System.Xml.Linq.XObject.Parent%2A> düğümleri için özelliği null.</span><span class="sxs-lookup"><span data-stu-id="bc683-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="bc683-112">Aşağıdaki örnek bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="bc683-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="bc683-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="bc683-114">Bitişik metin düğümleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bc683-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="bc683-115">Bir XML programlama modelleri sayısında bitişik metin düğümleri her zaman birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bc683-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="bc683-116">Bu, bazen metin düğümleri normalleştirmesini denir.</span><span class="sxs-lookup"><span data-stu-id="bc683-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="bc683-117">metin düğümleri Normalleştir değil.</span><span class="sxs-lookup"><span data-stu-id="bc683-117">does not normalize text nodes.</span></span> <span data-ttu-id="bc683-118">İki metin düğümleri aynı öğe eklerseniz, bitişik metin düğümleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="bc683-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="bc683-119">Ancak, bir dize yerine olarak belirtilen içeriği eklerseniz bir <xref:System.Xml.Linq.XText> düğümünün [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bitişiğindeki metin düğümü ile dize birleştirme.</span><span class="sxs-lookup"><span data-stu-id="bc683-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="bc683-120">Aşağıdaki örnek bunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="bc683-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="bc683-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="bc683-122">Boş metin düğümleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="bc683-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="bc683-123">Bazı XML programlama modellerinde metin düğümleri boş dize içermiyor garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="bc683-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="bc683-124">Mantık gibi bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="bc683-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="bc683-125">Ancak, bitişiğindeki metin düğümleri aynı nedenden dolayı boş dize olarak metin düğümü değerine ayarlayarak metnin bir metin düğümü kaldırırsanız mümkün silinmez.</span><span class="sxs-lookup"><span data-stu-id="bc683-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="bc683-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="bc683-127">Boş metin düğümü serileştirme etkiler.</span><span class="sxs-lookup"><span data-stu-id="bc683-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="bc683-128">Yalnızca boş bir alt metin düğümü bir öğe içeriyorsa, ile uzun etiket sözdizimi serileştirildiği: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="bc683-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="bc683-129">Kullanılabilir alt düğümler olmadan bir öğe içeriyorsa, kısa etiket sözdizimi ile serileştirildiği: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="bc683-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="bc683-130">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="bc683-131">Öznitelikleridir LINQ to XML ağacının ad alanları</span><span class="sxs-lookup"><span data-stu-id="bc683-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="bc683-132">Ad alanı bildirimi, XSLT ve XPath, gibi bazı programlama arabirimlerinde öznitelikleri aynı sözdizimine sahip olsa bile ad alanı bildirimi öznitelikler için dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="bc683-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="bc683-133">Bununla birlikte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları olarak depolanır <xref:System.Xml.Linq.XAttribute> XML ağacı nesneleri.</span><span class="sxs-lookup"><span data-stu-id="bc683-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="bc683-134">Bir ad alanı bildirimi içeren bir öğesi için öznitelikleri yinelemek, döndürülen koleksiyon öğeleri biri olarak ad alanı bildirimi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bc683-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="bc683-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Özelliği bir öznitelik ad alanı bildirimi olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bc683-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
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
  
 <span data-ttu-id="bc683-136">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="bc683-137">XPath eksen yöntemleri XDocument alt boşluk döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="bc683-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="bc683-138">için alt metin düğümleri sağlayan bir <xref:System.Xml.Linq.XDocument>metin düğümleri yalnızca boşluk içeren sürece.</span><span class="sxs-lookup"><span data-stu-id="bc683-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="bc683-139">Ancak, XPath nesne modeli boşluk bir belgenin alt düğümleri olarak bu nedenle içermez alt yineleme ne zaman bir <xref:System.Xml.Linq.XDocument> kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> ekseni metin düğümleri boşluk döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bc683-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="bc683-140">Ancak, ne zaman, yineleme alt bir <xref:System.Xml.Linq.XDocument> XPath eksen yöntemleri kullanarak metin düğümleri boşluk olmayan döndürülür.</span><span class="sxs-lookup"><span data-stu-id="bc683-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="bc683-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="bc683-142">XDeclaration nesneleri düğümleri olmayan</span><span class="sxs-lookup"><span data-stu-id="bc683-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="bc683-143">Alt düğümleri yineleme yaptığınızda bir <xref:System.Xml.Linq.XDocument>, XML bildirimi nesne görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc683-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="bc683-144">Alt düğümü değil, bu belgenin bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="bc683-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="bc683-145">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bc683-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc683-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc683-146">See also</span></span>

- [<span data-ttu-id="bc683-147">Gelişmiş LINQ to XML programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc683-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
