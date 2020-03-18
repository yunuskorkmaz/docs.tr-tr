---
title: Dizedeki karakterler (LINQ) (C#) karakterleri sorgulama
ms.date: 07/20/2015
ms.assetid: 727a1be7-dbec-4ab8-b414-bc2d56feb6ff
ms.openlocfilehash: d85e488a38a6167505732103b4c540cade6ea9bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345675"
---
# <a name="how-to-query-for-characters-in-a-string-linq-c"></a>Dizedeki karakterler (LINQ) (C#) karakterleri sorgulama
<xref:System.String> Sınıf genel <xref:System.Collections.Generic.IEnumerable%601> arabirimi uyguladığından, herhangi bir dize bir karakter dizisi olarak sorgulanabilir. Ancak, bu LINQ yaygın bir kullanımı değildir. Karmaşık desen eşleştirme işlemleri <xref:System.Text.RegularExpressions.Regex> için sınıfı kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, içerdiği sayısal basamak sayısını belirlemek için bir dize sorgular. Sorgunun ilk kez yürütüldükten sonra "yeniden kullanıldığını" unutmayın. Sorgunun kendisi herhangi bir gerçek sonuç depolamaz, çünkü bu mümkündür.  
  
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
 System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dizeleri (C#)](./linq-and-strings.md)
- [LINQ sorgularını normal ifadelerle birleştirme (C#)](./how-to-combine-linq-queries-with-regular-expressions.md)
