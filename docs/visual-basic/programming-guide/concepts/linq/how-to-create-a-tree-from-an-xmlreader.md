---
title: "Nasıl yapılır: bir XmlReader (Visual Basic) bir ağacı oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ceae7c2bee85e7b368322c8ba195dea9feff672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a><span data-ttu-id="685aa-102">Nasıl yapılır: bir XmlReader (Visual Basic) bir ağacı oluşturma</span><span class="sxs-lookup"><span data-stu-id="685aa-102">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="685aa-103">Bu konuda, doğrudan bir XML ağacı oluşturmak gösterilmiştir bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="685aa-103">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="685aa-104">Oluşturmak için bir <xref:System.Xml.Linq.XElement> gelen bir <xref:System.Xml.XmlReader>, getirin gerekir <xref:System.Xml.XmlReader> bir öğe düğümü üzerinde.</span><span class="sxs-lookup"><span data-stu-id="685aa-104">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="685aa-105"><xref:System.Xml.XmlReader> Açıklamaları atlar ve işlem, ancak yönergeleri <xref:System.Xml.XmlReader> konumlandırılmış bir metin düğümü üzerinde bir hata oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="685aa-105">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="685aa-106">Bu tür hataları önlemek için her zaman getirin <xref:System.Xml.XmlReader> bir XML ağacından oluşturmadan önce bir öğede <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="685aa-106">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="685aa-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="685aa-107">Example</span></span>  
 <span data-ttu-id="685aa-108">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="685aa-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="685aa-109">Aşağıdaki kod oluşturur bir `T:System.Xml.XmlReader` nesne ve ilk öğe düğüm bulana kadar okuma düğümleri.</span><span class="sxs-lookup"><span data-stu-id="685aa-109">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="685aa-110">Daha sonra yükler <xref:System.Xml.Linq.XElement> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="685aa-110">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 <span data-ttu-id="685aa-111">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="685aa-111">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="685aa-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="685aa-112">See Also</span></span>  
 [<span data-ttu-id="685aa-113">Ayrıştırma XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="685aa-113">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
