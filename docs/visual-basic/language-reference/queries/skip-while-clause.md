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
ms.openlocfilehash: af722f7aee021f244b411cdc61619b7de3c20607
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866235"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="fdab9-102">Skip While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fdab9-102">Skip While Clause (Visual Basic)</span></span>

<span data-ttu-id="fdab9-103">Belirtilen koşul olduğu sürece bir koleksiyondaki öğeleri atlar `true` ve kalan öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdab9-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdab9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdab9-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fdab9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fdab9-105">Parts</span></span>  
  
|<span data-ttu-id="fdab9-106">Terim</span><span class="sxs-lookup"><span data-stu-id="fdab9-106">Term</span></span>|<span data-ttu-id="fdab9-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="fdab9-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="fdab9-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fdab9-108">Required.</span></span> <span data-ttu-id="fdab9-109">İçin öğeleri test eden bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="fdab9-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="fdab9-110">İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="fdab9-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdab9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fdab9-111">Remarks</span></span>  

 <span data-ttu-id="fdab9-112">`Skip While`Yan tümce, sağlanan döndürene kadar öğeleri bir sorgu sonucunun başından atlar `expression` `false` .</span><span class="sxs-lookup"><span data-stu-id="fdab9-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="fdab9-113">`expression`Geri döndüğünde `false` , sorgu kalan tüm öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fdab9-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="fdab9-114">`expression`Kalan sonuçlar için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="fdab9-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="fdab9-115">Yan tümcesi, `Skip While` belirli bir `Where` `Where` koşulu karşılamayan bir sorgudaki tüm öğeleri dışlamak için kullanılan yan tümcesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="fdab9-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="fdab9-116">`Skip While`Yan tümcesi, yalnızca koşul karşılanmadığı sürece öğeleri dışlar.</span><span class="sxs-lookup"><span data-stu-id="fdab9-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="fdab9-117">`Skip While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="fdab9-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="fdab9-118">Yan tümcesini kullanarak, bir sorgu sonucunun başından belirli bir sonuç sayısını atlayabilirsiniz `Skip` .</span><span class="sxs-lookup"><span data-stu-id="fdab9-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdab9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="fdab9-119">Example</span></span>  

 <span data-ttu-id="fdab9-120">Aşağıdaki kod örneği, `Skip While` Birleşik Devletler ilk müşteri bulunana kadar sonuçları atlamak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fdab9-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="fdab9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fdab9-121">See also</span></span>

- [<span data-ttu-id="fdab9-122">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="fdab9-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fdab9-123">Sorgular</span><span class="sxs-lookup"><span data-stu-id="fdab9-123">Queries</span></span>](index.md)
- [<span data-ttu-id="fdab9-124">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fdab9-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="fdab9-125">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fdab9-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="fdab9-126">Skip Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="fdab9-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="fdab9-127">Take While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="fdab9-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="fdab9-128">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="fdab9-128">Where Clause</span></span>](where-clause.md)
