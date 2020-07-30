---
title: XML ağacından öğeleri, öznitelikleri ve düğümleri kaldırma (C#)
description: Öğeleri, öznitelikleri ve düğümleri bir XML ağacından kaldırmayı öğrenin. Kaldırma yöntemlerinin listesini ve kod örneğini görüntüleyin.
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300052"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>XML ağacından öğeleri, öznitelikleri ve düğümleri kaldırma (C#)

Bir XML ağacını değiştirebilir, öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırabilirsiniz.

Tek bir öğeyi veya bir XML belgesinden tek bir özniteliği kaldırmak basittir. Bununla birlikte, öğe veya öznitelik koleksiyonları kaldırılırken, önce bir koleksiyonu bir liste halinde ve ardından listeden öğeleri veya öznitelikleri silmelisiniz. En iyi yaklaşım, bunu <xref:System.Xml.Linq.Extensions.Remove%2A> sizin için sağlayacak olan genişletme yöntemini kullanmaktır.

Bunu yapmanın asıl nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak yapılır. İlk olarak bunları bir liste içine almayın veya uzantı yöntemlerini kullanmıyorsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür. Daha fazla bilgi için bkz. [karma bildirim kodu/zorunlu kod hataları (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).

Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Bir öğesini <xref:System.Xml.Linq.XAttribute> üst öğesinden kaldırır.|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Alt düğümleri bir öğesinden kaldırır <xref:System.Xml.Linq.XContainer> .|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Öğesinden içerik ve öznitelikleri kaldırır <xref:System.Xml.Linq.XElement> .|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|, Özniteliklerini kaldırır <xref:System.Xml.Linq.XElement> .|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|`null`Değerini geçirirseniz, özniteliğini kaldırır.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|`null`Değer ' i geçirirseniz, alt öğeyi kaldırır.|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Bir öğesini <xref:System.Xml.Linq.XNode> üst öğesinden kaldırır.|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Kaynak koleksiyondaki her özniteliği veya öğeyi üst öğesinden kaldırır.|

## <a name="example"></a>Örnek

### <a name="description"></a>Description

Bu örnek, öğeleri kaldırmak için üç yaklaşımlar gösterir. İlk olarak, tek bir öğeyi kaldırır. İkincisi, bir öğe koleksiyonunu alır, bunları işlecini kullanarak bunları <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> çıkarır ve koleksiyonu kaldırır. Son olarak, bir öğe koleksiyonunu alır ve genişletme yöntemini kullanarak onları kaldırır <xref:System.Xml.Linq.Extensions.Remove%2A> .

İşleci hakkında daha fazla bilgi için <xref:System.Linq.Enumerable.ToList%2A> bkz. [veri türlerini dönüştürme (C#)](./converting-data-types.md).

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

### <a name="comments"></a>Yorumlar

Bu kod şu çıkışı oluşturur:

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

İlk alt öğenin öğesinden çıkarıldığına dikkat edin `Child1` . Tüm alt öğeler öğeleri öğesinden `Child2` ve kaynağından kaldırılmıştır `Child3` .
