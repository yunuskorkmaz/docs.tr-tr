---
title: 'Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakter için'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: db535f55822fa40d8589ddf95f9f78adfa1b6f1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Nasıl yapılır: sorgu (LINQ) (C#) bir dizedeki karakter için
Çünkü <xref:System.String> sınıfı uygulayan genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir dize bir karakter dizisi sorgulanabilir. Ancak, bu yaygın bir kullanımdır LINQ değildir. İşlem eşleştirme karmaşık desen için kullanmak <xref:System.Text.RegularExpressions.Regex> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemek için bir dize sorgular. "İlk kez yürütüldükten sonra sorguyu yeniden kullanılacağını" unutmayın. Bu, sorgu herhangi bir gerçek sonuç depolamaz çünkü mümkündür.  
  
```csharp  
class QueryAString  
{  
    static void Main()  
    {  
        string aString = "ABCDE99F-J74-12-89A";  
  
        // Select only those characters that are numbers  
        IEnumerable<char> stringQuery =  
          from ch in aString  
          where Char.IsDigit(ch)  
          select ch;  
  
        // Execute the query  
        foreach (char c in stringQuery)  
            Console.Write(c + " ");  
  
        // Call the Count method on the existing query.  
        int count = stringQuery.Count();  
        Console.WriteLine("Count = {0}", count);  
  
        // Select all characters before the first '-'  
        IEnumerable<char> stringQuery2 = aString.TakeWhile(c => c != '-');  
  
        // Execute the second query  
        foreach (char c in stringQuery2)  
            Console.Write(c);  
  
        Console.WriteLine(System.Environment.NewLine + "Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
  Output: 9 9 7 4 1 2 8 9  
  Count = 8  
  ABCDE99F  
*/  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 .NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ ve dizeler (C#)](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 [Nasıl yapılır: normal ifadeler (C#) ile LINQ sorgularını birleştirme](../../../../csharp/programming-guide/concepts/linq/how-to-combine-linq-queries-with-regular-expressions.md)
