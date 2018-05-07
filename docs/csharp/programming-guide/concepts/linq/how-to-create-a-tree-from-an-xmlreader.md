---
title: 'Nasıl yapılır: bir ağaç XmlReader (C#) oluşturma'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 1a0f56655f2b328be5a6615088ef242061ddbd5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Nasıl yapılır: bir ağaç XmlReader (C#) oluşturma
Bu konuda, doğrudan bir XML ağacı oluşturmak gösterilmiştir bir <xref:System.Xml.XmlReader>. Oluşturmak için bir <xref:System.Xml.Linq.XElement> gelen bir <xref:System.Xml.XmlReader>, getirin gerekir <xref:System.Xml.XmlReader> bir öğe düğümü üzerinde. <xref:System.Xml.XmlReader> Açıklamaları atlar ve işlem, ancak yönergeleri <xref:System.Xml.XmlReader> konumlandırılmış bir metin düğümü üzerinde bir hata oluşturulur. Bu tür hataları önlemek için her zaman getirin <xref:System.Xml.XmlReader> bir XML ağacından oluşturmadan önce bir öğede <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Örnek  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 Aşağıdaki kod oluşturur bir `T:System.Xml.XmlReader` nesne ve ilk öğe düğüm bulana kadar okuma düğümleri. Daha sonra yükler <xref:System.Xml.Linq.XElement> nesnesi.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
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
 [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
