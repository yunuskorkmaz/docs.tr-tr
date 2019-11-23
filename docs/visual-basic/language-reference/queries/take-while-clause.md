---
title: Take While Tümcesi
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347106"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="5df32-102">Take While Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5df32-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="5df32-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span><span class="sxs-lookup"><span data-stu-id="5df32-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df32-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5df32-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5df32-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5df32-105">Parts</span></span>  
  
|<span data-ttu-id="5df32-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5df32-106">Term</span></span>|<span data-ttu-id="5df32-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5df32-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="5df32-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5df32-108">Required.</span></span> <span data-ttu-id="5df32-109">An expression that represents a condition to test elements for.</span><span class="sxs-lookup"><span data-stu-id="5df32-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="5df32-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5df32-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5df32-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5df32-111">Remarks</span></span>  
 <span data-ttu-id="5df32-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span><span class="sxs-lookup"><span data-stu-id="5df32-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="5df32-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span><span class="sxs-lookup"><span data-stu-id="5df32-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="5df32-114">The `expression` is ignored for the remaining results.</span><span class="sxs-lookup"><span data-stu-id="5df32-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="5df32-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span><span class="sxs-lookup"><span data-stu-id="5df32-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="5df32-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span><span class="sxs-lookup"><span data-stu-id="5df32-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="5df32-117">The `Take While` clause is most useful when you are working with an ordered query result.</span><span class="sxs-lookup"><span data-stu-id="5df32-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df32-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="5df32-118">Example</span></span>  
 <span data-ttu-id="5df32-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span><span class="sxs-lookup"><span data-stu-id="5df32-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5df32-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5df32-120">See also</span></span>

- [<span data-ttu-id="5df32-121">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5df32-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5df32-122">Sorgular</span><span class="sxs-lookup"><span data-stu-id="5df32-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="5df32-123">Select Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="5df32-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="5df32-124">From Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="5df32-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="5df32-125">Take Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="5df32-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="5df32-126">Skip While Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="5df32-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="5df32-127">Where Yan Tümcesi</span><span class="sxs-lookup"><span data-stu-id="5df32-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
