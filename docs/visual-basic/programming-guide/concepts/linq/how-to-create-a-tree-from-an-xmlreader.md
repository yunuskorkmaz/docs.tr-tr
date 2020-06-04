---
title: 'Nasıl yapılır: XmlReader’dan Ağaç Oluşturma'
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: 25c15ff08563b12b26041a536dfbca1c9cce260a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414614"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Nasıl yapılır: XmlReader 'dan ağaç oluşturma (Visual Basic)

Bu konu başlığında doğrudan bir XML ağacının nasıl oluşturulacağı gösterilmektedir <xref:System.Xml.XmlReader> . Bir öğesinden oluşturmak için, <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> öğesini bir <xref:System.Xml.XmlReader> öğe düğümüne konumlandırmalısınız. <xref:System.Xml.XmlReader>Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur. Bu tür hatalardan kaçınmak için, öğesinden bir <xref:System.Xml.XmlReader> XML ağacı oluşturmadan önce her zaman öğesini bir öğesine konumlandırın <xref:System.Xml.XmlReader> .

## <a name="example"></a>Örnek

Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](sample-xml-file-books-linq-to-xml.md).

Aşağıdaki kod bir nesnesi oluşturur `T:System.Xml.XmlReader` ve ardından ilk öğe düğümünü bulana kadar düğümleri okur. Daha sonra nesneyi yükler <xref:System.Xml.Linq.XElement> .

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

- [XML 'yi ayrıştırma (Visual Basic)](parsing-xml.md)
