---
title: XML bir dosyadan nasıl yüklenir (C#)
ms.date: 07/20/2015
ms.assetid: 3ed38487-8028-4209-9872-c8dce0ed4dfe
ms.openlocfilehash: 635b338bbaf9c15779bccab4d4c824037858b338
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169058"
---
# <a name="how-to-load-xml-from-a-file-c"></a><span data-ttu-id="8d6bb-102">XML bir dosyadan nasıl yüklenir (C#)</span><span class="sxs-lookup"><span data-stu-id="8d6bb-102">How to load XML from a file (C#)</span></span>
<span data-ttu-id="8d6bb-103">Bu konu, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> yöntemi kullanarak bir URI XML yüklemek için nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d6bb-103">This topic shows how to load XML from a URI by using the <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d6bb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d6bb-104">Example</span></span>  
 <span data-ttu-id="8d6bb-105">Aşağıdaki örnek, bir XML belgesinin bir dosyadan nasıl yüklenir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d6bb-105">The following example shows how to load an XML document from a file.</span></span> <span data-ttu-id="8d6bb-106">Aşağıdaki örnek books.xml yükler ve xml ağacını konsola boşaltır.</span><span class="sxs-lookup"><span data-stu-id="8d6bb-106">The following example loads books.xml and outputs the XML tree to the console.</span></span>  
  
 <span data-ttu-id="8d6bb-107">Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Kitaplar (LINQ-XML)](./sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8d6bb-107">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```csharp  
XElement booksFromFile = XElement.Load(@"books.xml");  
Console.WriteLine(booksFromFile);  
```  
  
 <span data-ttu-id="8d6bb-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8d6bb-108">This code produces the following output:</span></span>  
  
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
  