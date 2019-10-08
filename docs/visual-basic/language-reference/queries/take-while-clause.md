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
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004679"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="76dce-102">Take While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76dce-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="76dce-103">Belirtilen koşul `true` olduğu ve kalan öğeleri atlayan sürece bir koleksiyondaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="76dce-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76dce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76dce-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="76dce-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="76dce-105">Parts</span></span>  
  
|<span data-ttu-id="76dce-106">Terim</span><span class="sxs-lookup"><span data-stu-id="76dce-106">Term</span></span>|<span data-ttu-id="76dce-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="76dce-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="76dce-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="76dce-108">Required.</span></span> <span data-ttu-id="76dce-109">İçin öğeleri test eden bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="76dce-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="76dce-110">İfade, bir @no__t 0 değeri veya bir `Boolean` olarak değerlendirilecek `Integer` gibi işlevsel eşdeğerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="76dce-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76dce-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="76dce-111">Remarks</span></span>  
 <span data-ttu-id="76dce-112">@No__t-0 yan tümcesi, sağlanan `expression` `false` dönene kadar bir sorgu sonucunun başından itibaren öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="76dce-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="76dce-113">@No__t-0 ' ı `false` döndürürse, sorgu kalan tüm öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="76dce-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="76dce-114">@No__t-0, kalan sonuçlar için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="76dce-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="76dce-115">@No__t-0 yan tümcesi, `Where` yan tümcesinin belirli bir koşulu karşılayan bir sorgudaki tüm öğeleri dahil etmek için kullanılabilir `Where` tümceciğinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="76dce-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="76dce-116">@No__t-0 yan tümcesi yalnızca koşul karşılanmadığı sürece öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="76dce-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="76dce-117">@No__t-0 yan tümcesi, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="76dce-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76dce-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="76dce-118">Example</span></span>  
 <span data-ttu-id="76dce-119">Aşağıdaki kod örneği, hiçbir sipariş olmadan ilk müşteri bulunana kadar sonuçları almak için `Take While` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="76dce-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="76dce-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76dce-120">See also</span></span>

- [<span data-ttu-id="76dce-121">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="76dce-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="76dce-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="76dce-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="76dce-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="76dce-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="76dce-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="76dce-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="76dce-125">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="76dce-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="76dce-126">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="76dce-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="76dce-127">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="76dce-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
