---
title: CType İşlevi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: dbf01263723a9e2890dab57d5ffc3d467ed250fc
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212059"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="d0907-102">CType İşlevi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0907-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="d0907-103">Belirtilen veri türü, nesne, yapısı, sınıf veya arabirim için bir ifade açıkça dönüştürülmesinin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0907-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="d0907-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0907-104">Syntax</span></span>

```
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="d0907-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0907-105">Parts</span></span>

<span data-ttu-id="d0907-106">`expression` Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="d0907-106">`expression` Any valid expression.</span></span> <span data-ttu-id="d0907-107">Varsa değerini `expression` tarafından izin verilen aralığın dışında `typename`, Visual Basic bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d0907-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="d0907-108">`typename` Dahilinde geçerli olan herhangi bir ifade bir `As` yan tümcesinde bir `Dim` deyimi, diğer bir deyişle, tüm veri türü, nesne, yapısı, sınıfı veya arabirim adı.</span><span class="sxs-lookup"><span data-stu-id="d0907-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0907-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0907-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="d0907-110">Bir tür dönüştürmesi gerçekleştirmek için aşağıdaki işlevler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d0907-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="d0907-111">Dönüştürme işlevleri gibi yazın `CByte`, `CDbl`, ve `CInt` belirli veri türüne dönüştürme yapan.</span><span class="sxs-lookup"><span data-stu-id="d0907-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="d0907-112">Daha fazla bilgi için [tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d0907-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="d0907-113">[DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d0907-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="d0907-114">Bu işleçler, bir türden devralamaz veya diğer türü uyguluyor gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d0907-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="d0907-115">Biraz daha iyi performans sağlarlar `CType` ve ondan dönüştürme yaparken `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="d0907-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="d0907-116">`CType` Bu da dönüştürme kodunun ifadeyi değerlendiren kodun bir parçası olduğu anlamına gelir derlenmiş satır içidir.</span><span class="sxs-lookup"><span data-stu-id="d0907-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="d0907-117">Bazı durumlarda, dönüştürmeyi gerçekleştirmek için bir yordam çağrılmadığından kod daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="d0907-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="d0907-118">Öğesinden dönüştürme tanımlanmadıysa `expression` için `typename` (örneğin, `Integer` için `Date`), Visual Basic bir derleme zamanı hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d0907-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="d0907-119">Çalışma zamanında bir dönüştürme başarısız olursa uygun özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0907-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="d0907-120">Bir daraltma dönüşümü başarısız olursa bir <xref:System.OverflowException> en yaygın sonuçtur.</span><span class="sxs-lookup"><span data-stu-id="d0907-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="d0907-121">Dönüştürme tanımlanmamışsa, bir <xref:System.InvalidCastException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d0907-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="d0907-122">Örneğin, bu durum meydana gelebilir `expression` türünde `Object` ve onun çalışma zamanı tür dönüştürmesi bulunmadığında `typename`.</span><span class="sxs-lookup"><span data-stu-id="d0907-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="d0907-123">Veri türü `expression` veya `typename` bir sınıf veya yapı tanımladığınız, tanımlayabileceğiniz `CType` sınıf veya yapıda dönüştürme işleci.</span><span class="sxs-lookup"><span data-stu-id="d0907-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="d0907-124">Böylece `CType` işlevi gören bir *işleci aşırı*.</span><span class="sxs-lookup"><span data-stu-id="d0907-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="d0907-125">Bunu yaparsanız, sınıf veya yapı, oluşturulabilecek özel durumlar dahil olmak üzere ve dönüştürmelerin davranışını denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0907-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="d0907-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="d0907-126">Overloading</span></span>

<span data-ttu-id="d0907-127">`CType` İşleci de aşırı yüklenebilir bir sınıf veya yapı, kodunuz dışında tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="d0907-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="d0907-128">Kodunuz için veya bu tür bir sınıf veya yapı dönüştürüldüyse davranışını anladığınızdan emin olun, `CType` işleci.</span><span class="sxs-lookup"><span data-stu-id="d0907-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="d0907-129">Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d0907-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="d0907-130">Dinamik nesneleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d0907-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="d0907-131">Dinamik nesnelerin tür dönüştürmeleri kullanan kullanıcı tanımlı dinamik dönüştürmeler tarafından gerçekleştirilen <xref:System.Dynamic.DynamicObject.TryConvert%2A> veya <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d0907-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="d0907-132">Dinamik nesnelerle çalışıyorsanız kullanın <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> dinamik nesneyi dönüştürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0907-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="d0907-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0907-133">Example</span></span>

<span data-ttu-id="d0907-134">Aşağıdaki örnekte `CType` bir ifadeye dönüştürmek için işlevi `Single` veri türü.</span><span class="sxs-lookup"><span data-stu-id="d0907-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="d0907-135">Diğer örnekler için [örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="d0907-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0907-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0907-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="d0907-137">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d0907-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="d0907-138">Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d0907-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="d0907-139">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="d0907-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="d0907-140">Nasıl yapılır: Bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="d0907-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="d0907-141">.NET Framework'te tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d0907-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
