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
# <a name="programming-with-nodes-c"></a>Düğümlerle programlama (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bir XML Düzenleyicisi, bir dönüşüm sistemi veya rapor yazıcısı gibi programlar yazması gereken geliştiriciler genellikle öğeleri ve öznitelikleri daha ayrıntılı bir düzeyde ayrıntı düzeyinde çalışan programlar yazması gerekir. Genellikle düğüm düzeyinde çalışmamaları, metin düğümlerini işlemek, yönergeleri ve açıklamaları işlemek gerekir. Bu konu, düğüm düzeyinde programlama hakkında bazı ayrıntılar sağlar.  
  
## <a name="node-details"></a>Düğüm ayrıntıları  
 Programlama, düğüm düzeyinde çalışan bir programcı 'nin bilmelidir bir dizi ayrıntı vardır.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>XDocument 'in alt öğe düğümlerinin üst özelliği null olarak ayarlandı  
 <xref:System.Xml.Linq.XObject.Parent%2A>Özelliği <xref:System.Xml.Linq.XElement> üst düğümü değil üst öğeyi içerir. Öğesinin alt düğümlerinin <xref:System.Xml.Linq.XDocument> üst öğesi yok <xref:System.Xml.Linq.XElement> . Üst öğesi belgedir, <xref:System.Xml.Linq.XObject.Parent%2A> Bu nedenle bu düğümlerin özelliği null olarak ayarlanır.  
  
 Aşağıdaki örnek şunu gösterir:  
  
```csharp  
XDocument doc = XDocument.Parse(@"<!-- a comment --><Root/>");  
Console.WriteLine(doc.Nodes().OfType<XComment>().First().Parent == null);  
Console.WriteLine(doc.Root.Parent == null);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Bitişik metin düğümleri mümkündür  
 Bir dizi XML programlama modelinde, bitişik metin düğümleri her zaman birleştirilir. Bu bazen metin düğümlerinin normalleştirilmesi olarak adlandırılır. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]metin düğümlerini normalleştirilemez. Aynı öğeye iki metin düğümü eklerseniz, bu, bitişik metin düğümlerine neden olur. Ancak, düğüm olarak değil, bir dize olarak belirtilen içeriği eklerseniz <xref:System.Xml.Linq.XText> , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dizeyi bitişik bir metin düğümü ile birleştirebilirsiniz.  
  
 Aşağıdaki örnek şunu gösterir:  
  
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
  
```output  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Boş metin düğümleri mümkündür  
 Bazı XML programlama modellerinde, metin düğümlerinin boş dize içermediği garanti edilir. Bu tür bir metin düğümünün XML serileştirilmesi üzerinde hiçbir etkisi yoktur. Ancak, bitişik metin düğümlerinin mümkün olmasının aynı nedeni için, değerini boş dizeye ayarlayarak metin düğümünden metin kaldırırsanız, metin düğümünün kendisi silinmez.  
  
```csharp  
XElement xmlTree = new XElement("Root", "Content");  
XText textNode = xmlTree.Nodes().OfType<XText>().First();  
  
// the following line does not cause the removal of the text node.  
textNode.Value = "";  
  
XText textNode2 = xmlTree.Nodes().OfType<XText>().First();  
Console.WriteLine(">>{0}<<", textNode2);
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Boş bir metin düğümü serileştirme etkiler  
 Bir öğe yalnızca boş olan bir alt metin düğümü içeriyorsa, Long Tag sözdizimi ile serileştirilir: `<Child></Child>` . Bir öğe herhangi bir alt düğüm içermiyorsa, kısa etiket söz dizimi ile serileştirilir: `<Child />` .  
  
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
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Ad alanları LINQ to XML ağacındaki özniteliklerdir  
 Ad alanı bildirimleri özniteliklere aynı sözdizimine sahip olsa da XSLT ve XPath gibi bazı programlama arabirimlerinde, ad alanı bildirimleri öznitelik olarak kabul edilmez. Ancak, içinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , ad ALANLARı <xref:System.Xml.Linq.XAttribute> XML ağacında nesneler olarak depolanır. Bir ad alanı bildirimi içeren bir öğe için öznitelikler üzerinde yineleme yaparsanız, ad alanı bildirimini döndürülen koleksiyondaki öğelerden biri olarak görürsünüz.  
  
 <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>Özelliği, bir özniteliğin ad alanı bildirimi olup olmadığını gösterir.  
  
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
  
```output  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>XPath eksen yöntemleri, XDocument 'in alt boşluk değerini döndürmüyor  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]metin düğümlerinde yalnızca boşluk bulunduğu sürece alt metin düğümlerine izin verir <xref:System.Xml.Linq.XDocument> . Ancak, XPath nesne modeli bir belgenin alt düğümleri olarak boşluk içermez, bu nedenle eksen kullanarak alt öğeleri üzerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XContainer.Nodes%2A> boşluk metin düğümleri döndürülür. Ancak, XPath eksen yöntemlerini kullanarak bir öğesinin alt öğelerinde yineleme yaptığınızda <xref:System.Xml.Linq.XDocument> , boşluk metin düğümleri döndürülmez.  
  
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
  
```output  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>XDeclaration nesneleri düğüm değil  
 Bir ' ın alt düğümleri arasında yineleme yaparken <xref:System.Xml.Linq.XDocument> , XML bildirim nesnesini görmezsiniz. Bunun bir alt düğümü değil, belgenin bir özelliğidir.  
  
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
  
```output  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  