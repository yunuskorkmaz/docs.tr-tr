---
title: Sol dış birleştirmeleri gerçekleştirin (C#'da LINQ)
description: C#'da LINQ'u kullanarak sol dış birleştirmeleri nasıl gerçekleştireceklerini öğrenin.
ms.date: 12/01/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: cc08a1c8670623a10d1e0bf10221d02037a8d7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688585"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="0a1ca-103">Sol dış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0a1ca-103">Perform left outer joins</span></span>

<span data-ttu-id="0a1ca-104">Sol dış birleştirme, ikinci koleksiyonda ilişkili öğeler olup olmadığına bakılmaksızın, ilk koleksiyonun her öğesinin döndürüldildiği bir birleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="0a1ca-105">Bir grup birleştirme sonuçları <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> üzerinde yöntem çağırarak sol dış birleştirme gerçekleştirmek için LINQ kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="0a1ca-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a1ca-106">Example</span></span>

<span data-ttu-id="0a1ca-107">Aşağıdaki örnek, sol dış <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> birleştirme gerçekleştirmek için bir grup birleştirme sonuçlarında yöntemin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="0a1ca-108">İki koleksiyonun sol dış birliğini oluşturmanın ilk adımı, grup birleştirme kullanarak bir iç birleştirme gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="0a1ca-109">(Bkz. Bu işlemin bir açıklaması için [iç birleştirmeleri](perform-inner-joins.md) gerçekleştirin.) Bu `Person` örnekte, nesnelerin listesi eşleşen `Pet` `Person` `Pet.Owner`bir nesneye dayalı nesnelerin listesine iç-joined .</span><span class="sxs-lookup"><span data-stu-id="0a1ca-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="0a1ca-110">İkinci adım, ilk (sol) koleksiyonun her öğesini, bu öğenin doğru koleksiyonda eşleşmesi olmasa bile sonuç kümesine eklemektir.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="0a1ca-111">Bu grup birleştirme <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen öğelerin her dizi çağırarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="0a1ca-112">Bu örnekte, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen `Pet` nesnelerin her dizisinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="0a1ca-113">Yöntem, eşleşen `Pet` nesnelerin sırası herhangi `Person` bir nesne için boşsa tek bir varsayılan değer içeren `Person` bir koleksiyon döndürür ve böylece her nesnenin sonuç koleksiyonunda temsil edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="0a1ca-114">Bir başvuru türü için `null`varsayılan değer; bu nedenle, örnek, her `Pet` koleksiyonun her öğesine erişmeden önce null başvuru için denetler.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="0a1ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a1ca-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="0a1ca-116">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0a1ca-116">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="0a1ca-117">Gruplanmış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0a1ca-117">Perform grouped joins</span></span>](perform-grouped-joins.md)
- [<span data-ttu-id="0a1ca-118">Anonim türleri</span><span class="sxs-lookup"><span data-stu-id="0a1ca-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
