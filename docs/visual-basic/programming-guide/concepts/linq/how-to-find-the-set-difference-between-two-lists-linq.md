---
title: 'Nasıl yapılır: İki Liste Arasında Ayarlanmış Farkı Bulma (LINQ)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: f533b63b40325b34c5881c1e2f14aa4e576191c7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396603"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Nasıl yapılır: Iki liste arasındaki küme farkını bulma (LINQ) (Visual Basic)
Bu örnek, iki dize listesini karşılaştırmak ve names1. txt içinde olan ancak names2. txt içinde olmayan satırları çıkarmak için LINQ 'ın nasıl kullanılacağını gösterir.  
  
### <a name="to-create-the-data-files"></a>Veri dosyalarını oluşturmak için  
  
1. Names1. txt ve names2. txt ' i [nasıl yapılır: birleştirme ve karşılaştırma dize koleksiyonlarını (LINQ) (Visual Basic)](how-to-combine-and-compare-string-collections-linq.md)gösterildiği gibi çözüm klasörünüze kopyalayın.  
  
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
  
 ,,, Ve gibi Visual Basic bazı sorgu işlemleri türleri <xref:System.Linq.Enumerable.Except%2A> <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Concat%2A> yalnızca Yöntem tabanlı sözdiziminde ifade edilebilir.  
  
## <a name="compile-the-code"></a>Kodu derle  
`Imports`System. Linq ad alanı için bir deyimle birlikte Visual Basic konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](linq-and-strings.md)
