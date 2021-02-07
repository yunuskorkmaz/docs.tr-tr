---
description: 'Daha fazla bilgi edinin: Işleç önceliği (Entity SQL)'
title: İşleç önceliği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 72cfdecf7dfe4ce590d99e866429e771f9ede231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739332"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="5b49b-103">İşleç önceliği (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5b49b-103">Operator Precedence (Entity SQL)</span></span>

<span data-ttu-id="5b49b-104">Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguda birden çok işleç olduğunda, işleç önceliği işlemlerin gerçekleştirileceği diziyi belirler.</span><span class="sxs-lookup"><span data-stu-id="5b49b-104">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="5b49b-105">Yürütmenin sırası, sorgu sonucunu önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="5b49b-105">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="5b49b-106">İşleçler aşağıdaki tabloda gösterilen öncelik düzeylerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5b49b-106">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="5b49b-107">Daha yüksek düzeyi olan bir işleç, daha düşük düzeydeki bir işleçten önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5b49b-107">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="5b49b-108">Level</span><span class="sxs-lookup"><span data-stu-id="5b49b-108">Level</span></span>|<span data-ttu-id="5b49b-109">İşlem türü</span><span class="sxs-lookup"><span data-stu-id="5b49b-109">Operation type</span></span>|<span data-ttu-id="5b49b-110">Operatör</span><span class="sxs-lookup"><span data-stu-id="5b49b-110">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="5b49b-111">1</span><span class="sxs-lookup"><span data-stu-id="5b49b-111">1</span></span>|<span data-ttu-id="5b49b-112">Birincil</span><span class="sxs-lookup"><span data-stu-id="5b49b-112">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="5b49b-113">2</span><span class="sxs-lookup"><span data-stu-id="5b49b-113">2</span></span>|<span data-ttu-id="5b49b-114">Birli</span><span class="sxs-lookup"><span data-stu-id="5b49b-114">Unary</span></span>|`! not`|  
|<span data-ttu-id="5b49b-115">3</span><span class="sxs-lookup"><span data-stu-id="5b49b-115">3</span></span>|<span data-ttu-id="5b49b-116">Çarpımsal</span><span class="sxs-lookup"><span data-stu-id="5b49b-116">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="5b49b-117">4</span><span class="sxs-lookup"><span data-stu-id="5b49b-117">4</span></span>|<span data-ttu-id="5b49b-118">Toplamsal</span><span class="sxs-lookup"><span data-stu-id="5b49b-118">Additive</span></span>|`+ -`|  
|<span data-ttu-id="5b49b-119">5</span><span class="sxs-lookup"><span data-stu-id="5b49b-119">5</span></span>|<span data-ttu-id="5b49b-120">Sıralama</span><span class="sxs-lookup"><span data-stu-id="5b49b-120">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="5b49b-121">6</span><span class="sxs-lookup"><span data-stu-id="5b49b-121">6</span></span>|<span data-ttu-id="5b49b-122">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="5b49b-122">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="5b49b-123">7</span><span class="sxs-lookup"><span data-stu-id="5b49b-123">7</span></span>|<span data-ttu-id="5b49b-124">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="5b49b-124">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="5b49b-125">8</span><span class="sxs-lookup"><span data-stu-id="5b49b-125">8</span></span>|<span data-ttu-id="5b49b-126">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="5b49b-126">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="5b49b-127">Bir ifadedeki iki operatör aynı operatör öncelik düzeyine sahip olduğunda, sorgudaki konumlarına göre soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5b49b-127">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="5b49b-128">Örneğin, `x+y-z` olarak değerlendirilir `(x+y)-z` .</span><span class="sxs-lookup"><span data-stu-id="5b49b-128">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="5b49b-129">Bir sorgudaki operatörlerin tanımlanmış önceliğini geçersiz kılmak için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b49b-129">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="5b49b-130">Parantez içindeki her şey, sonucun parantez dışında herhangi bir operatör tarafından kullanılabilmesi için önce tek bir sonuç verecek şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5b49b-130">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="5b49b-131">Örneğin, ile `x+y*z` çarpar `y` `z` ve sonra ekler `x` , ancak `(x+y)*z` `x` sonucunu öğesine ekler `y` ve sonra sonucu ile çarpar `z` .</span><span class="sxs-lookup"><span data-stu-id="5b49b-131">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b49b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b49b-132">See also</span></span>

- [<span data-ttu-id="5b49b-133">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5b49b-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
