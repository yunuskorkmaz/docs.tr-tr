---
title: İki liste arasındaki küme farkını bulma (LINQ) (C#)
description: İki dize listesini karşılaştırmak ve bir listede olan ancak diğeri içinde olmayan satırları çıkarmak Için C# ' de LINQ kullanmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 01aba16b3489e4bf21a76bc715b6d4d2c9d250dd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159065"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>İki liste arasındaki küme farkını bulma (LINQ) (C#)

Bu örnek, iki dize listesini karşılaştırmak ve names1.txt ancak names2.txt olmayan satırları çıkarmak için LINQ 'ın nasıl kullanılacağını gösterir.  
  
### <a name="to-create-the-data-files"></a>Veri dosyalarını oluşturmak için  
  
1. names1.txt ve names2.txt, [dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)bölümünde gösterildiği gibi çözüm klasörünüze kopyalayın.  
  
## <a name="example"></a>Örnek  
  
```csharp  
class CompareLists  
{
    static void Main()  
    {  
        // Create the IEnumerable data sources.  
        string[] names1 = System.IO.File.ReadAllLines(@"../../../names1.txt");  
        string[] names2 = System.IO.File.ReadAllLines(@"../../../names2.txt");  
  
        // Create the query. Note that method syntax must be used here.  
        IEnumerable<string> differenceQuery =  
          names1.Except(names2);  
  
        // Execute the query.  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt");  
        foreach (string s in differenceQuery)  
            Console.WriteLine(s);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
     The following lines are in names1.txt but not names2.txt  
    Potra, Cristina  
    Noriega, Fabricio  
    Aw, Kam Foo  
    Toyoshima, Tim  
    Guy, Wey Yuan  
    Garcia, Debra  
     */  
```  
  
 C# içinde,, ve gibi bazı sorgu işlemleri türleri <xref:System.Linq.Enumerable.Except%2A> <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Concat%2A> yalnızca Yöntem tabanlı sözdiziminde ifade edilebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 `using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
