---
title: 'Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) (Visual Basic) oluşum sayısı'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: b3d34503e87aff1180dca4cb8233d668d35b0255
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051747"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a>Nasıl yapılır: Bir sözcüğün bir dizede (LINQ) (Visual Basic) oluşum sayısı
Bu örnek belirtilen bir sözcüğün bir dizede oluşumları saymak için LINQ sorgusu kullanmayı gösterir. Sayım gerçekleştirmeye unutmayın <xref:System.String.Split%2A> yöntemi bir kelimelerin dizi oluşturmak için çağrılır. Bir performans maliyetine yoktur <xref:System.String.Split%2A> yöntemi. Sözcükleri saymak için dize yalnızca işlemi ise kullanmayı düşünmelisiniz <xref:System.Text.RegularExpressions.Regex.Matches%2A> veya <xref:System.String.IndexOf%2A> yöntemleri yerine. Ancak, performans kritik bir sorunu değil ya da diğer sorgu türleri üzerinde gerçekleştirmek için önceden cümle ayırdıktan sonra sözcükler veya tümcecikler de saymak için LINQ kullanma mantıklıdır.  
  
## <a name="example"></a>Örnek  
  
```vb  
Class CountWords  
  
    Shared Sub Main()  
  
        Dim text As String = "Historically, the world of data and the world of objects" &   
                  " have not been well integrated. Programmers work in C# or Visual Basic" &   
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &   
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &   
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &   
                  " them. Data types often require translation between the two worlds; there are" &   
                  " different standard functions. Because the object world has no notion of query, a" &   
                  " query can only be represented as a string without compile-time type checking or" &   
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &   
                  " objects in memory is often tedious and error-prone."  
  
        Dim searchTerm As String = "data"  
  
        ' Convert the string into an array of words.  
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},   
                                                 StringSplitOptions.RemoveEmptyEntries)  
  
        ' Create and execute the query. It executes immediately   
        ' because a singleton value is produced.  
        ' Use ToLower to match "data" and "Data"   
        Dim matchQuery = From word In dataSource   
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()   
                      Select word  
  
        ' Count the matches.  
        Dim count As Integer = matchQuery.Count()  
        Console.WriteLine(count & " occurrence(s) of the search term """ &   
                          searchTerm & """ were found.")  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' 3 occurrence(s) of the search term "data" were found.  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve bir `Imports` System.Linq ad alanı bildirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
