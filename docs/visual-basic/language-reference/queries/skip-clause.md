---
title: Skip Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: c582b014bad4fa8fa3165d2b756f4bc955840cfc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349648"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="3b9b1-102">Skip Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b9b1-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="3b9b1-103">Koleksiyonda belirtilen sayıda öğeyi atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b9b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b9b1-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="3b9b1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3b9b1-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="3b9b1-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-106">Required.</span></span> <span data-ttu-id="3b9b1-107">Atlanacak dizinin öğe sayısını değerlendiren bir değer veya ifade.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b9b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b9b1-108">Remarks</span></span>  
 <span data-ttu-id="3b9b1-109">`Skip` yan tümcesi, bir sorgunun bir sonuç listesinin başlangıcında öğeleri atlamasına ve kalan öğeleri döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="3b9b1-110">Atlanacak öğe sayısı `count` parametresi tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="3b9b1-111">Sorgunun herhangi bir segmentinden bir veri aralığı döndürmek için `Take` yan tümcesiyle `Skip` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="3b9b1-112">Bunu yapmak için aralığın ilk öğesinin dizinini `Skip` yan tümcesine ve aralığın boyutunu `Take` yan tümcesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="3b9b1-113">Bir sorguda `Skip` yan tümcesini kullandığınızda, sonuçların, `Skip` yan tümcesinin amaçlanan sonuçları atlamasına olanak sağlayacak bir sırada döndürüldüğünden emin olmanız da gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="3b9b1-114">Sorgu sonuçlarını sıralama hakkında daha fazla bilgi için bkz. [order by yan tümcesi](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3b9b1-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="3b9b1-115">Belirtilen koşula bağlı olarak yalnızca belirli öğelerin yoksayılacağını belirtmek için `SkipWhile` yan tümcesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b9b1-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b9b1-116">Example</span></span>  
 <span data-ttu-id="3b9b1-117">Aşağıdaki kod örneği, sayfalardaki bir sorgudan veri döndürmek için `Take` yan tümcesiyle birlikte `Skip` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="3b9b1-118">`GetCustomers` işlevi, belirtilen başlangıç dizini değerine kadar listedeki müşterileri atlamak için `Skip` yan tümcesini kullanır ve bu dizin değerinden başlayan müşterilerin bir sayfasını döndürmek için `Take` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3b9b1-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b9b1-119">See also</span></span>

- [<span data-ttu-id="3b9b1-120">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="3b9b1-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3b9b1-121">Sorgular</span><span class="sxs-lookup"><span data-stu-id="3b9b1-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3b9b1-122">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3b9b1-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3b9b1-123">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3b9b1-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3b9b1-124">Order By Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3b9b1-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="3b9b1-125">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3b9b1-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="3b9b1-126">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="3b9b1-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
