---
title: XmlReader-LINQ to XML ağaç oluşturma
description: C# veya Visual Basic XML 'yi okumak ve bir XML ağacı oluşturmak için bir XmlReader kullanabilirsiniz. XmlReader 'yi bir öğe düğümüne doğru bir şekilde konumlandırmalısınız.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 659135ae9930d4ba63b13e436ebd278807e4256b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553198"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-linq-to-xml"></a>XmlReader 'dan ağaç oluşturma (LINQ to XML)

Bu makalede <xref:System.Xml.XmlReader> , C# veya Visual Basic doğrudan BIR XML ağacının nasıl oluşturulacağı gösterilmektedir. Bir öğesinden oluşturmak için <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> , öğesini bir <xref:System.Xml.XmlReader> öğe düğümüne yerleştirebilirsiniz. <xref:System.Xml.XmlReader>Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur. Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> öğesinden BIR XML ağacı oluşturmadan önce öğesini bir öğesine konumlandırın <xref:System.Xml.XmlReader> .

## <a name="example-load-xelement-object-from-an-xmlreader-object"></a>Örnek: bir XmlReader nesnesinden XElement nesnesini yükle

Bu örnek XML belgesi [örnek xml dosyasını kullanır: kitaplar](sample-xml-file-books.md).

Aşağıdaki kod bir nesne oluşturur <xref:System.Xml.XmlReader> , ilk öğe düğümünü bulana kadar düğümleri okur ve <xref:System.Xml.Linq.XElement> nesneyi yükler.

```csharp
XmlReader r = XmlReader.Create("books.xml");
while (r.NodeType != XmlNodeType.Element)
    r.Read();
XElement e = XElement.Load(r);
Console.WriteLine(e);
```

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Catalog>
   <Book id="bk101">
      <Author>Garghentini, Davide</Author>
      <Title>XML Developer's Guide</Title>
      <Genre>Computer</Genre>
      <Price>44.95</Price>
      <PublishDate>2000-10-01</PublishDate>
      <Description>An in-depth look at creating applications
      with XML.</Description>
   </Book>
   <Book id="bk102">
      <Author>Garcia, Debra</Author>
      <Title>Midnight Rain</Title>
      <Genre>Fantasy</Genre>
      <Price>5.95</Price>
      <PublishDate>2000-12-16</PublishDate>
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>
   </Book>
</Catalog>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML 'yi Ayrıştır](parse-string.md)
