---
title: Standart sorgu Işleçlerini birlikte zincirleme (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 89cf7f526bdc60881e901d7ca8f556e97488b220
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594832"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="3fc07-102">Standart sorgu Işleçlerini birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="3fc07-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="3fc07-103">Bu, [öğreticideki son konudur: Sorguları birlikte sorgulama (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) öğreticisi.</span><span class="sxs-lookup"><span data-stu-id="3fc07-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="3fc07-104">Standart sorgu işleçleri de birlikte zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3fc07-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="3fc07-105">Örneğin, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> işlecini birbirine bağlayabilirsiniz ve aynı zamanda bir geç şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3fc07-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="3fc07-106">Hiçbir ara sonuç tarafından gerçekleştirilmeyeceğini.</span><span class="sxs-lookup"><span data-stu-id="3fc07-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fc07-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fc07-107">Example</span></span>  
 <span data-ttu-id="3fc07-108">Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağrılmadan `ConvertCollectionToUpperCase`önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3fc07-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="3fc07-109">Yöntemi, bu `ConvertCollectionToUpperCase` öğreticideki `AppendString`önceki örneklerde kullanılan Lazy yöntemleriyle neredeyse tam olarak aynı şekilde çalışır. <xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="3fc07-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="3fc07-110">Bunun farkı, bu durumda <xref:System.Linq.Enumerable.Where%2A> yöntem kaynak koleksiyonu aracılığıyla yinelenir, ilk öğenin koşulu geçirmediğini belirler ve sonra geçecek bir sonraki öğeyi alır.</span><span class="sxs-lookup"><span data-stu-id="3fc07-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="3fc07-111">Daha sonra ikinci öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="3fc07-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="3fc07-112">Ancak, temel düşünce aynıdır: Ara koleksiyonlar, olmaları gerekmedikçe gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="3fc07-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="3fc07-113">Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçleri çağrılarına dönüştürülür ve aynı ilkeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3fc07-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="3fc07-114">Bu bölümdeki Office Open XML belgelerini sorgulayan tüm örnekler aynı ilkeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fc07-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="3fc07-115">Ertelenmiş yürütme ve yavaş değerlendirme, LINQ (ve LINQ to XML) etkin bir şekilde kullanmak için anlamanız gereken temel kavramlardır.</span><span class="sxs-lookup"><span data-stu-id="3fc07-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
            where s.CompareTo("D") >= 0  
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
  
 <span data-ttu-id="3fc07-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3fc07-116">This example produces the following output:</span></span>  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  