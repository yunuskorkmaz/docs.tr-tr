---
title: Düğümler (C#) ile programlama
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 92ec8445123a8b685bd6ea134aca0b792cab6d2d
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="62def-102">Düğümler (C#) ile programlama</span><span class="sxs-lookup"><span data-stu-id="62def-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="62def-103"> bir XML Düzenleyicisi, dönüştürme sistem ya da bir rapor yazıcı gibi programlar genellikle yazmak için isteyen geliştiriciler daha hassas bir ayrıntı düzeyinde öğeleri ve özniteliklerinin daha çalışan programlar yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62def-103"> developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="62def-104">Bunlar genellikle metin düğümleri, işleme yönergeleri ve açıklamalar düzenleme düğüm düzeyinde çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62def-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="62def-105">Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="62def-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="62def-106">Düğüm ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="62def-106">Node Details</span></span>  
 <span data-ttu-id="62def-107">Düğüm düzeyinde çalışma Programcı bilmeniz gereken programlama ayrıntılarını mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="62def-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="62def-108">Üst özelliği, alt düğümleri olarak XDocument Null olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="62def-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="62def-109"><xref:System.Xml.Linq.XObject.Parent%2A> Özelliği içeren üst <xref:System.Xml.Linq.XElement>, üst düğümü değil.</span><span class="sxs-lookup"><span data-stu-id="62def-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="62def-110">Alt düğümleri <xref:System.Xml.Linq.XDocument> üst öğeye sahip <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="62def-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="62def-111">Kendi üst belgesidir böylece <xref:System.Xml.Linq.XObject.Parent%2A> düğümleri için özelliği null.</span><span class="sxs-lookup"><span data-stu-id="62def-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="62def-112">Aşağıdaki örnekte bu gösterir:</span><span class="sxs-lookup"><span data-stu-id="62def-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="62def-113">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="62def-114">Bitişik metin düğümleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="62def-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="62def-115">XML programlama modelleri sayısında bitişik metin düğümleri her zaman birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="62def-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="62def-116">Buna bazen metin düğümleri normalleştirme denir.</span><span class="sxs-lookup"><span data-stu-id="62def-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="62def-117"> metin düğümleri normalleştirin değil.</span><span class="sxs-lookup"><span data-stu-id="62def-117"> does not normalize text nodes.</span></span> <span data-ttu-id="62def-118">İki metin düğümleri aynı öğeye eklerseniz, bitişiğindeki metin düğümleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="62def-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="62def-119">Ancak, bir dize olarak yerine olarak belirtilen içeriği eklerseniz, bir <xref:System.Xml.Linq.XText> düğümü [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bitişik metin düğümü dizeyle birleştirmek.</span><span class="sxs-lookup"><span data-stu-id="62def-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="62def-120">Aşağıdaki örnekte bu gösterir:</span><span class="sxs-lookup"><span data-stu-id="62def-120">The following example demonstrates this:</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does not add a new text node  
xmlTree.Add("new content");  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
  
// this does add a new, adjacent text node  
xmlTree.Add(new XText("more text"));  
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());  
```  
  
 <span data-ttu-id="62def-121">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="62def-122">Boş metin düğümleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="62def-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="62def-123">Bazı XML programlama modellerinde metin düğümleri boş dize içermemesi garanti.</span><span class="sxs-lookup"><span data-stu-id="62def-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="62def-124">Bu tür bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmaz mantık olur.</span><span class="sxs-lookup"><span data-stu-id="62def-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="62def-125">Ancak, bitişiğindeki metin düğümler aynı nedenden dolayı değeri boş dize, metin düğümü ayarlayarak metni metin düğüm kaldırırsanız olası silinmez.</span><span class="sxs-lookup"><span data-stu-id="62def-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="62def-126">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="62def-127">Seri hale getirme boş metin düğümü etkiler</span><span class="sxs-lookup"><span data-stu-id="62def-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="62def-128">Bir öğe yalnızca boş bir alt metin düğümü içeriyorsa uzun etiket sözdizimi ile seri değildir: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="62def-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="62def-129">Bir öğe doğabilecek alt düğüm içeriyorsa, kısa etiket sözdizimiyle seri değildir: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="62def-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="62def-130">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="62def-131">Ad alanları öznitelikleridir XML ağacına LINQ</span><span class="sxs-lookup"><span data-stu-id="62def-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="62def-132">Ad alanı bildirimleri XSLT ve XPath, gibi bazı programlama arabirimleri öznitelikleri, aynı sözdizimine sahip olsa da ad alanı bildirimleri öznitelikleri için dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="62def-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="62def-133">Bununla birlikte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları olarak depolanır <xref:System.Xml.Linq.XAttribute> XML ağacında nesneleri.</span><span class="sxs-lookup"><span data-stu-id="62def-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="62def-134">Bir ad alanı bildirimi içeren bir öğesinin özniteliklerini yinelemek, döndürülen koleksiyondaki öğelerin biri olarak ad alanı bildirimi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="62def-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="62def-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Özelliği, bir öznitelik bir ad alanı bildirimi olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62def-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="62def-136">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="62def-137">XPath eksen yöntemleri alt boşluklardan-XDocument döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="62def-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="62def-138"> için alt metin düğümleri sağlayan bir <xref:System.Xml.Linq.XDocument>, metin düğümleri yalnızca boşluk içeremez sürece.</span><span class="sxs-lookup"><span data-stu-id="62def-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="62def-139">Ancak, XPath nesne modeli beyaz alanı bir belgenin alt düğümleri olarak şekilde içermez alt yineleme ne zaman bir <xref:System.Xml.Linq.XDocument> kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> eksen, boşluk metin düğümleri döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="62def-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="62def-140">Ancak, ne zaman, yineleme alt bir <xref:System.Xml.Linq.XDocument> XPath eksen yöntemleri kullanarak, boşluk metin düğümleri olmayan döndürülür.</span><span class="sxs-lookup"><span data-stu-id="62def-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
```csharp  
// Create a document with some white-space child nodes of the document.  
XDocument root = XDocument.Parse(  
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
  
<Root/>  
  
<!--a comment-->  
", LoadOptions.PreserveWhitespace);  
  
// count the white-space child nodes using LINQ to XML  
Console.WriteLine(root.Nodes().OfType<XText>().Count());  
  
// count the white-space child nodes using XPathEvaluate  
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());   
```  
  
 <span data-ttu-id="62def-141">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="62def-142">XDeclaration nesneleri düğümleri olmayan</span><span class="sxs-lookup"><span data-stu-id="62def-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="62def-143">Yineleme zaman alt öğe düğümlerinin bir <xref:System.Xml.Linq.XDocument>, XML bildirimi nesnesi görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="62def-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="62def-144">Belgenin alt düğümü değil bunu bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="62def-144">It is a property of the document, not a child node of it.</span></span>  
  
```csharp  
XDocument doc = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root")  
);  
doc.Save("Temp.xml");  
Console.WriteLine(File.ReadAllText("Temp.xml"));  
  
// this shows that there is only one child node of the document  
Console.WriteLine(doc.Nodes().Count());  
```  
  
 <span data-ttu-id="62def-145">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="62def-145">This example produces the following output:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="62def-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62def-146">See Also</span></span>  
 [<span data-ttu-id="62def-147">Gelişmiş LINQ-XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="62def-147">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
