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
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="d90d7-103">İki liste arasındaki küme farkını bulma (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d90d7-103">How to find the set difference between two lists (LINQ) (C#)</span></span>

<span data-ttu-id="d90d7-104">Bu örnek, iki dize listesini karşılaştırmak ve names1.txt ancak names2.txt olmayan satırları çıkarmak için LINQ 'ın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d90d7-104">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="d90d7-105">Veri dosyalarını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d90d7-105">To create the data files</span></span>  
  
1. <span data-ttu-id="d90d7-106">names1.txt ve names2.txt, [dize koleksiyonlarını birleştirme ve karşılaştırma (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md)bölümünde gösterildiği gibi çözüm klasörünüze kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d90d7-106">Copy names1.txt and names2.txt to your solution folder as shown in [How to combine and compare string collections (LINQ) (C#)](./how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d90d7-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d90d7-107">Example</span></span>  
  
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
  
 <span data-ttu-id="d90d7-108">C# içinde,, ve gibi bazı sorgu işlemleri türleri <xref:System.Linq.Enumerable.Except%2A> <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Concat%2A> yalnızca Yöntem tabanlı sözdiziminde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d90d7-108">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d90d7-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d90d7-109">Compiling the Code</span></span>  

 <span data-ttu-id="d90d7-110">`using`System. LINQ ve System.IO ad alanları için yönergeler içeren bir C# konsol uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d90d7-110">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d90d7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d90d7-111">See also</span></span>

- [<span data-ttu-id="d90d7-112">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="d90d7-112">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
