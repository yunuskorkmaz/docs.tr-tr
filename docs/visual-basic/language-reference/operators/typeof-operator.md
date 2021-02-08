---
description: 'Daha fazla bilgi edinin: TypeOf Işleci (Visual Basic)'
title: TypeOf İşleci
ms.date: 07/20/2015
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
ms.openlocfilehash: 59a03095b2abbaa304221b30402b9a058954db63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795241"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="62348-103">TypeOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62348-103">TypeOf Operator (Visual Basic)</span></span>

<span data-ttu-id="62348-104">Bir ifadenin sonucunun çalışma zamanı türünün belirtilen türle tür uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="62348-104">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="62348-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="62348-105">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="62348-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="62348-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="62348-107">Döndürüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="62348-107">Returned.</span></span> <span data-ttu-id="62348-108">Bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="62348-108">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="62348-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62348-109">Required.</span></span> <span data-ttu-id="62348-110">Bir başvuru türü değerlendirilen herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="62348-110">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="62348-111">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="62348-111">Required.</span></span> <span data-ttu-id="62348-112">Herhangi bir veri türü adı.</span><span class="sxs-lookup"><span data-stu-id="62348-112">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62348-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62348-113">Remarks</span></span>  

 <span data-ttu-id="62348-114">`TypeOf`İşleci, çalışma zamanı türünün ile uyumlu olup olmadığını belirler `objectexpression` `typename` .</span><span class="sxs-lookup"><span data-stu-id="62348-114">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="62348-115">Uyumluluk, öğesinin tür kategorisine bağlıdır `typename` .</span><span class="sxs-lookup"><span data-stu-id="62348-115">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="62348-116">Aşağıdaki tabloda uyumluluğun nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62348-116">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="62348-117">Tür kategorisi `typename`</span><span class="sxs-lookup"><span data-stu-id="62348-117">Type category of `typename`</span></span>|<span data-ttu-id="62348-118">Uyumluluk ölçütü</span><span class="sxs-lookup"><span data-stu-id="62348-118">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="62348-119">Sınıf</span><span class="sxs-lookup"><span data-stu-id="62348-119">Class</span></span>|<span data-ttu-id="62348-120">`objectexpression` tür `typename` veya devralınıyor `typename`</span><span class="sxs-lookup"><span data-stu-id="62348-120">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="62348-121">Yapı</span><span class="sxs-lookup"><span data-stu-id="62348-121">Structure</span></span>|<span data-ttu-id="62348-122">`objectexpression` tür `typename`</span><span class="sxs-lookup"><span data-stu-id="62348-122">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="62348-123">Arabirim</span><span class="sxs-lookup"><span data-stu-id="62348-123">Interface</span></span>|<span data-ttu-id="62348-124">`objectexpression``typename`uygulayan bir sınıftan uygular veya devralır`typename`</span><span class="sxs-lookup"><span data-stu-id="62348-124">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="62348-125">Çalışma zamanı türü `objectexpression` Uyumluluk ölçütünü karşılıyorsa,, `result` olur `True` .</span><span class="sxs-lookup"><span data-stu-id="62348-125">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="62348-126">Aksi halde `result` , `False` .</span><span class="sxs-lookup"><span data-stu-id="62348-126">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="62348-127">`objectexpression`Null ise... `TypeOf` `Is` döndürüyor `False` , ve... `IsNot` döndürüyor `True` .</span><span class="sxs-lookup"><span data-stu-id="62348-127">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="62348-128">`TypeOf` her zaman `Is` bir... ifadesi oluşturmak için `TypeOf` `Is` veya bir... `IsNot` ifadesi oluşturmak için anahtar `TypeOf` `IsNot` sözcüğüyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62348-128">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62348-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="62348-129">Example</span></span>  

 <span data-ttu-id="62348-130">Aşağıdaki örnek, `TypeOf` `Is` çeşitli veri türleriyle iki nesne başvuru değişkenlerinin tür uyumluluğunu test etmek için... ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="62348-130">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="62348-131">Değişkeninin `refInteger` çalışma zamanı türü vardır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="62348-131">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="62348-132">İle uyumludur `Integer` ancak ile uyumlu değildir `Double` .</span><span class="sxs-lookup"><span data-stu-id="62348-132">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="62348-133">Değişkeninin `refForm` çalışma zamanı türü vardır <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="62348-133">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="62348-134">İle uyumludur çünkü bu, ' <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Form> den devraldığından <xref:System.Windows.Forms.Control> ve ' <xref:System.ComponentModel.IComponent> <xref:System.Windows.Forms.Form> <xref:System.ComponentModel.Component> den devraldığından, ' den ' dır <xref:System.ComponentModel.IComponent> .</span><span class="sxs-lookup"><span data-stu-id="62348-134">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="62348-135">Ancak, `refForm` ile uyumlu değildir <xref:System.Windows.Forms.Label> .</span><span class="sxs-lookup"><span data-stu-id="62348-135">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62348-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62348-136">See also</span></span>

- [<span data-ttu-id="62348-137">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="62348-137">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="62348-138">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="62348-138">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="62348-139">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="62348-139">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="62348-140">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="62348-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="62348-141">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="62348-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="62348-142">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="62348-142">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
