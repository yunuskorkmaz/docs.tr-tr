---
title: 'Nasıl yapılır: bir sözcüğün bir dizede (LINQ) (C#) yinelemeleri Say'
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: b7003ff015669626c9d037549b36c440e3cc1301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33318841"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a>Nasıl yapılır: bir sözcüğün bir dizede (LINQ) (C#) yinelemeleri Say
Bu örnek bir LINQ Sorgu belirtilen bir sözcüğün bir dizede yinelemelerini saymak için nasıl kullanılacağını gösterir. Count ilk kez gerçekleştirmek için unutmayın <xref:System.String.Split%2A> yöntemi sözcükler dizisi oluşturmak için çağrılır. Bir performans maliyeti yoktur <xref:System.String.Split%2A> yöntemi. Dize yalnızca işlemi sözcükleri saymak için ise, kullanmayı düşünmelisiniz <xref:System.Text.RegularExpressions.Regex.Matches%2A> veya <xref:System.String.IndexOf%2A> yöntemleri yerine. Ancak, performans kritik bir sorun değildir veya diğer sorgu türleri üzerinde gerçekleştirmek için cümle zaten ayırdıktan sonra kelimeler ve ifadeler de saymak için LINQ kullanılacak mantıklıdır.  
  
## <a name="example"></a>Örnek  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"   
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
