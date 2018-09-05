---
title: Ara gerçekleştirme (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: 56c4bb57a931362b3e14f6a8da917ae6907565d6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516549"
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="46887-102">Ara gerçekleştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="46887-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="46887-103">Dikkatli emin değilseniz, bazı durumlarda, önemli ölçüde, uygulamanızın bellek ve performans profili sorgularınızdaki koleksiyonların erken materialization neden olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46887-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="46887-104">Bazı standart sorgu işleçleri, tek bir öğe oluşturan önce kaynak koleksiyonu materialization neden.</span><span class="sxs-lookup"><span data-stu-id="46887-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="46887-105">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> önce tüm kaynak toplulukta tekrarlanan sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="46887-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="46887-106">Bu, ilk öğesinde, sıralı bir koleksiyonu almak pahalı olduğunu gösterir; her öğe bundan sonra pahalı değil.</span><span class="sxs-lookup"><span data-stu-id="46887-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="46887-107">Bu mantıklı: yapmak bu sorgu işleci için mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="46887-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46887-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="46887-108">Example</span></span>  
 <span data-ttu-id="46887-109">Bu örnek önceki örnekle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="46887-109">This example alters the previous example.</span></span> <span data-ttu-id="46887-110">`AppendString` Yöntem çağrılarını <xref:System.Linq.Enumerable.ToList%2A> kaynağı aracılığıyla yineleme önce.</span><span class="sxs-lookup"><span data-stu-id="46887-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="46887-111">Bu, materialization yol açar.</span><span class="sxs-lookup"><span data-stu-id="46887-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="46887-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="46887-112">This example produces the following output:</span></span>  
  
```  
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
  
 <span data-ttu-id="46887-113">Bu örnekte, gördüğünüz gibi çağrısı <xref:System.Linq.Enumerable.ToList%2A> neden `AppendString` ilk öğeyi oluşturan önce tüm kaynak numaralandırılamadı.</span><span class="sxs-lookup"><span data-stu-id="46887-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="46887-114">Kaynak uzun bir diziye varsa, bu uygulamanın bellek profili önemli ölçüde alter.</span><span class="sxs-lookup"><span data-stu-id="46887-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="46887-115">Ayrıca standart sorgu işleçlerini birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="46887-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="46887-116">Bu öğreticideki son konu bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="46887-116">The final topic in this tutorial illustrates this.</span></span>  
  
-   [<span data-ttu-id="46887-117">Zincirleme standart sorgu işleçleri (C#)</span><span class="sxs-lookup"><span data-stu-id="46887-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="46887-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46887-118">See Also</span></span>

- [<span data-ttu-id="46887-119">Öğretici: Sorguları birbirine (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="46887-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
