---
title: TypeOf İşleci (Visual Basic)
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
ms.openlocfilehash: 7162fcc24595bbb16d268d5d9e1ea4d82f6e67fb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829869"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="e0657-102">TypeOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0657-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="e0657-103">Bir veri türü için bir nesne başvuru değişkenini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="e0657-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0657-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0657-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="e0657-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0657-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e0657-106">Döndürdü.</span><span class="sxs-lookup"><span data-stu-id="e0657-106">Returned.</span></span> <span data-ttu-id="e0657-107">A `Boolean` değeri.</span><span class="sxs-lookup"><span data-stu-id="e0657-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="e0657-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0657-108">Required.</span></span> <span data-ttu-id="e0657-109">Bir başvuru türü için değerlendirilen bir ifade.</span><span class="sxs-lookup"><span data-stu-id="e0657-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="e0657-110">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="e0657-110">Required.</span></span> <span data-ttu-id="e0657-111">Tüm veri türü adı.</span><span class="sxs-lookup"><span data-stu-id="e0657-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0657-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0657-112">Remarks</span></span>  
 <span data-ttu-id="e0657-113">`TypeOf` İşleci belirler çalışma zamanı türü olup olmadığını `objectexpression` uyumludur `typename`.</span><span class="sxs-lookup"><span data-stu-id="e0657-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="e0657-114">Uyumluluk türü kategorisi bağlıdır `typename`.</span><span class="sxs-lookup"><span data-stu-id="e0657-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="e0657-115">Aşağıdaki tabloda, uyumluluk nasıl belirlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0657-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="e0657-116">Tür kategorisi `typename`</span><span class="sxs-lookup"><span data-stu-id="e0657-116">Type category of `typename`</span></span>|<span data-ttu-id="e0657-117">Uyumluluk ölçütü</span><span class="sxs-lookup"><span data-stu-id="e0657-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="e0657-118">örneği</span><span class="sxs-lookup"><span data-stu-id="e0657-118">Class</span></span>|<span data-ttu-id="e0657-119">`objectexpression` tür `typename` veya devralır `typename`</span><span class="sxs-lookup"><span data-stu-id="e0657-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="e0657-120">Yapı</span><span class="sxs-lookup"><span data-stu-id="e0657-120">Structure</span></span>|<span data-ttu-id="e0657-121">`objectexpression` türü `typename`</span><span class="sxs-lookup"><span data-stu-id="e0657-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="e0657-122">Arabirim</span><span class="sxs-lookup"><span data-stu-id="e0657-122">Interface</span></span>|<span data-ttu-id="e0657-123">`objectexpression` uygulayan `typename` veya uygulayan bir sınıftan devraldığı `typename`</span><span class="sxs-lookup"><span data-stu-id="e0657-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="e0657-124">Çalışma zamanı türü `objectexpression` uyumluluk ölçütü karşılayan `result` olduğu `True`.</span><span class="sxs-lookup"><span data-stu-id="e0657-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="e0657-125">Aksi takdirde, `result` olduğu `False`.</span><span class="sxs-lookup"><span data-stu-id="e0657-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="e0657-126">Varsa `objectexpression` null ise `TypeOf`... `Is` döndürür `False`, ve... `IsNot` döndürür `True`.</span><span class="sxs-lookup"><span data-stu-id="e0657-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="e0657-127">`TypeOf` her zaman ile kullanılan `Is` oluşturmak için anahtar sözcüğü bir `TypeOf`... `Is` ifade veya `IsNot` oluşturmak için anahtar sözcüğü bir `TypeOf`... `IsNot` ifade.</span><span class="sxs-lookup"><span data-stu-id="e0657-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0657-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0657-128">Example</span></span>  
 <span data-ttu-id="e0657-129">Aşağıdaki örnekte `TypeOf`... `Is` ifadeler iki tür uyumluluğu test etmek için çeşitli veri türleri ile başvuru değişkenleri nesne.</span><span class="sxs-lookup"><span data-stu-id="e0657-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="e0657-130">Değişken `refInteger` bir çalışma zamanı türü `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e0657-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="e0657-131">İle uyumlu `Integer` bilgisayardı `Double`.</span><span class="sxs-lookup"><span data-stu-id="e0657-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="e0657-132">Değişken `refForm` bir çalışma zamanı türü <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="e0657-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="e0657-133">İle uyumlu <xref:System.Windows.Forms.Form> ile kendi türü olduğu için <xref:System.Windows.Forms.Control> çünkü <xref:System.Windows.Forms.Form> devraldığı <xref:System.Windows.Forms.Control>ile <xref:System.ComponentModel.IComponent> çünkü <xref:System.Windows.Forms.Form> devralan <xref:System.ComponentModel.Component>, uygulayan<xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="e0657-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="e0657-134">Ancak, `refForm` ile uyumlu olmayan <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="e0657-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0657-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0657-135">See also</span></span>

- [<span data-ttu-id="e0657-136">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="e0657-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="e0657-137">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="e0657-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="e0657-138">Visual Basic'de Karşılaştırma işleçleri</span><span class="sxs-lookup"><span data-stu-id="e0657-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="e0657-139">Visual Basic'de İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="e0657-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e0657-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="e0657-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e0657-141">İşleçler ve İfadeler</span><span class="sxs-lookup"><span data-stu-id="e0657-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
