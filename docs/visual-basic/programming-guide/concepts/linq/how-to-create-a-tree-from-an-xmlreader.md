---
title: "Nasıl yapılır: (Visual Basic) Xmlreader'dan ağaç oluşturma"
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: d0826112821394ac6a81ba03e7803187aaec2796
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836473"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Nasıl yapılır: (Visual Basic) Xmlreader'dan ağaç oluşturma
Bu konuda, doğrudan bir XML ağacı oluşturma işlemi gösterilmektedir bir <xref:System.Xml.XmlReader>. Oluşturmak için bir <xref:System.Xml.Linq.XElement> gelen bir <xref:System.Xml.XmlReader>, siz de getirmelisiniz <xref:System.Xml.XmlReader> bir öğe düğümü üzerinde. <xref:System.Xml.XmlReader> Açıklamaları atlar ve işleme talimatları, ancak <xref:System.Xml.XmlReader> konumlandırılmış bir metin düğümü üzerinde bir hata oluşturulur. Bu tür hataları önlemek için her zaman konumlandırma <xref:System.Xml.XmlReader> XML ağacından oluşturmadan önce bir öğede <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Örnek  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod oluşturur bir `T:System.Xml.XmlReader` nesnesi ve ilk öğe düğümü bulana kadar okuma düğümleri. Ardından yükler <xref:System.Xml.Linq.XElement> nesne.  
  
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

- [Ayrıştırma XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
