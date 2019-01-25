---
title: 'Nasıl yapılır: (LINQ) iki liste arasında ayarlanmış farkı bulma (C#)'
ms.date: 07/20/2015
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
ms.openlocfilehash: 13166aaeba50d8cca33861d5489d7839d3933099
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712739"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="a0ba6-102">Nasıl yapılır: (LINQ) iki liste arasında ayarlanmış farkı bulma (C#)</span><span class="sxs-lookup"><span data-stu-id="a0ba6-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="a0ba6-103">Bu örnek, dizeleri iki liste karşılaştırın ve names1.txt ancak names2.txt olan satırlar çıkış için LINQ kullanma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0ba6-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="a0ba6-104">Veri dosyaları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a0ba6-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="a0ba6-105">Kopyalama names1.txt ve names2.txt Çözüm klasörünüz olarak gösterildiği gibi [nasıl yapılır: (LINQ) dize koleksiyonlarını birleştirme ve karşılaştırma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="a0ba6-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0ba6-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a0ba6-106">Example</span></span>  
  
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
  
 <span data-ttu-id="a0ba6-107">Sorgu işlemlerinde C# gibi bazı türleri <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, ve <xref:System.Linq.Enumerable.Concat%2A>, yalnızca yöntem tabanlı sözdizimi ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0ba6-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0ba6-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="a0ba6-108">Compiling the Code</span></span>  
 <span data-ttu-id="a0ba6-109">.NET Framework sürüm 3.5 veya üzeri bir System.Core.dll başvurusu ile hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="a0ba6-109">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ba6-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a0ba6-110">See also</span></span>

- [<span data-ttu-id="a0ba6-111">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="a0ba6-111">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
