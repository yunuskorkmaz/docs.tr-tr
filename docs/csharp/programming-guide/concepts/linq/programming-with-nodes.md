---
title: Düğümler (C#) ile programlama
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 060f487e6e92c2ca42a685cc03afbe438106b839
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="programming-with-nodes-c"></a>Düğümler (C#) ile programlama
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir XML Düzenleyicisi, dönüştürme sistem ya da bir rapor yazıcı gibi programlar genellikle yazmak için isteyen geliştiriciler daha hassas bir ayrıntı düzeyinde öğeleri ve özniteliklerinin daha çalışan programlar yazmanız gerekir. Bunlar genellikle metin düğümleri, işleme yönergeleri ve açıklamalar düzenleme düğüm düzeyinde çalışması gerekir. Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm ayrıntıları  
 Düğüm düzeyinde çalışma Programcı bilmeniz gereken programlama ayrıntılarını mevcuttur.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>Üst özelliği, alt düğümleri olarak XDocument Null olarak ayarlandı  
 <xref:System.Xml.Linq.XObject.Parent%2A> Özelliği içeren üst <xref:System.Xml.Linq.XElement>, üst düğümü değil. Alt düğümleri <xref:System.Xml.Linq.XDocument> üst öğeye sahip <xref:System.Xml.Linq.XElement>. Kendi üst belgesidir böylece <xref:System.Xml.Linq.XObject.Parent%2A> düğümleri için özelliği null.  
  
 Aşağıdaki örnekte bu gösterir:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik metin düğümleri mümkündür.  
 XML programlama modelleri sayısında bitişik metin düğümleri her zaman birleştirilir. Buna bazen metin düğümleri normalleştirme denir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metin düğümleri normalleştirin değil. İki metin düğümleri aynı öğeye eklerseniz, bitişiğindeki metin düğümleri neden olur. Ancak, bir dize olarak yerine olarak belirtilen içeriği eklerseniz, bir <xref:System.Xml.Linq.XText> düğümü [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bitişik metin düğümü dizeyle birleştirmek.  
  
 Aşağıdaki örnekte bu gösterir:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş metin düğümleri mümkündür.  
 Bazı XML programlama modellerinde metin düğümleri boş dize içermemesi garanti. Bu tür bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmaz mantık olur. Ancak, bitişiğindeki metin düğümler aynı nedenden dolayı değeri boş dize, metin düğümü ayarlayarak metni metin düğüm kaldırırsanız olası silinmez.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);   
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Seri hale getirme boş metin düğümü etkiler  
 Bir öğe yalnızca boş bir alt metin düğümü içeriyorsa uzun etiket sözdizimi ile seri değildir: `<Child></Child>`. Bir öğe doğabilecek alt düğüm içeriyorsa, kısa etiket sözdizimiyle seri değildir: `<Child />`.  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);   
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Ad alanları öznitelikleridir XML ağacına LINQ  
 Ad alanı bildirimleri XSLT ve XPath, gibi bazı programlama arabirimleri öznitelikleri, aynı sözdizimine sahip olsa da ad alanı bildirimleri öznitelikleri için dikkate alınmaz. Bununla birlikte, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad alanları olarak depolanır <xref:System.Xml.Linq.XAttribute> XML ağacında nesneleri. Bir ad alanı bildirimi içeren bir öğesinin özniteliklerini yinelemek, döndürülen koleksiyondaki öğelerin biri olarak ad alanı bildirimi görürsünüz.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> Özelliği, bir öznitelik bir ad alanı bildirimi olup olmadığını belirtir.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath eksen yöntemleri alt boşluklardan-XDocument döndürmüyor  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için alt metin düğümleri sağlayan bir <xref:System.Xml.Linq.XDocument>, metin düğümleri yalnızca boşluk içeremez sürece. Ancak, XPath nesne modeli beyaz alanı bir belgenin alt düğümleri olarak şekilde içermez alt yineleme ne zaman bir <xref:System.Xml.Linq.XDocument> kullanarak <xref:System.Xml.Linq.XContainer.Nodes%2A> eksen, boşluk metin düğümleri döndürülecek. Ancak, ne zaman, yineleme alt bir <xref:System.Xml.Linq.XDocument> XPath eksen yöntemleri kullanarak, boşluk metin düğümleri olmayan döndürülür.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration nesneleri düğümleri olmayan  
 Yineleme zaman alt öğe düğümlerinin bir <xref:System.Xml.Linq.XDocument>, XML bildirimi nesnesi görmezsiniz. Belgenin alt düğümü değil bunu bir özelliktir.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gelişmiş LINQ-XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
