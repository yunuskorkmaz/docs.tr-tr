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
# <a name="programming-with-nodes-visual-basic"></a>(Visual Basic) düğümlerle programlama
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeler ve öznitelikler daha hassas bir düzeyde ayrıntı çalışan programları yazmak bir XML Düzenleyicisi, bir dönüştürme sistemi veya bir rapor yazıcı gibi programlar genellikle yazmanız gereken geliştiriciler gerekir. Bunlar genellikle metin düğümleri, işleme yönergeleri ve açıklamaları düzenleme düğüm düzeyinde çalışması gerekir. Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm ayrıntıları  
 Bir dizi düğümü düzeyinde çalışan Programcı bilmeniz gereken programlama ayrıntılarını vardır.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Üst özellik, alt düğümleri, XDocument Null olarak ayarlandı  
 <xref:System.Xml.Linq.XObject.Parent%2A> Özelliği içeren üst <xref:System.Xml.Linq.XElement>, üst düğümü değil. Alt düğümleri <xref:System.Xml.Linq.XDocument> üst sahip <xref:System.Xml.Linq.XElement>. Üst belge olduğu şekilde <xref:System.Xml.Linq.XObject.Parent%2A> düğümleri için özelliği null.  
  
 Aşağıdaki örnek bunu gösterir:  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik metin düğümleri mümkündür.  
 Bir XML programlama modelleri sayısında bitişik metin düğümleri her zaman birleştirilir. Bu, bazen metin düğümleri normalleştirmesini denir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metin düğümleri Normalleştir değil. İki metin düğümleri aynı öğe eklerseniz, bitişik metin düğümleri neden olur. Ancak, bir dize yerine olarak belirtilen içeriği eklerseniz bir <xref:System.Xml.Linq.XText> düğümünün [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bitişiğindeki metin düğümü ile dize birleştirme.  
  
 Aşağıdaki örnek bunu gösterir:  
  
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
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş metin düğümleri mümkündür.  
 Bazı XML programlama modellerinde metin düğümleri boş dize içermiyor garanti edilir. Mantık gibi bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmasıdır. Ancak, bitişiğindeki metin düğümleri aynı nedenden dolayı boş dize olarak metin düğümü değerine ayarlayarak metnin bir metin düğümü kaldırırsanız mümkün silinmez.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Boş metin düğümü serileştirme etkiler.  
 Yalnızca boş bir alt metin düğümü bir öğe içeriyorsa, ile uzun etiket sözdizimi serileştirildiği: `<Child></Child>`. Kullanılabilir alt düğümler olmadan bir öğe içeriyorsa, kısa etiket sözdizimi ile serileştirildiği: `<Child />`.  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Öznitelikleridir LINQ to XML ağacının ad alanları  
 Ad alanı bildirimi, XSLT ve XPath, gibi bazı programlama arabirimlerinde öznitelikleri aynı sözdizimine sahip olsa bile ad alanı bildirimi öznitelikler için dikkate alınmaz. Bununla birlikte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları olarak depolanır <xref:System.Xml.Linq.XAttribute> XML ağacı nesneleri. Bir ad alanı bildirimi içeren bir öğesi için öznitelikleri yinelemek, döndürülen koleksiyon öğeleri biri olarak ad alanı bildirimi görürsünüz.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Özelliği bir öznitelik ad alanı bildirimi olup olmadığını gösterir.  
  
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
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath eksen yöntemleri XDocument alt boşluk döndürmüyor  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için alt metin düğümleri sağlayan bir <xref:System.Xml.Linq.XDocument>metin düğümleri yalnızca boşluk içeren sürece. Ancak, XPath nesne modeli boşluk bir belgenin alt düğümleri olarak bu nedenle içermez alt yineleme ne zaman bir <xref:System.Xml.Linq.XDocument> kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> ekseni metin düğümleri boşluk döndürülür. Ancak, ne zaman, yineleme alt bir <xref:System.Xml.Linq.XDocument> XPath eksen yöntemleri kullanarak metin düğümleri boşluk olmayan döndürülür.  
  
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
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration nesneleri düğümleri olmayan  
 Alt düğümleri yineleme yaptığınızda bir <xref:System.Xml.Linq.XDocument>, XML bildirimi nesne görmezsiniz. Alt düğümü değil, bu belgenin bir özelliktir.  
  
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

- [Gelişmiş LINQ to XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
