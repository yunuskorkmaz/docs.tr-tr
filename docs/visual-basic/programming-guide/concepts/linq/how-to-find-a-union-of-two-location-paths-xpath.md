---
title: "Nasıl yapılır: iki konum yolları (XPath-LINQ-XML) birleşimini Bul (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c82c09b4-cb0a-47ec-8cc3-a124144c2788
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c15ef409500a07d922563309301ea8f1442feee6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml-visual-basic"></a>Nasıl yapılır: iki konum yolları (XPath-LINQ-XML) birleşimini Bul (Visual Basic)
XPath iki XPath Konum yolları sonuçlarını birleşimi bulmanızı sağlar.  
  
 XPath ifadesi şöyledir:  
  
 `//Category|//Price`  
  
 Kullanarak aynı sonucu elde edebilirsiniz <xref:System.Linq.Enumerable.Concat%2A> standart sorgu işleci.  
  
## <a name="example"></a>Örnek  
 Bu örnekte tüm bulur `Category` öğeleri ve tüm `Price` öğeleri ve bunları tek bir koleksiyona art arda ekler. Unutmayın [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu çağrıları <xref:System.Xml.Linq.Extensions.InDocumentOrder%2A> sonuçları sıralamak için. XPath ifadesi değerlendirme sonuçlarını da belge sıradadır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: sayısal verileri (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```vb  
Dim data As XDocument = XDocument.Load("Data.xml")  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = _  
    data...<Category>.Concat(data...<Price>).InDocumentOrder()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = _  
    data.XPathSelectElements("//Category|//Price")  
  
If list1.Count() = list2.Count() And _  
        list1.Intersect(list2).Count() = list1.Count() Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
Results are identical  
<Category>A</Category>  
<Price>24.50</Price>  
<Category>B</Category>  
<Price>89.99</Price>  
<Category>A</Category>  
<Price>4.95</Price>  
<Category>A</Category>  
<Price>66.00</Price>  
<Category>B</Category>  
<Price>.99</Price>  
<Category>A</Category>  
<Price>29.00</Price>  
<Category>B</Category>  
<Price>6.99</Price>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML XPath kullanıcıların (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
