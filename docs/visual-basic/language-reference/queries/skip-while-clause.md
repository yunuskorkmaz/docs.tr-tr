---
description: 'Daha fazla bilgi edinin: Skip While tümcesi (Visual Basic)'
title: Skip While Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 6f2785fde1a62c10c914904ccba51510dbb1a041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773855"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="d3dfb-103">Skip While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3dfb-103">Skip While Clause (Visual Basic)</span></span>

<span data-ttu-id="d3dfb-104">Belirtilen koşul olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-104">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3dfb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d3dfb-105">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d3dfb-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d3dfb-106">Parts</span></span>  
  
|<span data-ttu-id="d3dfb-107">Süre</span><span class="sxs-lookup"><span data-stu-id="d3dfb-107">Term</span></span>|<span data-ttu-id="d3dfb-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="d3dfb-108">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d3dfb-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-109">Required.</span></span> <span data-ttu-id="d3dfb-110">İçin öğeleri test eden bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-110">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d3dfb-111">İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="d3dfb-111">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3dfb-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3dfb-112">Remarks</span></span>  

 <span data-ttu-id="d3dfb-113">`Skip While`Yan tümce, sağlanan döndürene kadar öğeleri bir sorgu sonucunun başından atlar `expression` `false` .</span><span class="sxs-lookup"><span data-stu-id="d3dfb-113">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d3dfb-114">`expression`Geri döndüğünde `false` , sorgu kalan tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-114">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="d3dfb-115">`expression`Kalan sonuçlar için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-115">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d3dfb-116">Yan tümcesi, `Skip While` belirli bir `Where` `Where` koşulu karşılamayan bir sorgudaki tüm öğeleri dışlamak için kullanılan yan tümcesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-116">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="d3dfb-117">`Skip While`Yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-117">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d3dfb-118">`Skip While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-118">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="d3dfb-119">Yan tümcesini kullanarak, bir sorgu sonucunun başından belirli bir sonuç sayısını atlayabilirsiniz `Skip` .</span><span class="sxs-lookup"><span data-stu-id="d3dfb-119">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3dfb-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3dfb-120">Example</span></span>  

 <span data-ttu-id="d3dfb-121">Aşağıdaki kod örneği, `Skip While` Birleşik Devletler ilk müşteri bulunana kadar sonuçları atlamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-121">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d3dfb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3dfb-122">See also</span></span>

- [<span data-ttu-id="d3dfb-123">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="d3dfb-123">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d3dfb-124">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d3dfb-124">Queries</span></span>](index.md)
- [<span data-ttu-id="d3dfb-125">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3dfb-125">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d3dfb-126">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3dfb-126">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="d3dfb-127">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3dfb-127">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="d3dfb-128">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3dfb-128">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="d3dfb-129">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3dfb-129">Where Clause</span></span>](where-clause.md)
