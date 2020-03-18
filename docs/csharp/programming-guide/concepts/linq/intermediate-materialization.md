---
title: Ara Maddeizasyon (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: af1eb7df7da02d8e72fc102cda4ee5f329dc7974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253157"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="9ba76-102">Ara Maddeizasyon (C#)</span><span class="sxs-lookup"><span data-stu-id="9ba76-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="9ba76-103">Dikkatli değilseniz, bazı durumlarda sorgularınızda koleksiyonların erken somutlaşmasına neden olarak uygulamanızın bellek ve performans profilini büyük ölçüde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ba76-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="9ba76-104">Bazı standart sorgu işleçleri, tek bir öğe vermeden önce kaynak koleksiyonlarının somutlaştırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="9ba76-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="9ba76-105">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> önce tüm kaynak koleksiyonunu yineler, sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="9ba76-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="9ba76-106">Bu, sipariş edilen bir koleksiyonun ilk öğesini almak pahalı olduğu anlamına gelir; bundan sonra her öğe pahalı değildir.</span><span class="sxs-lookup"><span data-stu-id="9ba76-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="9ba76-107">Bu mantıklı: Bu sorgu işleci nin aksini yapması imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="9ba76-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ba76-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ba76-108">Example</span></span>  
 <span data-ttu-id="9ba76-109">Bu örnek önceki örneği değiştirir.</span><span class="sxs-lookup"><span data-stu-id="9ba76-109">This example alters the previous example.</span></span> <span data-ttu-id="9ba76-110">Yöntem, `AppendString` <xref:System.Linq.Enumerable.ToList%2A> kaynak üzerinden yinelenmeden önce çağırır.</span><span class="sxs-lookup"><span data-stu-id="9ba76-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="9ba76-111">Bu maddeleşmeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="9ba76-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="9ba76-112">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9ba76-112">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="9ba76-113">Bu örnekte, ilk öğeyi <xref:System.Linq.Enumerable.ToList%2A> vermeden `AppendString` önce tüm kaynağının sayısala neden olan çağrısını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ba76-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="9ba76-114">Kaynak büyük bir dizi olsaydı, bu uygulamanın bellek profilini önemli ölçüde değiştirirdi.</span><span class="sxs-lookup"><span data-stu-id="9ba76-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="9ba76-115">Standart sorgu işleçleri de birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="9ba76-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="9ba76-116">Bu öğreticide son konu bu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="9ba76-116">The final topic in this tutorial illustrates this.</span></span>  
  
- [<span data-ttu-id="9ba76-117">Standart Sorgu Operatörlerini Birlikte Zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="9ba76-117">Chaining Standard Query Operators Together (C#)</span></span>](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="9ba76-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ba76-118">See also</span></span>

- [<span data-ttu-id="9ba76-119">Öğretici: Sorguları Birlikte Zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="9ba76-119">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
