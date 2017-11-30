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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 484eedffeaffb625cd43352dadedb8c99fbc65ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="cf0a3-102">İşleç önceliği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="cf0a3-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="cf0a3-103">Zaman bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu sahip birden çok işleç, İşleç önceliği işlemler gerçekleştirilir sırasını belirler.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="cf0a3-104">Yürütme sırasını, sorgu sonucu olarak önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="cf0a3-105">İşleçler aşağıdaki tabloda gösterilen öncelik düzeyine sahip.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="cf0a3-106">Daha yüksek bir düzeye sahip bir işleç daha düşük bir düzeye sahip bir işleç önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="cf0a3-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="cf0a3-107">Level</span></span>|<span data-ttu-id="cf0a3-108">İşlem türü</span><span class="sxs-lookup"><span data-stu-id="cf0a3-108">Operation type</span></span>|<span data-ttu-id="cf0a3-109">İşleç</span><span class="sxs-lookup"><span data-stu-id="cf0a3-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="cf0a3-110">1.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-110">1</span></span>|<span data-ttu-id="cf0a3-111">birincil</span><span class="sxs-lookup"><span data-stu-id="cf0a3-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="cf0a3-112">2</span><span class="sxs-lookup"><span data-stu-id="cf0a3-112">2</span></span>|<span data-ttu-id="cf0a3-113">Birli</span><span class="sxs-lookup"><span data-stu-id="cf0a3-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="cf0a3-114">3</span><span class="sxs-lookup"><span data-stu-id="cf0a3-114">3</span></span>|<span data-ttu-id="cf0a3-115">Çarpma</span><span class="sxs-lookup"><span data-stu-id="cf0a3-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="cf0a3-116">4</span><span class="sxs-lookup"><span data-stu-id="cf0a3-116">4</span></span>|<span data-ttu-id="cf0a3-117">ADDITIVE</span><span class="sxs-lookup"><span data-stu-id="cf0a3-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="cf0a3-118">5</span><span class="sxs-lookup"><span data-stu-id="cf0a3-118">5</span></span>|<span data-ttu-id="cf0a3-119">Sıralama</span><span class="sxs-lookup"><span data-stu-id="cf0a3-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="cf0a3-120">6</span><span class="sxs-lookup"><span data-stu-id="cf0a3-120">6</span></span>|<span data-ttu-id="cf0a3-121">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="cf0a3-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="cf0a3-122">7</span><span class="sxs-lookup"><span data-stu-id="cf0a3-122">7</span></span>|<span data-ttu-id="cf0a3-123">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="cf0a3-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="cf0a3-124">8</span><span class="sxs-lookup"><span data-stu-id="cf0a3-124">8</span></span>|<span data-ttu-id="cf0a3-125">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="cf0a3-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="cf0a3-126">İşleç önceliği düzeyde bir ifadede iki işleç sahip olduğunuzda, soldan sağa değerlendirilme sorgu konumlarına göre.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="cf0a3-127">Örneğin, `x+y-z` olarak değerlendirilir `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="cf0a3-128">Sorgu işleçlerinin tanımlı önceliği geçersiz kılmak için ayraç kullanın.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="cf0a3-129">Parantez içindeki her şeyi sonuç parantez dışında herhangi bir işleç tarafından kullanılabilir önce tek bir sonuç elde etmek üzere önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="cf0a3-130">Örneğin, `x+y*z` çarpar `y` tarafından `z` ve ardından ekler `x`, ancak `(x+y)*z` ekler `x` için `y` ve sonuç olarak çoğaltır `z`.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf0a3-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf0a3-131">See Also</span></span>  
 [<span data-ttu-id="cf0a3-132">Varlık SQL genel bakış</span><span class="sxs-lookup"><span data-stu-id="cf0a3-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
