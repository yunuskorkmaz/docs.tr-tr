---
title: XmlReader 'dan ağaç oluşturma (C#)
description: Doğrudan bir XmlReader 'dan bir XML ağacı oluşturmayı öğrenin. T:System.Xml.Xmlokuyucu nesnesinin nasıl oluşturulacağını gösteren bir örnek görürsünüz.
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 3801177e664d142652d38748d44eaf3f274239dd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302665"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>XmlReader 'dan ağaç oluşturma (C#)
Bu konu başlığında doğrudan bir XML ağacının nasıl oluşturulacağı gösterilmektedir <xref:System.Xml.XmlReader> . Bir öğesinden oluşturmak için, <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> öğesini bir <xref:System.Xml.XmlReader> öğe düğümüne konumlandırmalısınız. <xref:System.Xml.XmlReader>Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur. Bu tür hatalardan kaçınmak için, öğesinden bir <xref:System.Xml.XmlReader> XML ağacı oluşturmadan önce her zaman öğesini bir öğesine konumlandırın <xref:System.Xml.XmlReader> .  
  
## <a name="example"></a>Örnek  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod bir nesnesi oluşturur `T:System.Xml.XmlReader` ve ardından ilk öğe düğümünü bulana kadar düğümleri okur. Daha sonra nesneyi yükler <xref:System.Xml.Linq.XElement> .  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
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

- [XML 'yi ayrıştırma (C#)](how-to-parse-a-string.md)
