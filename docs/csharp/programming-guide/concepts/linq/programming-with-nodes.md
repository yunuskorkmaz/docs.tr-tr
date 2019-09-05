---
title: Düğümlerle programlama (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8c4c858cbc1fad4041c2e5ce62ca8a01dd1cfb2c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253142"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="2db62-102">Düğümlerle programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="2db62-102">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2db62-103">bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken geliştiriciler genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan programlar yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2db62-103">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="2db62-104">Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri ve açıklamaları işlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="2db62-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="2db62-105">Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="2db62-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="2db62-106">Düğüm ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="2db62-106">Node Details</span></span>  
 <span data-ttu-id="2db62-107">Programlama, düğüm düzeyinde çalışan bir programcı 'nin bilmelidir bir dizi ayrıntı vardır.</span><span class="sxs-lookup"><span data-stu-id="2db62-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="2db62-108">XDocument 'in alt öğe düğümlerinin üst özelliği null olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="2db62-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="2db62-109">Özelliği üst düğümü değil üst <xref:System.Xml.Linq.XElement>öğeyi içerir. <xref:System.Xml.Linq.XObject.Parent%2A></span><span class="sxs-lookup"><span data-stu-id="2db62-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="2db62-110">Öğesinin <xref:System.Xml.Linq.XDocument> alt düğümlerinin üst öğesi <xref:System.Xml.Linq.XElement>yok.</span><span class="sxs-lookup"><span data-stu-id="2db62-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2db62-111">Üst öğesi belgedir, bu nedenle <xref:System.Xml.Linq.XObject.Parent%2A> bu düğümlerin özelliği null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2db62-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="2db62-112">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="2db62-112">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="2db62-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-113">This example produces the following output:</span></span>  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="2db62-114">Bitişik metin düğümleri mümkündür</span><span class="sxs-lookup"><span data-stu-id="2db62-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="2db62-115">Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="2db62-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="2db62-116">Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2db62-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2db62-117">metin düğümlerini normalleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2db62-117">does not normalize text nodes.</span></span> <span data-ttu-id="2db62-118">Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2db62-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="2db62-119">Ancak, <xref:System.Xml.Linq.XText> düğüm olarak değil, bir dize olarak belirtilen içeriği eklerseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dizeyi bitişik bir metin düğümü ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2db62-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="2db62-120">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="2db62-120">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="2db62-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-121">This example produces the following output:</span></span>  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="2db62-122">Boş metin düğümleri mümkündür</span><span class="sxs-lookup"><span data-stu-id="2db62-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="2db62-123">Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="2db62-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="2db62-124">Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2db62-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="2db62-125">Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.</span><span class="sxs-lookup"><span data-stu-id="2db62-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 <span data-ttu-id="2db62-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-126">This example produces the following output:</span></span>  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="2db62-127">Boş bir metin düğümü serileştirme etkiler</span><span class="sxs-lookup"><span data-stu-id="2db62-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="2db62-128">Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>`.</span><span class="sxs-lookup"><span data-stu-id="2db62-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="2db62-129">Bir öğe herhangi bir alt düğüm içermiyorsa, kısa etiket söz dizimi ile serileştirilir: `<Child />`.</span><span class="sxs-lookup"><span data-stu-id="2db62-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 <span data-ttu-id="2db62-130">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="2db62-131">Ad alanları LINQ to XML ağacındaki özniteliklerdir</span><span class="sxs-lookup"><span data-stu-id="2db62-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="2db62-132">Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="2db62-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="2db62-133">Ancak, içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları XML ağacında <xref:System.Xml.Linq.XAttribute> nesneler olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="2db62-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="2db62-134">Bir ad alanı bildirimi içeren bir öğe için öznitelikler üzerinde yineleme yaparsanız, ad alanı bildirimini döndürülen koleksiyondaki öğelerden biri olarak görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="2db62-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="2db62-135">Özelliği <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> , bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2db62-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="2db62-136">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-136">This example produces the following output:</span></span>  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="2db62-137">XPath eksen yöntemleri, XDocument 'in alt boşluk değerini döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="2db62-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2db62-138">metin düğümlerinde yalnızca boşluk bulunduğu sürece alt <xref:System.Xml.Linq.XDocument>metin düğümlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="2db62-138">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="2db62-139">Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> eksen kullanarak alt öğeleri üzerinde yineleme yaptığınızda boşluk metin düğümleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2db62-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="2db62-140">Ancak, XPath eksen yöntemlerini kullanarak bir <xref:System.Xml.Linq.XDocument> öğesinin alt öğelerinde yineleme yaptığınızda, boşluk metin düğümleri döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="2db62-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="2db62-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-141">This example produces the following output:</span></span>  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="2db62-142">XDeclaration nesneleri düğüm değil</span><span class="sxs-lookup"><span data-stu-id="2db62-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="2db62-143">Bir <xref:System.Xml.Linq.XDocument>' ın alt düğümleri arasında yineleme yaparken, XML bildirim nesnesini görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2db62-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="2db62-144">Bunun bir alt düğümü değil, belgenin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2db62-144">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="2db62-145">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2db62-145">This example produces the following output:</span></span>  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  