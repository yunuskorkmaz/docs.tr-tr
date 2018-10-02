---
title: Biçimlendirme sayısal sonuçlar tablosunu (C# Başvurusu)
description: C# standart sayısal biçim dizeleri hakkında bilgi edinin
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 6f1cb5b49139cf9661e678cfc0ecc884a2749622
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863708"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="33a97-103">Biçimlendirme sayısal sonuçlar tablosunu (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="33a97-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="33a97-104">Aşağıdaki tablo, sayısal sonuçlarını biçimlendirme için desteklenen biçim belirticileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="33a97-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="33a97-105">Biçimlendirilmiş sonuç son sütunda "en-US" karşılık gelen <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="33a97-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="33a97-106">Biçim belirteci</span><span class="sxs-lookup"><span data-stu-id="33a97-106">Format specifier</span></span>|<span data-ttu-id="33a97-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33a97-107">Description</span></span>|<span data-ttu-id="33a97-108">Örnekler</span><span class="sxs-lookup"><span data-stu-id="33a97-108">Examples</span></span>|<span data-ttu-id="33a97-109">Sonuç</span><span class="sxs-lookup"><span data-stu-id="33a97-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="33a97-110">C ya da c</span><span class="sxs-lookup"><span data-stu-id="33a97-110">C or c</span></span>|<span data-ttu-id="33a97-111">Para Birimi</span><span class="sxs-lookup"><span data-stu-id="33a97-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="33a97-112">$2.50</span><span class="sxs-lookup"><span data-stu-id="33a97-112">$2.50</span></span><br /><br /> <span data-ttu-id="33a97-113">($2.50)</span><span class="sxs-lookup"><span data-stu-id="33a97-113">($2.50)</span></span>|  
|<span data-ttu-id="33a97-114">D veya d</span><span class="sxs-lookup"><span data-stu-id="33a97-114">D or d</span></span>|<span data-ttu-id="33a97-115">Ondalık</span><span class="sxs-lookup"><span data-stu-id="33a97-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="33a97-116">00025</span><span class="sxs-lookup"><span data-stu-id="33a97-116">00025</span></span>|  
|<span data-ttu-id="33a97-117">E veya e</span><span class="sxs-lookup"><span data-stu-id="33a97-117">E or e</span></span>|<span data-ttu-id="33a97-118">Üstel</span><span class="sxs-lookup"><span data-stu-id="33a97-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="33a97-119">2.50E + 005</span><span class="sxs-lookup"><span data-stu-id="33a97-119">2.50E+005</span></span>|  
|<span data-ttu-id="33a97-120">F veya f</span><span class="sxs-lookup"><span data-stu-id="33a97-120">F or f</span></span>|<span data-ttu-id="33a97-121">Sabit nokta</span><span class="sxs-lookup"><span data-stu-id="33a97-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="33a97-122">2.50</span><span class="sxs-lookup"><span data-stu-id="33a97-122">2.50</span></span><br /><br /> <span data-ttu-id="33a97-123">3</span><span class="sxs-lookup"><span data-stu-id="33a97-123">3</span></span>|  
|<span data-ttu-id="33a97-124">G veya g</span><span class="sxs-lookup"><span data-stu-id="33a97-124">G or g</span></span>|<span data-ttu-id="33a97-125">Genel</span><span class="sxs-lookup"><span data-stu-id="33a97-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="33a97-126">2,5</span><span class="sxs-lookup"><span data-stu-id="33a97-126">2.5</span></span>|  
|<span data-ttu-id="33a97-127">N veya n</span><span class="sxs-lookup"><span data-stu-id="33a97-127">N or n</span></span>|<span data-ttu-id="33a97-128">Sayısal</span><span class="sxs-lookup"><span data-stu-id="33a97-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="33a97-129">2,500,000.00</span><span class="sxs-lookup"><span data-stu-id="33a97-129">2,500,000.00</span></span>|  
|<span data-ttu-id="33a97-130">P ya da p</span><span class="sxs-lookup"><span data-stu-id="33a97-130">P or p</span></span>|<span data-ttu-id="33a97-131">Yüzde</span><span class="sxs-lookup"><span data-stu-id="33a97-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="33a97-132">%25.00</span><span class="sxs-lookup"><span data-stu-id="33a97-132">25.00%</span></span>|  
|<span data-ttu-id="33a97-133">R veya r</span><span class="sxs-lookup"><span data-stu-id="33a97-133">R or r</span></span>|<span data-ttu-id="33a97-134">Gidiş</span><span class="sxs-lookup"><span data-stu-id="33a97-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="33a97-135">2,5</span><span class="sxs-lookup"><span data-stu-id="33a97-135">2.5</span></span>|  
|<span data-ttu-id="33a97-136">X ya da x</span><span class="sxs-lookup"><span data-stu-id="33a97-136">X or x</span></span>|<span data-ttu-id="33a97-137">Onaltılık</span><span class="sxs-lookup"><span data-stu-id="33a97-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="33a97-138">FA</span><span class="sxs-lookup"><span data-stu-id="33a97-138">FA</span></span><br /><br /> <span data-ttu-id="33a97-139">FFFF</span><span class="sxs-lookup"><span data-stu-id="33a97-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="33a97-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33a97-140">Remarks</span></span>

<span data-ttu-id="33a97-141">Bir biçim belirticisi bir biçim dizesi oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="33a97-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="33a97-142">Biçim dizesi aşağıdaki şekildedir: `Axx`burada</span><span class="sxs-lookup"><span data-stu-id="33a97-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="33a97-143">`A` Biçimlendirme sayısal değere uygulanmış türünü denetleyen biçim belirticisi ' dir.</span><span class="sxs-lookup"><span data-stu-id="33a97-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="33a97-144">`xx` biçimlendirilmiş çıktı basamak sayısını etkiler. duyarlık belirticisi ' dir.</span><span class="sxs-lookup"><span data-stu-id="33a97-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="33a97-145">Duyarlık belirticisi aralıkları 0 ile 99 değeri.</span><span class="sxs-lookup"><span data-stu-id="33a97-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="33a97-146">Ondalık ("D" veya "d") ve ("X" veya "x") onaltılı biçim belirticileri yalnızca integral türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="33a97-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="33a97-147">Gidiş dönüş ("R" veya "r") biçim tanımlayıcısı sadece desteklenen <xref:System.Single>, <xref:System.Double>, ve <xref:System.Numerics.BigInteger> türleri.</span><span class="sxs-lookup"><span data-stu-id="33a97-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="33a97-148">Standart sayısal biçim dizeleri tarafından desteklenir:</span><span class="sxs-lookup"><span data-stu-id="33a97-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="33a97-149">Bazı aşırı yüklemeleri `ToString` tüm sayısal türlerin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="33a97-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="33a97-150">Örneğin, bir sayısal biçim dizesi sağlayabilirsiniz <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="33a97-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="33a97-151">.NET [bileşik biçimlendirme özelliği](../../../standard/base-types/composite-formatting.md), tarafından desteklenen <xref:System.String.Format%2A?displayProperty=nameWithType> örneğin bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="33a97-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="33a97-152">[İlişkilendirilmiş dizeler](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="33a97-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="33a97-153">Daha fazla bilgi için [standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="33a97-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33a97-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33a97-154">See also</span></span>

- [<span data-ttu-id="33a97-155">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="33a97-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="33a97-156">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="33a97-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="33a97-157">Türler için başvuru tabloları</span><span class="sxs-lookup"><span data-stu-id="33a97-157">Reference tables for types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="33a97-158">Biçimlendirme türleri</span><span class="sxs-lookup"><span data-stu-id="33a97-158">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="33a97-159">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="33a97-159">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="33a97-160">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="33a97-160">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="33a97-161">string</span><span class="sxs-lookup"><span data-stu-id="33a97-161">string</span></span>](string.md)
