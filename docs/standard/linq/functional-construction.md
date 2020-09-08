---
title: İşlevsel oluşturma-LINQ to XML
description: LINQ to XML, tek bir bildirimde bir XML ağacı oluşturmanızı sağlayan işlevsel oluşturma sağlar.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: bcdc153d7f60cfb165dcb741d62b6af5c07a148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553099"
---
# <a name="functional-construction-linq-to-xml"></a>İşlevsel oluşturma (LINQ to XML)

LINQ to XML *işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar. İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturmanıza olanak sağlar.

LINQ to XML programlama arabiriminin birkaç temel özelliği işlevsel oluşturma sırasında kullanılır:

- <xref:System.Xml.Linq.XElement>Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır. Örneğin, <xref:System.Xml.Linq.XElement> bir alt öğe haline gelen başka bir nesneyi geçirebilirsiniz. <xref:System.Xml.Linq.XAttribute>Öğesinin bir özniteliği haline gelen bir nesneyi geçirebilirsiniz. Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.
- <xref:System.Xml.Linq.XElement>Oluşturucuya `params` <xref:System.Object> herhangi bir sayıda nesne geçirebilmeniz için Oluşturucu türünde bir dizi alır. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.
- Bir nesne uygularsa <xref:System.Collections.Generic.IEnumerable%601> , nesne içindeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı ayrı eklenir. Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.

## <a name="example-create-an-xml-tree"></a>Örnek: bir XML ağacı oluşturma

Bir XML ağacı oluşturmak için kod yazmak üzere işlevsel oluşturma kullanabilirsiniz. Aşağıda bir örnek verilmiştir:

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

## <a name="example-create-an-xml-tree-using-linq-query-results"></a>Örnek: LINQ sorgu sonuçlarını kullanarak bir XML ağacı oluşturma

Bu özellikler, aşağıdaki örnekte olduğu gibi bir XML ağacı oluştururken LINQ sorgularının sonuçlarını kullanan kodu yazmanızı de sağlar:

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

Visual Basic, XML değişmez değerleri ile aynı şey gerçekleştirilir:

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
            Where CInt(el) > 2 _
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

## <a name="see-also"></a>Ayrıca bkz.

- [C 'de XML ağaçları oluşturma #](create-xml-trees.md)
- [Visual Basic XML sabit değerleri](xml-literals.md)
