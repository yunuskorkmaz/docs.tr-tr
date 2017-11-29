---
title: "Nasıl yapılır: (LINQ) (C#) iki liste arasında ayarlanmış farkı bulma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 8e8945f0-4aba-439d-8d5d-c8d1eeef4e71
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d3987063a039b53b1e9ea7b39958835b0617aa2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-c"></a><span data-ttu-id="2dbc7-102">Nasıl yapılır: (LINQ) (C#) iki liste arasında ayarlanmış farkı bulma</span><span class="sxs-lookup"><span data-stu-id="2dbc7-102">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>
<span data-ttu-id="2dbc7-103">Bu örnek LINQ listelerini dizeleri karşılaştırmak ve names1.txt ancak names2.txt olan satırlar çıkış için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2dbc7-103">This example shows how to use LINQ to compare two lists of strings and output those lines that are in names1.txt but not in names2.txt.</span></span>  
  
### <a name="to-create-the-data-files"></a><span data-ttu-id="2dbc7-104">Veri dosyaları oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2dbc7-104">To create the data files</span></span>  
  
1.  <span data-ttu-id="2dbc7-105">Kopyalama names1.txt ve names2.txt Çözüm klasörünüz gösterildiği gibi [nasıl yapılır: birleştirme ve karşılaştırma dizesi koleksiyonları (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span><span class="sxs-lookup"><span data-stu-id="2dbc7-105">Copy names1.txt and names2.txt to your solution folder as shown in [How to: Combine and Compare String Collections (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dbc7-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2dbc7-106">Example</span></span>  
  
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
  
 <span data-ttu-id="2dbc7-107">Bazı türleri sorgu C# ' ta, işlemleri gibi <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, ve <xref:System.Linq.Enumerable.Concat%2A>, yalnızca yöntem temelli sözdiziminde ifade edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2dbc7-107">Some types of query operations in C#, such as <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Concat%2A>, can only be expressed in method-based syntax.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2dbc7-108">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2dbc7-108">Compiling the Code</span></span>  
 <span data-ttu-id="2dbc7-109">.NET Framework sürüm 3.5 veya daha yüksek System.Core.dll başvuru hedefleyen bir proje oluşturun ve `using` System.Linq ve System.IO ad alanları için yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="2dbc7-109">Create a project that targets the .NET Framework  version 3.5 or higher, with a reference to System.Core.dll and `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dbc7-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dbc7-110">See Also</span></span>  
 [<span data-ttu-id="2dbc7-111">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="2dbc7-111">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)
