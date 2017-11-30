---
title: "Açık Sayısal Dönüşümler Tablosu (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a366328035b205b93a50ff6d212a06576ee801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="541a9-102">Açık Sayısal Dönüşümler Tablosu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="541a9-102">Explicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="541a9-103">Açık sayısal dönüşüm var olduğu örtük dönüştürme, bir cast ifadesi kullanarak herhangi diğer bir sayısal tür, herhangi bir sayısal tür dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="541a9-103">Explicit numeric conversion is used to convert any numeric type to any other numeric type, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="541a9-104">Aşağıdaki tabloda bu dönüşümleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="541a9-104">The following table shows these conversions.</span></span>  
  
 <span data-ttu-id="541a9-105">Dönüştürme hakkında daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="541a9-105">For more information about conversions, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
|<span data-ttu-id="541a9-106">Başlangıç</span><span class="sxs-lookup"><span data-stu-id="541a9-106">From</span></span>|<span data-ttu-id="541a9-107">Bitiş</span><span class="sxs-lookup"><span data-stu-id="541a9-107">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="541a9-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="541a9-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="541a9-109">`byte`, `ushort`, `uint`, `ulong`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-109">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="541a9-110">bayt</span><span class="sxs-lookup"><span data-stu-id="541a9-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="541a9-111">`Sbyte`veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-111">`Sbyte` or `char`</span></span>|  
|[<span data-ttu-id="541a9-112">kısa</span><span class="sxs-lookup"><span data-stu-id="541a9-112">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="541a9-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="541a9-114">ushort</span><span class="sxs-lookup"><span data-stu-id="541a9-114">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="541a9-115">`sbyte`, `byte`, `short`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-115">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="541a9-116">int</span><span class="sxs-lookup"><span data-stu-id="541a9-116">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="541a9-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="541a9-118">uint</span><span class="sxs-lookup"><span data-stu-id="541a9-118">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="541a9-119">`sbyte`, `byte`, `short`, `ushort`, `int`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-119">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="541a9-120">uzun</span><span class="sxs-lookup"><span data-stu-id="541a9-120">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="541a9-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="541a9-122">ulong</span><span class="sxs-lookup"><span data-stu-id="541a9-122">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="541a9-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, veya`char`</span><span class="sxs-lookup"><span data-stu-id="541a9-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="541a9-124">char</span><span class="sxs-lookup"><span data-stu-id="541a9-124">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="541a9-125">`sbyte`, `byte`, veya`short`</span><span class="sxs-lookup"><span data-stu-id="541a9-125">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="541a9-126">kayan nokta</span><span class="sxs-lookup"><span data-stu-id="541a9-126">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="541a9-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="541a9-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="541a9-128">çift</span><span class="sxs-lookup"><span data-stu-id="541a9-128">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="541a9-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, veya`decimal`</span><span class="sxs-lookup"><span data-stu-id="541a9-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="541a9-130">ondalık</span><span class="sxs-lookup"><span data-stu-id="541a9-130">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="541a9-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, veya`double`</span><span class="sxs-lookup"><span data-stu-id="541a9-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541a9-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="541a9-132">Remarks</span></span>  
  
-   <span data-ttu-id="541a9-133">Açık sayısal dönüşüm oluşturma durumlar duyarlık veya sonuç kaybına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="541a9-133">The explicit numeric conversion may cause loss of precision or result in throwing exceptions.</span></span>  
  
-   <span data-ttu-id="541a9-134">Dönüştürürken bir `decimal` en yakın tam sayı değeri sıfıra doğru tamsayı türü, bu değer değerine yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="541a9-134">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="541a9-135">Sonuçta elde edilen tam sayı değeri hedef türü aralık dışında ise bir <xref:System.OverflowException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="541a9-135">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
-   <span data-ttu-id="541a9-136">Gelen dönüştürürken bir `double` veya `float` tamsayı türü, değerin değerine kısaltılır.</span><span class="sxs-lookup"><span data-stu-id="541a9-136">When you convert from a `double` or `float` value to an integral type, the value is truncated.</span></span> <span data-ttu-id="541a9-137">Sonuç tam sayı değeri hedef değeri aralığın dışında ise, sonuç bağlamını kontrol taşma bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="541a9-137">If the resulting integral value is outside the range of the destination value, the result depends on the overflow checking context.</span></span> <span data-ttu-id="541a9-138">Checked bağlamında bir `OverflowException` olduğu sırada denetlenmeyen bir bağlamda, durum, hedef türü belirtilmeyen bir değeri sonucudur.</span><span class="sxs-lookup"><span data-stu-id="541a9-138">In a checked context, an `OverflowException` is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
-   <span data-ttu-id="541a9-139">Dönüştürürken `double` için `float`, `double` değeri yuvarlanır en yakın `float` değeri.</span><span class="sxs-lookup"><span data-stu-id="541a9-139">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="541a9-140">Varsa `double` değeri çok küçük veya sığması için çok büyük hedef türü sonucu sıfır ya da sonsuz olacaktır.</span><span class="sxs-lookup"><span data-stu-id="541a9-140">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
-   <span data-ttu-id="541a9-141">Dönüştürürken `float` veya `double` için `decimal`, kaynak değerin dönüştürülür `decimal` gösterimi ve gerekirse 28 ondalık basamak sonra en yakın sayıya yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="541a9-141">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="541a9-142">Kaynak değerin değerini bağlı olarak, aşağıdaki sonuçları biriyle karşılaşabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="541a9-142">Depending on the value of the source value, one of the following results may occur:</span></span>  
  
    -   <span data-ttu-id="541a9-143">Kaynak değerin olarak gösterilemeyecek kadar küçük olup olmadığını bir `decimal`, sonuç sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="541a9-143">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  
  
    -   <span data-ttu-id="541a9-144">Kaynak değerin NaN (sayı değil), ise sonsuz, veya olarak gösterilemeyecek kadar çok büyük bir `decimal`, bir `OverflowException` oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="541a9-144">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an `OverflowException` is thrown.</span></span>  
  
-   <span data-ttu-id="541a9-145">Dönüştürürken `decimal` için `float` veya `double`, `decimal` değeri yuvarlanır en yakın `double` veya `float` değeri.</span><span class="sxs-lookup"><span data-stu-id="541a9-145">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="541a9-146">Açık dönüştürme hakkında daha fazla bilgi için C# dil belirtimi Explicit bakın.</span><span class="sxs-lookup"><span data-stu-id="541a9-146">For more information on explicit conversion, see Explicit in the C# Language Specification.</span></span> <span data-ttu-id="541a9-147">Spec erişim hakkında daha fazla bilgi için bkz: [C# dil belirtimi](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="541a9-147">For more information on how to access the spec, see [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541a9-148">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="541a9-148">See Also</span></span>  
 [<span data-ttu-id="541a9-149">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="541a9-149">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="541a9-150">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="541a9-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="541a9-151">Atama ve tür dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="541a9-151">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="541a9-152">() İşleci</span><span class="sxs-lookup"><span data-stu-id="541a9-152">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)  
 [<span data-ttu-id="541a9-153">Tam sayı türleri tablosu</span><span class="sxs-lookup"><span data-stu-id="541a9-153">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="541a9-154">Yerleşik türler tablosu</span><span class="sxs-lookup"><span data-stu-id="541a9-154">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="541a9-155">Örtük sayısal dönüşümler tablosu</span><span class="sxs-lookup"><span data-stu-id="541a9-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
