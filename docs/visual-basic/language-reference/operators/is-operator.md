---
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
ms.openlocfilehash: 1c2d87ef0a8202332c87af552f488d652c400213
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812269"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="77b4f-102">İşleç (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77b4f-102">Is operator (Visual Basic)</span></span>

<span data-ttu-id="77b4f-103">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="77b4f-103">Compares two object reference variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="77b4f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="77b4f-104">Syntax</span></span>

```vb
result = object1 Is object2
```

## <a name="parts"></a><span data-ttu-id="77b4f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="77b4f-105">Parts</span></span>

 `result`  
 <span data-ttu-id="77b4f-106">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77b4f-106">Required.</span></span> <span data-ttu-id="77b4f-107">Herhangi bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="77b4f-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="77b4f-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77b4f-108">Required.</span></span> <span data-ttu-id="77b4f-109">Herhangi bir `Object` ad.</span><span class="sxs-lookup"><span data-stu-id="77b4f-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="77b4f-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="77b4f-110">Required.</span></span> <span data-ttu-id="77b4f-111">Herhangi bir `Object` ad.</span><span class="sxs-lookup"><span data-stu-id="77b4f-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77b4f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77b4f-112">Remarks</span></span>

<span data-ttu-id="77b4f-113">`Is`İşleci iki nesne başvurusunun aynı nesneye başvurmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="77b4f-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="77b4f-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="77b4f-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="77b4f-115">`object1`Ve `object2` her ikisi de tam aynı nesne örneğine başvurur, ise, olur `result` `True` `result` `False` .</span><span class="sxs-lookup"><span data-stu-id="77b4f-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>

> [!NOTE]
> <span data-ttu-id="77b4f-116">`Is`Anahtar sözcüğü, Select... içinde de kullanılır [. Case bildirisi](../statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77b4f-116">The `Is` keyword is also used in the [Select...Case Statement](../statements/select-case-statement.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="77b4f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="77b4f-117">Example</span></span>

<span data-ttu-id="77b4f-118">Aşağıdaki örnek, `Is` nesne başvuruları çiftlerini karşılaştırmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="77b4f-118">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="77b4f-119">Sonuçlar, `Boolean` iki nesnenin aynı olup olmadığını temsil eden bir değere atanır.</span><span class="sxs-lookup"><span data-stu-id="77b4f-119">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>

[!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]

<span data-ttu-id="77b4f-120">Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77b4f-120">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>

## <a name="use-typeof-operator-with-is-operator"></a><span data-ttu-id="77b4f-121">With işleci ile TypeOf işleci kullanın</span><span class="sxs-lookup"><span data-stu-id="77b4f-121">Use TypeOf operator with Is operator</span></span>

<span data-ttu-id="77b4f-122">`Is` işleci, bir `TypeOf` `TypeOf` `Is` nesne değişkeninin bir veri türüyle uyumlu olup olmadığını test eden bir... ifadesi oluşturmak için anahtar sözcükle birlikte de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77b4f-122">`Is` operator can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span> <span data-ttu-id="77b4f-123">Örnek:</span><span class="sxs-lookup"><span data-stu-id="77b4f-123">For example:</span></span>

```vb
If TypeOf sender Is Button Then
```

## <a name="see-also"></a><span data-ttu-id="77b4f-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77b4f-124">See also</span></span>

- [<span data-ttu-id="77b4f-125">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="77b4f-125">TypeOf Operator</span></span>](typeof-operator.md)
- [<span data-ttu-id="77b4f-126">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="77b4f-126">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="77b4f-127">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="77b4f-127">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="77b4f-128">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="77b4f-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="77b4f-129">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="77b4f-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="77b4f-130">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="77b4f-130">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
