---
title: Örtük ve Açık Dönüştürmeler (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 8a0909641b653a1800bdf3f50ec1dfe993411824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656171"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="5e538-102">Örtük ve Açık Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e538-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="5e538-103">Bir *örtük dönüşüm* kaynak kodda özel bir sözdizimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5e538-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="5e538-104">Aşağıdaki örnekte, Visual Basic örtük olarak değerini dönüştürür `k` atanarak önce bir tek duyarlıklı kayan noktalı değeri `q`.</span><span class="sxs-lookup"><span data-stu-id="5e538-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="5e538-105">Bir *açık dönüşüm* bir tür dönüştürme anahtar kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e538-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="5e538-106">Visual Basic istenen veri türüne parantez içindeki ifadenin coerce birkaç gibi anahtar sözcükler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e538-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="5e538-107">Bu anahtar sözcükler işlevleri gibi davranır ancak yürütme bir işlev çağrısı ile biraz daha hızlı olacak şekilde kodu satır içi derleyici üretir.</span><span class="sxs-lookup"><span data-stu-id="5e538-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="5e538-108">Önceki örnekte, aşağıdaki uzantısına `CInt` anahtar sözcüğü değerine dönüştürür `q` atanarak önce geri tamsayıya `k`.</span><span class="sxs-lookup"><span data-stu-id="5e538-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="5e538-109">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5e538-109">Conversion Keywords</span></span>  
 <span data-ttu-id="5e538-110">Aşağıdaki tabloda kullanılabilir dönüşüm anahtar sözcükleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e538-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="5e538-111">Tür dönüştürme anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="5e538-111">Type conversion keyword</span></span>|<span data-ttu-id="5e538-112">Bir ifade veri türüne dönüştürür</span><span class="sxs-lookup"><span data-stu-id="5e538-112">Converts an expression to data type</span></span>|<span data-ttu-id="5e538-113">Dönüştürülecek ifade izin verilen veri türleri</span><span class="sxs-lookup"><span data-stu-id="5e538-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="5e538-114">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="5e538-115">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="5e538-116">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="5e538-117">Herhangi bir sayısal tür (de dahil olmak üzere `SByte` ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="5e538-118">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="5e538-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="5e538-120">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="5e538-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="5e538-122">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="5e538-123">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="5e538-124">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="5e538-125">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="5e538-126">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="5e538-127">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="5e538-128">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="5e538-129">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="5e538-130">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="5e538-131">Herhangi bir türü</span><span class="sxs-lookup"><span data-stu-id="5e538-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="5e538-132">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="5e538-133">Herhangi bir sayısal tür (de dahil olmak üzere `Byte` ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="5e538-134">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="5e538-135">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="5e538-136">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="5e538-137">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="5e538-138">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="5e538-139">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `Char`, `Char` diziye `Date`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="5e538-140">Belirtilen tür virgül aşağıdaki (`,`)</span><span class="sxs-lookup"><span data-stu-id="5e538-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="5e538-141">Dönüştürülürken bir *başlangıç veri türü* (bir başlangıç türünde bir dizi dahil), aynı karşılık gelen dönüştürme anahtar sözcüğü için izin verilen olarak türleri</span><span class="sxs-lookup"><span data-stu-id="5e538-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="5e538-142">Dönüştürülürken bir *bileşik veri türü*, bunu uygulayan arabirimleri ve devraldığı sınıfları</span><span class="sxs-lookup"><span data-stu-id="5e538-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="5e538-143">Üzerinde aşırı sınıf veya yapı için dönüştürülürken `CType`, bu sınıf veya yapı</span><span class="sxs-lookup"><span data-stu-id="5e538-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="5e538-144">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="5e538-145">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="5e538-146">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="5e538-147">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="5e538-148">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="5e538-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="5e538-149">Herhangi bir sayısal tür (de dahil olmak üzere `Byte`, `SByte`ve türleri numaralandırılan), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="5e538-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="5e538-150">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="5e538-150">The CType Function</span></span>  
 <span data-ttu-id="5e538-151">[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) iki bağımsız değişkenler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="5e538-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="5e538-152">İlk dönüştürülecek ifadesidir ve hedef veri türü veya nesne sınıfı saniyedir.</span><span class="sxs-lookup"><span data-stu-id="5e538-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="5e538-153">İlk bağımsız değişkeni bir türde bir ifade olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5e538-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="5e538-154">`CType` olan bir *satır içi işlev*derlenmiş kod anlamı dönüştürme yapar, genellikle bir işlev oluşturmadan çağırın.</span><span class="sxs-lookup"><span data-stu-id="5e538-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="5e538-155">Bu performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="5e538-155">This improves performance.</span></span>  
  
 <span data-ttu-id="5e538-156">Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5e538-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="5e538-157">Başlangıç türleri</span><span class="sxs-lookup"><span data-stu-id="5e538-157">Elementary Types</span></span>  
 <span data-ttu-id="5e538-158">Aşağıdaki örnek kullanımını gösteren `CType`.</span><span class="sxs-lookup"><span data-stu-id="5e538-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="5e538-159">Bileşik türler</span><span class="sxs-lookup"><span data-stu-id="5e538-159">Composite Types</span></span>  
 <span data-ttu-id="5e538-160">Kullanabileceğiniz `CType` bileşik veri türleri de başlangıç türleri için farklı değerler dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="5e538-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="5e538-161">Aşağıdaki örnekte olduğu gibi arabirimlerinden birini türde bir nesne sınıfının coerce için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e538-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="5e538-162">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="5e538-162">Array Types</span></span>  
 <span data-ttu-id="5e538-163">`CType` Ayrıca aşağıdaki örnekte olduğu gibi dizi veri türleri dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e538-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="5e538-164">Daha fazla bilgi ve bir örnek için bkz: [dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="5e538-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="5e538-165">CType tanımlama türleri</span><span class="sxs-lookup"><span data-stu-id="5e538-165">Types Defining CType</span></span>  
 <span data-ttu-id="5e538-166">Tanımlayabileceğiniz `CType` bir sınıf veya yapı tanımladığınız.</span><span class="sxs-lookup"><span data-stu-id="5e538-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="5e538-167">Bu sınıf veya yapı türü gelen ve giden değerleri dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e538-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="5e538-168">Daha fazla bilgi ve bir örnek için bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5e538-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e538-169">Dönüşüm anahtar sözcüğü ile kullanılan değerleri hedef veri türü için geçerli olmalıdır veya bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="5e538-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="5e538-170">Dönüştürme çalışırsanız, örneğin, bir `Long` için bir `Integer`, değeri `Long` için geçerli aralıkta olmalıdır `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="5e538-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="5e538-171">Belirtme `CType` kaynak türü hedef türünden türetilmemiş varsa bir sınıf türünden çalışma zamanında başka bir başarısız dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="5e538-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="5e538-172">Bu tür bir hata oluşturduğunda bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="5e538-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="5e538-173">Ancak, türlerinden birini bir yapı veya tanımladığınız sınıfı ise ve tanımladığınız `CType` gereksinimlerini karşılayıp karşılamadığını bu yapısı veya sınıfı, bir dönüştürme başarılı olabilmesi için `CType`.</span><span class="sxs-lookup"><span data-stu-id="5e538-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="5e538-174">Bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5e538-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="5e538-175">Açık bir dönüştürme gerçekleştirmek olduğu olarak da bilinen *atama* verilen veri türü veya nesne sınıfı için bir ifade.</span><span class="sxs-lookup"><span data-stu-id="5e538-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e538-176">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e538-176">See Also</span></span>  
 [<span data-ttu-id="5e538-177">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="5e538-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="5e538-178">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="5e538-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="5e538-179">Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür</span><span class="sxs-lookup"><span data-stu-id="5e538-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="5e538-180">Yapılar</span><span class="sxs-lookup"><span data-stu-id="5e538-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5e538-181">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="5e538-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="5e538-182">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5e538-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="5e538-183">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="5e538-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
