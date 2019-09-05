---
title: İşleç önceliği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 2d8c78f410708fd1aa843ee8f14f7243a9f686c0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249776"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="f7095-102">İşleç önceliği (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f7095-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="f7095-103">Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguda birden çok işleç olduğunda, işleç önceliği işlemlerin gerçekleştirileceği diziyi belirler.</span><span class="sxs-lookup"><span data-stu-id="f7095-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="f7095-104">Yürütmenin sırası, sorgu sonucunu önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="f7095-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="f7095-105">İşleçler aşağıdaki tabloda gösterilen öncelik düzeylerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f7095-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="f7095-106">Daha yüksek düzeyi olan bir işleç, daha düşük düzeydeki bir işleçten önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7095-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="f7095-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="f7095-107">Level</span></span>|<span data-ttu-id="f7095-108">İşlem türü</span><span class="sxs-lookup"><span data-stu-id="f7095-108">Operation type</span></span>|<span data-ttu-id="f7095-109">İşleç</span><span class="sxs-lookup"><span data-stu-id="f7095-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="f7095-110">1\.</span><span class="sxs-lookup"><span data-stu-id="f7095-110">1</span></span>|<span data-ttu-id="f7095-111">Birincil</span><span class="sxs-lookup"><span data-stu-id="f7095-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="f7095-112">2</span><span class="sxs-lookup"><span data-stu-id="f7095-112">2</span></span>|<span data-ttu-id="f7095-113">Li</span><span class="sxs-lookup"><span data-stu-id="f7095-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="f7095-114">3</span><span class="sxs-lookup"><span data-stu-id="f7095-114">3</span></span>|<span data-ttu-id="f7095-115">Çarpma</span><span class="sxs-lookup"><span data-stu-id="f7095-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="f7095-116">4</span><span class="sxs-lookup"><span data-stu-id="f7095-116">4</span></span>|<span data-ttu-id="f7095-117">Msal</span><span class="sxs-lookup"><span data-stu-id="f7095-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="f7095-118">5</span><span class="sxs-lookup"><span data-stu-id="f7095-118">5</span></span>|<span data-ttu-id="f7095-119">Sıralama</span><span class="sxs-lookup"><span data-stu-id="f7095-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="f7095-120">6</span><span class="sxs-lookup"><span data-stu-id="f7095-120">6</span></span>|<span data-ttu-id="f7095-121">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="f7095-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="f7095-122">7</span><span class="sxs-lookup"><span data-stu-id="f7095-122">7</span></span>|<span data-ttu-id="f7095-123">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="f7095-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="f7095-124">8</span><span class="sxs-lookup"><span data-stu-id="f7095-124">8</span></span>|<span data-ttu-id="f7095-125">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="f7095-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="f7095-126">Bir ifadedeki iki operatör aynı operatör öncelik düzeyine sahip olduğunda, sorgudaki konumlarına göre soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7095-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="f7095-127">Örneğin, `x+y-z` olarak `(x+y)-z`değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7095-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="f7095-128">Bir sorgudaki operatörlerin tanımlanmış önceliğini geçersiz kılmak için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f7095-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="f7095-129">Parantez içindeki her şey, sonucun parantez dışında herhangi bir operatör tarafından kullanılabilmesi için önce tek bir sonuç verecek şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7095-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="f7095-130">Örneğin, `x+y*z` ile `x` `(x+y)*z` `z`çarpar `y` ve sonra ekler, ancak sonucunu öğesine `x` ekler`y` ve sonra sonucu ile çarpar. `z`</span><span class="sxs-lookup"><span data-stu-id="f7095-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7095-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7095-131">See also</span></span>

- [<span data-ttu-id="f7095-132">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f7095-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
