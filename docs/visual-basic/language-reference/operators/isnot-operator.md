---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ffafff915af8a94e9bc135246064e4c049d41838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596468"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="fac69-102">IsNot İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fac69-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="fac69-103">İki nesne başvurusu değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fac69-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac69-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fac69-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="fac69-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fac69-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="fac69-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fac69-106">Required.</span></span> <span data-ttu-id="fac69-107">A `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="fac69-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="fac69-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fac69-108">Required.</span></span> <span data-ttu-id="fac69-109">Tüm `Object` değişkenin veya ifadenin.</span><span class="sxs-lookup"><span data-stu-id="fac69-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="fac69-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="fac69-110">Required.</span></span> <span data-ttu-id="fac69-111">Tüm `Object` değişkenin veya ifadenin.</span><span class="sxs-lookup"><span data-stu-id="fac69-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fac69-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fac69-112">Remarks</span></span>  
 <span data-ttu-id="fac69-113">`IsNot` İşleci belirleyen iki nesne başvuru farklı nesnelere başvuru değilse.</span><span class="sxs-lookup"><span data-stu-id="fac69-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="fac69-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="fac69-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="fac69-115">Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olduğu `False`; Eğer öyleyse, `result` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="fac69-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="fac69-116">`IsNot` tersidir `Is` işleci.</span><span class="sxs-lookup"><span data-stu-id="fac69-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="fac69-117">Avantajı `IsNot` garip söz dizimiyle kaçınabilirsiniz olan `Not` ve `Is`, hangi okumak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fac69-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="fac69-118">Kullanabileceğiniz `Is` ve `IsNot` hem erken bağlanmış ve geç bağlama nesnelerini test etmek için işleçler.</span><span class="sxs-lookup"><span data-stu-id="fac69-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fac69-119">`IsNot` Döndürüldüğü ifadeleri karşılaştırma işleci kullanılamaz `TypeOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="fac69-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="fac69-120">Bunun yerine, kullanmalısınız `Not` ve `Is` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="fac69-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fac69-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="fac69-121">Example</span></span>  
 <span data-ttu-id="fac69-122">Aşağıdaki kod örneği, hem de kullandığı `Is` işleci ve `IsNot` aynı karşılaştırma gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="fac69-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fac69-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fac69-123">See also</span></span>
- [<span data-ttu-id="fac69-124">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="fac69-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="fac69-125">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="fac69-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="fac69-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="fac69-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="fac69-127">Nasıl yapılır: İki nesnenin aynı olup olmadığını test etme</span><span class="sxs-lookup"><span data-stu-id="fac69-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
