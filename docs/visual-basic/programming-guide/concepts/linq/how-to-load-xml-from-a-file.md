---
title: 'Nasıl yapılır: dosyadan XML yükleme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: 985c011d78b8386996ff4803194c8510e7ea0048
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582068"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="8afbc-102">Nasıl yapılır: dosyadan XML yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8afbc-102">How to: Load XML from a File (Visual Basic)</span></span>

<span data-ttu-id="8afbc-103">Bu konuda <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> yöntemi kullanılarak bir URI 'den XML yükleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8afbc-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="8afbc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8afbc-104">Example</span></span>

<span data-ttu-id="8afbc-105">Aşağıdaki örnek, bir dosyadan bir XML belgesinin nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8afbc-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="8afbc-106">Aşağıdaki örnek, Books. xml ' i yükler ve XML ağacını konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8afbc-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>

<span data-ttu-id="8afbc-107">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8afbc-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

<span data-ttu-id="8afbc-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8afbc-108">This code produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8afbc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8afbc-109">See also</span></span>

- [<span data-ttu-id="8afbc-110">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8afbc-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
