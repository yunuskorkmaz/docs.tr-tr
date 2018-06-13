---
title: Sol dış birleştirmeler gerçekleştirme
description: Sol dış birleştirmeler gerçekleştirme.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: aacab1ac6f4ab2c10b393cf0b2c578a13d9b9306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284283"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="4cbf2-103">Sol dış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4cbf2-103">Perform left outer joins</span></span>
<span data-ttu-id="4cbf2-104">Sol dış birleşim bir birleşim değil de, ilk koleksiyonun her öğesine, bunu herhangi bir ilişkili öğe ikinci koleksiyonda olup bağımsız olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="4cbf2-105">LINQ çağırarak bir sol dış birleşim gerçekleştirmek için kullanabileceğiniz <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> group JOIN sonuçlarını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cbf2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="4cbf2-106">Example</span></span>  
 <span data-ttu-id="4cbf2-107">Aşağıdaki örnekte nasıl kullanılacağı ortaya <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> bir sol dış birleşim gerçekleştirmek için bir grup birleştirme sonuçlarını yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="4cbf2-108">Sol dış birleşim iki koleksiyonların oluşturan ilk adımı, bir grup birleşim kullanarak bir iç birleştirme gerçekleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="4cbf2-109">(Bkz [iç birleştirmeler gerçekleştirme](perform-inner-joins.md) bu işlemin bir açıklama için.) Bu örnekte, listesini `Person` nesneleri iç katılmış listesine `Pet` nesneleri temel alarak bir `Person` eşleşen nesne `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="4cbf2-110">İkinci adım sonuç o öğeye sağ koleksiyonunda herhangi bir eşleşme sahip olsa bile kümesinde ilk (soldaki) koleksiyonun her öğesine eklemektir.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="4cbf2-111">Bu çağırarak gerçekleştirilir <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> group JOIN öğelerinden eşleşen her dizisi üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="4cbf2-112">Bu örnekte, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> eşleşen her dizisi adlı `Pet` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="4cbf2-113">Yöntemi, tek bir varsayılan değer içeren bir koleksiyon döndürür eşleşen sırası `Pet` nesneleri için boş `Person` nesnesi, böylece, her sağlar `Person` nesne sonucu koleksiyonunda temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cbf2-114">Bir başvuru türü için varsayılan değer `null`; bu nedenle, her birinin her öğe erişmeden önce bir null başvuru için örnek denetler `Pet` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a><span data-ttu-id="4cbf2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cbf2-115">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="4cbf2-116">İç birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4cbf2-116">Perform inner joins</span></span>](perform-inner-joins.md)  
 [<span data-ttu-id="4cbf2-117">Gruplanmış birleşimler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="4cbf2-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="4cbf2-118">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="4cbf2-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
