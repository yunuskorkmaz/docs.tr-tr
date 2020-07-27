---
title: Ara materialization (C#)
description: Bu C# örneği, ilk öğeyi bırakmadan önce bir sorgunun AppendString 'in kaynağın tamamını numaralandırması için yol gösteren ara materialization 'ı gösterir.
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 30951aaeea261efbd414205bcc54b63106324344
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165724"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="70021-103">Ara materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="70021-103">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="70021-104">Dikkatli değilseniz, bazı durumlarda, Sorgularınızdaki koleksiyonların erken olarak kullanıma hazır hale gelmesine neden olarak uygulamanızın bellek ve performans profilini büyük ölçüde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70021-104">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="70021-105">Bazı standart sorgu işleçleri, tek bir öğeyi oluşturmadan önce kaynak koleksiyonlarının çalışmasının oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="70021-105">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="70021-106">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> ilk olarak tüm kaynak koleksiyonu boyunca yinelenir, sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="70021-106">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="70021-107">Bu, sıralı bir koleksiyonun ilk öğesini almak pahalı olduğu anlamına gelir; Bundan sonra her öğe pahalı değildir.</span><span class="sxs-lookup"><span data-stu-id="70021-107">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="70021-108">Bu anlamlı olur: Bu sorgu işlecinin başka bir şekilde yapması imkansız olabilir.</span><span class="sxs-lookup"><span data-stu-id="70021-108">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70021-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="70021-109">Example</span></span>  
 <span data-ttu-id="70021-110">Bu örnek, önceki örneği değiştirir.</span><span class="sxs-lookup"><span data-stu-id="70021-110">This example alters the previous example.</span></span> <span data-ttu-id="70021-111">`AppendString`Yöntemi, <xref:System.Linq.Enumerable.ToList%2A> kaynak üzerinde yineleme yapmadan önce çağırır.</span><span class="sxs-lookup"><span data-stu-id="70021-111">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="70021-112">Bu, materialization oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="70021-112">This causes materialization.</span></span>  
  
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
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
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
  
 <span data-ttu-id="70021-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="70021-113">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="70021-114">Bu örnekte, çağrısının <xref:System.Linq.Enumerable.ToList%2A> `AppendString` ilk öğeyi bırakmadan önce tüm kaynağını numaralandırmasına neden olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70021-114">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="70021-115">Kaynak büyük bir diziyse, bu, uygulamanın bellek profilini önemli ölçüde değiştirecek.</span><span class="sxs-lookup"><span data-stu-id="70021-115">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="70021-116">Standart sorgu işleçleri de birlikte zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="70021-116">Standard query operators can also be chained together.</span></span> <span data-ttu-id="70021-117">Bu öğreticideki son konu, bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="70021-117">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="70021-118">Standart sorgu Işleçlerini birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="70021-118">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="70021-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70021-119">See also</span></span>

- [<span data-ttu-id="70021-120">Öğretici: sorguları birlikte zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="70021-120">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
