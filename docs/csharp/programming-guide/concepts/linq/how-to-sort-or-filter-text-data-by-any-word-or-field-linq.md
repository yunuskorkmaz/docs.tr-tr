---
title: "Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c04d42f-4a78-42c8-9ec8-57ef18fe13a9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ccc48745918081663317e746953be6e0f09cdd8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-sort-or-filter-text-data-by-any-word-or-field-linq-c"></a><span data-ttu-id="96264-102">Nasıl yapılır: sıralama veya filtre metni verilerle herhangi bir sözcük veya alana (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="96264-102">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>
<span data-ttu-id="96264-103">Aşağıdaki örnek, satırın herhangi bir alana göre virgülle ayrılmış değerler gibi yapılandırılmış metin satırı sıralama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="96264-103">The following example shows how to sort lines of structured text, such as comma-separated values, by any field in the line.</span></span> <span data-ttu-id="96264-104">Alan, çalışma zamanında dinamik olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="96264-104">The field may be dynamically specified at runtime.</span></span> <span data-ttu-id="96264-105">Scores.csv alanları dört test puanları bir dizi tarafından izlenen öğrencinin kimlik numarasını temsil ettiğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="96264-105">Assume that the fields in scores.csv represent a student's ID number, followed by a series of four test scores.</span></span>  
  
### <a name="to-create-a-file-that-contains-data"></a><span data-ttu-id="96264-106">Veri içeren bir dosya oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="96264-106">To create a file that contains data</span></span>  
  
1.  <span data-ttu-id="96264-107">Konusundan scores.csv veri kopyalamak [nasıl yapılır: içerik katılma öğesinden farklı dosyaları (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) ve çözüm klasörüne kaydedin.</span><span class="sxs-lookup"><span data-stu-id="96264-107">Copy the scores.csv data from the topic [How to: Join Content from Dissimilar Files (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-join-content-from-dissimilar-files-linq.md) and save it to your solution folder.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96264-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="96264-108">Example</span></span>  
  
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
  
 <span data-ttu-id="96264-109">Bu örnek ayrıca bir sorgu değişkeni döndürme gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="96264-109">This example also demonstrates how to return a query variable from a method.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="96264-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="96264-110">Compiling the Code</span></span>  
 <span data-ttu-id="96264-111">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="96264-111">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96264-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="96264-112">See Also</span></span>  
 [<span data-ttu-id="96264-113">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="96264-113">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
