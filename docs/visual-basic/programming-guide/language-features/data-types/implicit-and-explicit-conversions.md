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
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008264"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="59951-102">Örtük ve Açık Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59951-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="59951-103">Bir *örtük dönüştürme* kaynak kodunda özel bir sözdizimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="59951-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="59951-104">Aşağıdaki örnekte, Visual Basic değeri örtük olarak dönüştürür `k` giderek önce bir tek duyarlıklı kayan nokta değerine `q`.</span><span class="sxs-lookup"><span data-stu-id="59951-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="59951-105">Bir *açık dönüştürme* bir tür dönüştürme anahtar sözcüğünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="59951-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="59951-106">Visual Basic, istenen veri türüne parantez içinde bir ifade coerce birkaç tür anahtar sözcükler sağlar.</span><span class="sxs-lookup"><span data-stu-id="59951-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="59951-107">Bu anahtar sözcükler işlevleri gibi davranır, ancak yürütme bir işlev çağrısıyla biraz daha hızlıdır, bu nedenle, derleyici satır içi kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59951-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="59951-108">Önceki örnekte, aşağıdaki uzantısına `CInt` anahtar sözcüğü değerini dönüştürür `q` geri giderek önce tamsayı `k`.</span><span class="sxs-lookup"><span data-stu-id="59951-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="59951-109">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="59951-109">Conversion Keywords</span></span>  
 <span data-ttu-id="59951-110">Aşağıdaki tabloda kullanılabilir dönüşüm anahtar sözcükleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="59951-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="59951-111">Tür dönüştürme anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="59951-111">Type conversion keyword</span></span>|<span data-ttu-id="59951-112">Bir ifadenin veri türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="59951-112">Converts an expression to data type</span></span>|<span data-ttu-id="59951-113">Dönüştürülecek ifade izin verilen veri türleri</span><span class="sxs-lookup"><span data-stu-id="59951-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="59951-114">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="59951-115">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="59951-116">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="59951-117">Herhangi bir sayısal tür (dahil olmak üzere `SByte` ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="59951-118">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="59951-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="59951-120">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="59951-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="59951-122">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="59951-123">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="59951-124">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="59951-125">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="59951-126">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="59951-127">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="59951-128">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="59951-129">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="59951-130">Object Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="59951-131">Herhangi bir türü</span><span class="sxs-lookup"><span data-stu-id="59951-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="59951-132">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="59951-133">Herhangi bir sayısal tür (dahil olmak üzere `Byte` ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="59951-134">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="59951-135">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="59951-136">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="59951-137">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="59951-138">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="59951-139">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `Char`, `Char` dizi `Date`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="59951-140">Belirtilen tür virgülün (`,`)</span><span class="sxs-lookup"><span data-stu-id="59951-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="59951-141">Dönüştürülürken bir *başlangıç veri türü* (bir basit türü bir dizi dahil), aynı karşılık gelen dönüştürme anahtar sözcüğü için izin verilen türleri</span><span class="sxs-lookup"><span data-stu-id="59951-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="59951-142">Dönüştürülürken bir *bileşik veri türü*, bunu uyguladığı arayüzlerin ve devraldığı sınıfları</span><span class="sxs-lookup"><span data-stu-id="59951-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="59951-143">Bir sınıf veya yapı için üzerinde aşırı dönüştürülürken `CType`, bu sınıf ya da yapı</span><span class="sxs-lookup"><span data-stu-id="59951-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="59951-144">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="59951-145">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="59951-146">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="59951-147">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="59951-148">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="59951-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="59951-149">Herhangi bir sayısal tür (dahil olmak üzere `Byte`, `SByte`ve numaralandırılan türleri), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="59951-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="59951-150">CType işlevi</span><span class="sxs-lookup"><span data-stu-id="59951-150">The CType Function</span></span>  
 <span data-ttu-id="59951-151">[CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) iki bağımsız değişken üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="59951-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="59951-152">Birincisi dönüştürülecek ifade ve hedef veri türü veya nesne sınıfı saniyedir.</span><span class="sxs-lookup"><span data-stu-id="59951-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="59951-153">İlk bağımsız değişkeni bir tür değil bir ifade olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="59951-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="59951-154">`CType` olan bir *satır içi işlev*derlenmiş kodunu anlamı yapar dönüştürme, genellikle bir işlev oluşturmadan çağırın.</span><span class="sxs-lookup"><span data-stu-id="59951-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="59951-155">Bu, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="59951-155">This improves performance.</span></span>  
  
 <span data-ttu-id="59951-156">Bir karşılaştırması `CType` diğer tür dönüşüm anahtar sözcükleri ile bkz: [DirectCast işleci](../../../../visual-basic/language-reference/operators/directcast-operator.md) ve [TryCast işleci](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59951-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="59951-157">Basit türler</span><span class="sxs-lookup"><span data-stu-id="59951-157">Elementary Types</span></span>  
 <span data-ttu-id="59951-158">Aşağıdaki örnek, kullanımını gösterir `CType`.</span><span class="sxs-lookup"><span data-stu-id="59951-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="59951-159">Bileşik türler</span><span class="sxs-lookup"><span data-stu-id="59951-159">Composite Types</span></span>  
 <span data-ttu-id="59951-160">Kullanabileceğiniz `CType` bileşik veri türleri de basit türler için farklı değerler dönüştürmek için.</span><span class="sxs-lookup"><span data-stu-id="59951-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="59951-161">Coerce aşağıdaki örnekteki gibi arabirimlerinden birini türde bir nesne sınıfı için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59951-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="59951-162">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="59951-162">Array Types</span></span>  
 <span data-ttu-id="59951-163">`CType` Aşağıdaki örnekte gösterildiği gibi dizi veri türleri de dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59951-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="59951-164">Daha fazla bilgi ve örnek için bkz. [dizi dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="59951-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="59951-165">CType tanımlama türleri</span><span class="sxs-lookup"><span data-stu-id="59951-165">Types Defining CType</span></span>  
 <span data-ttu-id="59951-166">Tanımlayabileceğiniz `CType` bir sınıf veya yapı tanımladığınız üzerinde.</span><span class="sxs-lookup"><span data-stu-id="59951-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="59951-167">Bu sınıf veya yapı türünü gelen ve değerleri dönüştürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="59951-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="59951-168">Daha fazla bilgi ve örnek için bkz. [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59951-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59951-169">Bir hata meydana gelir veya bir dönüştürme anahtar sözcüğü ile kullanılan değerleri hedef veri türü için geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59951-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="59951-170">Örneğin, dönüştürmeyi denediğinizde bir `Long` için bir `Integer`, değerini `Long` geçerli aralığında olmalıdır `Integer` veri türü.</span><span class="sxs-lookup"><span data-stu-id="59951-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="59951-171">Belirtme `CType` kaynak türü hedef türünden türetilmemiş bir sınıf türünden başka bir başarısız çalışma zamanında için dönüştürülecek.</span><span class="sxs-lookup"><span data-stu-id="59951-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="59951-172">Böyle bir hata oluşturur bir <xref:System.InvalidCastException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="59951-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="59951-173">Ancak, türlerinden bir yapı ya da tanımladığınız sınıf varsa ve tanımladığınız `CType` gereksinimlerini karşılıyorsa, yapı veya sınıf üzerinde bir dönüştürme başarılı olabilmesi için `CType`.</span><span class="sxs-lookup"><span data-stu-id="59951-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="59951-174">Bkz: [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="59951-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="59951-175">Açık bir dönüştürme gerçekleştirmek olan olarak da bilinen *atama* belirtilen veri türü veya nesne sınıfı için bir ifade.</span><span class="sxs-lookup"><span data-stu-id="59951-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59951-176">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59951-176">See also</span></span>

- [<span data-ttu-id="59951-177">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="59951-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="59951-178">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="59951-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="59951-179">Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="59951-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="59951-180">Yapılar</span><span class="sxs-lookup"><span data-stu-id="59951-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="59951-181">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="59951-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="59951-182">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="59951-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="59951-183">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="59951-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
