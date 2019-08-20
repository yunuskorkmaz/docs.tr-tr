---
title: 'Nasıl yapılır: Iki liste arasındaki (LINQ) (C#) küme farkını bulma'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: decdbe45afd12581a53ed70ec843ee72f54f0409
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593346"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>Nasıl yapılır: Iki liste arasındaki (LINQ) (C#) küme farkını bulma
Bu örnek, iki dize listesini karşılaştırmak ve names1. txt içinde olan ancak names2. txt içinde olmayan satırları çıkarmak için LINQ 'ın nasıl kullanılacağını gösterir.  
  
### <a name="to-create-the-data-files"></a>Veri dosyalarını oluşturmak için  
  
1. Names1. txt ve names2. txt dosyasını çözüm klasörünüze kopyalamak için [şöyle gösterildiği gibi kopyalayın: Dize koleksiyonlarını birleştirin ve karşılaştırın (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).  
  
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
  
 C#, <xref:System.Linq.Enumerable.Except%2A>, ,<xref:System.Linq.Enumerable.Union%2A>Ve <xref:System.Linq.Enumerable.Distinct%2A> gibibazısorguişlemleritürleriyalnızcaYöntemtabanlısözdizimindeifadeedilebilir<xref:System.Linq.Enumerable.Concat%2A>.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 System. C# LINQ ve System.IO ad alanları `using` için yönergeler içeren bir konsol uygulaması projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
