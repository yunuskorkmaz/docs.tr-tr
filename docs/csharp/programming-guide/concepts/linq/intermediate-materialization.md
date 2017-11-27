---
title: Ara Materialization (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 46d347921e24bc5504c69534d7b5c087818a6c7f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="intermediate-materialization-c"></a><span data-ttu-id="8b7c6-102">Ara Materialization (C#)</span><span class="sxs-lookup"><span data-stu-id="8b7c6-102">Intermediate Materialization (C#)</span></span>
<span data-ttu-id="8b7c6-103">Dikkatli değilse, bazı durumlarda, büyük ölçüde, uygulamanızın bellek ve performans profili sorgularınızda koleksiyonların erken materialization neden olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-103">If you are not careful, in some situations you can drastically alter the memory and performance profile of your application by causing premature materialization of collections in your queries.</span></span> <span data-ttu-id="8b7c6-104">Bazı standart sorgu işleçleri, tek bir öğe oluşturan önce kendi kaynak koleksiyonu materialization neden.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-104">Some standard query operators cause materialization of their source collection before yielding a single element.</span></span> <span data-ttu-id="8b7c6-105">Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> önce tüm kaynak toplulukta tekrarlanan sonra tüm öğeleri sıralar ve son olarak ilk öğe verir.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-105">For example, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> first iterates through its entire source collection, then sorts all items, and then finally yields the first item.</span></span> <span data-ttu-id="8b7c6-106">Bu, sıralı bir koleksiyonu ilk öğesini almak pahalı olduğunu gösterir; her öğe bundan sonra pahalı değil.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-106">This means that it is expensive to get the first item of an ordered collection; each item thereafter is not expensive.</span></span> <span data-ttu-id="8b7c6-107">Bu mantıklı: Bu sorgu işleci aksini yapmasını olanaksız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-107">This makes sense: It would be impossible for that query operator to do otherwise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b7c6-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b7c6-108">Example</span></span>  
 <span data-ttu-id="8b7c6-109">Bu örnek, önceki örnekte değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-109">This example alters the previous example.</span></span> <span data-ttu-id="8b7c6-110">`AppendString` Yöntem çağrılarını <xref:System.Linq.Enumerable.ToList%2A> kaynak yineleme önce.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-110">The `AppendString` method calls <xref:System.Linq.Enumerable.ToList%2A> before iterating through the source.</span></span> <span data-ttu-id="8b7c6-111">Bu materialization neden olur.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-111">This causes materialization.</span></span>  
  
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
  
 <span data-ttu-id="8b7c6-112">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="8b7c6-112">This example produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="8b7c6-113">Bu örnekte, gördüğünüz çağrısı <xref:System.Linq.Enumerable.ToList%2A> neden `AppendString` ilk öğe sağlayan önce tüm kaynak numaralandırılamadı.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-113">In this example, you can see that the call to <xref:System.Linq.Enumerable.ToList%2A> causes `AppendString` to enumerate its entire source before yielding the first item.</span></span> <span data-ttu-id="8b7c6-114">Kaynak uzun bir diziye olsaydı, bu uygulamanın bellek profili önemli ölçüde alter.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-114">If the source were a large array, this would significantly alter the memory profile of the application.</span></span>  
  
 <span data-ttu-id="8b7c6-115">Standart sorgu işleçleri de birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-115">Standard query operators can also be chained together.</span></span> <span data-ttu-id="8b7c6-116">Bu öğreticinin son konusunda bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-116">The final topic in this tutorial illustrates this.</span></span>  
  
-   [<span data-ttu-id="8b7c6-117">Zincirleme standart sorgu işleçleri birlikte (C#)</span><span class="sxs-lookup"><span data-stu-id="8b7c6-117">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a><span data-ttu-id="8b7c6-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b7c6-118">See Also</span></span>  
 [<span data-ttu-id="8b7c6-119">Öğretici: Sorguları birlikte (C#) zincirleme</span><span class="sxs-lookup"><span data-stu-id="8b7c6-119">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
