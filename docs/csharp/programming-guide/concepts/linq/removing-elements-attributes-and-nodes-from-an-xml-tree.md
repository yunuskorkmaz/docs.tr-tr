---
title: Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591265"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırma (C#)

Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.

Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir. Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz. En iyi yaklaşım, bunu sizin için <xref:System.Xml.Linq.Extensions.Remove%2A> sağlayacak olan genişletme yöntemini kullanmaktır.

Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır. İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür. Daha fazla bilgi için bkz. [karma bildirim kodu/zorunlu kod hataları (LINQ to XML)C#()](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).

Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Bir <xref:System.Xml.Linq.XAttribute> öğesini üst öğesinden kaldırır.|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Alt düğümleri bir <xref:System.Xml.Linq.XContainer>öğesinden kaldırır.|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Öğesinden içerik ve öznitelikleri kaldırır <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|, Özniteliklerini <xref:System.Xml.Linq.XElement>kaldırır.|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Değerini geçirirseniz `null` , özniteliğini kaldırır.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Değer ' i `null` geçirirseniz, alt öğeyi kaldırır.|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Bir <xref:System.Xml.Linq.XNode> öğesini üst öğesinden kaldırır.|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir. İlk olarak, tek bir öğeyi kaldırır. İkincisi, bir öğe koleksiyonunu alır, bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işlecini kullanarak bunları çıkarır ve koleksiyonu kaldırır. Son olarak, bir öğe koleksiyonunu alır ve <xref:System.Xml.Linq.Extensions.Remove%2A> genişletme yöntemini kullanarak onları kaldırır.

<xref:System.Linq.Enumerable.ToList%2A> İşleci hakkında daha fazla bilgi için bkz. [veri türlerini dönüştürme (C#)](./converting-data-types.md).

### <a name="code"></a>Kod

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

### <a name="comments"></a>Açıklamalar

Bu kod aşağıdaki çıktıyı üretir:

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

İlk alt öğenin öğesinden `Child1`çıkarıldığına dikkat edin. Tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından `Child3`kaldırılmıştır.
