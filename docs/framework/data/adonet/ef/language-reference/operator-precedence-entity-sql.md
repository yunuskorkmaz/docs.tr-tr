---
title: İşleç önceliği (varlık SQL)
ms.date: 03/30/2017
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
ms.openlocfilehash: 722ebe5f0ec530f8c7f86e9f9901451b060903f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760356"
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="aa07b-102">İşleç önceliği (varlık SQL)</span><span class="sxs-lookup"><span data-stu-id="aa07b-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="aa07b-103">Olduğunda bir [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sorgu sahip birden çok işleç, İşleç önceliği işlemleri gerçekleştirilir sırasını belirler.</span><span class="sxs-lookup"><span data-stu-id="aa07b-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="aa07b-104">Yürütme sırası, sorgu sonucu olarak önemli ölçüde etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="aa07b-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="aa07b-105">İşleçler, öncelik düzeyleri aşağıdaki tabloda gösterilen sahip.</span><span class="sxs-lookup"><span data-stu-id="aa07b-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="aa07b-106">Daha yüksek bir düzeye sahip bir işleç, daha düşük bir düzeye sahip bir işleç önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aa07b-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="aa07b-107">Düzey</span><span class="sxs-lookup"><span data-stu-id="aa07b-107">Level</span></span>|<span data-ttu-id="aa07b-108">İşlem türü</span><span class="sxs-lookup"><span data-stu-id="aa07b-108">Operation type</span></span>|<span data-ttu-id="aa07b-109">İşleç</span><span class="sxs-lookup"><span data-stu-id="aa07b-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="aa07b-110">1.</span><span class="sxs-lookup"><span data-stu-id="aa07b-110">1</span></span>|<span data-ttu-id="aa07b-111">Birincil</span><span class="sxs-lookup"><span data-stu-id="aa07b-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="aa07b-112">2</span><span class="sxs-lookup"><span data-stu-id="aa07b-112">2</span></span>|<span data-ttu-id="aa07b-113">Birli</span><span class="sxs-lookup"><span data-stu-id="aa07b-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="aa07b-114">3</span><span class="sxs-lookup"><span data-stu-id="aa07b-114">3</span></span>|<span data-ttu-id="aa07b-115">Çarpma</span><span class="sxs-lookup"><span data-stu-id="aa07b-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="aa07b-116">4</span><span class="sxs-lookup"><span data-stu-id="aa07b-116">4</span></span>|<span data-ttu-id="aa07b-117">Eklenebilir</span><span class="sxs-lookup"><span data-stu-id="aa07b-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="aa07b-118">5</span><span class="sxs-lookup"><span data-stu-id="aa07b-118">5</span></span>|<span data-ttu-id="aa07b-119">Sıralama</span><span class="sxs-lookup"><span data-stu-id="aa07b-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="aa07b-120">6</span><span class="sxs-lookup"><span data-stu-id="aa07b-120">6</span></span>|<span data-ttu-id="aa07b-121">Eşitlik</span><span class="sxs-lookup"><span data-stu-id="aa07b-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="aa07b-122">7</span><span class="sxs-lookup"><span data-stu-id="aa07b-122">7</span></span>|<span data-ttu-id="aa07b-123">Koşullu VE</span><span class="sxs-lookup"><span data-stu-id="aa07b-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="aa07b-124">8</span><span class="sxs-lookup"><span data-stu-id="aa07b-124">8</span></span>|<span data-ttu-id="aa07b-125">Koşullu VEYA</span><span class="sxs-lookup"><span data-stu-id="aa07b-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="aa07b-126">İki işleç bir ifadede aynı işleci öncelik düzeyine sahip olduğunuzda, bunlar, sağdan sola değerlendirilir sorgu konumlarına göre.</span><span class="sxs-lookup"><span data-stu-id="aa07b-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="aa07b-127">Örneğin, `x+y-z` değerlendirmesinde `(x+y)-z`.</span><span class="sxs-lookup"><span data-stu-id="aa07b-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="aa07b-128">Parantez tanımlı sorgu işleçleri önceliği geçersiz kılmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa07b-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="aa07b-129">Parantez içindeki her şeyi ilk sonuç parantezler dışında herhangi bir işleç tarafından kullanılabilir önce tek bir sonuç elde etmek üzere değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aa07b-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="aa07b-130">Örneğin, `x+y*z` çarpar `y` tarafından `z` ve ekler `x`, ancak `(x+y)*z` ekler `x` için `y` ve sonucu çarpan `z`.</span><span class="sxs-lookup"><span data-stu-id="aa07b-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa07b-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa07b-131">See also</span></span>

- [<span data-ttu-id="aa07b-132">Entity SQL’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="aa07b-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
