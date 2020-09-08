---
title: XML ağacına öğe, öznitelik ve düğüm ekleme-LINQ to XML
description: Bir XML ağacına içerik (öğe, öznitelik, açıklama, işleme yönergeleri, metin ve CDATA) eklemeyi öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 5225560a3f3c94dcb7d4c65e66accddcead84b70
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553558"
---
# <a name="add-elements-attributes-and-nodes-to-an-xml-tree-linq-to-xml"></a>XML ağacına öğe, öznitelik ve düğüm ekleme (LINQ to XML)

Bir XML ağacına içerik (öğeler, öznitelikler, açıklamalar, işleme yönergeleri, metin ve CDATA) ekleyebilirsiniz.

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

## <a name="example-create-two-xml-trees-and-modify-one-of-them"></a>Örnek: iki XML ağacı oluşturma ve bunlardan birini değiştirme

Aşağıdaki örnek iki XML ağacı oluşturur ve bunlardan birini değiştirir.

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
// Even though Child9 doesn't exist in srcTree, the following statement won't
// throw an exception, and nothing will be added to xmlTree.
xmlTree.Add(srcTree.Element("Child9"));
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element1>1</Element1>
        <Element2>2</Element2>
        <Element3>3</Element3>
        <Element4>4</Element4>
        <Element5>5</Element5>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child2>2</Child2>
        <Child3>3</Child3>
        <Child4>4</Child4>
        <Child5>5</Child5>
    </Root>

xmlTree.Add(<NewChild>new content</NewChild>)
xmlTree.Add( _
    From el In srcTree.Elements() _
    Where CInt(el) > 3 _
    Select el)

' Even though Child9 doesn't exist in srcTree, the following statement
' won't throw an exception, and nothing will be added to xmlTree.
xmlTree.Add(srcTree.Element("Child9"))
Console.WriteLine(xmlTree)
```

Bu örnek aşağıdaki çıktıyı üretir:

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
