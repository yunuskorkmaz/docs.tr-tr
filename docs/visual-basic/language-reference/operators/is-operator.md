---
description: 'Şu konuda daha fazla bilgi edinin: Bu işleç (Visual Basic)'
title: İşleç
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 0912ebd9bc9c33149568c6cea0197ef24c305ff2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665694"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="be0b1-103">İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be0b1-103">Is operator (Visual Basic)</span></span>

<span data-ttu-id="be0b1-104">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="be0b1-104">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="be0b1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="be0b1-105">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="be0b1-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="be0b1-106">Parts</span></span>

 `result`  
 <span data-ttu-id="be0b1-107">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="be0b1-107">Required.</span></span> <span data-ttu-id="be0b1-108">Herhangi bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="be0b1-108">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="be0b1-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="be0b1-109">Required.</span></span> <span data-ttu-id="be0b1-110">Herhangi bir `Object` ad.</span><span class="sxs-lookup"><span data-stu-id="be0b1-110">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="be0b1-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="be0b1-111">Required.</span></span> <span data-ttu-id="be0b1-112">Herhangi bir `Object` ad.</span><span class="sxs-lookup"><span data-stu-id="be0b1-112">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be0b1-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be0b1-113">Remarks</span></span>

<span data-ttu-id="be0b1-114">`Is`İşleci iki nesne başvurusunun aynı nesneye başvurmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="be0b1-114">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="be0b1-115">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="be0b1-115">However, it does not perform value comparisons.</span></span> <span data-ttu-id="be0b1-116">`object1`Ve `object2` her ikisi de tam aynı nesne örneğine başvurur, ise, olur `result` `True` `result` `False` .</span><span class="sxs-lookup"><span data-stu-id="be0b1-116">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="be0b1-117">`Is`Anahtar sözcüğü, Select... içinde de kullanılır [. Case bildirisi](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="be0b1-117">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="be0b1-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="be0b1-118">Example</span></span>

<span data-ttu-id="be0b1-119">Aşağıdaki örnek, `Is` nesne başvuruları çiftlerini karşılaştırmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="be0b1-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="be0b1-120">Sonuçlar, `Boolean` iki nesnenin aynı olup olmadığını temsil eden bir değere atanır.</span><span class="sxs-lookup"><span data-stu-id="be0b1-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="be0b1-121">Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be0b1-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="be0b1-122">With işleci ile TypeOf işleci kullanın</span><span class="sxs-lookup"><span data-stu-id="be0b1-122">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="be0b1-123">`Is` işleci, bir `TypeOf` `TypeOf` `Is` nesne değişkeninin bir veri türüyle uyumlu olup olmadığını test eden bir... ifadesi oluşturmak için anahtar sözcükle birlikte de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be0b1-123">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="be0b1-124">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="be0b1-124">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="be0b1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be0b1-125">See also</span></span>

- [<span data-ttu-id="be0b1-126">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="be0b1-126">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="be0b1-127">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="be0b1-127">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="be0b1-128">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="be0b1-128">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="be0b1-129">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="be0b1-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="be0b1-130">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="be0b1-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="be0b1-131">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="be0b1-131">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
