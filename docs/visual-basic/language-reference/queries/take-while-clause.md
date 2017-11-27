---
title: "Take While Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="30b6f-102">Take While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30b6f-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="30b6f-103">Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğeleri içeren `true` ve kalan öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="30b6f-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30b6f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30b6f-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="30b6f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="30b6f-105">Parts</span></span>  
  
|<span data-ttu-id="30b6f-106">Terim</span><span class="sxs-lookup"><span data-stu-id="30b6f-106">Term</span></span>|<span data-ttu-id="30b6f-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="30b6f-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="30b6f-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="30b6f-108">Required.</span></span> <span data-ttu-id="30b6f-109">Öğeleri için test etmek için bir koşul temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="30b6f-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="30b6f-110">İfade döndürmelidir bir `Boolean` değeri veya işlevsel bir eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="30b6f-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30b6f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30b6f-111">Remarks</span></span>  
 <span data-ttu-id="30b6f-112">`Take While` Yan tümcesi bir sorgu sonucunun başından öğeleri sağlanan kadar içerir `expression` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="30b6f-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="30b6f-113">Sonra `expression` döndürür `false`, sorgu tüm kalan öğeleri atlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="30b6f-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="30b6f-114">`expression` İçin kalan sonuçları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="30b6f-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="30b6f-115">`Take While` Yan tümcesini farklı olarak `Where` yan tümcesinde, `Where` yan tümcesi, bir sorgudan belirli bir koşula tüm öğeleri dahil etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="30b6f-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="30b6f-116">`Take While` Yan tümcesi koşula uyulmadığını yalnızca ilk kez kadar öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="30b6f-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="30b6f-117">`Take While` Sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="30b6f-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30b6f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="30b6f-118">Example</span></span>  
 <span data-ttu-id="30b6f-119">Aşağıdaki kod örneğinde `Take While` siparişler olmadan ilk müşteri bulunana kadar sonuçları almak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="30b6f-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="30b6f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30b6f-120">See Also</span></span>  
 [<span data-ttu-id="30b6f-121">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="30b6f-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="30b6f-122">Sorguları</span><span class="sxs-lookup"><span data-stu-id="30b6f-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="30b6f-123">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="30b6f-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="30b6f-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="30b6f-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="30b6f-125">Take tümcesi</span><span class="sxs-lookup"><span data-stu-id="30b6f-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="30b6f-126">Skip While tümcesi</span><span class="sxs-lookup"><span data-stu-id="30b6f-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="30b6f-127">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="30b6f-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
