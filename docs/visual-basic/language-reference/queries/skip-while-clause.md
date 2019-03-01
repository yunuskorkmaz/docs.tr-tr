---
title: Skip While Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 380372d6aaf8df3050e0ba8606b74eb3834dec67
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972605"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="da9e6-102">Skip While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da9e6-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="da9e6-103">Belirtilen bir koşulu olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="da9e6-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da9e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da9e6-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="da9e6-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="da9e6-105">Parts</span></span>  
  
|<span data-ttu-id="da9e6-106">Terim</span><span class="sxs-lookup"><span data-stu-id="da9e6-106">Term</span></span>|<span data-ttu-id="da9e6-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="da9e6-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="da9e6-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="da9e6-108">Required.</span></span> <span data-ttu-id="da9e6-109">Test etmek için öğeleri için bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="da9e6-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="da9e6-110">İfade döndürmelidir bir `Boolean` değer veya bir işlev eşdeğer gibi bir `Integer` olarak değerlendirilecek bir `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="da9e6-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da9e6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da9e6-111">Remarks</span></span>  
 <span data-ttu-id="da9e6-112">`Skip While` Yan tümcesi bir sorgu sonucunun başına sağlanan kadar öğeleri atlar `expression` döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="da9e6-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="da9e6-113">Sonra `expression` döndürür `false`, sorgunun kalan tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="da9e6-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="da9e6-114">`expression` Kalan sonuçları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="da9e6-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="da9e6-115">`Skip While` Yan tümcesi farklıdır `Where` yan tümcesinde, `Where` yan tümcesi, belirli bir koşulu karşılamayan bir sorgudan tüm öğeleri hariç tutmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="da9e6-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="da9e6-116">`Skip While` Yan tümcesi koşulu karşılanmadı yalnızca ilk kez kadar öğeleri hariç tutar.</span><span class="sxs-lookup"><span data-stu-id="da9e6-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="da9e6-117">`Skip While` Bir sıralı sorgu sonucu ile çalışırken yan tümcesi en kullanışlı.</span><span class="sxs-lookup"><span data-stu-id="da9e6-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="da9e6-118">Kullanarak bir sorgu sonucunun baştan sonuçları belirli sayıda atlayabilir `Skip` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="da9e6-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da9e6-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="da9e6-119">Example</span></span>  
 <span data-ttu-id="da9e6-120">Aşağıdaki kod örneğinde `Skip While` Amerika Birleşik Devletleri ilk müşteriden bulunana kadar sonuçları atlamak için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="da9e6-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="da9e6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da9e6-121">See also</span></span>
- [<span data-ttu-id="da9e6-122">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="da9e6-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="da9e6-123">Sorgular</span><span class="sxs-lookup"><span data-stu-id="da9e6-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="da9e6-124">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="da9e6-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="da9e6-125">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="da9e6-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="da9e6-126">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="da9e6-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="da9e6-127">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="da9e6-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="da9e6-128">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="da9e6-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
