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
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="ad420-102">Nasıl yapılır: XmlReader (C#) öğesinden ağaç oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad420-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="ad420-103">Bu konu başlığında doğrudan bir <xref:System.Xml.XmlReader>xml ağacının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ad420-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ad420-104">Bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlReader> öğesinden oluşturmak için, öğesini bir öğe düğümüne konumlandırmalısınız. <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="ad420-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="ad420-105">Açıklamaları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümüne yerleştirilse bir hata oluşur. <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="ad420-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="ad420-106">Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> <xref:System.Xml.XmlReader>öğesinden bir XML ağacı oluşturmadan önce her zaman öğesini bir öğesine konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="ad420-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad420-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad420-107">Example</span></span>  
 <span data-ttu-id="ad420-108">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Kitaplar (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ad420-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ad420-109">Aşağıdaki kod bir `T:System.Xml.XmlReader` nesnesi oluşturur ve ardından ilk öğe düğümünü bulana kadar düğümleri okur.</span><span class="sxs-lookup"><span data-stu-id="ad420-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="ad420-110">Daha sonra <xref:System.Xml.Linq.XElement> nesneyi yükler.</span><span class="sxs-lookup"><span data-stu-id="ad420-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="ad420-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ad420-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad420-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad420-112">See also</span></span>

- [<span data-ttu-id="ad420-113">XML (C#) ayrıştırılıyor</span><span class="sxs-lookup"><span data-stu-id="ad420-113">Parsing XML (C#)</span></span>](./parsing-xml.md)
