---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: a7a0952ebe13b732ce706c3dad97a6da3b5cb85d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966560"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="b6a46-102">IsNot İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6a46-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="b6a46-103">İki nesne başvurusu değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b6a46-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6a46-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="b6a46-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b6a46-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b6a46-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b6a46-106">Required.</span></span> <span data-ttu-id="b6a46-107">A `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="b6a46-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="b6a46-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b6a46-108">Required.</span></span> <span data-ttu-id="b6a46-109">Tüm `Object` değişkenin veya ifadenin.</span><span class="sxs-lookup"><span data-stu-id="b6a46-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="b6a46-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="b6a46-110">Required.</span></span> <span data-ttu-id="b6a46-111">Tüm `Object` değişkenin veya ifadenin.</span><span class="sxs-lookup"><span data-stu-id="b6a46-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6a46-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6a46-112">Remarks</span></span>  
 <span data-ttu-id="b6a46-113">`IsNot` İşleci belirleyen iki nesne başvuru farklı nesnelere başvuru değilse.</span><span class="sxs-lookup"><span data-stu-id="b6a46-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="b6a46-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="b6a46-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="b6a46-115">Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olduğu `False`; Eğer öyleyse, `result` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="b6a46-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="b6a46-116">`IsNot` tersidir `Is` işleci.</span><span class="sxs-lookup"><span data-stu-id="b6a46-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="b6a46-117">Avantajı `IsNot` garip söz dizimiyle kaçınabilirsiniz olan `Not` ve `Is`, hangi okumak zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="b6a46-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="b6a46-118">Kullanabileceğiniz `Is` ve `IsNot` hem erken bağlanmış ve geç bağlama nesnelerini test etmek için işleçler.</span><span class="sxs-lookup"><span data-stu-id="b6a46-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6a46-119">`IsNot` Döndürüldüğü ifadeleri karşılaştırma işleci kullanılamaz `TypeOf` işleci.</span><span class="sxs-lookup"><span data-stu-id="b6a46-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="b6a46-120">Bunun yerine, kullanmalısınız `Not` ve `Is` işleçleri.</span><span class="sxs-lookup"><span data-stu-id="b6a46-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a46-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6a46-121">Example</span></span>  
 <span data-ttu-id="b6a46-122">Aşağıdaki kod örneği, hem de kullandığı `Is` işleci ve `IsNot` aynı karşılaştırma gerçekleştirmek için işleci.</span><span class="sxs-lookup"><span data-stu-id="b6a46-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="b6a46-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6a46-123">See also</span></span>
- [<span data-ttu-id="b6a46-124">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="b6a46-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="b6a46-125">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="b6a46-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="b6a46-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="b6a46-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b6a46-127">Nasıl yapılır: İki nesnenin aynı olup olmadığını test etme</span><span class="sxs-lookup"><span data-stu-id="b6a46-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
