---
title: "Nasıl yapılır: Xmlreader'dan (C#) bir ağaç oluşturun"
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: f0e75e4d3f6964fa44c41265c1c276c32fb9e87d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501760"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Nasıl yapılır: Xmlreader'dan (C#) bir ağaç oluşturun
Bu konuda, doğrudan bir XML ağacı oluşturma işlemi gösterilmektedir bir <xref:System.Xml.XmlReader>. Oluşturmak için bir <xref:System.Xml.Linq.XElement> gelen bir <xref:System.Xml.XmlReader>, siz de getirmelisiniz <xref:System.Xml.XmlReader> bir öğe düğümü üzerinde. <xref:System.Xml.XmlReader> Açıklamaları atlar ve işleme talimatları, ancak <xref:System.Xml.XmlReader> konumlandırılmış bir metin düğümü üzerinde bir hata oluşturulur. Bu tür hataları önlemek için her zaman konumlandırma <xref:System.Xml.XmlReader> XML ağacından oluşturmadan önce bir öğede <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod oluşturur bir `T:System.Xml.XmlReader` nesnesi ve ilk öğe düğümü bulana kadar okuma düğümleri. Ardından yükler <xref:System.Xml.Linq.XElement> nesne.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
