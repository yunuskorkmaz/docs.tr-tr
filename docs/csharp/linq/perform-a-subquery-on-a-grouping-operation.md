---
title: (C# üzerinde LINQ) gruplandırma işleminde alt sorgu gerçekleştirme
description: C# içinde LINQ kullanarak bir gruplandırma işleminde alt sorgu gerçekleştirme yapma.
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: a3757a7d358a310dd1404f85e34178f6e561bcb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688429"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="fdf27-103">Gruplandırma işleminde alt sorgu gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="fdf27-103">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="fdf27-104">Bu makalede, kaynak verileri gruplar halinde sıralar ve sonra bir alt sorgu her bir grup üzerinde tek tek gerçekleştiren bir sorgu oluşturmak için iki farklı yolu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fdf27-104">This article shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="fdf27-105">Her örnekte temel tekniği kullanarak kaynak öğeleri gruplandırmak için olan bir *devamlılık* adlı `newGroup`ve ardından yeni bir alt sorgu karşı oluşturma `newGroup`.</span><span class="sxs-lookup"><span data-stu-id="fdf27-105">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="fdf27-106">Bu alt sorgu, dış sorgu tarafından oluşturulan her yeni gruba göre çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="fdf27-106">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="fdf27-107">Bu örnekte son çıkışı değil bir grup ancak anonim türler düz dizisi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fdf27-107">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
<span data-ttu-id="fdf27-108">Gruba hakkında daha fazla bilgi için bkz. [group yan tümcesi](../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="fdf27-108">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
<span data-ttu-id="fdf27-109">Devamlılıklar hakkında daha fazla bilgi için bkz: [içine](../language-reference/keywords/into.md).</span><span class="sxs-lookup"><span data-stu-id="fdf27-109">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="fdf27-110">Aşağıdaki örnek, veri kaynağı olarak bir bellek içi veri yapısı kullanır, ancak tüm LINQ veri kaynağı türü için aynı ilkeler geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="fdf27-110">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf27-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdf27-111">Example</span></span>

> [!NOTE]
> <span data-ttu-id="fdf27-112">Bu örnekte örnek koda tanımlanan nesneleri başvuruları içeren [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="fdf27-112">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)] 

<span data-ttu-id="fdf27-113">Yukarıdaki kod parçacığında sorgu ayrıca yöntem sözdizimini kullanarak yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf27-113">The query in the snippet above can also be written using method syntax.</span></span> <span data-ttu-id="fdf27-114">Aşağıdaki kod parçacığı, yöntem sözdizimi kullanılarak yazılmış anlamsal olarak eşdeğer bir sorgu yok.</span><span class="sxs-lookup"><span data-stu-id="fdf27-114">The following code snippet has a semantically equivalent query written using method syntax.</span></span>

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a><span data-ttu-id="fdf27-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdf27-115">See also</span></span>

- [<span data-ttu-id="fdf27-116">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="fdf27-116">Language Integrated Query (LINQ)</span></span>](index.md)
