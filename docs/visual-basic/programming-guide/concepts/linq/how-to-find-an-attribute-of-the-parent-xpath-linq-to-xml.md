---
title: "Nasıl yapılır: bir öznitelik üst (XPath-LINQ-XML) bulunamadı (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d2572fd-27d4-426c-b079-16854cb9ec7d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4da7888ab838dacbdda097f24580745692d407fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="d7115-102">Nasıl yapılır: bir öznitelik üst (XPath-LINQ-XML) bulunamadı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7115-102">How to: Find an Attribute of the Parent (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d7115-103">Bu konuda, üst öğesine gidin ve bunu bir öznitelik bulunamadı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7115-103">This topic shows how to navigate to the parent element and find an attribute of it.</span></span>  
  
 <span data-ttu-id="d7115-104">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="d7115-104">The XPath expression is:</span></span>  
  
 `../@id`  
  
## <a name="example"></a><span data-ttu-id="d7115-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7115-105">Example</span></span>  
 <span data-ttu-id="d7115-106">Bu örnek ilk bulur bir `Author` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d7115-106">This example first finds an `Author` element.</span></span> <span data-ttu-id="d7115-107">Ardından bulduğu `id` üst öğesinin özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d7115-107">It then finds the `id` attribute of the parent element.</span></span>  
  
 <span data-ttu-id="d7115-108">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Books (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d7115-108">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).</span></span>  
  
```vb  
Dim books As XDocument = XDocument.Load("Books.xml")  
Dim author As XElement = books.Root.<Book>.<Author>.FirstOrDefault()  
  
' LINQ to XML query  
Dim att1 As XAttribute = author.Parent.Attribute("id")  
  
' XPath expression  
Dim att2 As XAttribute = DirectCast(author.XPathEvaluate("../@id"),  _  
    IEnumerable).Cast(Of XAttribute)().First()  
  
If att1 Is att2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(att1)  
```  
  
 <span data-ttu-id="d7115-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="d7115-109">This example produces the following output:</span></span>  
  
```  
Results are identical  
id="bk101"  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7115-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7115-110">See Also</span></span>  
 [<span data-ttu-id="d7115-111">LINQ-XML XPath kullanıcıların (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7115-111">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
