---
title: "İşleç önceliği (varlık SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 537c9ae7c92c6abcbe597970f2b0ec29e399bc62
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="9a38d-102">İşleç önceliği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="9a38d-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="9a38d-103">Zaman bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu sahip birden çok işleç, İşleç önceliği işlemler gerçekleştirilir sırasını belirler.</span><span class="sxs-lookup"><span data-stu-id="9a38d-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="9a38d-104">Yürütme sırasını, sorgu sonucu olarak önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="9a38d-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="9a38d-105">İşleçler aşağıdaki tabloda gösterilen öncelik düzeyine sahip.</span><span class="sxs-lookup"><span data-stu-id="9a38d-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="9a38d-106">Daha yüksek bir düzeye sahip bir işleç daha düşük bir düzeye sahip bir işleç önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9a38d-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="9a38d-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="9a38d-107">Level</span></span>|<span data-ttu-id="9a38d-108">İşlem türü</span><span class="sxs-lookup"><span data-stu-id="9a38d-108">Operation type</span></span>|<span data-ttu-id="9a38d-109">İşleç</span><span class="sxs-lookup"><span data-stu-id="9a38d-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="9a38d-110">1.</span><span class="sxs-lookup"><span data-stu-id="9a38d-110">1</span></span>|<span data-ttu-id="9a38d-111">birincil</span><span class="sxs-lookup"><span data-stu-id="9a38d-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="9a38d-112">2</span><span class="sxs-lookup"><span data-stu-id="9a38d-112">2</span></span>|<span data-ttu-id="9a38d-113">Birli</span><span class="sxs-lookup"><span data-stu-id="9a38d-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="9a38d-114">3</span><span class="sxs-lookup"><span data-stu-id="9a38d-114">3</span></span>|<span data-ttu-id="9a38d-115">Çarpma</span><span class="sxs-lookup"><span data-stu-id="9a38d-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="9a38d-116">4</span><span class="sxs-lookup"><span data-stu-id="9a38d-116">4</span></span>|<span data-ttu-id="9a38d-117">ADDITIVE</span><span class="sxs-lookup"><span data-stu-id="9a38d-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="9a38d-118">5</span><span class="sxs-lookup"><span data-stu-id="9a38d-118">5</span></span>|<span data-ttu-id="9a38d-119">Sıralama</span><span class="sxs-lookup"><span data-stu-id="9a38d-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="9a38d-120">6</span><span class="sxs-lookup"><span data-stu-id="9a38d-120">6</span></span>|<span data-ttu-id="9a38d-121">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="9a38d-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="9a38d-122">7</span><span class="sxs-lookup"><span data-stu-id="9a38d-122">7</span></span>|<span data-ttu-id="9a38d-123">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="9a38d-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="9a38d-124">8</span><span class="sxs-lookup"><span data-stu-id="9a38d-124">8</span></span>|<span data-ttu-id="9a38d-125">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="9a38d-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="9a38d-126">İşleç önceliği düzeyde bir ifadede iki işleç sahip olduğunuzda, soldan sağa değerlendirilme sorgu konumlarına göre.</span><span class="sxs-lookup"><span data-stu-id="9a38d-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="9a38d-127">Örneğin, `x+y-z` olarak değerlendirilir `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="9a38d-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="9a38d-128">Sorgu işleçlerinin tanımlı önceliği geçersiz kılmak için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="9a38d-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="9a38d-129">Parantez içindeki her şeyi sonuç parantez dışında herhangi bir işleç tarafından kullanılabilir önce tek bir sonuç elde etmek üzere önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9a38d-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="9a38d-130">Örneğin, `x+y*z` çarpar `y` tarafından `z` ve ardından ekler `x`, ancak `(x+y)*z` ekler `x` için `y` ve sonuç olarak çoğaltır `z`.</span><span class="sxs-lookup"><span data-stu-id="9a38d-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a38d-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a38d-131">See Also</span></span>  
 [<span data-ttu-id="9a38d-132">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9a38d-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
