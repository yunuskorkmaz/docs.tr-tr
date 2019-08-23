---
title: IsNot İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966931"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="7f279-102">IsNot İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f279-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="7f279-103">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="7f279-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f279-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f279-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="7f279-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="7f279-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7f279-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7f279-106">Required.</span></span> <span data-ttu-id="7f279-107">Bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="7f279-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="7f279-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7f279-108">Required.</span></span> <span data-ttu-id="7f279-109">Herhangi `Object` bir değişken veya ifade.</span><span class="sxs-lookup"><span data-stu-id="7f279-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="7f279-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="7f279-110">Required.</span></span> <span data-ttu-id="7f279-111">Herhangi `Object` bir değişken veya ifade.</span><span class="sxs-lookup"><span data-stu-id="7f279-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f279-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f279-112">Remarks</span></span>  
 <span data-ttu-id="7f279-113">`IsNot` İşleci iki nesne başvurusunun farklı nesnelere başvuracağını belirler.</span><span class="sxs-lookup"><span data-stu-id="7f279-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="7f279-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="7f279-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="7f279-115">`object1` Ve her`object2` ikisi de`result` tam aynınesne`result` örneğine `False` başvurur,`True`ise, olur.</span><span class="sxs-lookup"><span data-stu-id="7f279-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="7f279-116">`IsNot`, `Is` işlecinin tersidir.</span><span class="sxs-lookup"><span data-stu-id="7f279-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="7f279-117">' Nin `IsNot` avantajı, ve ile `Not` garip söz dizimini önlemenize ve `Is`bu da okunması zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f279-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="7f279-118">`Is` Ve`IsNot` işleçlerini, hem erken hem de geç bağlantılı nesneleri test etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f279-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f279-119">`IsNot` İşleç ,`TypeOf` işleçten döndürülen ifadeleri karşılaştırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7f279-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="7f279-120">Bunun yerine, `Not` ve `Is` işleçlerini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7f279-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f279-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="7f279-121">Example</span></span>  
 <span data-ttu-id="7f279-122">Aşağıdaki kod örneği aynı karşılaştırmayı başarmak için `Is` hem işlecini `IsNot` hem de işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f279-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="7f279-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f279-123">See also</span></span>

- [<span data-ttu-id="7f279-124">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="7f279-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="7f279-125">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="7f279-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="7f279-126">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="7f279-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7f279-127">Nasıl yapılır: Iki nesnenin aynı olup olmadığını test etme</span><span class="sxs-lookup"><span data-stu-id="7f279-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
