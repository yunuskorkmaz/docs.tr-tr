---
title: "Örtük ve Açık Dönüştürmeler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e9dd698e1cc84464cd12d33767feec960c511ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="c77bb-102">Örtük ve Açık Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c77bb-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="c77bb-103">Bir *örtük dönüşüm* kaynak kodda özel bir sözdizimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c77bb-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="c77bb-104">Aşağıdaki örnekte, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] örtük olarak değerini dönüştürür `k` atanarak önce bir tek duyarlıklı kayan noktalı değeri `q`.</span><span class="sxs-lookup"><span data-stu-id="c77bb-104">In the following example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="c77bb-105">Bir *açık dönüşüm* bir tür dönüştürme anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="c77bb-105">An *explicit conversion* uses a type conversion keyword.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c77bb-106">İstenen veri türüne parantez içindeki ifadenin coerce birkaç gibi anahtar sözcükler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c77bb-106"> provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="c77bb-107">Bu anahtar sözcükler işlevleri gibi davranır ancak yürütme bir işlev çağrısı ile biraz daha hızlı olacak şekilde kodu satır içi derleyici üretir.</span><span class="sxs-lookup"><span data-stu-id="c77bb-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="c77bb-108">Önceki örnekte, aşağıdaki uzantısına `CInt` anahtar sözcüğü değerine dönüştürür `q` atanarak önce geri tamsayıya `k`.</span><span class="sxs-lookup"><span data-stu-id="c77bb-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="c77bb-109">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-109">Conversion Keywords</span></span>  
 <span data-ttu-id="c77bb-110">Aşağıdaki tabloda kullanılabilir dönüşüm anahtar sözcükleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c77bb-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="c77bb-111">Tür dönüştürme anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="c77bb-111">Type conversion keyword</span></span>|<span data-ttu-id="c77bb-112">Bir ifade veri türüne dönüştürür</span><span class="sxs-lookup"><span data-stu-id="c77bb-112">Converts an expression to data type</span></span>|<span data-ttu-id="c77bb-113">Dönüştürülecek ifade izin verilen veri türleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="c77bb-114">Boole veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="c77bb-115">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="c77bb-116">Byte veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="c77bb-117">Herhangi bir sayısal tür (de dahil olmak üzere `SByte` ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="c77bb-118">Char veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="c77bb-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="c77bb-120">Tarih veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="c77bb-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="c77bb-122">Double veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="c77bb-123">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="c77bb-124">Ondalık veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="c77bb-125">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="c77bb-126">Integer veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="c77bb-127">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="c77bb-128">Long veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="c77bb-129">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="c77bb-130">Nesne veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="c77bb-131">Herhangi bir türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="c77bb-132">SByte veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="c77bb-133">Herhangi bir sayısal tür (de dahil olmak üzere `Byte` ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="c77bb-134">Short veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="c77bb-135">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="c77bb-136">Single veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="c77bb-137">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="c77bb-138">Dize veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="c77bb-139">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `Char`, `Char` diziye `Date`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="c77bb-140">Belirtilen tür virgül aşağıdaki (`,`)</span><span class="sxs-lookup"><span data-stu-id="c77bb-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="c77bb-141">Dönüştürülürken bir *başlangıç veri türü* (bir başlangıç türünde bir dizi dahil), aynı karşılık gelen dönüştürme anahtar sözcüğü için izin verilen olarak türleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="c77bb-142">Dönüştürülürken bir *bileşik veri türü*, bunu uygulayan arabirimleri ve devraldığı sınıfları</span><span class="sxs-lookup"><span data-stu-id="c77bb-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="c77bb-143">Üzerinde aşırı sınıf veya yapı için dönüştürülürken `CType`, bu sınıf veya yapı</span><span class="sxs-lookup"><span data-stu-id="c77bb-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="c77bb-144">Uınteger veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="c77bb-145">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="c77bb-146">ULong veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="c77bb-147">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="c77bb-148">UShort veri türü</span><span class="sxs-lookup"><span data-stu-id="c77bb-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="c77bb-149">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="c77bb-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="c77bb-150">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="c77bb-150">The CType Function</span></span>  
 <span data-ttu-id="c77bb-151">[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) iki bağımsız değişkenler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c77bb-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="c77bb-152">İlk dönüştürülecek ifadesidir ve hedef veri türü veya nesne sınıfı saniyedir.</span><span class="sxs-lookup"><span data-stu-id="c77bb-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="c77bb-153">İlk bağımsız değişkeni bir türde bir ifade olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c77bb-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="c77bb-154">`CType`olan bir *satır içi işlev*derlenmiş kod anlamı dönüştürme yapar, genellikle bir işlev oluşturmadan çağırın.</span><span class="sxs-lookup"><span data-stu-id="c77bb-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="c77bb-155">Bu performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="c77bb-155">This improves performance.</span></span>  
  
 <span data-ttu-id="c77bb-156">Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c77bb-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="c77bb-157">Başlangıç türleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-157">Elementary Types</span></span>  
 <span data-ttu-id="c77bb-158">Aşağıdaki örnek kullanımını gösteren `CType`.</span><span class="sxs-lookup"><span data-stu-id="c77bb-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="c77bb-159">Bileşik türler</span><span class="sxs-lookup"><span data-stu-id="c77bb-159">Composite Types</span></span>  
 <span data-ttu-id="c77bb-160">Kullanabileceğiniz `CType` bileşik veri türleri de başlangıç türleri için farklı değerler dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="c77bb-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="c77bb-161">Aşağıdaki örnekte olduğu gibi arabirimlerinden birini türde bir nesne sınıfının coerce için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c77bb-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="c77bb-162">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-162">Array Types</span></span>  
 <span data-ttu-id="c77bb-163">`CType`Ayrıca aşağıdaki örnekte olduğu gibi dizi veri türleri dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c77bb-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 <span data-ttu-id="c77bb-164">Daha fazla bilgi ve bir örnek için bkz: [dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c77bb-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="c77bb-165">CType tanımlama türleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-165">Types Defining CType</span></span>  
 <span data-ttu-id="c77bb-166">Tanımlayabileceğiniz `CType` bir sınıf veya yapı tanımladığınız.</span><span class="sxs-lookup"><span data-stu-id="c77bb-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="c77bb-167">Bu sınıf veya yapı türü gelen ve giden değerleri dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c77bb-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="c77bb-168">Daha fazla bilgi ve bir örnek için bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c77bb-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c77bb-169">Dönüşüm anahtar sözcüğü ile kullanılan değerleri hedef veri türü için geçerli olmalıdır veya bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="c77bb-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="c77bb-170">Dönüştürme çalışırsanız, örneğin, bir `Long` için bir `Integer`, değeri `Long` için geçerli aralıkta olmalıdır `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="c77bb-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c77bb-171">Belirtme `CType` kaynak türü hedef türünden türetilmemiş varsa bir sınıf türünden çalışma zamanında başka bir başarısız dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="c77bb-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="c77bb-172">Bu tür bir hata oluşturduğunda bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="c77bb-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="c77bb-173">Ancak, türlerinden birini bir yapı veya tanımladığınız sınıfı ise ve tanımladığınız `CType` gereksinimlerini karşılayıp karşılamadığını bu yapısı veya sınıfı, bir dönüştürme başarılı olabilmesi için `CType`.</span><span class="sxs-lookup"><span data-stu-id="c77bb-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="c77bb-174">Bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c77bb-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="c77bb-175">Açık bir dönüştürme gerçekleştirmek olduğu olarak da bilinen *atama* verilen veri türü veya nesne sınıfı için bir ifade.</span><span class="sxs-lookup"><span data-stu-id="c77bb-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77bb-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c77bb-176">See Also</span></span>  
 [<span data-ttu-id="c77bb-177">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="c77bb-178">Dizeler ve diğer türleri arasında dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c77bb-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="c77bb-179">Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür</span><span class="sxs-lookup"><span data-stu-id="c77bb-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="c77bb-180">Yapıları</span><span class="sxs-lookup"><span data-stu-id="c77bb-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="c77bb-181">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="c77bb-182">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="c77bb-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="c77bb-183">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c77bb-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
