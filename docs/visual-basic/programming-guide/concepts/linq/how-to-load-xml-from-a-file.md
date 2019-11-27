---
title: 'Nasıl yapılır: dosyadan XML yükleme'
ms.date: 07/20/2015
ms.assetid: e2d337ad-8ac8-4671-b694-30e5ca1413b7
ms.openlocfilehash: 72a5adb8c7165f8113584f27bea64efde4ec58fb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336105"
---
# <a name="how-to-load-xml-from-a-file-visual-basic"></a><span data-ttu-id="200c4-102">Nasıl yapılır: dosyadan XML yükleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="200c4-102">How to: Load XML from a File (Visual Basic)</span></span>

<span data-ttu-id="200c4-103">Bu konuda <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> yöntemi kullanılarak bir URI 'den XML yükleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="200c4-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="200c4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="200c4-104">Example</span></span>

<span data-ttu-id="200c4-105">Aşağıdaki örnek, bir dosyadan bir XML belgesinin nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="200c4-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="200c4-106">Aşağıdaki örnek, Books. xml ' i yükler ve XML ağacını konsola çıkarır.</span><span class="sxs-lookup"><span data-stu-id="200c4-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>

<span data-ttu-id="200c4-107">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: kitaplar (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="200c4-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>

```vb
Dim booksFromFile As XElement = XElement.Load("books.xml")
Console.WriteLine(booksFromFile)
```

<span data-ttu-id="200c4-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="200c4-108">This code produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="200c4-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="200c4-109">See also</span></span>

- [<span data-ttu-id="200c4-110">XML 'yi ayrıştırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="200c4-110">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
