---
title: XML Ağacına Öğeler, Öznitelikler ve Düğümler Ekleme (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 20d8d9d9c592f5f570d7c94298dcee41763c1f1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169581"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>XML Ağacına Öğeler, Öznitelikler ve Düğümler Ekleme (C#)
Varolan bir XML ağacına içerik (öğeler, öznitelikler, yorumlar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.  
  
## <a name="methods-for-adding-content"></a>İçerik Ekleme Yöntemleri  
 Aşağıdaki yöntemler, bir veya <xref:System.Xml.Linq.XElement> bir <xref:System.Xml.Linq.XDocument>alt içerik eklemek:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Alt içeriğin sonuna içerik <xref:System.Xml.Linq.XContainer>ekler.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Alt içeriğin başında içerik <xref:System.Xml.Linq.XContainer>ekler.|  
  
 Aşağıdaki yöntemler, bir <xref:System.Xml.Linq.XNode>. Kardeş içerik eklediğiniz en yaygın <xref:System.Xml.Linq.XElement>düğüm, geçerli kardeş içeriği eklemekle birlikte diğer düğüm <xref:System.Xml.Linq.XText> türlerine veya <xref:System.Xml.Linq.XComment>.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Sonra içerik <xref:System.Xml.Linq.XNode>ekler.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Önce içerik <xref:System.Xml.Linq.XNode>ekler.|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, iki XML ağacı oluşturur ve ağaçlardan birini değiştirir.  
  
### <a name="code"></a>Kod  
  
```csharp  
XElement srcTree = new XElement("Root",
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a>Yorumlar  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  