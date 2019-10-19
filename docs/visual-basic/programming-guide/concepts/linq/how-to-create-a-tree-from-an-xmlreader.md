---
title: "Nasıl yapılır: XmlReader 'dan ağaç oluşturma (Visual Basic)"
ms.date: 07/20/2015
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
ms.openlocfilehash: c90fbee29a380824cdc32dd62622e55ea40044fd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583020"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="a1c22-102">Nasıl yapılır: XmlReader 'dan ağaç oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1c22-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>

<span data-ttu-id="a1c22-103">Bu konu başlığında doğrudan bir <xref:System.Xml.XmlReader> XML ağacının nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a1c22-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="a1c22-104">Bir <xref:System.Xml.XmlReader> <xref:System.Xml.Linq.XElement> oluşturmak için, <xref:System.Xml.XmlReader> bir öğe düğümüne konumlandırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a1c22-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="a1c22-105">@No__t_0 Yorumları ve işleme talimatlarını atlar, ancak <xref:System.Xml.XmlReader> bir metin düğümünde konumlandırılmışsa bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a1c22-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="a1c22-106">Bu tür hatalardan kaçınmak için, <xref:System.Xml.XmlReader> bir XML ağacı oluşturmadan önce <xref:System.Xml.XmlReader> her zaman bir öğe üzerinde konumlandırın.</span><span class="sxs-lookup"><span data-stu-id="a1c22-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>

## <a name="example"></a><span data-ttu-id="a1c22-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1c22-107">Example</span></span>

<span data-ttu-id="a1c22-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a1c22-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

<span data-ttu-id="a1c22-109">Aşağıdaki kod bir `T:System.Xml.XmlReader` nesnesi oluşturur ve ilk öğe düğümünü bulana kadar düğümleri okur.</span><span class="sxs-lookup"><span data-stu-id="a1c22-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="a1c22-110">Daha sonra <xref:System.Xml.Linq.XElement> nesnesini yükler.</span><span class="sxs-lookup"><span data-stu-id="a1c22-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>

```vb
Dim r As XmlReader = XmlReader.Create("books.xml")
Do While r.NodeType <> XmlNodeType.Element
    r.Read()
Loop
Dim e As XElement = XElement.Load(r)
Console.WriteLine(e)
```

<span data-ttu-id="a1c22-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a1c22-111">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a1c22-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1c22-112">See also</span></span>

- [<span data-ttu-id="a1c22-113">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1c22-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
