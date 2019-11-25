---
title: XmlReader 'dan ağaç oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 196779a10678bdd3aa5399cf883af8c4b074e5df
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141319"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="5d8d3-102">XmlReader 'dan ağaç oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="5d8d3-102">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="5d8d3-103">Bu konu başlığında doğrudan bir <xref:System.Xml.XmlReader> XML ağacının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="5d8d3-104">Bir <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> oluşturmak için, <xref:System.Xml.XmlReader> bir öğe düğümüne konumlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="5d8d3-105"><xref:System.Xml.XmlReader> Yorumları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümünde konumlandırılmışsa bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="5d8d3-106">Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> bir XML ağacı oluşturmadan önce <xref:System.Xml.XmlReader> her zaman bir öğe üzerinde konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d8d3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5d8d3-107">Example</span></span>  
 <span data-ttu-id="5d8d3-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5d8d3-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="5d8d3-109">Aşağıdaki kod bir `T:System.Xml.XmlReader` nesnesi oluşturur ve ilk öğe düğümünü bulana kadar düğümleri okur.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="5d8d3-110">Daha sonra <xref:System.Xml.Linq.XElement> nesnesini yükler.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="5d8d3-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5d8d3-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5d8d3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8d3-112">See also</span></span>

- [<span data-ttu-id="5d8d3-113">XML (C#) ayrıştırılıyor</span><span class="sxs-lookup"><span data-stu-id="5d8d3-113">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
