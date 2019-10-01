---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 32e8f9532244679d2994b0e3d98279d75f7e77b4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701045"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="82278-102">IsNot İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82278-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="82278-103">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="82278-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="82278-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82278-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="82278-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="82278-105">Parts</span></span>
 <span data-ttu-id="82278-106">`result` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="82278-106">`result` Required.</span></span> <span data-ttu-id="82278-107">@No__t-0 değeri.</span><span class="sxs-lookup"><span data-stu-id="82278-107">A `Boolean` value.</span></span>

 <span data-ttu-id="82278-108">`object1` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="82278-108">`object1` Required.</span></span> <span data-ttu-id="82278-109">Herhangi bir `Object` değişkeni veya ifadesi.</span><span class="sxs-lookup"><span data-stu-id="82278-109">Any `Object` variable or expression.</span></span>

 <span data-ttu-id="82278-110">`object2` gereklidir.</span><span class="sxs-lookup"><span data-stu-id="82278-110">`object2` Required.</span></span> <span data-ttu-id="82278-111">Herhangi bir `Object` değişkeni veya ifadesi.</span><span class="sxs-lookup"><span data-stu-id="82278-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="82278-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82278-112">Remarks</span></span>
 <span data-ttu-id="82278-113">@No__t-0 işleci, iki nesne başvurusunun farklı nesnelere başvuracağını belirler.</span><span class="sxs-lookup"><span data-stu-id="82278-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="82278-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="82278-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="82278-115">@No__t-0 ve `object2` her ikisi de tam aynı nesne örneğine başvurur, `result` `False`; Aksi takdirde, @no__t 4 `True` ' tir.</span><span class="sxs-lookup"><span data-stu-id="82278-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>

 <span data-ttu-id="82278-116">`IsNot`, `Is` işlecinin tersidir.</span><span class="sxs-lookup"><span data-stu-id="82278-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="82278-117">@No__t-0 ' nın avantajı, okunması zor olabilecek `Not` ve `Is` ile garip söz dizimini önlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="82278-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="82278-118">@No__t-0 ve `IsNot` işleçlerini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82278-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="82278-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="82278-119">Example</span></span>
 <span data-ttu-id="82278-120">Aşağıdaki kod örneği, aynı karşılaştırmayı gerçekleştirmek için hem `Is` işlecini hem de `IsNot` işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="82278-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="see-also"></a><span data-ttu-id="82278-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82278-121">See also</span></span>

- [<span data-ttu-id="82278-122">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="82278-122">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="82278-123">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="82278-123">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="82278-124">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="82278-124">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="82278-125">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme</span><span class="sxs-lookup"><span data-stu-id="82278-125">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
