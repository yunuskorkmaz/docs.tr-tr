---
title: 'Nasıl yapılır: İki Liste Arasında Ayarlanmış Farkı Bulma (LINQ)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: cd33c08416cce5afb6cf7507335f753160b8c6ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344578"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)
Bu örnek, iki dize listesini karşılaştırmak ve names1. txt içinde olan ancak names2. txt içinde olmayan satırları çıkarmak için LINQ 'ın nasıl kullanılacağını gösterir.  
  
### <a name="to-create-the-data-files"></a>Veri dosyalarını oluşturmak için  
  
1. Names1. txt ve names2. txt ' i [nasıl yapılır: birleştirme ve karşılaştırma dize koleksiyonlarını (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)gösterildiği gibi çözüm klasörünüze kopyalayın.  
  
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
  
 Visual Basic <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>ve <xref:System.Linq.Enumerable.Concat%2A>gibi bazı sorgu işlemleri türleri yalnızca Yöntem tabanlı sözdiziminde ifade edilebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleme  
System. Linq ad alanı için `Imports` ifadesiyle bir VB.NET konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
