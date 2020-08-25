---
title: IsNot işleci
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ea978f8874cee20fb3a005189fd846f7564da777
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811047"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="5565d-102">IsNot İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5565d-102">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="5565d-103">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="5565d-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="5565d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5565d-104">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="5565d-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="5565d-105">Parts</span></span>

- `result`

  <span data-ttu-id="5565d-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5565d-106">Required.</span></span> <span data-ttu-id="5565d-107">Bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="5565d-107">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="5565d-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5565d-108">Required.</span></span> <span data-ttu-id="5565d-109">Herhangi bir `Object` değişken veya ifade.</span><span class="sxs-lookup"><span data-stu-id="5565d-109">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="5565d-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5565d-110">Required.</span></span> <span data-ttu-id="5565d-111">Herhangi bir `Object` değişken veya ifade.</span><span class="sxs-lookup"><span data-stu-id="5565d-111">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="5565d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5565d-112">Remarks</span></span>

<span data-ttu-id="5565d-113">`IsNot`İşleci iki nesne başvurusunun farklı nesnelere başvuracağını belirler.</span><span class="sxs-lookup"><span data-stu-id="5565d-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="5565d-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="5565d-114">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="5565d-115">`object1`Ve `object2` her ikisi de tam aynı nesne örneğine başvurur, ise, olur `result` `False` `result` `True` .</span><span class="sxs-lookup"><span data-stu-id="5565d-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="5565d-116">`IsNot` , `Is` işlecinin tersidir.</span><span class="sxs-lookup"><span data-stu-id="5565d-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="5565d-117">' Nin avantajı, `IsNot` ve ile garip söz dizimini önlemenize `Not` ve bu `Is` da okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="5565d-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="5565d-118">`Is`Ve `IsNot` işleçlerini, hem erken hem de geç bağlantılı nesneleri test etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5565d-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="5565d-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5565d-119">Example</span></span>

<span data-ttu-id="5565d-120">Aşağıdaki kod örneği `Is` `IsNot` aynı karşılaştırmayı başarmak için hem işlecini hem de işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5565d-120">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="5565d-121">IsNot işleci ile TypeOf işleci kullanın</span><span class="sxs-lookup"><span data-stu-id="5565d-121">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="5565d-122">Visual Basic 14 ' ten başlayarak, bir `TypeOf` `IsNot` nesnenin veri türüyle uyumlu olup olmadığını test etmek için işlecini işleciyle kullanabilirsiniz *not* .</span><span class="sxs-lookup"><span data-stu-id="5565d-122">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="5565d-123">Örnek:</span><span class="sxs-lookup"><span data-stu-id="5565d-123">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="5565d-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5565d-124">See also</span></span>

- [<span data-ttu-id="5565d-125">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="5565d-125">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="5565d-126">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="5565d-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="5565d-127">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="5565d-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="5565d-128">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme</span><span class="sxs-lookup"><span data-stu-id="5565d-128">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
