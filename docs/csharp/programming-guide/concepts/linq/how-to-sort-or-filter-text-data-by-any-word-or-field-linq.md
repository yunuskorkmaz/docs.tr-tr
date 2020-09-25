---
title: Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)
description: Metin verilerini herhangi bir sözcük veya alana göre sıralamayı veya filtreleyeceğinizi öğrenin. Yapılandırılmış metnin satırlarını satırdaki herhangi bir alana göre sıralamak için bir örneğe bakın.
ms.date: 07/20/2015
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
ms.openlocfilehash: 05858cc787d3916b204910df10d3291796cebc02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203949"
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a>Her kelime veya alana göre metin verilerini sıralama veya filtreleme (LINQ) (C#)

Aşağıdaki örnek, virgülle ayrılmış değerler gibi yapılandırılmış metnin çizgilerinin satırdaki herhangi bir alana göre nasıl sıralanacağını gösterir. Alan, çalışma zamanında dinamik olarak belirtilmiş olabilir. scores.csv içindeki alanların, bir öğrencinin KIMLIK numarasını temsil ettiğini ve ardından dört test puanı serisi olduğunu varsayalım.  
  
### <a name="to-create-a-file-that-contains-data"></a>Veri içeren bir dosya oluşturmak için  
  
1. scores.csv verileri, [benzer dosyalardan (LINQ) (C#) içerik ekleme](./how-to-join-content-from-dissimilar-files-linq.md) ve çözüm klasörünüze kaydetme konusundan kopyalayın.  
  
## <a name="example"></a>Örnek  
  
```csharp  
public class SortLines  
{  
    static void Main()  
    {  
        // Create an IEnumerable data source  
        string[] scores = System.IO.File.ReadAllLines(@"../../../scores.csv");  
  
        // Change this to any value from 0 to 4.  
        int sortField = 1;  
  
        Console.WriteLine("Sorted highest to lowest by field [{0}]:", sortField);  
  
        // Demonstrates how to return query from a method.  
        // The query is executed here.  
        foreach (string str in RunQuery(scores, sortField))  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // Returns the query variable, not query results!  
    static IEnumerable<string> RunQuery(IEnumerable<string> source, int num)  
    {  
        // Split the string and sort on field[num]  
        var scoreQuery = from line in source  
                         let fields = line.Split(',')  
                         orderby fields[num] descending  
                         select line;  
  
        return scoreQuery;  
    }  
}  
/* Output (if sortField == 1):  
   Sorted highest to lowest by field [1]:  
    116, 99, 86, 90, 94  
    120, 99, 82, 81, 79  
    111, 97, 92, 81, 60  
    114, 97, 89, 85, 82  
    121, 96, 85, 91, 60  
    122, 94, 92, 91, 91  
    117, 93, 92, 80, 87  
    118, 92, 90, 83, 78  
    113, 88, 94, 65, 91  
    112, 75, 84, 91, 39  
    119, 68, 79, 88, 92  
    115, 35, 72, 91, 70  
 */  
```  
  
 Bu örnek ayrıca bir yöntemden nasıl sorgu değişkeni dönebileceğinizi gösterir.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ ve dizeler (C#)](./linq-and-strings.md)
