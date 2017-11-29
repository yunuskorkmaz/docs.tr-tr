---
title: "CType İşlevi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6118ca5f73a0d446842c33859e0623032082bcd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="93edd-102">CType İşlevi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93edd-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="93edd-103">Belirtilen veri türü, nesne, yapısı, sınıf veya arabirim için açıkça bir ifade dönüştürmenin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="93edd-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93edd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93edd-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="93edd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="93edd-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="93edd-106">Herhangi bir geçerli ifade.</span><span class="sxs-lookup"><span data-stu-id="93edd-106">Any valid expression.</span></span> <span data-ttu-id="93edd-107">Varsa değerini `expression` tarafından izin verilen aralığın dışında `typename`, Visual Basic bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="93edd-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="93edd-108">Yasal içinde herhangi bir ifade bir `As` yan tümcesinde bir `Dim` deyimi, diğer bir deyişle, tüm veri türü, nesne, yapısı, sınıf veya arabirimi adı.</span><span class="sxs-lookup"><span data-stu-id="93edd-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93edd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="93edd-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="93edd-110">Tür dönüştürme gerçekleştirmek için aşağıdaki işlevler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="93edd-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="93edd-111">Dönüşüm işlevleri gibi yazın `CByte`, `CDbl`, ve `CInt` belirli bir veri türüne dönüştürme gerçekleştirin.</span><span class="sxs-lookup"><span data-stu-id="93edd-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="93edd-112">Daha fazla bilgi için bkz: [tür dönüştürme işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="93edd-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="93edd-113">[DirectCast işleci](../../../visual-basic/language-reference/operators/directcast-operator.md) veya [TryCast işleci](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="93edd-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="93edd-114">Bu işleçlere bir tür devralınmalıdır veya diğer tür gerektirir.</span><span class="sxs-lookup"><span data-stu-id="93edd-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="93edd-115">Değerinden biraz daha iyi performans sağlayabilirsiniz `CType` ve ondan dönüştürülürken `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="93edd-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="93edd-116">`CType`dönüştürme kodu ifadeyi hesaplar kodun bir parçası olduğu anlamına gelir derlenmiş satır içi olur.</span><span class="sxs-lookup"><span data-stu-id="93edd-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="93edd-117">Dönüştürme gerçekleştirmek için hiçbir yordam adlı çünkü bazı durumlarda, kodu daha hızlı çalışır.</span><span class="sxs-lookup"><span data-stu-id="93edd-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="93edd-118">Hiçbir dönüştürme tanımlanmış olması durumunda `expression` için `typename` (örneğin, `Integer` için `Date`), Visual Basic derleme zamanı hata iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93edd-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="93edd-119">Çalışma zamanında bir dönüştürme başarısız olursa, uygun özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="93edd-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="93edd-120">Daraltma dönüştürme başarısız olursa, bir <xref:System.OverflowException> en yaygın sonucudur.</span><span class="sxs-lookup"><span data-stu-id="93edd-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="93edd-121">Dönüştürme tanımsızsa bir <xref:System.InvalidCastException> içinde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="93edd-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="93edd-122">Örneğin, bu durum `expression` türü `Object` ve çalışma zamanı türü için dönüştürme `typename`.</span><span class="sxs-lookup"><span data-stu-id="93edd-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="93edd-123">Veri türü `expression` veya `typename` bir sınıf ya da tanımladığınız, yapısı, tanımlayabilirsiniz `CType` sınıf veya yapı bir dönüşüm işleci olarak.</span><span class="sxs-lookup"><span data-stu-id="93edd-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="93edd-124">Böylece `CType` gibi davranan bir *işleci aşırı*.</span><span class="sxs-lookup"><span data-stu-id="93edd-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="93edd-125">Bunu yaparsanız, sınıf veya yapı atılabilen özel durumlar dahil olmak üzere, gelen ve dönüşümler davranışını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93edd-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="93edd-126">Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="93edd-126">Overloading</span></span>  
 <span data-ttu-id="93edd-127">`CType` İşleci ayrıca aşırı yüklenebilir bir sınıf veya kodunuzu dışında tanımlanmış yapısı.</span><span class="sxs-lookup"><span data-stu-id="93edd-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="93edd-128">Kodunuz için veya böyle bir sınıf veya yapı dönüştürür, davranışını anladığınızdan emin olun, `CType` işleci.</span><span class="sxs-lookup"><span data-stu-id="93edd-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="93edd-129">Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="93edd-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="93edd-130">Dinamik nesneler dönüştürme</span><span class="sxs-lookup"><span data-stu-id="93edd-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="93edd-131">Tür dönüştürmeleri dinamik nesnelerin kullanan kullanıcı tanımlı dinamik dönüşümler tarafından gerçekleştirilen <xref:System.Dynamic.DynamicObject.TryConvert%2A> veya <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="93edd-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="93edd-132">Dinamik nesnelerle çalışıyorsanız kullanmak <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> dinamik Nesne dönüştürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="93edd-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93edd-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="93edd-133">Example</span></span>  
 <span data-ttu-id="93edd-134">Aşağıdaki örnek kullanır `CType` bir ifadeyi dönüştürmek için işlevi `Single` veri türü.</span><span class="sxs-lookup"><span data-stu-id="93edd-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 <span data-ttu-id="93edd-135">Ek örnekler için bkz: [dolaylı ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="93edd-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93edd-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="93edd-136">See Also</span></span>  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="93edd-137">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="93edd-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="93edd-138">Dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="93edd-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="93edd-139">Operator deyimi</span><span class="sxs-lookup"><span data-stu-id="93edd-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="93edd-140">Nasıl yapılır: bir dönüşüm işleci tanımlama</span><span class="sxs-lookup"><span data-stu-id="93edd-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="93edd-141">.NET Framework'te tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="93edd-141">Type Conversion in the .NET Framework</span></span>](http://msdn.microsoft.com/library/ba36154f-064c-47d3-9f05-72f93a7ca96d)
