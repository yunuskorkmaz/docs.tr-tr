---
title: Take While Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869663"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="dc5fe-102">Take While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc5fe-102">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="dc5fe-103">Belirtilen koşul olduğu `true` ve kalan öğeleri atlayan sürece bir koleksiyondaki öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc5fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc5fe-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="dc5fe-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="dc5fe-105">Parts</span></span>  
  
|<span data-ttu-id="dc5fe-106">Terim</span><span class="sxs-lookup"><span data-stu-id="dc5fe-106">Term</span></span>|<span data-ttu-id="dc5fe-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="dc5fe-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="dc5fe-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-108">Required.</span></span> <span data-ttu-id="dc5fe-109">İçin öğeleri test eden bir koşulu temsil eden bir ifade.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="dc5fe-110">İfade bir `Boolean` değer veya işlev eşdeğerini döndürmelidir, örneğin, `Integer` bir olarak değerlendirilir `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="dc5fe-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc5fe-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc5fe-111">Remarks</span></span>  

 <span data-ttu-id="dc5fe-112">`Take While`Yan tümcesi, sağlanan dönüşceye kadar bir sorgu sonucunun başından alınan öğeleri içerir `expression` `false` .</span><span class="sxs-lookup"><span data-stu-id="dc5fe-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="dc5fe-113">`expression`Döndürmeden sonra `false` sorgu kalan tüm öğeleri atlar.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="dc5fe-114">`expression`Kalan sonuçlar için yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="dc5fe-115">Yan tümcesi, `Take While` belirli bir `Where` `Where` koşulu karşılayan bir sorgudaki tüm öğeleri dahil etmek için kullanılan yan tümcesinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="dc5fe-116">`Take While`Yan tümcesi yalnızca koşul karşılanmadığı sürece öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="dc5fe-117">`Take While`Yan tümce, sıralı bir sorgu sonucuyla çalışırken en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc5fe-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc5fe-118">Example</span></span>  

 <span data-ttu-id="dc5fe-119">Aşağıdaki kod örneği, `Take While` bir sipariş olmadan ilk müşteri bulunana kadar sonuçları almak için yan tümcesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dc5fe-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc5fe-120">See also</span></span>

- [<span data-ttu-id="dc5fe-121">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="dc5fe-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="dc5fe-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="dc5fe-122">Queries</span></span>](index.md)
- [<span data-ttu-id="dc5fe-123">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="dc5fe-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="dc5fe-124">From yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="dc5fe-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="dc5fe-125">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="dc5fe-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="dc5fe-126">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="dc5fe-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="dc5fe-127">WHERE yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="dc5fe-127">Where Clause</span></span>](where-clause.md)
