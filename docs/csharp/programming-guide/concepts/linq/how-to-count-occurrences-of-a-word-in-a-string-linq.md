---
title: Dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (C#)
description: Bu örnek, bir dizedeki belirli bir sözcüğün tekrarlamalarını saymak Için C# dilinde bir LINQ sorgusu kullanır. Bir dizi sözcük oluşturmak için Split yöntemini kullanır.
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: e0ac7b338706c3f363fb21284e895bd1c7c48b6c
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89466124"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a>Dizedeki bir sözcüğün tekrarlamalarını sayma (LINQ) (C#)
Bu örnek, bir dizedeki belirli bir sözcüğün tekrarlamalarını saymak için bir LINQ sorgusunun nasıl kullanılacağını gösterir. Count işlemini gerçekleştirmek için öncelikle <xref:System.String.Split%2A> yöntemin bir dizi sözcük oluşturmak için çağrıldığını unutmayın. Yöntemin performans maliyeti vardır <xref:System.String.Split%2A> . Dizedeki tek işlem kelimeleri saymaya ise <xref:System.Text.RegularExpressions.Regex.Matches%2A> bunun yerine veya yöntemlerini kullanmayı göz önünde bulundurmanız gerekir <xref:System.String.IndexOf%2A> . Ancak, performans kritik bir sorun değilse veya tümceyi zaten böldüğünüz takdirde, diğer sorgu türlerini kullanmak için tümceyi daha önce ayırdıysanız, LINQ 'ı kullanarak sözcükleri veya tümceleri de saymanız mantıklıdır.  
  
## <a name="example"></a>Örnek  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET APIs. On the other side" +  
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
 `using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
