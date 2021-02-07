---
description: ': CType Işlevi (Visual Basic) hakkında daha fazla bilgi'
title: CType İşlevi
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 9732f52b40e5f762769ba5dc340c000e7e1ba17a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701267"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="b3ea4-103">CType İşlevi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3ea4-103">CType Function (Visual Basic)</span></span>

<span data-ttu-id="b3ea4-104">Bir ifadeyi belirtilen veri türüne, nesneye, yapıya, sınıfa veya arabirime açıkça dönüştürmenin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-104">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="b3ea4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3ea4-105">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="b3ea4-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="b3ea4-106">Parts</span></span>

<span data-ttu-id="b3ea4-107">`expression` Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-107">`expression` Any valid expression.</span></span> <span data-ttu-id="b3ea4-108">Değeri `expression` tarafından izin verilen aralığın dışındaysa `typename` Visual Basic bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-108">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="b3ea4-109">`typename` Deyimdeki bir yan tümce içinde geçerli olan herhangi bir ifade `As` `Dim` , diğer bir deyişle, herhangi bir veri türü, nesne, yapı, sınıf veya arabirimin adı.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-109">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3ea4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3ea4-110">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="b3ea4-111">Bir tür dönüştürmesi gerçekleştirmek için aşağıdaki işlevleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3ea4-111">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="b3ea4-112">`CByte` `CDbl` `CInt` Belirli bir veri türüne dönüştürme gerçekleştiren, ve gibi tür dönüştürme işlevleri.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-112">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="b3ea4-113">Daha fazla bilgi için bkz. [tür dönüştürme işlevleri](type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b3ea4-113">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="b3ea4-114">[DirectCast İşleci](../operators/directcast-operator.md) veya [TryCast İşleci](../operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b3ea4-114">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="b3ea4-115">Bu işleçler, bir türün diğer türden devralmasını veya uygulamayı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-115">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="b3ea4-116">`CType`Veri türüne dönüştürme işleminden daha iyi bir performans sağlayabilir `Object` .</span><span class="sxs-lookup"><span data-stu-id="b3ea4-116">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="b3ea4-117">`CType` satır içi olarak derlenir, bu da dönüştürme kodunun ifadeyi değerlendiren kodun bir parçası olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-117">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="b3ea4-118">Bazı durumlarda, dönüştürme işlemini gerçekleştirmek için hiçbir yordam çağrılmadığından kod daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-118">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="b3ea4-119">' Den `expression` `typename` ' e (örneğin, öğesinden) hiçbir dönüştürme tanımlanmazsa `Integer` `Date` , Visual Basic bir derleme zamanı hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-119">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="b3ea4-120">Çalışma zamanında bir dönüştürme başarısız olursa, uygun özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-120">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="b3ea4-121">Daraltma dönüştürmesi başarısız olursa, <xref:System.OverflowException> en sık görülen sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-121">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="b3ea4-122">Dönüştürme tanımsızdır, bir <xref:System.InvalidCastException> içinde atılır.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-122">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="b3ea4-123">Örneğin, bu durum, `expression` türü ise `Object` ve çalışma zamanı türünün öğesine dönüştürülmesine sahip olması durumunda gerçekleşebilir `typename` .</span><span class="sxs-lookup"><span data-stu-id="b3ea4-123">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="b3ea4-124">Veri türü `expression` veya `typename` tanımladığınız bir sınıf veya yapı ise, `CType` Bu sınıf veya yapı üzerinde bir dönüştürme işleci olarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-124">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="b3ea4-125">Bu, `CType` *aşırı yüklenmiş bir operatör* olarak görev yapar.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-125">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="b3ea4-126">Bunu yaparsanız, oluşturulabilecek özel durumlar da dahil olmak üzere sınıfınıza veya yapınızı dönüştürme davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-126">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="b3ea4-127">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="b3ea4-127">Overloading</span></span>

<span data-ttu-id="b3ea4-128">`CType`İşleci, kodunuzun dışında tanımlanan bir sınıf veya yapı üzerinde de aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-128">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="b3ea4-129">Kodunuz bu tür bir sınıfa veya yapıya dönüştürürse, işlecinin davranışını anladığınızdan emin olun `CType` .</span><span class="sxs-lookup"><span data-stu-id="b3ea4-129">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="b3ea4-130">Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b3ea4-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="b3ea4-131">Dinamik nesneleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b3ea4-131">Converting Dynamic Objects</span></span>

<span data-ttu-id="b3ea4-132">Dinamik nesnelerin tür dönüştürmeleri, veya yöntemlerini kullanan kullanıcı tanımlı dinamik dönüştürmeler tarafından gerçekleştirilir <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> .</span><span class="sxs-lookup"><span data-stu-id="b3ea4-132">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="b3ea4-133">Dinamik nesnelerle çalışıyorsanız, <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> dinamik nesneyi dönüştürmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-133">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="b3ea4-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3ea4-134">Example</span></span>

<span data-ttu-id="b3ea4-135">Aşağıdaki örnek, `CType` bir ifadeyi veri türüne dönüştürmek için işlevini kullanır `Single` .</span><span class="sxs-lookup"><span data-stu-id="b3ea4-135">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="b3ea4-136">Daha fazla örnek için bkz. [örtük ve açık dönüştürmeler](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="b3ea4-136">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3ea4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3ea4-137">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="b3ea4-138">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b3ea4-138">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="b3ea4-139">Dönüşüm İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b3ea4-139">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="b3ea4-140">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3ea4-140">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="b3ea4-141">Nasıl yapılır: Dönüştürme İşleci Tanımlama</span><span class="sxs-lookup"><span data-stu-id="b3ea4-141">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b3ea4-142">.NET Framework'te Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b3ea4-142">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
