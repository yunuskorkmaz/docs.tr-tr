---
title: Zincirleme sorguları örneği (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 90c2ba1c9125114f9e26f4afeb3ff6373ff01d9c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594826"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="88e19-102">Zincirleme sorguları örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="88e19-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="88e19-103">Bu örnek, önceki örnekte oluşturulur ve hem ertelenmiş yürütme hem de yavaş değerlendirme kullanan iki sorguyu zincirleyen ne olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="88e19-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88e19-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="88e19-104">Example</span></span>  
 <span data-ttu-id="88e19-105">Bu örnekte, belirtilen bir dizeyi kaynak koleksiyondaki her dizeye `AppendString`bağlayan ve ardından yeni dizeleri veren başka bir genişletme yöntemi tanıtılmıştır.</span><span class="sxs-lookup"><span data-stu-id="88e19-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="88e19-106">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="88e19-106">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="88e19-107">Bu örnekte, her bir genişletme yönteminin, kaynak koleksiyondaki her öğe için tek bir kez çalıştığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88e19-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="88e19-108">Bu örnekte ne kadar net bir şekilde gruplandık, ancak koleksiyonları oluşturan sorguları birbirine zincirlediğimiz halde ara koleksiyonlar gerçekleştirilmiş değildir.</span><span class="sxs-lookup"><span data-stu-id="88e19-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="88e19-109">Bunun yerine, her öğe bir geç yönteminden bir sonrakine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="88e19-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="88e19-110">Bu, ilk olarak bir dize dizisi alacak bir yaklaşımdan çok daha küçük bir bellek parmak izine neden olur, ardından büyük harfe dönüştürülmüş bir ikinci dize dizisi oluşturur ve son olarak her bir dizenin ünlem işareti bulunan üçüncü bir dizi dizeyi oluşturur Buna eklenen noktaları.</span><span class="sxs-lookup"><span data-stu-id="88e19-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="88e19-111">Bu öğreticideki sonraki konu, ara materialization gösterir:</span><span class="sxs-lookup"><span data-stu-id="88e19-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="88e19-112">Ara materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="88e19-112">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="88e19-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88e19-113">See also</span></span>

- [<span data-ttu-id="88e19-114">Öğretici: Sorguları birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="88e19-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
