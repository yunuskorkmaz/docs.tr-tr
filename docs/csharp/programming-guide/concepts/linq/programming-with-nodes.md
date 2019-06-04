---
title: Düğümleri (C#) ile programlama
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 7229b03e1bbb4f7cd861cb946307867b87234a21
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487307"
---
# <a name="programming-with-nodes-c"></a>Düğümleri (C#) ile programlama
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeler ve öznitelikler daha hassas bir düzeyde ayrıntı çalışan programları yazmak bir XML Düzenleyicisi, bir dönüştürme sistemi veya bir rapor yazıcı gibi programlar genellikle yazmanız gereken geliştiriciler gerekir. Bunlar genellikle metin düğümleri, işleme yönergeleri ve açıklamaları düzenleme düğüm düzeyinde çalışması gerekir. Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm ayrıntıları  
 Bir dizi düğümü düzeyinde çalışan Programcı bilmeniz gereken programlama ayrıntılarını vardır.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Üst özellik, alt düğümleri, XDocument Null olarak ayarlandı  
 <xref:System.Xml.Linq.XObject.Parent%2A> Özelliği içeren üst <xref:System.Xml.Linq.XElement>, üst düğümü değil. Alt düğümleri <xref:System.Xml.Linq.XDocument> üst sahip <xref:System.Xml.Linq.XElement>. Üst belge olduğu şekilde <xref:System.Xml.Linq.XObject.Parent%2A> düğümleri için özelliği null.  
  
 Aşağıdaki örnek bunu gösterir:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik metin düğümleri mümkündür.  
 Bir XML programlama modelleri sayısında bitişik metin düğümleri her zaman birleştirilir. Bu, bazen metin düğümleri normalleştirmesini denir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metin düğümleri Normalleştir değil. İki metin düğümleri aynı öğe eklerseniz, bitişik metin düğümleri neden olur. Ancak, bir dize yerine olarak belirtilen içeriği eklerseniz bir <xref:System.Xml.Linq.XText> düğümünün [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bitişiğindeki metin düğümü ile dize birleştirme.  
  
 Aşağıdaki örnek bunu gösterir:  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş metin düğümleri mümkündür.  
 Bazı XML programlama modellerinde metin düğümleri boş dize içermiyor garanti edilir. Mantık gibi bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmasıdır. Ancak, bitişiğindeki metin düğümleri aynı nedenden dolayı boş dize olarak metin düğümü değerine ayarlayarak metnin bir metin düğümü kaldırırsanız mümkün silinmez.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Boş metin düğümü serileştirme etkiler.  
 Yalnızca boş bir alt metin düğümü bir öğe içeriyorsa, ile uzun etiket sözdizimi serileştirildiği: `<Child></Child>`. Kullanılabilir alt düğümler olmadan bir öğe içeriyorsa, kısa etiket sözdizimi ile serileştirildiği: `<Child />`.  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Öznitelikleridir LINQ to XML ağacının ad alanları  
 Ad alanı bildirimi, XSLT ve XPath, gibi bazı programlama arabirimlerinde öznitelikleri aynı sözdizimine sahip olsa bile ad alanı bildirimi öznitelikler için dikkate alınmaz. Bununla birlikte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları olarak depolanır <xref:System.Xml.Linq.XAttribute> XML ağacı nesneleri. Bir ad alanı bildirimi içeren bir öğesi için öznitelikleri yinelemek, döndürülen koleksiyon öğeleri biri olarak ad alanı bildirimi görürsünüz.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Özelliği bir öznitelik ad alanı bildirimi olup olmadığını gösterir.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath eksen yöntemleri XDocument alt boşluk döndürmüyor  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için alt metin düğümleri sağlayan bir <xref:System.Xml.Linq.XDocument>metin düğümleri yalnızca boşluk içeren sürece. Ancak, XPath nesne modeli boşluk bir belgenin alt düğümleri olarak bu nedenle içermez alt yineleme ne zaman bir <xref:System.Xml.Linq.XDocument> kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> eksen, boşluk metin düğümleri döndürülür. Ancak, ne zaman, yineleme alt bir <xref:System.Xml.Linq.XDocument> XPath eksen yöntemleri kullanarak, boşluk metin düğümleri değil döndürülür.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration nesneleri düğümleri olmayan  
 Alt düğümleri yineleme yaptığınızda bir <xref:System.Xml.Linq.XDocument>, XML bildirimi nesne görmezsiniz. Alt düğümü değil, bu belgenin bir özelliktir.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  