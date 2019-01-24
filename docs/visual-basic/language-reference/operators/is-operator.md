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
ms.openlocfilehash: a78189a6b82100665ac07b9d7c89590613ec1e1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745629"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="63941-102">Is İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63941-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="63941-103">İki nesne başvurusu değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="63941-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63941-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63941-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="63941-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="63941-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="63941-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63941-106">Required.</span></span> <span data-ttu-id="63941-107">Tüm `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="63941-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="63941-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63941-108">Required.</span></span> <span data-ttu-id="63941-109">Tüm `Object` adı.</span><span class="sxs-lookup"><span data-stu-id="63941-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="63941-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="63941-110">Required.</span></span> <span data-ttu-id="63941-111">Tüm `Object` adı.</span><span class="sxs-lookup"><span data-stu-id="63941-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63941-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63941-112">Remarks</span></span>  
 <span data-ttu-id="63941-113">`Is` İşleci iki nesne başvurusunun aynı nesneye başvuruyorsa, belirler.</span><span class="sxs-lookup"><span data-stu-id="63941-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="63941-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="63941-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="63941-115">Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olduğu `True`; Eğer öyleyse, `result` olduğu `False`.</span><span class="sxs-lookup"><span data-stu-id="63941-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="63941-116">`Is` ile de kullanılabilir `TypeOf` yapmak için anahtar sözcüğü bir `TypeOf`... `Is` ifadesi, bir nesne değişkeninin veri türü ile uyumlu olup olmadığını test eder.</span><span class="sxs-lookup"><span data-stu-id="63941-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63941-117">`Is` Anahtar sözcüğü kullanılan ayrıca [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="63941-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63941-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="63941-118">Example</span></span>  
 <span data-ttu-id="63941-119">Aşağıdaki örnekte `Is` nesne başvuruları çiftlerini karşılaştırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="63941-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="63941-120">Sonuçları atanan bir `Boolean` iki nesnenin aynı olup olmadığını değerini temsil eden.</span><span class="sxs-lookup"><span data-stu-id="63941-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="63941-121">Yukarıdaki örnekte de gösterildiği gibi kullanabileceğiniz `Is` işleci hem de test etmek için erken bağlı ve nesneler'geç bağlama.</span><span class="sxs-lookup"><span data-stu-id="63941-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63941-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63941-122">See also</span></span>
- [<span data-ttu-id="63941-123">TypeOf İşleci</span><span class="sxs-lookup"><span data-stu-id="63941-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="63941-124">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="63941-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="63941-125">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="63941-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="63941-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="63941-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="63941-127">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="63941-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="63941-128">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="63941-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
