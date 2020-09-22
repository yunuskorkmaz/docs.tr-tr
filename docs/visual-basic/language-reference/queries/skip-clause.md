---
title: Skip Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 40e89160baf663f7d6785e5d3e09ad6cc4eefbde
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866312"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="16b61-102">Skip Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16b61-102">Skip Clause (Visual Basic)</span></span>

<span data-ttu-id="16b61-103">Koleksiyonda belirtilen sayıda öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="16b61-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16b61-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="16b61-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="16b61-105">Parts</span></span>  

 `count`  
 <span data-ttu-id="16b61-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="16b61-106">Required.</span></span> <span data-ttu-id="16b61-107">Atlanacak dizinin öğe sayısını değerlendiren bir değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="16b61-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16b61-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16b61-108">Remarks</span></span>  

 <span data-ttu-id="16b61-109">`Skip`Yan tümce bir sorgunun bir sonuç listesinin başlangıcında öğeleri atlamasına ve kalan öğeleri döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b61-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="16b61-110">Atlanacak öğe sayısı parametresi tarafından tanımlanır `count` .</span><span class="sxs-lookup"><span data-stu-id="16b61-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="16b61-111">`Skip` `Take` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="16b61-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="16b61-112">Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="16b61-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="16b61-113">`Skip`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Skip` amaçlanan sonuçları atlayıp atlamalarını sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="16b61-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="16b61-114">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="16b61-114">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="16b61-115">`SkipWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin yoksayılacağını belirtmek için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16b61-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16b61-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="16b61-116">Example</span></span>  

 <span data-ttu-id="16b61-117">Aşağıdaki kod örneği, yan tümcesini, `Skip` `Take` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="16b61-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="16b61-118">`GetCustomers`İşlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="16b61-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="16b61-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16b61-119">See also</span></span>

- [<span data-ttu-id="16b61-120">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="16b61-120">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="16b61-121">Sorgular</span><span class="sxs-lookup"><span data-stu-id="16b61-121">Queries</span></span>](index.md)
- [<span data-ttu-id="16b61-122">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="16b61-122">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="16b61-123">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="16b61-123">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="16b61-124">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="16b61-124">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="16b61-125">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="16b61-125">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="16b61-126">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="16b61-126">Take Clause</span></span>](take-clause.md)
