---
title: Zincirleme Sorgular Örneği (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205420"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="acb16-102">Zincirleme Sorgular Örneği (C#)</span><span class="sxs-lookup"><span data-stu-id="acb16-102">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="acb16-103">Bu örnek, önceki örnekte birdiziliş oluşturur ve hem ertelenmiş yürütme hem de tembel değerlendirme kullanan iki sorguyu bir araya zincirlediğinizde ne olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="acb16-103">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acb16-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="acb16-104">Example</span></span>  
 <span data-ttu-id="acb16-105">Bu örnekte, kaynak koleksiyonundaki `AppendString`her dize ye belirli bir dize ekleyen ve sonra yeni dizeleri veren başka bir uzantı yöntemi getirilir.</span><span class="sxs-lookup"><span data-stu-id="acb16-105">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="acb16-106">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="acb16-106">This example produces the following output:</span></span>  
  
```output  
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
  
 <span data-ttu-id="acb16-107">Bu örnekte, her uzantı yönteminin kaynak koleksiyonundaki her öğe için birer birer çalıştığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acb16-107">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="acb16-108">Bu örnekten açıkça anlaşılan şey, koleksiyonlar oluşturan sorguları birbirine zincirleme olsa kılmış olsak da, hiçbir ara koleksiyon gerçekleşmemiş olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="acb16-108">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="acb16-109">Bunun yerine, her öğe bir tembel yöntemden diğerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="acb16-109">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="acb16-110">Bu, ilk olarak bir dizi dize alacak, sonra büyük harfe dönüştürülmüş ikinci bir dize dizisi oluşturacak ve son olarak her dizeün ünlem aldığı üçüncü bir dize dizisi oluşturacak bir yaklaşımdan çok daha küçük bir bellek ayak izi ile sonuçlanır puanlar eklenir.</span><span class="sxs-lookup"><span data-stu-id="acb16-110">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="acb16-111">Bu öğreticibir sonraki konu ara maddeleştirme göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="acb16-111">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="acb16-112">Ara Maddeizasyon (C#)</span><span class="sxs-lookup"><span data-stu-id="acb16-112">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="acb16-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb16-113">See also</span></span>

- [<span data-ttu-id="acb16-114">Öğretici: Sorguları Birlikte Zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="acb16-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
