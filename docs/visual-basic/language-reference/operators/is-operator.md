---
title: "Is İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="3a543-102">Is İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a543-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="3a543-103">İki nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3a543-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a543-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a543-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="3a543-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="3a543-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="3a543-106">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a543-106">Required.</span></span> <span data-ttu-id="3a543-107">Tüm `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="3a543-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="3a543-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a543-108">Required.</span></span> <span data-ttu-id="3a543-109">Tüm `Object` adı.</span><span class="sxs-lookup"><span data-stu-id="3a543-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="3a543-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3a543-110">Required.</span></span> <span data-ttu-id="3a543-111">Tüm `Object` adı.</span><span class="sxs-lookup"><span data-stu-id="3a543-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a543-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a543-112">Remarks</span></span>  
 <span data-ttu-id="3a543-113">`Is` İşleci belirleyen iki nesne başvuruları aynı nesneye başvuran durumunda.</span><span class="sxs-lookup"><span data-stu-id="3a543-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="3a543-114">Ancak, değer karşılaştırmaları gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="3a543-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="3a543-115">Varsa `object1` ve `object2` hem de tam aynı nesne örneği için bkz `result` olan `True`; yoksa `result` olan `False`.</span><span class="sxs-lookup"><span data-stu-id="3a543-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="3a543-116">`Is`ile de kullanılabilir `TypeOf` yapmak için anahtar sözcüğü bir `TypeOf`... `Is` bir nesne değişkeninin veri türü ile uyumlu olup olmadığını sınar ifadesi,.</span><span class="sxs-lookup"><span data-stu-id="3a543-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a543-117">`Is` Anahtar sözcüğü kullanılan de [seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3a543-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a543-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3a543-118">Example</span></span>  
 <span data-ttu-id="3a543-119">Aşağıdaki örnek kullanır `Is` nesne başvuruları çiftlerini karşılaştırmak için işleci.</span><span class="sxs-lookup"><span data-stu-id="3a543-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="3a543-120">Sonuçları atanan bir `Boolean` iki nesnenin aynı olup olmadığını gösteren değeri.</span><span class="sxs-lookup"><span data-stu-id="3a543-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="3a543-121">Önceki örnekte gösterdiği gibi kullanabileceğiniz `Is` hem de test etmek için işleci erken bağlama ve nesneleri'geç bağlama.</span><span class="sxs-lookup"><span data-stu-id="3a543-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a543-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a543-122">See Also</span></span>  
 [<span data-ttu-id="3a543-123">TypeOf işleci</span><span class="sxs-lookup"><span data-stu-id="3a543-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="3a543-124">IsNot işleci</span><span class="sxs-lookup"><span data-stu-id="3a543-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="3a543-125">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="3a543-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="3a543-126">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="3a543-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="3a543-127">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="3a543-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="3a543-128">İşleçler ve ifadeler</span><span class="sxs-lookup"><span data-stu-id="3a543-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
