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
ms.openlocfilehash: 0cce36073b53442bce63f966f3bd94bd5d70d2a8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406333"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="9c0e6-102">TypeOf İşleci (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c0e6-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="9c0e6-103">Bir ifadenin sonucunun çalışma zamanı türünün belirtilen türle tür uyumlu olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="9c0e6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c0e6-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="9c0e6-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="9c0e6-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9c0e6-106">Döndürüldüğünde.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-106">Returned.</span></span> <span data-ttu-id="9c0e6-107">Bir `Boolean` değer.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="9c0e6-108">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-108">Required.</span></span> <span data-ttu-id="9c0e6-109">Bir başvuru türü değerlendirilen herhangi bir ifade.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="9c0e6-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-110">Required.</span></span> <span data-ttu-id="9c0e6-111">Herhangi bir veri türü adı.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c0e6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c0e6-112">Remarks</span></span>  
 <span data-ttu-id="9c0e6-113">`TypeOf`İşleci, çalışma zamanı türünün ile uyumlu olup olmadığını belirler `objectexpression` `typename` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="9c0e6-114">Uyumluluk, öğesinin tür kategorisine bağlıdır `typename` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="9c0e6-115">Aşağıdaki tabloda uyumluluğun nasıl belirlendiği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="9c0e6-116">Tür kategorisi`typename`</span><span class="sxs-lookup"><span data-stu-id="9c0e6-116">Type category of `typename`</span></span>|<span data-ttu-id="9c0e6-117">Uyumluluk ölçütü</span><span class="sxs-lookup"><span data-stu-id="9c0e6-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="9c0e6-118">Sınıf</span><span class="sxs-lookup"><span data-stu-id="9c0e6-118">Class</span></span>|<span data-ttu-id="9c0e6-119">`objectexpression`tür `typename` veya devralınıyor`typename`</span><span class="sxs-lookup"><span data-stu-id="9c0e6-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="9c0e6-120">Yapı</span><span class="sxs-lookup"><span data-stu-id="9c0e6-120">Structure</span></span>|<span data-ttu-id="9c0e6-121">`objectexpression`tür`typename`</span><span class="sxs-lookup"><span data-stu-id="9c0e6-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="9c0e6-122">Arabirim</span><span class="sxs-lookup"><span data-stu-id="9c0e6-122">Interface</span></span>|<span data-ttu-id="9c0e6-123">`objectexpression``typename`uygulayan bir sınıftan uygular veya devralır`typename`</span><span class="sxs-lookup"><span data-stu-id="9c0e6-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="9c0e6-124">Çalışma zamanı türü `objectexpression` Uyumluluk ölçütünü karşılıyorsa,, `result` olur `True` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="9c0e6-125">Aksi halde `result` , `False` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="9c0e6-126">`objectexpression`Null ise... `TypeOf` `Is` döndürüyor `False` , ve... `IsNot` döndürüyor `True` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="9c0e6-127">`TypeOf`her zaman `Is` bir... ifadesi oluşturmak için `TypeOf` `Is` veya bir... `IsNot` ifadesi oluşturmak için anahtar `TypeOf` `IsNot` sözcüğüyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c0e6-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c0e6-128">Example</span></span>  
 <span data-ttu-id="9c0e6-129">Aşağıdaki örnek, `TypeOf` `Is` çeşitli veri türleriyle iki nesne başvuru değişkenlerinin tür uyumluluğunu test etmek için... ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="9c0e6-130">Değişkeninin `refInteger` çalışma zamanı türü vardır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="9c0e6-131">İle uyumludur `Integer` ancak ile uyumlu değildir `Double` .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="9c0e6-132">Değişkeninin `refForm` çalışma zamanı türü vardır <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="9c0e6-133">İle uyumludur çünkü bu, ' <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Control> <xref:System.Windows.Forms.Form> den devraldığından <xref:System.Windows.Forms.Control> ve ' <xref:System.ComponentModel.IComponent> <xref:System.Windows.Forms.Form> <xref:System.ComponentModel.Component> den devraldığından, ' den ' dır <xref:System.ComponentModel.IComponent> .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="9c0e6-134">Ancak, `refForm` ile uyumlu değildir <xref:System.Windows.Forms.Label> .</span><span class="sxs-lookup"><span data-stu-id="9c0e6-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0e6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c0e6-135">See also</span></span>

- [<span data-ttu-id="9c0e6-136">Is İşleci</span><span class="sxs-lookup"><span data-stu-id="9c0e6-136">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="9c0e6-137">IsNot İşleci</span><span class="sxs-lookup"><span data-stu-id="9c0e6-137">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="9c0e6-138">Visual Basic'de Karşılaştırma İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9c0e6-138">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="9c0e6-139">Visual Basic'de İşleç Önceliği</span><span class="sxs-lookup"><span data-stu-id="9c0e6-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="9c0e6-140">İşlevselliğe Göre Listelenmiş İşleçler</span><span class="sxs-lookup"><span data-stu-id="9c0e6-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="9c0e6-141">İşleçler ve Ifadeler</span><span class="sxs-lookup"><span data-stu-id="9c0e6-141">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
