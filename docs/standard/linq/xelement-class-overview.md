---
title: XElement sınıfına genel bakış
description: XElement sınıfı XML öğelerini temsil eder. Öğeleri oluşturmak ve değiştirmek, öznitelikleri ve alt öğeleri eklemek ve seri hale getirmek için kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553129"
---
# <a name="xelement-class-overview"></a>XElement sınıfına genel bakış

<xref:System.Xml.Linq.XElement>Sınıfı, LINQ to XML temel sınıflardan biridir. Bir XML öğesini temsil eder. Aşağıdaki liste, için bu sınıfı neleri kullanacağınızı gösterir:

- Öğeleri oluşturun.
- Öğenin içeriğini değiştirin.
- Alt öğeleri ekleyin, değiştirin veya silin.
- Öznitelikleri bir öğeye ekleyin.
- Metin biçimindeki bir öğenin içeriğini seri hale getirme.

Ayrıca, ve gibi diğer sınıflarla da birlikte kullanabilirsiniz <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .

Bu makalede, sınıfı tarafından sunulan işlevleri açıklanmaktadır <xref:System.Xml.Linq.XElement> .

## <a name="construct-xml-trees"></a>XML ağaçları oluşturun

XML ağaçlarını aşağıdakiler dahil farklı yollarla oluşturabilirsiniz:

- Kodda bir XML ağacı oluşturabilirsiniz. Daha fazla bilgi için bkz. [xml ağaçları](functional-construction.md).
- Bir <xref:System.IO.TextReader> metin dosyası veya bir Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırabilirsiniz. Daha fazla bilgi için bkz. [XML 'ı ayrıştırma](parse-string.md).
- <xref:System.Xml.XmlReader>Ağacı doldurmak için kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.
- İçine içerik yazabileceği bir modülünüzün varsa, bir <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yazıcı oluşturmak, yazıcıyı modüle geçirmek ve ardından <xref:System.Xml.XmlWriter> XML ağacını doldurmak için öğesine yazılan içeriği kullanmak için yöntemini kullanabilirsiniz.

Aşağıdaki örnek bir ağaç oluşturur. C# sürümü iç içe öğe oluşturmaları kullanır. Aynı tekniği Visual Basic de kullanabilirsiniz, ancak bu örnekte XML değişmez değerleri kullanılmaktadır.

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

Ayrıca, aşağıdaki örnekte gösterildiği gibi bir XML ağacını doldurmak için LINQ to XML bir sorgu kullanabilirsiniz:

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a>XML ağaçlarını serileştirme

XML ağacını bir <xref:System.IO.File> , a veya olarak seri hale getirebilirsiniz <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .

Daha fazla bilgi için bkz. [XML ağaçlarını serileştirme](preserve-white-space-serializing.md).

## <a name="retrieve-xml-data-via-axis-methods"></a>XML verilerini eksen yöntemleri aracılığıyla alma

Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz. LINQ to XML sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.

Daha fazla bilgi için bkz. [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md).

## <a name="query-xml-trees"></a>XML ağaçlarını sorgula

Bir XML ağacından veri çıkaran LINQ to XML sorguları yazabilirsiniz.

Daha fazla bilgi için bkz. [sorgu xml ağaçlarına genel bakış](query-xml-trees-overview.md).

## <a name="modify-xml-trees"></a>XML ağaçlarını değiştirme

Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi farklı yollarla değiştirebilirsiniz. Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.

Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme](in-memory-xml-tree-modification-vs-functional-construction.md).

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış](functional-vs-procedural-programming.md)
