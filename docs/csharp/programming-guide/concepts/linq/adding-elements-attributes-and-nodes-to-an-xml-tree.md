---
title: XML ağacına öğe, öznitelik ve düğüm ekleme (C#)
description: Öğeler, öznitelikler, açıklamalar, işleme talimatları ve metin gibi içeriği varolan bir XML ağacına ekleme yöntemleri hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 78a84401494e2d4280799632fa42dc95574e3e10
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105551"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a>XML ağacına öğe, öznitelik ve düğüm ekleme (C#)
Mevcut bir XML ağacına içerik (öğe, öznitelik, yorum, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.  
  
## <a name="methods-for-adding-content"></a>Içerik ekleme yöntemleri  
 Aşağıdaki yöntemler bir veya öğesine alt içerik ekler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> :  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Öğesinin alt içeriğinin sonuna içerik ekler <xref:System.Xml.Linq.XContainer> .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Öğesinin alt içeriğinin başlangıcına içerik ekler <xref:System.Xml.Linq.XContainer> .|  
  
 Aşağıdaki yöntemler bir öğesinin eşdüzey düğümleri olarak içerik ekler <xref:System.Xml.Linq.XNode> . Eşdüzey içerik eklediğiniz en yaygın düğüm, <xref:System.Xml.Linq.XElement> veya gibi diğer düğüm türlerine geçerli eşdüzey içerik eklemenize olanak sağlar <xref:System.Xml.Linq.XText> <xref:System.Xml.Linq.XComment> .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Öğesinden sonra içerik ekler <xref:System.Xml.Linq.XNode> .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Öğesinden önce içerik ekler <xref:System.Xml.Linq.XNode> .|  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek iki XML ağacı oluşturur ve sonra ağaçlardan birini değiştirir.  
  
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
 Bu kod şu çıkışı oluşturur:  
  
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
  