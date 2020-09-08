---
title: Düğümlerle programlama-LINQ to XML
description: Bir XML ağacının düğüm düzeyinde nasıl kod kullanacağınızı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 8f9d5c8656a06a9b40a3833aaf7e190b9ba3f0a6
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553285"
---
# <a name="programming-with-nodes-linq-to-xml"></a><span data-ttu-id="e56aa-103">Düğümlerle programlama (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e56aa-103">Programming with nodes (LINQ to XML)</span></span>

<span data-ttu-id="e56aa-104">Bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken LINQ to XML geliştiricilerin genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan koda ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="e56aa-104">LINQ to XML developers who need to write programs such as an XML editor, a transform system, or a report writer often need code that works at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="e56aa-105">Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri işlemek ve yorumları işlemek gerekir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-105">They often need to work at the node level, manipulating text nodes, processing instructions, and processing comments.</span></span> <span data-ttu-id="e56aa-106">Bu makalede düğüm düzeyinde programlama hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e56aa-106">This article provides information about programming at the node level.</span></span>

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a><span data-ttu-id="e56aa-107">Örnek: `Parent` XDocument öğesinin alt düğümlerinin özellik değerleri şu şekilde ayarlanır: `null`</span><span class="sxs-lookup"><span data-stu-id="e56aa-107">Example: The `Parent` property values of the child nodes of XDocument are set to `null`</span></span>

<span data-ttu-id="e56aa-108"><xref:System.Xml.Linq.XObject.Parent%2A>Özelliği <xref:System.Xml.Linq.XElement> üst düğümü değil üst öğeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-108">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="e56aa-109">Öğesinin alt düğümlerinin <xref:System.Xml.Linq.XDocument> üst öğesi yok <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="e56aa-109">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e56aa-110">Üst öğesi belgedir, <xref:System.Xml.Linq.XObject.Parent%2A> Bu nedenle bu düğümlerin özelliği olarak ayarlanır `null` .</span><span class="sxs-lookup"><span data-stu-id="e56aa-110">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to `null`.</span></span>

<span data-ttu-id="e56aa-111">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-111">The following example demonstrates this:</span></span>

```csharp
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);
Console.WriteLine(doc.Root.Parent == null);
```

```vb
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)
Console.WriteLine(doc.Root.Parent Is Nothing)
```

<span data-ttu-id="e56aa-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-112">This example produces the following output:</span></span>

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a><span data-ttu-id="e56aa-113">Örnek: metin ekleme, yeni bir metin düğümü oluşturabilir veya oluşturmayabilir</span><span class="sxs-lookup"><span data-stu-id="e56aa-113">Example: Adding text may or may not create a new text node</span></span>

<span data-ttu-id="e56aa-114">Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-114">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="e56aa-115">Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e56aa-115">This is sometimes called normalization of text nodes.</span></span> <span data-ttu-id="e56aa-116">LINQ to XML metin düğümlerini normalleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="e56aa-116">LINQ to XML doesn't normalize text nodes.</span></span> <span data-ttu-id="e56aa-117">Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur.</span><span class="sxs-lookup"><span data-stu-id="e56aa-117">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="e56aa-118">Ancak, düğüm olarak değil, bir dize olarak belirtilen içeriği eklerseniz <xref:System.Xml.Linq.XText> , LINQ to XML dizeyi bitişik bir metin düğümü ile birleştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="e56aa-118">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, LINQ to XML might merge the string with an adjacent text node.</span></span> <span data-ttu-id="e56aa-119">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-119">The following example demonstrates this.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");

Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this doesn't add a new text node
xmlTree.Add("new content");
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());

// this does add a new, adjacent text node
xmlTree.Add(new XText("more text"));
Console.WriteLine(xmlTree.Nodes().OfType<XText>().Count());
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

' This doesn't add a new text node.
xmlTree.Add("new content")
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())

'// This does add a new, adjacent text node.
xmlTree.Add(New XText("more text"))
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())
```

 <span data-ttu-id="e56aa-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-120">This example produces the following output:</span></span>

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a><span data-ttu-id="e56aa-121">Örnek: bir metin düğümü değeri boş dizeye ayarlandığında düğüm silinmez</span><span class="sxs-lookup"><span data-stu-id="e56aa-121">Example: Setting a text node value to the empty string doesn't delete the node</span></span>

<span data-ttu-id="e56aa-122">Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-122">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="e56aa-123">Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e56aa-123">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="e56aa-124">Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.</span><span class="sxs-lookup"><span data-stu-id="e56aa-124">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself won't be deleted.</span></span>

```csharp
XElement xmlTree = new XElement("Root", "Content");
XText textNode = xmlTree.Nodes().OfType<XText>().First();

// the following line doesn't cause the removal of the text node.
textNode.Value = "";

XText textNode2 = xmlTree.Nodes().OfType<XText>().First();
Console.WriteLine(">>{0}<<", textNode2);
```

```vb
Dim xmlTree As XElement = <Root>Content</Root>
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()

' The following line doesn't cause the removal of the text node.
textNode.Value = ""

Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()
Console.WriteLine(">>{0}<<", textNode2)
```

<span data-ttu-id="e56aa-125">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-125">This example produces the following output:</span></span>

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a><span data-ttu-id="e56aa-126">Örnek: boş bir metin düğümü olan bir öğe, metin düğümü olmayan bir öğeden farklı şekilde serileştirilir</span><span class="sxs-lookup"><span data-stu-id="e56aa-126">Example: An element with one empty text node is serialized differently from one with no text node</span></span>

<span data-ttu-id="e56aa-127">Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>` .</span><span class="sxs-lookup"><span data-stu-id="e56aa-127">If an element contains only a child text node that's empty, it's serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="e56aa-128">Bir öğe bir alt düğüm içermiyorsa, bu, kısa etiket söz dizimi ile serileştirilir: `<Child />` .</span><span class="sxs-lookup"><span data-stu-id="e56aa-128">If an element contains no child nodes whatsoever, it's serialized with the short tag syntax: `<Child />`.</span></span>

```csharp
XElement child1 = new XElement("Child1",
    new XText("")
);
XElement child2 = new XElement("Child2");
Console.WriteLine(child1);
Console.WriteLine(child2);
```

```vb
Dim child1 As XElement = New XElement("Child1", _
    New XText("") _
)
Dim child2 As XElement = New XElement("Child2")
Console.WriteLine(child1)
Console.WriteLine(child2)
```

<span data-ttu-id="e56aa-129">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-129">This example produces the following output:</span></span>

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="e56aa-130">Örnek: ad alanları LINQ to XML ağacındaki özniteliklerdir</span><span class="sxs-lookup"><span data-stu-id="e56aa-130">Example: Namespaces are attributes in the LINQ to XML tree</span></span>

<span data-ttu-id="e56aa-131">Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="e56aa-131">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations aren't considered to be attributes.</span></span> <span data-ttu-id="e56aa-132">Ancak, LINQ to XML ' de, ad alanları <xref:System.Xml.Linq.XAttribute> XML ağacında nesneler olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e56aa-132">However, in LINQ to XML, namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="e56aa-133">Bir ad alanı bildirimi içeren bir öğenin özniteliklerinde yineleme yaparsanız, ad alanı bildirimi döndürülen koleksiyondaki öğelerden biridir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-133">If you iterate through the attributes of an element that contains a namespace declaration, the namespace declaration is one of the items in the returned collection.</span></span> <span data-ttu-id="e56aa-134"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>Özelliği, bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-134">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root
    xmlns='http://www.adventure-works.com'
    xmlns:fc='www.fourthcoffee.com'
    AnAttribute='abc'/>");
foreach (XAttribute att in root.Attributes())
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);
```

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

<span data-ttu-id="e56aa-135">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-135">This example produces the following output:</span></span>

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a><span data-ttu-id="e56aa-136">Örnek: XPath eksen yöntemleri, XDocument 'in alt metin düğümlerini döndürmez</span><span class="sxs-lookup"><span data-stu-id="e56aa-136">Example: XPath axis methods don't return the child text nodes of XDocument</span></span>

<span data-ttu-id="e56aa-137"><xref:System.Xml.Linq.XDocument>Metin düğümlerinde yalnızca boşluk bulunduğu sürece, LINQ to XML alt metin düğümlerine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-137">LINQ to XML allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="e56aa-138">Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle eksen kullanarak alt öğeleri üzerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> boşluk metin düğümleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e56aa-138">However, the XPath object model doesn't include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="e56aa-139">Ancak, XPath eksen yöntemlerini kullanarak bir öğesinin alt öğelerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> boşluk metin düğümleri döndürülmez.</span><span class="sxs-lookup"><span data-stu-id="e56aa-139">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes won't be returned.</span></span>

```csharp
// Create a document with some white space child nodes of the document.
XDocument root = XDocument.Parse(
@"<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<Root/>

<!--a comment-->
", LoadOptions.PreserveWhitespace);

// count the white space child nodes using LINQ to XML
Console.WriteLine(root.Nodes().OfType<XText>().Count());

// count the white space child nodes using XPathEvaluate
Console.WriteLine(((IEnumerable)root.XPathEvaluate("text()")).OfType<XText>().Count());
```

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

<span data-ttu-id="e56aa-140">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-140">This example produces the following output:</span></span>

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a><span data-ttu-id="e56aa-141">Bir XDocument 'in XML bildirimi düğümü bir alt düğüm değil, bir özelliktir</span><span class="sxs-lookup"><span data-stu-id="e56aa-141">The XML declaration node of an XDocument is a property, not a child node</span></span>

<span data-ttu-id="e56aa-142">Bir öğesinin alt düğümlerinde yineleme yaparken <xref:System.Xml.Linq.XDocument> , XML bildirim nesnesini görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e56aa-142">When you iterate through the child nodes of an <xref:System.Xml.Linq.XDocument>, you won't see the XML declaration object.</span></span> <span data-ttu-id="e56aa-143">Bunun bir alt düğümü değil, belgenin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e56aa-143">It's a property of the document, not a child node of it.</span></span>

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

```vb
Dim doc As XDocument = _
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<Root/>

doc.Save("Temp.xml")
Console.WriteLine(File.ReadAllText("Temp.xml"))

' This shows that there is only one child node of the document.
Console.WriteLine(doc.Nodes().Count())
```

<span data-ttu-id="e56aa-144">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e56aa-144">This example produces the following output:</span></span>

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
