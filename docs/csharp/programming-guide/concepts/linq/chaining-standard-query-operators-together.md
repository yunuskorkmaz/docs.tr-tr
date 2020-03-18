---
title: Standart Sorgu Operatörlerini Birlikte Zincirleme (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204209"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="06854-102">Standart Sorgu Operatörlerini Birlikte Zincirleme (C#)</span><span class="sxs-lookup"><span data-stu-id="06854-102">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="06854-103">Bu Öğretici son [konu: Zincirleme Sorgular Birlikte (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) öğretici.</span><span class="sxs-lookup"><span data-stu-id="06854-103">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="06854-104">Standart sorgu işleçleri de birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="06854-104">The standard query operators can also be chained together.</span></span> <span data-ttu-id="06854-105">Örneğin, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatörü arayabilirsiniz ve aynı zamanda tembel bir şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="06854-105">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="06854-106">Hiçbir ara sonuç onun tarafından somutlaştırılamaktadır.</span><span class="sxs-lookup"><span data-stu-id="06854-106">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06854-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="06854-107">Example</span></span>  
 <span data-ttu-id="06854-108">Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntem aramadan `ConvertCollectionToUpperCase`önce çağrılır.</span><span class="sxs-lookup"><span data-stu-id="06854-108">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="06854-109">Yöntem, <xref:System.Linq.Enumerable.Where%2A> bu öğreticide önceki örneklerde kullanılan tembel yöntemlerle hemen `ConvertCollectionToUpperCase` `AppendString`hemen aynı şekilde çalışır ve .</span><span class="sxs-lookup"><span data-stu-id="06854-109">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="06854-110">Bir fark, bu durumda, <xref:System.Linq.Enumerable.Where%2A> yöntem in kaynak koleksiyonu üzerinden iterates, ilk öğe nin yüklem geçmiyor belirler ve daha sonra geçmek bir sonraki öğe, alır.</span><span class="sxs-lookup"><span data-stu-id="06854-110">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="06854-111">Daha sonra ikinci öğeyi verir.</span><span class="sxs-lookup"><span data-stu-id="06854-111">It then yields the second item.</span></span>  
  
 <span data-ttu-id="06854-112">Ancak, temel fikir aynıdır: Ara koleksiyonlar olması gerekmedikçe gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="06854-112">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="06854-113">Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçlerine çağrılara dönüştürülür ve aynı ilkeler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="06854-113">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="06854-114">Office Open XML belgelerini sorgulayan bu bölümdeki tüm örnekler aynı ilkeyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="06854-114">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="06854-115">Ertelenmiş yürütme ve tembel değerlendirme, LINQ'yi (ve Linq'den XML'e) etkili bir şekilde kullanmak için anlamanız gereken temel kavramlardan bazılarıdır.</span><span class="sxs-lookup"><span data-stu-id="06854-115">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
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
  
 <span data-ttu-id="06854-116">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="06854-116">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
