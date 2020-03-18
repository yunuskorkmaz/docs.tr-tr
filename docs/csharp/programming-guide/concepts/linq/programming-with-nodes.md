---
title: Düğümlü Programlama (C#)
ms.date: 07/20/2015
ms.assetid: c38df0f2-c805-431a-93ff-9103a4284c2f
ms.openlocfilehash: 05c2e95fe97effda7b537a7ac2d8f5780f4e212b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168320"
---
# <a name="programming-with-nodes-c"></a>Düğümlü Programlama (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML düzenleyicisi, dönüştürme sistemi veya rapor yazarı gibi programlar yazması gereken geliştiricilerin genellikle öğelerden ve özniteliklerden daha ince bir ayrıntı düzeyinde çalışan programlar yazmaları gerekir. Genellikle düğüm düzeyinde, metin düğümleri işleme, yönergeleri işleme ve yorum çalışması gerekir. Bu konu düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm Ayrıntıları  
 Düğüm düzeyinde çalışan bir programcının bilmesi gereken programlamanın birkaç ayrıntısı vardır.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>XDocument'ın Alt Düğümlerinin Üst Özelliği Null olarak ayarlanır  
 Özellik, <xref:System.Xml.Linq.XObject.Parent%2A> üst <xref:System.Xml.Linq.XElement>düğümü değil, üst öğeyi içerir. Çocuk düğümlerinin <xref:System.Xml.Linq.XDocument> ebeveyni <xref:System.Xml.Linq.XElement>yoktur. Üst leri belgedir, <xref:System.Xml.Linq.XObject.Parent%2A> bu nedenle bu düğümlerin özelliği geçersiz kılınacak şekilde ayarlanmıştır.  
  
 Aşağıdaki örnek bunu göstermektedir:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik Metin Düğümleri Mümkündür  
 Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir. Buna bazen metin düğümlerinin normalleştirilmesi denir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]metin düğümlerini normalleştirmez. Aynı öğeye iki metin düğümü eklerseniz, bitişik metin düğümleri neden olur. Ancak, <xref:System.Xml.Linq.XText> düğüm yerine dize olarak belirtilen içerik eklerseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dizeyi bitişik metin düğümüyle birleştirir.  
  
 Aşağıdaki örnek bunu göstermektedir:  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş Metin Düğümleri Mümkündür  
 Bazı XML programlama modellerinde metin düğümlerinin boş dizeyi içermemesi garanti edilir. Akıl, böyle bir metin düğümü XML serileştirme üzerinde hiçbir etkisi olmasıdır. Ancak, bitişik metin düğümlerinin mümkün olmasıyla aynı nedenle, metni bir metin düğümünden, değerini boş dizeye ayarlayarak kaldırırsanız, metin düğümünün kendisi silinmez.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Boş Metin Düğümü Serileştirmeyi Etkiler  
 Bir öğe boş olan yalnızca bir alt metin düğümü içeriyorsa, uzun `<Child></Child>`etiket sözdizimi ile seri hale getirilir: . Bir öğe alt düğüm içermiyorsa, kısa etiket sözdizimi ile `<Child />`seri hale getirilir: .  
  
```csharp  
XElement child1 = new XElement("Child1",  
    new XText("")  
);  
XElement child2 = new XElement("Child2");  
Console.WriteLine(child1);  
Console.WriteLine(child2);
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Ad Boşlukları, LINQ'daki XML Ağacı'ndaki Özniteliklerdir  
 Ad alanı bildirimleri özniteliklerle aynı sözdizimine sahip olsa da, XSLT ve XPath gibi bazı programlama arabirimlerinde ad alanı bildirimleri öznitelik olarak kabul edilmez. Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], ad boşlukları XML ağacında nesne olarak <xref:System.Xml.Linq.XAttribute> depolanır. Ad alanı bildirimi içeren bir öğenin özniteliklerini yinelerseniz, ad alanı bildirimini döndürülen koleksiyondaki öğelerden biri olarak görürsünüz.  
  
 Özellik, <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> öznitelik bir ad alanı bildirimi olup olmadığını gösterir.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>");  
foreach (XAttribute att in root.Attributes())  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, att.IsNamespaceDeclaration);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath Ekseni Yöntemleri XDocument'ın Alt Beyaz Alanını Döndürmeyin  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]metin düğümleri yalnızca beyaz <xref:System.Xml.Linq.XDocument>boşluk içerdiği sürece, bir alt metin düğümleri için izin verir. Ancak, XPath nesnesi modeli bir belgenin alt düğümleri olarak beyaz boşluk içermez, bu <xref:System.Xml.Linq.XDocument> nedenle <xref:System.Xml.Linq.XContainer.Nodes%2A> ekseni kullanarak bir alt metin düğümleri ile yinelediğinizde, beyaz alan metin düğümleri döndürülür. Ancak, XPath ekseni yöntemlerini <xref:System.Xml.Linq.XDocument> kullanarak bir alt bölümü ile yinelediğinizde, beyaz alan metin düğümleri döndürülmez.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration Nesneleri Düğüm değildir  
 Bir <xref:System.Xml.Linq.XDocument>çocuk düğümleri ile yinelediğinizde, XML bildirim nesnesini görmezsiniz. Bu belgenin bir özelliği, bir çocuk düğümü değil.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  