---
title: Düğümlerle programlama (C#)
description: Düğümlerle programlama hakkında bilgi edinin. Bu, geliştiricilerin öğeleri ve öznitelikleri daha ayrıntılı bir ayrıntı düzeyinde çalışan programlar yazmasını sağlar.
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8a31d6459ab644a682d480239cabc3d88fd7dc14
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301690"
---
# <a name="programming-with-nodes-c"></a><span data-ttu-id="fb687-104">Düğümlerle programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="fb687-104">Programming with Nodes (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb687-105">bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken geliştiriciler genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan programlar yazması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb687-105">developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="fb687-106">Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri ve açıklamaları işlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="fb687-106">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="fb687-107">Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="fb687-107">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="fb687-108">Düğüm ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="fb687-108">Node Details</span></span>  
 <span data-ttu-id="fb687-109">Programlama, düğüm düzeyinde çalışan bir programcı 'nin bilmelidir bir dizi ayrıntı vardır.</span><span class="sxs-lookup"><span data-stu-id="fb687-109">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="fb687-110">XDocument 'in alt öğe düğümlerinin üst özelliği null olarak ayarlandı</span><span class="sxs-lookup"><span data-stu-id="fb687-110">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="fb687-111"><xref:System.Xml.Linq.XObject.Parent%2A>Özelliği <xref:System.Xml.Linq.XElement> üst düğümü değil üst öğeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="fb687-111">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="fb687-112">Öğesinin alt düğümlerinin <xref:System.Xml.Linq.XDocument> üst öğesi yok <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="fb687-112">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="fb687-113">Üst öğesi belgedir, <xref:System.Xml.Linq.XObject.Parent%2A> Bu nedenle bu düğümlerin özelliği null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fb687-113">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="fb687-114">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="fb687-114">The following example demonstrates this:</span></span>  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 <span data-ttu-id="fb687-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-115">This example produces the following output:</span></span>  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="fb687-116">Bitişik metin düğümleri mümkündür</span><span class="sxs-lookup"><span data-stu-id="fb687-116">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="fb687-117">Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="fb687-117">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="fb687-118">Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fb687-118">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb687-119">metin düğümlerini normalleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fb687-119">does not normalize text nodes.</span></span> <span data-ttu-id="fb687-120">Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="fb687-120">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="fb687-121">Ancak, düğüm olarak değil, bir dize olarak belirtilen içeriği eklerseniz <xref:System.Xml.Linq.XText> , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dizeyi bitişik bir metin düğümü ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb687-121">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="fb687-122">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="fb687-122">The following example demonstrates this:</span></span>  
  
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
  
 <span data-ttu-id="fb687-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-123">This example produces the following output:</span></span>  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="fb687-124">Boş metin düğümleri mümkündür</span><span class="sxs-lookup"><span data-stu-id="fb687-124">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="fb687-125">Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="fb687-125">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="fb687-126">Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fb687-126">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="fb687-127">Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.</span><span class="sxs-lookup"><span data-stu-id="fb687-127">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 <span data-ttu-id="fb687-128">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-128">This example produces the following output:</span></span>  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="fb687-129">Boş bir metin düğümü serileştirme etkiler</span><span class="sxs-lookup"><span data-stu-id="fb687-129">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="fb687-130">Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>` .</span><span class="sxs-lookup"><span data-stu-id="fb687-130">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="fb687-131">Bir öğe herhangi bir alt düğüm içermiyorsa, kısa etiket söz dizimi ile serileştirilir: `<Child />` .</span><span class="sxs-lookup"><span data-stu-id="fb687-131">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 <span data-ttu-id="fb687-132">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-132">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="fb687-133">Ad alanları LINQ to XML ağacındaki özniteliklerdir</span><span class="sxs-lookup"><span data-stu-id="fb687-133">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="fb687-134">Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="fb687-134">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="fb687-135">Ancak, içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , ad ALANLARı <xref:System.Xml.Linq.XAttribute> XML ağacında nesneler olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="fb687-135">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="fb687-136">Bir ad alanı bildirimi içeren bir öğe için öznitelikler üzerinde yineleme yaparsanız, ad alanı bildirimini döndürülen koleksiyondaki öğelerden biri olarak görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="fb687-136">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="fb687-137"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>Özelliği, bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fb687-137">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 <span data-ttu-id="fb687-138">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-138">This example produces the following output:</span></span>  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="fb687-139">XPath eksen yöntemleri, XDocument 'in alt boşluk değerini döndürmüyor</span><span class="sxs-lookup"><span data-stu-id="fb687-139">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="fb687-140">metin düğümlerinde yalnızca boşluk bulunduğu sürece alt metin düğümlerine izin verir <xref:System.Xml.Linq.XDocument> .</span><span class="sxs-lookup"><span data-stu-id="fb687-140">allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="fb687-141">Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle eksen kullanarak alt öğeleri üzerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> boşluk metin düğümleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fb687-141">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white-space text nodes will be returned.</span></span> <span data-ttu-id="fb687-142">Ancak, XPath eksen yöntemlerini kullanarak bir öğesinin alt öğelerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> , boşluk metin düğümleri döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="fb687-142">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white-space text nodes will not be returned.</span></span>  
  
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
  
 <span data-ttu-id="fb687-143">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-143">This example produces the following output:</span></span>  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="fb687-144">XDeclaration nesneleri düğüm değil</span><span class="sxs-lookup"><span data-stu-id="fb687-144">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="fb687-145">Bir ' ın alt düğümleri arasında yineleme yaparken <xref:System.Xml.Linq.XDocument> , XML bildirim nesnesini görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb687-145">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="fb687-146">Bunun bir alt düğümü değil, belgenin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="fb687-146">It is a property of the document, not a child node of it.</span></span>  
  
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
  
 <span data-ttu-id="fb687-147">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fb687-147">This example produces the following output:</span></span>  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  