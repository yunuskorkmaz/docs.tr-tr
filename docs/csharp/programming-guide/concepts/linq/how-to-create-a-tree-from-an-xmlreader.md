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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="2ca7a-104">XmlReader 'dan ağaç oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="2ca7a-104">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="2ca7a-105">Bu konu başlığında doğrudan bir XML ağacının nasıl oluşturulacağı gösterilmektedir <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="2ca7a-105">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="2ca7a-106">Bir öğesinden oluşturmak için, <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> öğesini bir <xref:System.Xml.XmlReader> öğe düğümüne konumlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="2ca7a-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="2ca7a-107"><xref:System.Xml.XmlReader>Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="2ca7a-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="2ca7a-108">Bu tür hatalardan kaçınmak için, öğesinden bir <xref:System.Xml.XmlReader> XML ağacı oluşturmadan önce her zaman öğesini bir öğesine konumlandırın <xref:System.Xml.XmlReader> .</span><span class="sxs-lookup"><span data-stu-id="2ca7a-108">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ca7a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ca7a-109">Example</span></span>  
 <span data-ttu-id="2ca7a-110">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2ca7a-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2ca7a-111">Aşağıdaki kod bir nesnesi oluşturur `T:System.Xml.XmlReader` ve ardından ilk öğe düğümünü bulana kadar düğümleri okur.</span><span class="sxs-lookup"><span data-stu-id="2ca7a-111">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="2ca7a-112">Daha sonra nesneyi yükler <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="2ca7a-112">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="2ca7a-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2ca7a-113">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ca7a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ca7a-114">See also</span></span>

- [<span data-ttu-id="2ca7a-115">XML 'yi ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="2ca7a-115">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
