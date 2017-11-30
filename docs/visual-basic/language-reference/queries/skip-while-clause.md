---
title: "Skip While Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="a224c-102">Skip While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a224c-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="a224c-103">Belirtilen bir koşul olduğu sürece bir koleksiyondaki öğelerin atlar `true` ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="a224c-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a224c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a224c-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a224c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="a224c-105">Parts</span></span>  
  
|<span data-ttu-id="a224c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="a224c-106">Term</span></span>|<span data-ttu-id="a224c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="a224c-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="a224c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a224c-108">Required.</span></span> <span data-ttu-id="a224c-109">Öğeleri için test etmek için bir koşul temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="a224c-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="a224c-110">İfade döndürmelidir bir `Boolean` değeri veya işlevsel bir eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a224c-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a224c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a224c-111">Remarks</span></span>  
 <span data-ttu-id="a224c-112">`Skip While` Yan tümcesi atlar sağlanan kadar bir sorgu sonucunun başından öğeleri `expression` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="a224c-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="a224c-113">Sonra `expression` döndürür `false`, kalan tüm öğeleri sorgu döndürür.</span><span class="sxs-lookup"><span data-stu-id="a224c-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="a224c-114">`expression` İçin kalan sonuçları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="a224c-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="a224c-115">`Skip While` Yan tümcesini farklı olarak `Where` yan tümcesinde, `Where` yan tümcesi, belirli bir koşula karşılamayan bir sorgudan tüm öğeleri dışlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a224c-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="a224c-116">`Skip While` Yan tümcesi koşula uyulmadığını yalnızca ilk kez kadar öğeleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="a224c-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="a224c-117">`Skip While` Sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="a224c-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="a224c-118">Kullanarak bir sorgu sonucunun sonuçları başlangıçtan itibaren belirli sayıda atlayabilir `Skip` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a224c-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a224c-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="a224c-119">Example</span></span>  
 <span data-ttu-id="a224c-120">Aşağıdaki kod örneğinde `Skip While` Amerika Birleşik Devletleri ilk müşteriden bulunana kadar sonuçları atlamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a224c-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a224c-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a224c-121">See Also</span></span>  
 [<span data-ttu-id="a224c-122">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="a224c-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="a224c-123">Sorguları</span><span class="sxs-lookup"><span data-stu-id="a224c-123">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="a224c-124">Select tümcesi</span><span class="sxs-lookup"><span data-stu-id="a224c-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="a224c-125">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="a224c-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="a224c-126">Skip tümcesi</span><span class="sxs-lookup"><span data-stu-id="a224c-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="a224c-127">Take While tümcesi</span><span class="sxs-lookup"><span data-stu-id="a224c-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="a224c-128">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="a224c-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
