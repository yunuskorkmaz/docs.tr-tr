---
title: Düğümlerle Programlama
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 9c64c348f5d26172f26593b927e6bc24baf365bf
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794409"
---
# <a name="programming-with-nodes-visual-basic"></a>Düğümlerle programlama (Visual Basic)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken geliştiriciler genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan programlar yazması gerekir. Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri ve açıklamaları işlemek gerekir. Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm ayrıntıları  
 Programlama, düğüm düzeyinde çalışan bir programcı 'nin bilmelidir bir dizi ayrıntı vardır.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>XDocument 'in alt öğe düğümlerinin üst özelliği null olarak ayarlandı  
 <xref:System.Xml.Linq.XObject.Parent%2A> Özelliği üst düğümü değil üst <xref:System.Xml.Linq.XElement>öğeyi içerir. Öğesinin <xref:System.Xml.Linq.XDocument> alt düğümlerinin üst öğesi <xref:System.Xml.Linq.XElement>yok. Üst öğesi belgedir, bu nedenle bu düğümlerin <xref:System.Xml.Linq.XObject.Parent%2A> özelliği null olarak ayarlanır.  
  
 Aşağıdaki örnek şunu gösterir:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik metin düğümleri mümkündür  
 Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir. Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]metin düğümlerini normalleştirilemez. Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur. Ancak, <xref:System.Xml.Linq.XText> düğüm olarak değil, bir dize olarak belirtilen içeriği eklerseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dizeyi bitişik bir metin düğümü ile birleştirebilirsiniz.  
  
 Aşağıdaki örnek şunu gösterir:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş metin düğümleri mümkündür  
 Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir. Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur. Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```console  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Boş bir metin düğümü serileştirme etkiler  
 Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>`. Bir öğe herhangi bir alt düğüm içermiyorsa, kısa etiket söz dizimi ile serileştirilir: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Ad alanları LINQ to XML ağacındaki özniteliklerdir  
 Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak kabul edilmez. Ancak, içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları XML ağacında <xref:System.Xml.Linq.XAttribute> nesneler olarak depolanır. Bir ad alanı bildirimi içeren bir öğe için öznitelikler üzerinde yineleme yaparsanız, ad alanı bildirimini döndürülen koleksiyondaki öğelerden biri olarak görürsünüz.  
  
 Özelliği <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> , bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.  
  
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
  
```console  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath eksen yöntemleri, XDocument 'in alt boşluk değerini döndürmüyor  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]metin düğümlerinde yalnızca boşluk bulunduğu sürece alt <xref:System.Xml.Linq.XDocument>metin düğümlerine izin verir. Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> eksen kullanarak alt öğeleri üzerinde yineleme yaptığınızda boşluk metin düğümleri döndürülür. Ancak, XPath eksen yöntemlerini kullanarak bir <xref:System.Xml.Linq.XDocument> öğesinin alt öğelerinde yineleme yaptığınızda boşluk metin düğümleri döndürülmez.  
  
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
  
```console  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration nesneleri düğüm değil  
 Bir <xref:System.Xml.Linq.XDocument>' ın alt düğümleri arasında yineleme yaparken, XML bildirim nesnesini görmezsiniz. Bunun bir alt düğümü değil, belgenin bir özelliğidir.  
  
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
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />
1
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş LINQ to XML Programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
