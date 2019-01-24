---
title: Zincirleme örneği sorgular (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: b77de6b1e5bd81ac70165640aecf0d4ce89be03d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677366"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="33318-102">Zincirleme örneği sorgular (C#)</span><span class="sxs-lookup"><span data-stu-id="33318-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="33318-103">Bu örnek önceki örneğe dayanmaktadır ve her ikisi de ertelenmiş yürütme ve geç değerlendirme kullanın, zincir birlikte iki sorgular ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33318-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33318-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="33318-104">Example</span></span>  
 <span data-ttu-id="33318-105">Bu örnekte, başka bir genişletme yöntemi sunulmuştur, `AppendString`, kaynak koleksiyondaki her dize üzerine belirtilen bir dize ekler ve ardından yeni bir dize verir.</span><span class="sxs-lookup"><span data-stu-id="33318-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="33318-106">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="33318-106">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="33318-107">Bu örnekte, her bir genişletme yöntemi bir kaynak koleksiyondaki her öğe için aynı anda çalıştığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33318-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="33318-108">Ne bu örnekten açık olmalıdır, biz koleksiyonları yield sorguları birbirine zincirlenmiş olsa bile, Ara koleksiyon gerçekleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="33318-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="33318-109">Bunun yerine, her öğe yavaş bir yöntemden diğerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="33318-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="33318-110">Büyük harf ve son olarak üçüncü bir ünlem işareti sahip olduğu her bir dizenin bir dize dizisi oluşturmak için önce bir dize dizisi alın ve ardından ikinci bir dize dizisi oluşturan bir yaklaşım daha çok daha küçük bellek Ayak izi bu sonuçlarında dönüştürüldü eklenmiş bir işaret eder.</span><span class="sxs-lookup"><span data-stu-id="33318-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="33318-111">Bu öğreticide bir sonraki konu Ara gerçekleştirme gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="33318-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
-   [<span data-ttu-id="33318-112">Ara gerçekleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="33318-112">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="33318-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33318-113">See also</span></span>

- [<span data-ttu-id="33318-114">Öğretici: Sorguları birbirine zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="33318-114">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
