---
description: 'Daha fazla bilgi edinin: örtük ve açık dönüştürmeler (Visual Basic)'
title: Örtük ve Açık Dönüştürmeler
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
ms.openlocfilehash: 6a53c0998025cc8c19274c67d9dfe1c50a4f1373
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483956"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="95892-103">Örtük ve Açık Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95892-103">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="95892-104">*Örtük dönüştürme* , kaynak kodunda özel bir sözdizimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="95892-104">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="95892-105">Aşağıdaki örnekte, Visual Basic değerini ' a atamadan önce, değeri örtük olarak `k` tek duyarlıklı kayan noktalı değere dönüştürür `q` .</span><span class="sxs-lookup"><span data-stu-id="95892-105">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="95892-106">*Açık dönüştürme* bir tür dönüştürme anahtar sözcüğü kullanır.</span><span class="sxs-lookup"><span data-stu-id="95892-106">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="95892-107">Visual Basic, parantez içindeki bir ifadeyi istenen veri türüne döndüren birkaç anahtar sözcük sağlar.</span><span class="sxs-lookup"><span data-stu-id="95892-107">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="95892-108">Bu anahtar sözcükler işlevler gibi davranır ancak derleyici, kodu satır içi olarak oluşturur, böylece yürütme bir işlev çağrısıyla biraz daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="95892-108">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="95892-109">Önceki örneğin aşağıdaki uzantısında, `CInt` anahtar sözcüğü `q` öğesine atamadan önce değeri bir tamsayıya dönüştürür `k` .</span><span class="sxs-lookup"><span data-stu-id="95892-109">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="95892-110">Dönüşüm Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95892-110">Conversion Keywords</span></span>

<span data-ttu-id="95892-111">Aşağıdaki tabloda kullanılabilir dönüştürme anahtar sözcükleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="95892-111">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="95892-112">Tür dönüştürme anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="95892-112">Type conversion keyword</span></span>|<span data-ttu-id="95892-113">Bir ifadeyi veri türüne dönüştürür</span><span class="sxs-lookup"><span data-stu-id="95892-113">Converts an expression to data type</span></span>|<span data-ttu-id="95892-114">Dönüştürülecek ifadenin izin verilen veri türleri</span><span class="sxs-lookup"><span data-stu-id="95892-114">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="95892-115">Boolean Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-115">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="95892-116">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-116">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="95892-117">Byte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-117">Byte Data Type</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="95892-118">Herhangi bir sayısal tür ( `SByte` ve numaralandırılmış türler dahil),, `Boolean` `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-118">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="95892-119">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-119">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="95892-120">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-120">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="95892-121">Date Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-121">Date Data Type</span></span>](../../../language-reference/data-types/date-data-type.md)|<span data-ttu-id="95892-122">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-122">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="95892-123">Double Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-123">Double Data Type</span></span>](../../../language-reference/data-types/double-data-type.md)|<span data-ttu-id="95892-124">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-124">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="95892-125">Decimal Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-125">Decimal Data Type</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="95892-126">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-126">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="95892-127">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="95892-128">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-128">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="95892-129">Long Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-129">Long Data Type</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="95892-130">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-130">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="95892-131">Nesne Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-131">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)|<span data-ttu-id="95892-132">Herhangi bir tür</span><span class="sxs-lookup"><span data-stu-id="95892-132">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="95892-133">SByte Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-133">SByte Data Type</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="95892-134">Herhangi bir sayısal tür ( `Byte` ve numaralandırılmış türler dahil),, `Boolean` `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-134">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="95892-135">Short Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-135">Short Data Type</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="95892-136">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-136">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="95892-137">Single Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-137">Single Data Type</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="95892-138">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-138">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="95892-139">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-139">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)|<span data-ttu-id="95892-140">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `Char` , `Char` dizi, `Date` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-140">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="95892-141">Virgül () sonrasında belirtilen tür `,`</span><span class="sxs-lookup"><span data-stu-id="95892-141">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="95892-142">Bir *Öğesel veri türüne* dönüştürme sırasında (bir öğesel türün dizisi dahil), karşılık gelen dönüştürme anahtar sözcüğü için izin verilen türler</span><span class="sxs-lookup"><span data-stu-id="95892-142">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="95892-143">*Bileşik veri türüne* dönüştürme yaparken, uyguladığı arabirimler ve devraldığı sınıflar</span><span class="sxs-lookup"><span data-stu-id="95892-143">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="95892-144">Daha fazla yüklü olan bir sınıfa veya yapıya dönüştürme sırasında `CType` , bu sınıf veya yapı</span><span class="sxs-lookup"><span data-stu-id="95892-144">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="95892-145">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-145">UInteger Data Type</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="95892-146">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-146">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="95892-147">ULong Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-147">ULong Data Type</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="95892-148">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-148">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="95892-149">UShort Veri Türü</span><span class="sxs-lookup"><span data-stu-id="95892-149">UShort Data Type</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="95892-150">Herhangi bir sayısal tür ( `Byte` , `SByte` ve numaralandırılmış türler dahil), `Boolean` , `String` , `Object`</span><span class="sxs-lookup"><span data-stu-id="95892-150">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="95892-151">CType Işlevi</span><span class="sxs-lookup"><span data-stu-id="95892-151">The CType Function</span></span>

<span data-ttu-id="95892-152">[CType işlevi](../../../language-reference/functions/ctype-function.md) iki bağımsız değişken üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="95892-152">The [CType Function](../../../language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="95892-153">İlki dönüştürülecek ifade, ikincisi ise hedef veri türü veya nesne sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="95892-153">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="95892-154">İlk bağımsız değişkenin bir tür değil bir ifade olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="95892-154">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="95892-155">`CType` , bir *satır içi işlevdir*, yani derlenmiş kod, genellikle bir işlev çağrısı oluşturmadan dönüştürmeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="95892-155">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="95892-156">Bu, performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="95892-156">This improves performance.</span></span>

<span data-ttu-id="95892-157">`CType`Diğer tür dönüştürme anahtar sözcükleriyle bir karşılaştırması için bkz. [DirectCast Işleci](../../../language-reference/operators/directcast-operator.md) ve [TryCast İşleci](../../../language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="95892-157">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="95892-158">Elemensel türler</span><span class="sxs-lookup"><span data-stu-id="95892-158">Elementary Types</span></span>

<span data-ttu-id="95892-159">Aşağıdaki örnek öğesinin kullanımını gösterir `CType` .</span><span class="sxs-lookup"><span data-stu-id="95892-159">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="95892-160">Bileşik türler</span><span class="sxs-lookup"><span data-stu-id="95892-160">Composite Types</span></span>

<span data-ttu-id="95892-161">`CType`Değerleri bileşik veri türlerine ve öğesel türlere dönüştürmek için ' i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95892-161">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="95892-162">Ayrıca, aşağıdaki örnekte olduğu gibi, bir nesne sınıfını arabirimlerinden biri türüne zorlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95892-162">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="95892-163">Dizi türleri</span><span class="sxs-lookup"><span data-stu-id="95892-163">Array Types</span></span>

<span data-ttu-id="95892-164">`CType` , aşağıdaki örnekte olduğu gibi dizi veri türlerini de dönüştürebilir.</span><span class="sxs-lookup"><span data-stu-id="95892-164">`CType` can also convert array data types, as in the following example.</span></span>

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

<span data-ttu-id="95892-165">Daha fazla bilgi ve bir örnek için bkz. [dizi dönüştürmeleri](array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="95892-165">For more information and an example, see [Array Conversions](array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="95892-166">CType tanımlayan türler</span><span class="sxs-lookup"><span data-stu-id="95892-166">Types Defining CType</span></span>

<span data-ttu-id="95892-167">`CType`Tanımladığınız bir sınıf veya yapı üzerinde tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95892-167">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="95892-168">Bu, değerleri sınıfınızın veya yapınızın türüne ve türünden dönüştürmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="95892-168">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="95892-169">Daha fazla bilgi ve bir örnek için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="95892-169">For more information and an example, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="95892-170">Bir dönüştürme anahtar sözcüğüyle kullanılan değerlerin hedef veri türü için geçerli olması gerekir veya bir hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="95892-170">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="95892-171">Örneğin, bir ' a dönüştürmeye çalışırsanız, `Long` `Integer` değeri `Long` veri türü için geçerli aralık dahilinde olmalıdır `Integer` .</span><span class="sxs-lookup"><span data-stu-id="95892-171">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="95892-172">`CType`Kaynak türü hedef türünden türemezse, çalışma zamanında bir sınıf türünden diğerine dönüştürme yapmak için belirtme.</span><span class="sxs-lookup"><span data-stu-id="95892-172">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="95892-173">Bu tür bir hata <xref:System.InvalidCastException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95892-173">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="95892-174">Ancak, türlerden biri tanımladığınız bir yapı veya sınıf ise ve `CType` Bu yapıda veya sınıfta tanımladıysanız, bir dönüştürme işlemi, gereksinimlerinizi karşılıyorsa başarılı olabilir `CType` .</span><span class="sxs-lookup"><span data-stu-id="95892-174">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="95892-175">Bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="95892-175">See [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="95892-176">Açık bir dönüştürme gerçekleştirmek, belirli bir veri türüne veya nesne sınıfına bir ifade *atama* olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="95892-176">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="95892-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95892-177">See also</span></span>

- [<span data-ttu-id="95892-178">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="95892-178">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="95892-179">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="95892-179">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="95892-180">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="95892-180">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="95892-181">Yapılar</span><span class="sxs-lookup"><span data-stu-id="95892-181">Structures</span></span>](structures.md)
- [<span data-ttu-id="95892-182">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="95892-182">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="95892-183">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="95892-183">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="95892-184">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="95892-184">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
