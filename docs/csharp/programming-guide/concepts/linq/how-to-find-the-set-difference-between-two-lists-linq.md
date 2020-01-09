---
title: İki liste arasında küme farkını bulma (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 227405428a1b418cbe6ceb3d0e3274595307e5ef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345934"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="c4f76-102">İki liste arasında küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4f76-102">How to find the set difference between two lists (LINQ) (C#)</span></span>
<span data-ttu-id="c4f76-103">Bu örnek, iki dize listesini karşılaştırmak ve names1. txt içinde olan ancak names2. txt içinde olmayan satırları çıkarmak için LINQ 'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4f76-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="c4f76-104">Veri dosyalarını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c4f76-104">To create the data files</span></span>  
  
1. <span data-ttu-id="c4f76-105">Names1. txt ve names2. txt dosyasını, [dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)bölümünde gösterildiği gibi çözüm klasörünüze kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c4f76-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4f76-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4f76-106">Example</span></span>  
  
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
  
 <span data-ttu-id="c4f76-107"><xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>ve C#<xref:System.Linq.Enumerable.Concat%2A>gibi bazı sorgu işlemleri türleri yalnızca Yöntem tabanlı sözdiziminde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="c4f76-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c4f76-108">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="c4f76-108">Compiling the Code</span></span>  
 <span data-ttu-id="c4f76-109">System. C# lınq ve System.IO ad alanları için `using` yönergeler içeren bir konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c4f76-109">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f76-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4f76-110">See also</span></span>

- [<span data-ttu-id="c4f76-111">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="c4f76-111">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
