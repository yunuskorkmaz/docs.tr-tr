---
title: 'Nasıl yapılır: XmlReader (C#) öğesinden ağaç oluşturma'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: f632bbdad7d52ea37e2587516792dfd13178d702
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593881"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Nasıl yapılır: XmlReader (C#) öğesinden ağaç oluşturma
Bu konu başlığında doğrudan bir <xref:System.Xml.XmlReader>xml ağacının nasıl oluşturulacağı gösterilmektedir. Bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> öğesinden oluşturmak için, öğesini bir öğe düğümüne konumlandırmalısınız. <xref:System.Xml.XmlReader> Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur. <xref:System.Xml.XmlReader> Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader>öğesinden bir XML ağacı oluşturmadan önce her zaman öğesini bir öğesine konumlandırın.  
  
## <a name="example"></a>Örnek  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod bir `T:System.Xml.XmlReader` nesnesi oluşturur ve ardından ilk öğe düğümünü bulana kadar düğümleri okur. Daha sonra <xref:System.Xml.Linq.XElement> nesneyi yükler.  
  
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

- [XML (C#) ayrıştırılıyor](./parsing-xml.md)
