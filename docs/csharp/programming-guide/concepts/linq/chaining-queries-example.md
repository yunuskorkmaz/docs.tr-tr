---
title: Zincirleme sorguları örnek (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: d28f5f4ed4f9e6deb5f6f3d381d310ebcef6e132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327698"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="cece0-102">Zincirleme sorguları örnek (C#)</span><span class="sxs-lookup"><span data-stu-id="cece0-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="cece0-103">Bu örnek önceki örneği oluşturur ve her ikisi de ertelenmiş yürütme ve geç değerlendirme kullanın, zinciri birlikte iki sorgular ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cece0-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cece0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cece0-104">Example</span></span>  
 <span data-ttu-id="cece0-105">Bu örnekte, başka bir uzantı metodu sunulmuştur, `AppendString`, hangi kaynak koleksiyondaki her dize üzerine belirtilen bir dize ekler ve yeni dizeler ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="cece0-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cece0-106">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="cece0-106">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="cece0-107">Bu örnekte, her bir genişletme yöntemi kaynak koleksiyondaki her öğe için bir kerede çalıştığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cece0-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="cece0-108">Ne bu örnekten açık olmalıdır, biz koleksiyonları verim sorguları birbirine zincirlenmiş olsa da, Ara koleksiyon gerçekleştirilip olur.</span><span class="sxs-lookup"><span data-stu-id="cece0-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="cece0-109">Bunun yerine, her öğe bir yavaş yönteminden sonraki geçirilir.</span><span class="sxs-lookup"><span data-stu-id="cece0-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="cece0-110">Büyük harf ve son olarak üçüncü bir her dize ünlem sahip olduğu bir dize dizisi oluşturmak için ilk dizelerden oluşan bir dizi alın ve ardından ikinci bir dize dizisi oluşturma bu sonuçlarında bir yaklaşım daha çok daha küçük bir bellek alanını dönüştürüldü noktaları eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="cece0-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="cece0-111">Bu öğreticide sonraki konu Ara materialization gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="cece0-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
-   [<span data-ttu-id="cece0-112">Ara Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="cece0-112">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="cece0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cece0-113">See Also</span></span>  
 [<span data-ttu-id="cece0-114">Öğretici: Sorguları birlikte (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="cece0-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
