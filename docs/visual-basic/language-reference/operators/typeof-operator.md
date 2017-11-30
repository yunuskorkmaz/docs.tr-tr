---
title: "TypeOf İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="d9a6c-102">TypeOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9a6c-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="d9a6c-103">Bir veri türü için bir nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9a6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9a6c-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="d9a6c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d9a6c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d9a6c-106">Döndürdü.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-106">Returned.</span></span> <span data-ttu-id="d9a6c-107">A `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="d9a6c-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-108">Required.</span></span> <span data-ttu-id="d9a6c-109">Bir başvuru türü değerlendirir herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="d9a6c-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-110">Required.</span></span> <span data-ttu-id="d9a6c-111">Tüm veri türü adı.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9a6c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9a6c-112">Remarks</span></span>  
 <span data-ttu-id="d9a6c-113">`TypeOf` İşleci belirler çalışma zamanı türü olup olmadığını `objectexpression` ile uyumlu `typename`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="d9a6c-114">Uyumluluk ve türü kategorisine göre değişir `typename`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="d9a6c-115">Aşağıdaki tabloda, uyumluluk nasıl belirlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="d9a6c-116">Türü kategorisi`typename`</span><span class="sxs-lookup"><span data-stu-id="d9a6c-116">Type category of `typename`</span></span>|<span data-ttu-id="d9a6c-117">Uyumluluk ölçütü</span><span class="sxs-lookup"><span data-stu-id="d9a6c-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="d9a6c-118">örneği</span><span class="sxs-lookup"><span data-stu-id="d9a6c-118">Class</span></span>|<span data-ttu-id="d9a6c-119">`objectexpression`tür `typename` veya devralır`typename`</span><span class="sxs-lookup"><span data-stu-id="d9a6c-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="d9a6c-120">Yapı</span><span class="sxs-lookup"><span data-stu-id="d9a6c-120">Structure</span></span>|<span data-ttu-id="d9a6c-121">`objectexpression`türü`typename`</span><span class="sxs-lookup"><span data-stu-id="d9a6c-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="d9a6c-122">Arabirim</span><span class="sxs-lookup"><span data-stu-id="d9a6c-122">Interface</span></span>|<span data-ttu-id="d9a6c-123">`objectexpression`uygulayan `typename` veya uygulayan bir sınıftan`typename`</span><span class="sxs-lookup"><span data-stu-id="d9a6c-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="d9a6c-124">Çalışma zamanı türü `objectexpression` uyumluluk ölçütü karşılayan `result` olan `True`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="d9a6c-125">Aksi takdirde, `result` olan `False`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="d9a6c-126">Varsa `objectexpression` null ise `TypeOf`... `Is` döndürür `False`, ve... `IsNot` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="d9a6c-127">`TypeOf`her zaman kullanılması `Is` oluşturmak için anahtar sözcüğü bir `TypeOf`... `Is` ifadesi veya ile `IsNot` oluşturmak için anahtar sözcüğü bir `TypeOf`... `IsNot` ifade.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9a6c-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9a6c-128">Example</span></span>  
 <span data-ttu-id="d9a6c-129">Aşağıdaki örnek kullanır `TypeOf`... `Is` iki tür uyumluluğunu test etmek için ifadeleri nesne başvuru değişkenini çeşitli veri türlerine sahip.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 <span data-ttu-id="d9a6c-130">Değişkeni `refInteger` bir çalışma zamanı türü `Integer`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="d9a6c-131">İle uyumlu `Integer` bilgisayardı `Double`.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="d9a6c-132">Değişkeni `refForm` bir çalışma zamanı türü <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="d9a6c-133">İle uyumlu <xref:System.Windows.Forms.Form> , kendi türü ile olduğundan <xref:System.Windows.Forms.Control> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.Windows.Forms.Control>ile <xref:System.ComponentModel.IComponent> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.ComponentModel.Component>, uygulayan<xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="d9a6c-134">Ancak, `refForm` ile uyumlu olmayan <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9a6c-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9a6c-135">See Also</span></span>  
 [<span data-ttu-id="d9a6c-136">Is işleci</span><span class="sxs-lookup"><span data-stu-id="d9a6c-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="d9a6c-137">IsNot işleci</span><span class="sxs-lookup"><span data-stu-id="d9a6c-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="d9a6c-138">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="d9a6c-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="d9a6c-139">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="d9a6c-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d9a6c-140">İşlevselliğe göre listelenmiş işleçler</span><span class="sxs-lookup"><span data-stu-id="d9a6c-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d9a6c-141">İşleçler ve ifadeler</span><span class="sxs-lookup"><span data-stu-id="d9a6c-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
