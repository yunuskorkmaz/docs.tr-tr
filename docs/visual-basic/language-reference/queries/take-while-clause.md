---
title: Take While Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 181cc641bb12329c898cc3bb226ea49f0836e979
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932033"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="52206-102">Take While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52206-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="52206-103">Belirtilen koşul sürece öğeleri bir koleksiyona dahil `true` ve kalan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="52206-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52206-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52206-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="52206-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="52206-105">Parts</span></span>  
  
|<span data-ttu-id="52206-106">Terim</span><span class="sxs-lookup"><span data-stu-id="52206-106">Term</span></span>|<span data-ttu-id="52206-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="52206-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="52206-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="52206-108">Required.</span></span> <span data-ttu-id="52206-109">Test etmek için öğeleri için bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="52206-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="52206-110">İfade döndürmelidir bir `Boolean` değer veya bir işlev eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="52206-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52206-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52206-111">Remarks</span></span>  
 <span data-ttu-id="52206-112">`Take While` Yan tümcesi başından itibaren bir sorgu sonucunun öğelerini sağlanan kadar içerir `expression` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="52206-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="52206-113">Sonra `expression` döndürür `false`, sorgunun kalan tüm öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="52206-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="52206-114">`expression` Kalan sonuçları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="52206-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="52206-115">`Take While` Yan tümcesi farklıdır `Where` yan tümcesinde, `Where` yan tümcesi, bir sorgudan belirli bir koşulu karşılayan tüm öğeleri dahil etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="52206-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="52206-116">`Take While` Yan tümcesi koşulu karşılanmadı yalnızca ilk kez kadar öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="52206-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="52206-117">`Take While` Bir sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlı.</span><span class="sxs-lookup"><span data-stu-id="52206-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52206-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="52206-118">Example</span></span>  
 <span data-ttu-id="52206-119">Aşağıdaki kod örneğinde `Take While` ilk müşteri siparişleri olmadan bulunana kadar sonuçları almak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="52206-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="52206-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52206-120">See Also</span></span>  
 [<span data-ttu-id="52206-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="52206-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="52206-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="52206-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="52206-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="52206-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="52206-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="52206-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="52206-125">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="52206-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="52206-126">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="52206-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="52206-127">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="52206-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
