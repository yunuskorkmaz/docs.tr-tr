---
title: Is İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917213"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="eba6e-102">Is İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eba6e-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="eba6e-103">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="eba6e-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eba6e-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="eba6e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="eba6e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="eba6e-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="eba6e-106">Required.</span></span> <span data-ttu-id="eba6e-107">Herhangi `Boolean` bir değer.</span><span class="sxs-lookup"><span data-stu-id="eba6e-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="eba6e-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="eba6e-108">Required.</span></span> <span data-ttu-id="eba6e-109">Herhangi `Object` bir ad.</span><span class="sxs-lookup"><span data-stu-id="eba6e-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="eba6e-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="eba6e-110">Required.</span></span> <span data-ttu-id="eba6e-111">Herhangi `Object` bir ad.</span><span class="sxs-lookup"><span data-stu-id="eba6e-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eba6e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eba6e-112">Remarks</span></span>  
 <span data-ttu-id="eba6e-113">`Is` İşleci iki nesne başvurusunun aynı nesneye başvurmasını belirler.</span><span class="sxs-lookup"><span data-stu-id="eba6e-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="eba6e-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="eba6e-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="eba6e-115">`object1` Ve her`object2` ikisi de`result` tam aynınesne`result` örneğine `True` başvurur,`False`ise, olur.</span><span class="sxs-lookup"><span data-stu-id="eba6e-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="eba6e-116">`Is`Ayrıca, `TypeOf` `TypeOf`... yapmak için anahtar sözcükle birlikte kullanılabilir. `Is` bir nesne değişkeninin bir veri türüyle uyumlu olup olmadığını test eden ifadesi.</span><span class="sxs-lookup"><span data-stu-id="eba6e-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eba6e-117">`Is` Anahtar sözcüğü, [Select... içinde de kullanılır. Case bildirisi](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="eba6e-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba6e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="eba6e-118">Example</span></span>  
 <span data-ttu-id="eba6e-119">Aşağıdaki örnek, nesne başvuruları `Is` çiftlerini karşılaştırmak için işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="eba6e-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="eba6e-120">Sonuçlar, iki nesnenin aynı olup `Boolean` olmadığını temsil eden bir değere atanır.</span><span class="sxs-lookup"><span data-stu-id="eba6e-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="eba6e-121">Yukarıdaki örnekte gösterildiği gibi, `Is` işlecini kullanarak hem erken hem de geç bağlantılı nesneleri test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eba6e-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba6e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eba6e-122">See also</span></span>

- [<span data-ttu-id="eba6e-123">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="eba6e-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="eba6e-124">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="eba6e-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="eba6e-125">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="eba6e-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="eba6e-126">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="eba6e-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="eba6e-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="eba6e-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="eba6e-128">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="eba6e-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
