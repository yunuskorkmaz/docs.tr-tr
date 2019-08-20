---
title: 'Nasıl yapılır: Dizedeki karakterleri sorgulama (LINQ) (C#)'
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: 1212ebcf264aab756eca1acb81ae617c2218a065
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592883"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Nasıl yapılır: Dizedeki karakterleri sorgulama (LINQ) (C#)
<xref:System.String> Sınıfı genel<xref:System.Collections.Generic.IEnumerable%601> arabirimi uyguladığından, herhangi bir dize bir karakter dizisi olarak sorgulanabilir. Ancak bu, LINQ 'in yaygın bir kullanımı değildir. Karmaşık kalıp eşleştirme işlemleri için <xref:System.Text.RegularExpressions.Regex> sınıfını kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemede bir dizeyi sorgular. Sorgunun ilk kez yürütüldükten sonra "yeniden kullanılır" olduğunu unutmayın. Sorgunun kendisi gerçek sonuçları depolamadığından bu mümkündür.  
  
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
 System. C# LINQ ve System.IO ad alanları `using` için yönergeler içeren bir konsol uygulaması projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
- [Nasıl yapılır: LINQ sorgularını normal Ifadelerle birleştirme (C#)](./how-to-combine-linq-queries-with-regular-expressions.md)
