---
title: İşleç önceliği (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: f8aa0f213a24d6431d8910af849571a67fbd9f57
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175648"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="ff677-102">İşleç önceliği (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ff677-102">Operator Precedence (Entity SQL)</span></span>

<span data-ttu-id="ff677-103">Bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorguda birden çok işleç olduğunda, işleç önceliği işlemlerin gerçekleştirileceği diziyi belirler.</span><span class="sxs-lookup"><span data-stu-id="ff677-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="ff677-104">Yürütmenin sırası, sorgu sonucunu önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="ff677-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="ff677-105">İşleçler aşağıdaki tabloda gösterilen öncelik düzeylerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ff677-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="ff677-106">Daha yüksek düzeyi olan bir işleç, daha düşük düzeydeki bir işleçten önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ff677-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="ff677-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="ff677-107">Level</span></span>|<span data-ttu-id="ff677-108">İşlem türü</span><span class="sxs-lookup"><span data-stu-id="ff677-108">Operation type</span></span>|<span data-ttu-id="ff677-109">İşleç</span><span class="sxs-lookup"><span data-stu-id="ff677-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="ff677-110">1</span><span class="sxs-lookup"><span data-stu-id="ff677-110">1</span></span>|<span data-ttu-id="ff677-111">Birincil</span><span class="sxs-lookup"><span data-stu-id="ff677-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="ff677-112">2</span><span class="sxs-lookup"><span data-stu-id="ff677-112">2</span></span>|<span data-ttu-id="ff677-113">Birli</span><span class="sxs-lookup"><span data-stu-id="ff677-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="ff677-114">3</span><span class="sxs-lookup"><span data-stu-id="ff677-114">3</span></span>|<span data-ttu-id="ff677-115">Çarpımsal</span><span class="sxs-lookup"><span data-stu-id="ff677-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="ff677-116">4</span><span class="sxs-lookup"><span data-stu-id="ff677-116">4</span></span>|<span data-ttu-id="ff677-117">Toplamsal</span><span class="sxs-lookup"><span data-stu-id="ff677-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="ff677-118">5</span><span class="sxs-lookup"><span data-stu-id="ff677-118">5</span></span>|<span data-ttu-id="ff677-119">Sıralama</span><span class="sxs-lookup"><span data-stu-id="ff677-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="ff677-120">6</span><span class="sxs-lookup"><span data-stu-id="ff677-120">6</span></span>|<span data-ttu-id="ff677-121">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="ff677-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="ff677-122">7</span><span class="sxs-lookup"><span data-stu-id="ff677-122">7</span></span>|<span data-ttu-id="ff677-123">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="ff677-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="ff677-124">8</span><span class="sxs-lookup"><span data-stu-id="ff677-124">8</span></span>|<span data-ttu-id="ff677-125">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="ff677-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="ff677-126">Bir ifadedeki iki operatör aynı operatör öncelik düzeyine sahip olduğunda, sorgudaki konumlarına göre soldan sağa değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ff677-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="ff677-127">Örneğin, `x+y-z` olarak değerlendirilir `(x+y)-z` .</span><span class="sxs-lookup"><span data-stu-id="ff677-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="ff677-128">Bir sorgudaki operatörlerin tanımlanmış önceliğini geçersiz kılmak için parantezleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff677-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="ff677-129">Parantez içindeki her şey, sonucun parantez dışında herhangi bir operatör tarafından kullanılabilmesi için önce tek bir sonuç verecek şekilde değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ff677-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="ff677-130">Örneğin, ile `x+y*z` çarpar `y` `z` ve sonra ekler `x` , ancak `(x+y)*z` `x` sonucunu öğesine ekler `y` ve sonra sonucu ile çarpar `z` .</span><span class="sxs-lookup"><span data-stu-id="ff677-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff677-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff677-131">See also</span></span>

- [<span data-ttu-id="ff677-132">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff677-132">Entity SQL Overview</span></span>](entity-sql-overview.md)
