---
title: İki liste (LINQ) (C#) arasındaki küme farkı nasıl bulabilirim?
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 03fae5451ee395487e73ed7c38d465c3f891e0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169187"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a>İki liste (LINQ) (C#) arasındaki küme farkı nasıl bulabilirim?
Bu örnek, iki dize listesini karşılaştırmak için LINQ'nin nasıl kullanılacağını ve names1.txt'de olmayan ancak names2.txt'de olmayan bu satırları niçin çıkarı elde edilmeyeceğini gösterir.  
  
### <a name="to-create-the-data-files"></a>Veri dosyalarını oluşturmak için  
  
1. String [koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)'de gösterildiği gibi, names1.txt ve names2.txt'yi çözüm klasörünüze kopyalayın.  
  
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
  
 C#'daki bazı sorgu işlemleri <xref:System.Linq.Enumerable.Except%2A>türleri <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A>, <xref:System.Linq.Enumerable.Concat%2A>, , ve , gibi yalnızca yöntem tabanlı sözdizimiile ifade edilebilir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 System.Linq ve System.IO `using` ad alanları için yönergeleri içeren bir C# konsolu uygulama projesi oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve Dizeleri (C#)](./linq-and-strings.md)
