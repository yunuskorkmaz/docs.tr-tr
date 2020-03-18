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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="2581b-102">XmlReader'dan ağaç oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="2581b-102">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="2581b-103">Bu konu, doğrudan bir <xref:System.Xml.XmlReader>XML ağacının nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2581b-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2581b-104">Bir, <xref:System.Xml.Linq.XElement> bir <xref:System.Xml.XmlReader>öğe düğümü <xref:System.Xml.XmlReader> üzerinde konumlandırmak gerekir bir oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="2581b-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="2581b-105"><xref:System.Xml.XmlReader> Açıklamalar ve işleme yönergeleri atlar, <xref:System.Xml.XmlReader> ancak metin düğümü üzerinde konumlandırılmışsa, bir hata atılır.</span><span class="sxs-lookup"><span data-stu-id="2581b-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="2581b-106">Bu tür hataları önlemek <xref:System.Xml.XmlReader> için, her zaman bir XML <xref:System.Xml.XmlReader>ağacı oluşturmadan önce bir öğe üzerinde konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="2581b-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2581b-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2581b-107">Example</span></span>  
 <span data-ttu-id="2581b-108">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Kitaplar (LINQ-XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2581b-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2581b-109">Aşağıdaki kod bir `T:System.Xml.XmlReader` nesne oluşturur ve ilk öğe düğümlerini bulana kadar düğümleri okur.</span><span class="sxs-lookup"><span data-stu-id="2581b-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="2581b-110">Daha sonra <xref:System.Xml.Linq.XElement> nesneyi yükler.</span><span class="sxs-lookup"><span data-stu-id="2581b-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="2581b-111">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2581b-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2581b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2581b-112">See also</span></span>

- [<span data-ttu-id="2581b-113">Ayrıştırma XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2581b-113">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
