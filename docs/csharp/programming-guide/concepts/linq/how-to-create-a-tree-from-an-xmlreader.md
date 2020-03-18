---
title: XmlReader'dan ağaç oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 9ead6352112d9e1b56bd70699c90133e432f96b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169278"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>XmlReader'dan ağaç oluşturma (C#)
Bu konu, doğrudan bir <xref:System.Xml.XmlReader>XML ağacının nasıl oluşturulabildiğini gösterir. Bir, <xref:System.Xml.Linq.XElement> bir <xref:System.Xml.XmlReader>öğe düğümü <xref:System.Xml.XmlReader> üzerinde konumlandırmak gerekir bir oluşturmak için. <xref:System.Xml.XmlReader> Açıklamalar ve işleme yönergeleri atlar, <xref:System.Xml.XmlReader> ancak metin düğümü üzerinde konumlandırılmışsa, bir hata atılır. Bu tür hataları önlemek <xref:System.Xml.XmlReader> için, her zaman bir XML <xref:System.Xml.XmlReader>ağacı oluşturmadan önce bir öğe üzerinde konumlandırın.  
  
## <a name="example"></a>Örnek  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Kitaplar (LINQ-XML)](./sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod bir `T:System.Xml.XmlReader` nesne oluşturur ve ilk öğe düğümlerini bulana kadar düğümleri okur. Daha sonra <xref:System.Xml.Linq.XElement> nesneyi yükler.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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

- [Ayrıştırma XML (C#)](how-to-parse-a-string.md)
