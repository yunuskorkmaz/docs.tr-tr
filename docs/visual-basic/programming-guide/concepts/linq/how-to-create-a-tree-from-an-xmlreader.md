---
title: "Nasıl yapılır: XmlReader 'dan ağaç oluşturma (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: c90fbee29a380824cdc32dd62622e55ea40044fd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583020"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Nasıl yapılır: XmlReader 'dan ağaç oluşturma (Visual Basic)

Bu konu başlığında doğrudan bir <xref:System.Xml.XmlReader> XML ağacının nasıl oluşturulacağı gösterilmektedir. Bir <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> oluşturmak için, <xref:System.Xml.XmlReader> bir öğe düğümüne konumlandırmalısınız. @No__t_0 Yorumları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümünde konumlandırılmışsa bir hata oluşturulur. Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> bir XML ağacı oluşturmadan önce <xref:System.Xml.XmlReader> her zaman bir öğe üzerinde konumlandırın.

## <a name="example"></a>Örnek

Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).

Aşağıdaki kod bir `T:System.Xml.XmlReader` nesnesi oluşturur ve ilk öğe düğümünü bulana kadar düğümleri okur. Daha sonra <xref:System.Xml.Linq.XElement> nesnesini yükler.

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

- [XML 'yi ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
