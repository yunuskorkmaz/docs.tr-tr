---
title: XAttribute sınıfına genel bakış
description: XAttribute sınıfı, XML özniteliklerini temsil eder. LINQ to XML özniteliklerle çalışma, öğelerle çalışmaya benzer.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552944"
---
# <a name="xattribute-class-overview"></a>XAttribute sınıfına genel bakış

Öznitelikler, bir öğesiyle ilişkili ad-değer çiftleridir. <xref:System.Xml.Linq.XAttribute>Sınıfı XML özniteliklerini temsil eder.

LINQ to XML özniteliklerle çalışma, öğelerle çalışmaya benzer. Oluşturucular benzerdir. Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir. Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine benzer.

Öznitelikleri bir öğeye eklenme sırası korunur. Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.

## <a name="the-xattribute-constructor"></a>XAttribute Oluşturucusu

Sınıfının aşağıdaki Oluşturucusu, <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanabileceğiniz bir sınıftır:

|Oluşturucu|Description|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|Bir <xref:System.Xml.Linq.XAttribute> nesnesi oluşturur. `name`Bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.|

## <a name="example-create-an-element-with-an-attribute"></a>Örnek: özniteliği olan bir öğe oluşturma

Aşağıdaki örnek, bir özniteliği içeren bir öğe oluşturma ortak görevini gösterir.

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a>Örnek: özniteliklerin Işlevsel olarak oluşturulması

<xref:System.Xml.Linq.XAttribute>Aşağıdaki örnekte gösterildiği gibi nesneleri oluşturma ile satır içi nesneler oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a>Öznitelikler düğüm değildir

Öznitelikler ve öğeler arasında bazı farklılıklar vardır. <xref:System.Xml.Linq.XAttribute> nesneler XML ağacında düğüm değildir. Bunlar bir XML öğesiyle ilişkili ad-değer çiftleridir. Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır. <xref:System.Xml.Linq.XAttribute>Nesneler gerçekte XML ağacında düğümler olmasa da nesnelerle çalışma, nesnelerle çalışmaya <xref:System.Xml.Linq.XAttribute> benzer <xref:System.Xml.Linq.XElement> .

Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir. Birçok geliştirici bu ayrım ile ilgilenmez.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML genel bakış](linq-xml-overview.md)
