---
title: Düğümler (Visual Basic) ile programlama
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 871755ef0293513f07c60b1d5735c47692163b78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648352"
---
# <a name="programming-with-nodes-visual-basic"></a>Düğümler (Visual Basic) ile programlama
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML Düzenleyicisi, dönüştürme sistem ya da bir rapor yazıcı gibi programlar genellikle yazmak için isteyen geliştiriciler daha hassas bir ayrıntı düzeyinde öğeleri ve özniteliklerinin daha çalışan programlar yazmanız gerekir. Bunlar genellikle metin düğümleri, işleme yönergeleri ve açıklamalar düzenleme düğüm düzeyinde çalışması gerekir. Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm ayrıntıları  
 Düğüm düzeyinde çalışma Programcı bilmeniz gereken programlama ayrıntılarını mevcuttur.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Üst özelliği, alt düğümleri olarak XDocument Null olarak ayarlandı  
 <xref:System.Xml.Linq.XObject.Parent%2A> Özelliği içeren üst <xref:System.Xml.Linq.XElement>, üst düğümü değil. Alt düğümleri <xref:System.Xml.Linq.XDocument> üst öğeye sahip <xref:System.Xml.Linq.XElement>. Kendi üst belgesidir böylece <xref:System.Xml.Linq.XObject.Parent%2A> düğümleri için özelliği null.  
  
 Aşağıdaki örnekte bu gösterir:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik metin düğümleri mümkündür.  
 XML programlama modelleri sayısında bitişik metin düğümleri her zaman birleştirilir. Buna bazen metin düğümleri normalleştirme denir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metin düğümleri normalleştirin değil. İki metin düğümleri aynı öğeye eklerseniz, bitişiğindeki metin düğümleri neden olur. Ancak, bir dize olarak yerine olarak belirtilen içeriği eklerseniz, bir <xref:System.Xml.Linq.XText> düğümü [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bitişik metin düğümü dizeyle birleştirmek.  
  
 Aşağıdaki örnekte bu gösterir:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş metin düğümleri mümkündür.  
 Bazı XML programlama modellerinde metin düğümleri boş dize içermemesi garanti. Bu tür bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmaz mantık olur. Ancak, bitişiğindeki metin düğümler aynı nedenden dolayı değeri boş dize, metin düğümü ayarlayarak metni metin düğüm kaldırırsanız olası silinmez.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Seri hale getirme boş metin düğümü etkiler  
 Bir öğe yalnızca boş bir alt metin düğümü içeriyorsa uzun etiket sözdizimi ile seri değildir: `<Child></Child>`. Bir öğe doğabilecek alt düğüm içeriyorsa, kısa etiket sözdizimiyle seri değildir: `<Child />`.  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Ad alanları öznitelikleridir XML ağacına LINQ  
 Ad alanı bildirimleri XSLT ve XPath, gibi bazı programlama arabirimleri öznitelikleri, aynı sözdizimine sahip olsa da ad alanı bildirimleri öznitelikleri için dikkate alınmaz. Bununla birlikte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları olarak depolanır <xref:System.Xml.Linq.XAttribute> XML ağacında nesneleri. Bir ad alanı bildirimi içeren bir öğesinin özniteliklerini yinelemek, döndürülen koleksiyondaki öğelerin biri olarak ad alanı bildirimi görürsünüz.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Özelliği, bir öznitelik bir ad alanı bildirimi olup olmadığını belirtir.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath eksen yöntemleri alt boşluklardan-XDocument döndürmüyor  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için alt metin düğümleri sağlayan bir <xref:System.Xml.Linq.XDocument>, metin düğümleri yalnızca boşluk içeremez sürece. Ancak, XPath nesne modeli beyaz alanı bir belgenin alt düğümleri olarak şekilde içermez alt yineleme ne zaman bir <xref:System.Xml.Linq.XDocument> kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> eksen, boşluk metin düğümleri döndürülecek. Ancak, ne zaman, yineleme alt bir <xref:System.Xml.Linq.XDocument> XPath eksen yöntemleri kullanarak, boşluk metin düğümleri olmayan döndürülür.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration nesneleri düğümleri olmayan  
 Yineleme zaman alt öğe düğümlerinin bir <xref:System.Xml.Linq.XDocument>, XML bildirimi nesnesi görmezsiniz. Belgenin alt düğümü değil bunu bir özelliktir.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
