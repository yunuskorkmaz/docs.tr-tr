---
title: "Nasıl yapılır: Xmlreader'dan ağaç oluşturma (C#)"
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: fb65c7b74bf3bd006fd4f545e4587efe9a392131
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496194"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="59b84-102">Nasıl yapılır: Xmlreader'dan ağaç oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="59b84-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="59b84-103">Bu konuda, doğrudan bir XML ağacı oluşturma işlemi gösterilmektedir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="59b84-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="59b84-104">Oluşturmak için bir <xref:System.Xml.Linq.XElement> gelen bir <xref:System.Xml.XmlReader>, siz de getirmelisiniz <xref:System.Xml.XmlReader> bir öğe düğümü üzerinde.</span><span class="sxs-lookup"><span data-stu-id="59b84-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="59b84-105"><xref:System.Xml.XmlReader> Açıklamaları atlar ve işleme talimatları, ancak <xref:System.Xml.XmlReader> konumlandırılmış bir metin düğümü üzerinde bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="59b84-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="59b84-106">Bu tür hataları önlemek için her zaman konumlandırma <xref:System.Xml.XmlReader> XML ağacından oluşturmadan önce bir öğede <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="59b84-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59b84-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="59b84-107">Example</span></span>  
 <span data-ttu-id="59b84-108">Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="59b84-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="59b84-109">Aşağıdaki kod oluşturur bir `T:System.Xml.XmlReader` nesnesi ve ilk öğe düğümü bulana kadar okuma düğümleri.</span><span class="sxs-lookup"><span data-stu-id="59b84-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="59b84-110">Ardından yükler <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="59b84-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="59b84-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="59b84-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59b84-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59b84-112">See also</span></span>

- [<span data-ttu-id="59b84-113">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="59b84-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
