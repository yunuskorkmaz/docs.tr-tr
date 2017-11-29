---
title: "Nasıl yapılır: iki liste (LINQ) (Visual Basic) arasında ayarlanmış farkı bulma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 267e348ac528b210e25c5b8b6e01294a225bc48e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Nasıl yapılır: iki liste (LINQ) (Visual Basic) arasında ayarlanmış farkı bulma
Bu örnek LINQ listelerini dizeleri karşılaştırmak ve names1.txt ancak names2.txt olan satırlar çıkış için nasıl kullanılacağını gösterir.  
  
### <a name="to-create-the-data-files"></a>Veri dosyaları oluşturmak için  
  
1.  Kopyalama names1.txt ve names2.txt Çözüm klasörünüz gösterildiği gibi [nasıl yapılır: birleştirme ve karşılaştırma dizesi koleksiyonları (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).  
  
## <a name="example"></a>Örnek  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 Sorgu işlemleri Visual Basic'te gibi bazı türleri <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, ve <xref:System.Linq.Enumerable.Concat%2A>, yalnızca yöntem temelli sözdiziminde ifade edilebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
