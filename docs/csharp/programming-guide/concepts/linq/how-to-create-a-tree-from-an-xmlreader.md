---
title: 'Nasıl yapılır: bir ağaç XmlReader (C#) oluşturma'
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 1a0f56655f2b328be5a6615088ef242061ddbd5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317277"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="c6a6c-102">Nasıl yapılır: bir ağaç XmlReader (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6a6c-102">How to: Create a Tree from an XmlReader (C#)</span></span>
<span data-ttu-id="c6a6c-103">Bu konuda, doğrudan bir XML ağacı oluşturmak gösterilmiştir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c6a6c-104">Oluşturmak için bir <xref:System.Xml.Linq.XElement> gelen bir <xref:System.Xml.XmlReader>, getirin gerekir <xref:System.Xml.XmlReader> bir öğe düğümü üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="c6a6c-105"><xref:System.Xml.XmlReader> Açıklamaları atlar ve işlem, ancak yönergeleri <xref:System.Xml.XmlReader> konumlandırılmış bir metin düğümü üzerinde bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="c6a6c-106">Bu tür hataları önlemek için her zaman getirin <xref:System.Xml.XmlReader> bir XML ağacından oluşturmadan önce bir öğede <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6a6c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6a6c-107">Example</span></span>  
 <span data-ttu-id="c6a6c-108">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c6a6c-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c6a6c-109">Aşağıdaki kod oluşturur bir `T:System.Xml.XmlReader` nesne ve ilk öğe düğüm bulana kadar okuma düğümleri.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="c6a6c-110">Daha sonra yükler <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="c6a6c-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c6a6c-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6a6c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6a6c-112">See Also</span></span>  
 [<span data-ttu-id="c6a6c-113">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="c6a6c-113">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
