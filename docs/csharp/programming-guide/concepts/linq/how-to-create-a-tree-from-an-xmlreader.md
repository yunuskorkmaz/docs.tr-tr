---
title: "Nasıl yapılır: XmlReader 'dan ağaç oluşturma (C#)"
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: a0cff596e0a6d50aefab3645a99beec3277d05ec
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418318"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Nasıl yapılır: XmlReader 'dan ağaç oluşturma (C#)
Bu konu başlığında doğrudan bir <xref:System.Xml.XmlReader> XML ağacının nasıl oluşturulacağı gösterilmektedir. Bir <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> oluşturmak için, <xref:System.Xml.XmlReader> bir öğe düğümüne konumlandırmalısınız. <xref:System.Xml.XmlReader> Yorumları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümünde konumlandırılmışsa bir hata oluşturulur. Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> bir XML ağacı oluşturmadan önce <xref:System.Xml.XmlReader> her zaman bir öğe üzerinde konumlandırın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod bir `T:System.Xml.XmlReader` nesnesi oluşturur ve ilk öğe düğümünü bulana kadar düğümleri okur. Daha sonra <xref:System.Xml.Linq.XElement> nesnesini yükler.  
  
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

- [XML (C#) ayrıştırılıyor](how-to-parse-a-string.md)
