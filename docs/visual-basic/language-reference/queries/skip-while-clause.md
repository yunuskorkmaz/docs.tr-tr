---
title: Skip While Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359651"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="d6205-102">Skip While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6205-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="d6205-103">Belirtilen koşul olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6205-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6205-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6205-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d6205-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d6205-105">Parts</span></span>  
  
|<span data-ttu-id="d6205-106">Terim</span><span class="sxs-lookup"><span data-stu-id="d6205-106">Term</span></span>|<span data-ttu-id="d6205-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="d6205-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d6205-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="d6205-108">Required.</span></span> <span data-ttu-id="d6205-109">İçin öğeleri test eden bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d6205-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d6205-110">İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="d6205-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6205-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6205-111">Remarks</span></span>  
 <span data-ttu-id="d6205-112">`Skip While`Yan tümce, sağlanan döndürene kadar öğeleri bir sorgu sonucunun başından atlar `expression` `false` .</span><span class="sxs-lookup"><span data-stu-id="d6205-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d6205-113">`expression`Geri döndüğünde `false` , sorgu kalan tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6205-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="d6205-114">`expression`Kalan sonuçlar için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d6205-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d6205-115">Yan tümcesi, `Skip While` belirli bir `Where` `Where` koşulu karşılamayan bir sorgudaki tüm öğeleri dışlamak için kullanılan yan tümcesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d6205-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="d6205-116">`Skip While`Yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="d6205-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d6205-117">`Skip While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="d6205-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="d6205-118">Yan tümcesini kullanarak, bir sorgu sonucunun başından belirli bir sonuç sayısını atlayabilirsiniz `Skip` .</span><span class="sxs-lookup"><span data-stu-id="d6205-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6205-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d6205-119">Example</span></span>  
 <span data-ttu-id="d6205-120">Aşağıdaki kod örneği, `Skip While` Birleşik Devletler ilk müşteri bulunana kadar sonuçları atlamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6205-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d6205-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6205-121">See also</span></span>

- [<span data-ttu-id="d6205-122">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="d6205-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d6205-123">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d6205-123">Queries</span></span>](index.md)
- [<span data-ttu-id="d6205-124">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6205-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="d6205-125">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6205-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="d6205-126">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6205-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="d6205-127">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6205-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="d6205-128">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d6205-128">Where Clause</span></span>](where-clause.md)
