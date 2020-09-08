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
# <a name="programming-with-nodes-linq-to-xml"></a>Düğümlerle programlama (LINQ to XML)

Bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken LINQ to XML geliştiricilerin genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan koda ihtiyacı vardır. Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri işlemek ve yorumları işlemek gerekir. Bu makalede düğüm düzeyinde programlama hakkında bilgi sağlanır.

## <a name="example-the-parent-property-values-of-the-child-nodes-of-xdocument-are-set-to-null"></a>Örnek: `Parent` XDocument öğesinin alt düğümlerinin özellik değerleri şu şekilde ayarlanır: `null`

<xref:System.Xml.Linq.XObject.Parent%2A>Özelliği <xref:System.Xml.Linq.XElement> üst düğümü değil üst öğeyi içerir. Öğesinin alt düğümlerinin <xref:System.Xml.Linq.XDocument> üst öğesi yok <xref:System.Xml.Linq.XElement> . Üst öğesi belgedir, <xref:System.Xml.Linq.XObject.Parent%2A> Bu nedenle bu düğümlerin özelliği olarak ayarlanır `null` .

Aşağıdaki örnek şunu gösterir:

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
True
True
```

## <a name="example-adding-text-may-or-may-not-create-a-new-text-node"></a>Örnek: metin ekleme, yeni bir metin düğümü oluşturabilir veya oluşturmayabilir

Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir. Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır. LINQ to XML metin düğümlerini normalleştirilemiyor. Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur. Ancak, düğüm olarak değil, bir dize olarak belirtilen içeriği eklerseniz <xref:System.Xml.Linq.XText> , LINQ to XML dizeyi bitişik bir metin düğümü ile birleştirebilirler. Aşağıdaki örnek bunu gösterir.

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

 Bu örnek aşağıdaki çıktıyı üretir:

```output
1
1
2
```

## <a name="example-setting-a-text-node-value-to-the-empty-string-doesnt-delete-the-node"></a>Örnek: bir metin düğümü değeri boş dizeye ayarlandığında düğüm silinmez

Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir. Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur. Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
>><<
```

## <a name="example-an-element-with-one-empty-text-node-is-serialized-differently-from-one-with-no-text-node"></a>Örnek: boş bir metin düğümü olan bir öğe, metin düğümü olmayan bir öğeden farklı şekilde serileştirilir

Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>` . Bir öğe bir alt düğüm içermiyorsa, bu, kısa etiket söz dizimi ile serileştirilir: `<Child />` .

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

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Child1></Child1>
<Child2 />
```

## <a name="example-namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Örnek: ad alanları LINQ to XML ağacındaki özniteliklerdir

Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak değerlendirilmez. Ancak, LINQ to XML ' de, ad alanları <xref:System.Xml.Linq.XAttribute> XML ağacında nesneler olarak depolanır. Bir ad alanı bildirimi içeren bir öğenin özniteliklerinde yineleme yaparsanız, ad alanı bildirimi döndürülen koleksiyondaki öğelerden biridir. <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>Özelliği, bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True
AnAttribute="abc"  IsNamespaceDeclaration:False
```

## <a name="example-xpath-axis-methods-dont-return-the-child-text-nodes-of-xdocument"></a>Örnek: XPath eksen yöntemleri, XDocument 'in alt metin düğümlerini döndürmez

<xref:System.Xml.Linq.XDocument>Metin düğümlerinde yalnızca boşluk bulunduğu sürece, LINQ to XML alt metin düğümlerine izin verir. Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle eksen kullanarak alt öğeleri üzerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> boşluk metin düğümleri döndürülür. Ancak, XPath eksen yöntemlerini kullanarak bir öğesinin alt öğelerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> boşluk metin düğümleri döndürülmez.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
3
0
```

### <a name="the-xml-declaration-node-of-an-xdocument-is-a-property-not-a-child-node"></a>Bir XDocument 'in XML bildirimi düğümü bir alt düğüm değil, bir özelliktir

Bir öğesinin alt düğümlerinde yineleme yaparken <xref:System.Xml.Linq.XDocument> , XML bildirim nesnesini görmezsiniz. Bunun bir alt düğümü değil, belgenin bir özelliğidir.

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

Bu örnek aşağıdaki çıktıyı üretir:

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<Root />
1
```
