---
title: XML ağacından öğe, öznitelik ve düğümleri kaldırma-LINQ to XML
description: Öğeleri, öznitelikleri ve diğer düğüm türlerini bir XML ağacından kaldırmayı öğrenin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553889"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a>XML ağacından öğeleri, öznitelikleri ve düğümleri kaldırma (LINQ to XML)

Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.

Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir. Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz. En iyi yaklaşım, <xref:System.Xml.Linq.Extensions.Remove%2A> bunu yapmak için genişletme yöntemini kullanmaktır.

Bu yaklaşımı kullanmanın başlıca nedeni, bir XML ağacından aldığınız koleksiyonların çoğu ertelenmiş yürütme kullanılarak yapılır. Önce bunları bir liste içine veya genişletme yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşabilirsiniz. Daha fazla bilgi için bkz. [karma bildirime dayalı/zorunlu kod hataları](mixed-declarative-imperative-code-bugs.md).

Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Bir üst öğeden kaldırın <xref:System.Xml.Linq.XAttribute> .|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Alt düğümleri bir öğesinden kaldırın <xref:System.Xml.Linq.XContainer> .|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|İçinden içerik ve öznitelikleri kaldırın <xref:System.Xml.Linq.XElement> .|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Özniteliklerini kaldırın <xref:System.Xml.Linq.XElement> .|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Değeri geçirirseniz özniteliği kaldırın `null` .|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Değeri geçirirseniz alt öğesi kaldırın `null` .|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Bir üst öğeden kaldırın <xref:System.Xml.Linq.XNode> .|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırın.|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a>Örnek: tek bir öğeyi kaldırın ve iki şekilde bir öğe koleksiyonunu kaldırın

Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir. İlk olarak, tek bir öğeyi kaldırır. İkincisi, bir öğe koleksiyonunu alır, bunları işlecini kullanarak bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> çıkarır ve sonra koleksiyonu kaldırır. Son olarak, bir öğe koleksiyonunu alır ve genişletme yöntemini kullanarak onları kaldırır <xref:System.Xml.Linq.Extensions.Remove%2A> .

İşleci hakkında daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> bkz. [veri türlerini dönüştürme (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) ve [veri türlerini dönüştürme (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1/>
            <GrandChild2/>
            <GrandChild3/>
        </Child1>
        <Child2>
            <GrandChild4/>
            <GrandChild5/>
            <GrandChild6/>
        </Child2>
        <Child3>
            <GrandChild7/>
            <GrandChild8/>
            <GrandChild9/>
        </Child3>
    </Root>
root.<Child1>.<GrandChild1>.Remove()
root.<Child2>.Elements().ToList().Remove()
root.<Child3>.Elements().Remove()
Console.WriteLine(root)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

İlk alt öğe öğesinden kaldırılmıştır `Child1` ve tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından kaldırılmıştır `Child3` .
