---
title: XML Ağacından Öğeleri, Öznitelikleri ve Düğümleri Kaldırma (C#)
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: badaa6bab35367d62a73f56c5221cb7d6d4a45f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591265"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a>XML Ağacından Öğeleri, Öznitelikleri ve Düğümleri Kaldırma (C#)

Öğeleri, öznitelikleri ve diğer düğüm türlerini kaldırarak bir XML ağacını değiştirebilirsiniz.

Bir XML belgesinden tek bir öğeyi veya tek bir özniteliği kaldırmak kolaydır. Ancak, öğe veya öznitelik koleksiyonlarını kaldırırken, önce bir koleksiyonu bir listeye eklemeniz ve ardından öğeleri veya öznitelikleri listeden silmeniz gerekir. En iyi yaklaşım, <xref:System.Xml.Linq.Extensions.Remove%2A> bunu sizin için yapacak uzantı yöntemini kullanmaktır.

Bunu yapmanın temel nedeni, bir XML ağacından aldığınız koleksiyonların çoğunun ertelenmiş yürütme kullanılarak elde edilmesidir. Bunları ilk önce bir listeye dahil etmezseniz veya uzantı yöntemlerini kullanmazsanız, belirli bir hata sınıfıyla karşılaşmanız mümkündür. Daha fazla bilgi için bkz: [Karışık Bildirim kodu/Zorunlu Kod Hataları (LINQ - XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).

Aşağıdaki yöntemler bir XML ağacından düğümleri ve öznitelikleri kaldırır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|Bir ebeveynini <xref:System.Xml.Linq.XAttribute> kaldırır.|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|Alt düğümleri bir <xref:System.Xml.Linq.XContainer>'den kaldırır.|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|İçeriği ve öznitelikleri <xref:System.Xml.Linq.XElement>bir 'den kaldırır.|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Bir <xref:System.Xml.Linq.XElement>' nin özniteliklerini kaldırır.|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Değer için `null` geçerseniz, özniteliği kaldırır.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Değer için `null` geçerseniz, alt öğeyi kaldırır.|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|Bir ebeveynini <xref:System.Xml.Linq.XNode> kaldırır.|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|Kaynak koleksiyonundaki her özniteliği veya öğeyi üst öğeden kaldırır.|

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Bu örnek, öğeleri kaldırmak için üç yaklaşım gösterir. İlk olarak, tek bir öğeyi kaldırır. İkinci olarak, bir öğe koleksiyonunu alır, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> işleci kullanarak bunları somutlaştırır ve koleksiyonu kaldırır. Son olarak, bir öğe koleksiyonu alır ve <xref:System.Xml.Linq.Extensions.Remove%2A> uzantı yöntemini kullanarak bunları kaldırır.

<xref:System.Linq.Enumerable.ToList%2A> İşleç hakkında daha fazla bilgi için [bkz.](./converting-data-types.md)

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

İlk torun öğesinin `Child1`. Tüm torun elemanları `Child2` kaldırıldı `Child3`ve .
