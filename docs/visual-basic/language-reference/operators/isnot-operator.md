---
description: 'Hakkında daha fazla bilgi edinin: ınot Işleci (Visual Basic)'
title: IsNot işleci
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- comparison operators [Visual Basic]
- TypeOf...IsNot expression
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: ac3e127676dfa57d14e07838152022de62fc336b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665672"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="6a3f6-103">IsNot İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a3f6-103">IsNot Operator (Visual Basic)</span></span>

<span data-ttu-id="6a3f6-104">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-104">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a3f6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a3f6-105">Syntax</span></span>

```vb
result = object1 IsNot object2
```

## <a name="parts"></a><span data-ttu-id="6a3f6-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6a3f6-106">Parts</span></span>

- `result`

  <span data-ttu-id="6a3f6-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-107">Required.</span></span> <span data-ttu-id="6a3f6-108">Bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-108">A `Boolean` value.</span></span>

- `object1`

  <span data-ttu-id="6a3f6-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-109">Required.</span></span> <span data-ttu-id="6a3f6-110">Herhangi bir `Object` değişken veya ifade.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-110">Any `Object` variable or expression.</span></span>

- `object2`

  <span data-ttu-id="6a3f6-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-111">Required.</span></span> <span data-ttu-id="6a3f6-112">Herhangi bir `Object` değişken veya ifade.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-112">Any `Object` variable or expression.</span></span>

## <a name="remarks"></a><span data-ttu-id="6a3f6-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a3f6-113">Remarks</span></span>

<span data-ttu-id="6a3f6-114">`IsNot`İşleci iki nesne başvurusunun farklı nesnelere başvuracağını belirler.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-114">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="6a3f6-115">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-115">However, it doesn't perform value comparisons.</span></span> <span data-ttu-id="6a3f6-116">`object1`Ve `object2` her ikisi de tam aynı nesne örneğine başvurur, ise, olur `result` `False` `result` `True` .</span><span class="sxs-lookup"><span data-stu-id="6a3f6-116">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they don't, `result` is `True`.</span></span>

<span data-ttu-id="6a3f6-117">`IsNot` , `Is` işlecinin tersidir.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-117">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="6a3f6-118">' Nin avantajı, `IsNot` ve ile garip söz dizimini önlemenize `Not` ve bu `Is` da okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-118">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>

 <span data-ttu-id="6a3f6-119">`Is`Ve `IsNot` işleçlerini, hem erken hem de geç bağlantılı nesneleri test etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-119">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>

## <a name="example"></a><span data-ttu-id="6a3f6-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a3f6-120">Example</span></span>

<span data-ttu-id="6a3f6-121">Aşağıdaki kod örneği `Is` `IsNot` aynı karşılaştırmayı başarmak için hem işlecini hem de işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-121">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>

[!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]

## <a name="use-typeof-operator-with-isnot-operator"></a><span data-ttu-id="6a3f6-122">IsNot işleci ile TypeOf işleci kullanın</span><span class="sxs-lookup"><span data-stu-id="6a3f6-122">Use TypeOf operator with IsNot operator</span></span>

<span data-ttu-id="6a3f6-123">Visual Basic 14 ' ten başlayarak, bir `TypeOf` `IsNot` nesnenin veri türüyle uyumlu olup olmadığını test etmek için işlecini işleciyle kullanabilirsiniz  .</span><span class="sxs-lookup"><span data-stu-id="6a3f6-123">Starting with Visual Basic 14, you can use the `TypeOf` operator with the `IsNot` operator to test whether an object is *not* compatible with a data type.</span></span> <span data-ttu-id="6a3f6-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6a3f6-124">For example:</span></span>

```vb
If TypeOf sender IsNot Button Then
```

## <a name="see-also"></a><span data-ttu-id="6a3f6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a3f6-125">See also</span></span>

- [<span data-ttu-id="6a3f6-126">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="6a3f6-126">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="6a3f6-127">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="6a3f6-127">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="6a3f6-128">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="6a3f6-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="6a3f6-129">Nasıl yapılır: İki Nesnenin Aynı Olup Olmadığını Test Etme</span><span class="sxs-lookup"><span data-stu-id="6a3f6-129">How to: Test Whether Two Objects Are the Same</span></span>](../../programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
