---
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
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350887"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="27a37-102">TypeOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27a37-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="27a37-103">Bir ifadenin sonucunun çalışma zamanı türünün belirtilen türle tür uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="27a37-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="27a37-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27a37-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="27a37-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="27a37-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="27a37-106">Döndürüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="27a37-106">Returned.</span></span> <span data-ttu-id="27a37-107">Bir `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="27a37-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="27a37-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="27a37-108">Required.</span></span> <span data-ttu-id="27a37-109">Bir başvuru türü değerlendirilen herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="27a37-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="27a37-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="27a37-110">Required.</span></span> <span data-ttu-id="27a37-111">Herhangi bir veri türü adı.</span><span class="sxs-lookup"><span data-stu-id="27a37-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27a37-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27a37-112">Remarks</span></span>  
 <span data-ttu-id="27a37-113">`TypeOf` işleci, `objectexpression` çalışma zamanı türünün `typename`uyumlu olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="27a37-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="27a37-114">Uyumluluk `typename`türü kategorisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="27a37-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="27a37-115">Aşağıdaki tabloda uyumluluğun nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="27a37-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="27a37-116">`typename` kategorisi türü</span><span class="sxs-lookup"><span data-stu-id="27a37-116">Type category of `typename`</span></span>|<span data-ttu-id="27a37-117">Uyumluluk ölçütü</span><span class="sxs-lookup"><span data-stu-id="27a37-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="27a37-118">Sınıf</span><span class="sxs-lookup"><span data-stu-id="27a37-118">Class</span></span>|<span data-ttu-id="27a37-119">`objectexpression` `typename` veya `typename` devralınıyor</span><span class="sxs-lookup"><span data-stu-id="27a37-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="27a37-120">Yapı</span><span class="sxs-lookup"><span data-stu-id="27a37-120">Structure</span></span>|<span data-ttu-id="27a37-121">`objectexpression` türü `typename`</span><span class="sxs-lookup"><span data-stu-id="27a37-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="27a37-122">Arabirim</span><span class="sxs-lookup"><span data-stu-id="27a37-122">Interface</span></span>|<span data-ttu-id="27a37-123">`objectexpression`, `typename` uygular veya `typename` uygulayan bir sınıftan devralır</span><span class="sxs-lookup"><span data-stu-id="27a37-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="27a37-124">`objectexpression` çalışma zamanı türü uyumluluk ölçütünü karşılıyorsa `result` `True`.</span><span class="sxs-lookup"><span data-stu-id="27a37-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="27a37-125">Aksi takdirde, `result` `False`.</span><span class="sxs-lookup"><span data-stu-id="27a37-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="27a37-126">`objectexpression` null ise, `TypeOf`...`Is` `False`döndürür ve...`IsNot` `True`döndürür.</span><span class="sxs-lookup"><span data-stu-id="27a37-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="27a37-127">`TypeOf` her zaman bir `TypeOf`...`Is` ifadesi oluşturmak için `Is` anahtar sözcüğüyle veya `IsNot`... `TypeOf`ifadesi oluşturmak için`IsNot` anahtar sözcüğüyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="27a37-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a37-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="27a37-128">Example</span></span>  
 <span data-ttu-id="27a37-129">Aşağıdaki örnek, çeşitli veri türleriyle iki nesne başvuru değişkenlerinin tür uyumluluğunu test etmek için `TypeOf`...`Is` ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="27a37-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="27a37-130">`refInteger` değişken `Integer`çalışma zamanı türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27a37-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="27a37-131">`Integer` ile uyumludur, ancak `Double`değildir.</span><span class="sxs-lookup"><span data-stu-id="27a37-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="27a37-132">`refForm` değişken <xref:System.Windows.Forms.Form>çalışma zamanı türüne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27a37-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="27a37-133"><xref:System.Windows.Forms.Form> ile uyumludur çünkü bu, <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Control>devraldığından ve <xref:System.ComponentModel.IComponent> <xref:System.Windows.Forms.Form> uygulayan <xref:System.ComponentModel.Component>devraldığından <xref:System.ComponentModel.IComponent>ile <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="27a37-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="27a37-134">Ancak, `refForm` <xref:System.Windows.Forms.Label>uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="27a37-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a37-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27a37-135">See also</span></span>

- [<span data-ttu-id="27a37-136">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="27a37-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="27a37-137">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="27a37-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="27a37-138">Visual Basic karşılaştırma Işleçleri</span><span class="sxs-lookup"><span data-stu-id="27a37-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="27a37-139">Visual Basic operatör önceliği</span><span class="sxs-lookup"><span data-stu-id="27a37-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="27a37-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="27a37-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="27a37-141">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="27a37-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
