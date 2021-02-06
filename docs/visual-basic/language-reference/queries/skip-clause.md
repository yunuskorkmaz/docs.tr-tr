---
description: 'Daha fazla bilgi edinin: Skip tümcesi (Visual Basic)'
title: Skip Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 6af702f65a724ea8c3d5a6122fb5f7a0ed5f6755
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653556"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="0cf4c-103">Skip Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cf4c-103">Skip Clause (Visual Basic)</span></span>

<span data-ttu-id="0cf4c-104">Koleksiyonda belirtilen sayıda öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-104">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf4c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0cf4c-105">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="0cf4c-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0cf4c-106">Parts</span></span>  

 `count`  
 <span data-ttu-id="0cf4c-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-107">Required.</span></span> <span data-ttu-id="0cf4c-108">Atlanacak dizinin öğe sayısını değerlendiren bir değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-108">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cf4c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cf4c-109">Remarks</span></span>  

 <span data-ttu-id="0cf4c-110">`Skip`Yan tümce bir sorgunun bir sonuç listesinin başlangıcında öğeleri atlamasına ve kalan öğeleri döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-110">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="0cf4c-111">Atlanacak öğe sayısı parametresi tarafından tanımlanır `count` .</span><span class="sxs-lookup"><span data-stu-id="0cf4c-111">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="0cf4c-112">`Skip` `Take` Bir sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-112">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="0cf4c-113">Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-113">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="0cf4c-114">`Skip`Bir sorguda yan tümcesini kullandığınızda, sonuçların `Skip` amaçlanan sonuçları atlayıp atlamalarını sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-114">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="0cf4c-115">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0cf4c-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="0cf4c-116">`SkipWhile`Belirtilen koşula bağlı olarak yalnızca belirli öğelerin yoksayılacağını belirtmek için yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-116">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cf4c-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cf4c-117">Example</span></span>  

 <span data-ttu-id="0cf4c-118">Aşağıdaki kod örneği, yan tümcesini, `Skip` `Take` sayfalardaki bir sorgudan veri döndürmek için yan tümcesiyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-118">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="0cf4c-119">`GetCustomers`İşlevi, `Skip` sağlanan başlangıç dizini değerine kadar listedeki müşterileri atlamak için yan tümcesini kullanır ve `Take` Bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-119">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0cf4c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf4c-120">See also</span></span>

- [<span data-ttu-id="0cf4c-121">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="0cf4c-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0cf4c-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="0cf4c-122">Queries</span></span>](index.md)
- [<span data-ttu-id="0cf4c-123">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="0cf4c-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="0cf4c-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="0cf4c-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="0cf4c-125">Order by yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="0cf4c-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="0cf4c-126">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0cf4c-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="0cf4c-127">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="0cf4c-127">Take Clause</span></span>](take-clause.md)
