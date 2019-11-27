---
title: Skip While Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333139"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="d6329-102">Skip While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6329-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="d6329-103">Belirtilen koşul `true` olduğu sürece bir koleksiyondaki öğeleri atlar ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6329-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6329-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6329-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d6329-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d6329-105">Parts</span></span>  
  
|<span data-ttu-id="d6329-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d6329-106">Term</span></span>|<span data-ttu-id="d6329-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d6329-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d6329-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d6329-108">Required.</span></span> <span data-ttu-id="d6329-109">İçin öğeleri test eden bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d6329-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d6329-110">İfade bir `Boolean` değeri veya bir `Boolean`olarak değerlendirilecek `Integer` gibi işlevsel eşdeğerini döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="d6329-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6329-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6329-111">Remarks</span></span>  
 <span data-ttu-id="d6329-112">`Skip While` yan tümcesi, sağlanan `expression` `false`dönene kadar öğeleri bir sorgu sonucunun başından atlar.</span><span class="sxs-lookup"><span data-stu-id="d6329-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d6329-113">`expression` `false`dönerse, sorgu kalan tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6329-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="d6329-114">Kalan sonuçlar için `expression` yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d6329-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d6329-115">`Skip While` yan tümcesi, `Where` yan tümcesinin, belirli bir koşulu karşılamayan bir sorgudaki tüm öğeleri dışlamak için kullanılabilir `Where` yan tümcesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d6329-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="d6329-116">`Skip While` yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="d6329-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d6329-117">`Skip While` yan tümcesi, düzenli bir sorgu sonucuyla çalışırken en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d6329-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="d6329-118">`Skip` yan tümcesini kullanarak bir sorgu sonucunun başından itibaren belirli sayıda sonucu atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d6329-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6329-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6329-119">Example</span></span>  
 <span data-ttu-id="d6329-120">Aşağıdaki kod örneği, Birleşik Devletler ilk müşteri bulunana kadar sonuçları atlamak için `Skip While` yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6329-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d6329-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6329-121">See also</span></span>

- [<span data-ttu-id="d6329-122">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="d6329-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d6329-123">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d6329-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d6329-124">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6329-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="d6329-125">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6329-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="d6329-126">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6329-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="d6329-127">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6329-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="d6329-128">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6329-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
