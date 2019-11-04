---
title: Sayısal sonuçlar tablosunu biçimlendirme- C# başvuru
ms.custom: seodec18
description: Standart sayısal C# biçim dizeleri hakkında bilgi edinin
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 2cba5e704787ae6368b2543c985babf2fde3b4dd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422749"
---
# <a name="formatting-numeric-results-table-c-reference"></a><span data-ttu-id="b42f8-103">Sayısal sonuçlar tablosunu biçimlendirme (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="b42f8-103">Formatting numeric results table (C# Reference)</span></span>

<span data-ttu-id="b42f8-104">Aşağıdaki tabloda sayısal sonuçları biçimlendirmek için desteklenen biçim belirticileri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b42f8-104">The following table shows supported format specifiers for formatting numeric results.</span></span> <span data-ttu-id="b42f8-105">Son sütundaki biçimlendirilen sonuç, "en-US" <xref:System.Globalization.CultureInfo>karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b42f8-105">The formatted result in the last column corresponds to the "en-US" <xref:System.Globalization.CultureInfo>.</span></span>

|<span data-ttu-id="b42f8-106">Biçim belirteci</span><span class="sxs-lookup"><span data-stu-id="b42f8-106">Format specifier</span></span>|<span data-ttu-id="b42f8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b42f8-107">Description</span></span>|<span data-ttu-id="b42f8-108">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b42f8-108">Examples</span></span>|<span data-ttu-id="b42f8-109">Sonuç</span><span class="sxs-lookup"><span data-stu-id="b42f8-109">Result</span></span>|  
|----------------------|-----------------|--------------|------------|  
|<span data-ttu-id="b42f8-110">C veya c</span><span class="sxs-lookup"><span data-stu-id="b42f8-110">C or c</span></span>|<span data-ttu-id="b42f8-111">Para Birimi</span><span class="sxs-lookup"><span data-stu-id="b42f8-111">Currency</span></span>|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|<span data-ttu-id="b42f8-112">$2,50</span><span class="sxs-lookup"><span data-stu-id="b42f8-112">$2.50</span></span><br /><br /> <span data-ttu-id="b42f8-113">($2,50)</span><span class="sxs-lookup"><span data-stu-id="b42f8-113">($2.50)</span></span>|  
|<span data-ttu-id="b42f8-114">D veya d</span><span class="sxs-lookup"><span data-stu-id="b42f8-114">D or d</span></span>|<span data-ttu-id="b42f8-115">Ondalık</span><span class="sxs-lookup"><span data-stu-id="b42f8-115">Decimal</span></span>|`string s = $"{25:D5}";`|<span data-ttu-id="b42f8-116">00025</span><span class="sxs-lookup"><span data-stu-id="b42f8-116">00025</span></span>|  
|<span data-ttu-id="b42f8-117">E veya e</span><span class="sxs-lookup"><span data-stu-id="b42f8-117">E or e</span></span>|<span data-ttu-id="b42f8-118">Simge</span><span class="sxs-lookup"><span data-stu-id="b42f8-118">Exponential</span></span>|`string s = $"{250000:E2}";`|<span data-ttu-id="b42f8-119">2.50 e + 005</span><span class="sxs-lookup"><span data-stu-id="b42f8-119">2.50E+005</span></span>|  
|<span data-ttu-id="b42f8-120">F veya f</span><span class="sxs-lookup"><span data-stu-id="b42f8-120">F or f</span></span>|<span data-ttu-id="b42f8-121">Sabit nokta</span><span class="sxs-lookup"><span data-stu-id="b42f8-121">Fixed-point</span></span>|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|<span data-ttu-id="b42f8-122">2,50</span><span class="sxs-lookup"><span data-stu-id="b42f8-122">2.50</span></span><br /><br /> <span data-ttu-id="b42f8-123">3</span><span class="sxs-lookup"><span data-stu-id="b42f8-123">3</span></span>|  
|<span data-ttu-id="b42f8-124">G veya g</span><span class="sxs-lookup"><span data-stu-id="b42f8-124">G or g</span></span>|<span data-ttu-id="b42f8-125">Genel</span><span class="sxs-lookup"><span data-stu-id="b42f8-125">General</span></span>|`string s = $"{2.5:G}";`|<span data-ttu-id="b42f8-126">2,5</span><span class="sxs-lookup"><span data-stu-id="b42f8-126">2.5</span></span>|  
|<span data-ttu-id="b42f8-127">N veya n</span><span class="sxs-lookup"><span data-stu-id="b42f8-127">N or n</span></span>|<span data-ttu-id="b42f8-128">rakamlardan</span><span class="sxs-lookup"><span data-stu-id="b42f8-128">Numeric</span></span>|`string s = $"{2500000:N}";`|<span data-ttu-id="b42f8-129">2\.500.000,00</span><span class="sxs-lookup"><span data-stu-id="b42f8-129">2,500,000.00</span></span>|  
|<span data-ttu-id="b42f8-130">P veya p</span><span class="sxs-lookup"><span data-stu-id="b42f8-130">P or p</span></span>|<span data-ttu-id="b42f8-131">Yüzde</span><span class="sxs-lookup"><span data-stu-id="b42f8-131">Percent</span></span>|`string s = $"{0.25:P}";`|<span data-ttu-id="b42f8-132">% 25,00</span><span class="sxs-lookup"><span data-stu-id="b42f8-132">25.00%</span></span>|  
|<span data-ttu-id="b42f8-133">R veya r</span><span class="sxs-lookup"><span data-stu-id="b42f8-133">R or r</span></span>|<span data-ttu-id="b42f8-134">Gidiş</span><span class="sxs-lookup"><span data-stu-id="b42f8-134">Round-trip</span></span>|`string s = $"{2.5:R}";`|<span data-ttu-id="b42f8-135">2,5</span><span class="sxs-lookup"><span data-stu-id="b42f8-135">2.5</span></span>|  
|<span data-ttu-id="b42f8-136">X veya x</span><span class="sxs-lookup"><span data-stu-id="b42f8-136">X or x</span></span>|<span data-ttu-id="b42f8-137">Onaltılık</span><span class="sxs-lookup"><span data-stu-id="b42f8-137">Hexadecimal</span></span>|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|<span data-ttu-id="b42f8-138">BELIRLEDIĞINIZ</span><span class="sxs-lookup"><span data-stu-id="b42f8-138">FA</span></span><br /><br /> <span data-ttu-id="b42f8-139">'DIR</span><span class="sxs-lookup"><span data-stu-id="b42f8-139">FFFF</span></span>|  

## <a name="remarks"></a><span data-ttu-id="b42f8-140">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b42f8-140">Remarks</span></span>

<span data-ttu-id="b42f8-141">Bir biçim dizesi oluşturmak için Biçim belirleyicisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b42f8-141">You use a format specifier to create a format string.</span></span> <span data-ttu-id="b42f8-142">Biçim dizesi şu biçimdedir: `Axx`, burada</span><span class="sxs-lookup"><span data-stu-id="b42f8-142">The format string is of the following form: `Axx`, where</span></span>

- <span data-ttu-id="b42f8-143">`A`, sayısal değere uygulanan biçimlendirme türünü denetleyen biçim belirticisidir.</span><span class="sxs-lookup"><span data-stu-id="b42f8-143">`A` is the format specifier, which controls the type of formatting applied to the numeric value.</span></span>
- <span data-ttu-id="b42f8-144">`xx`, biçimlendirilen çıktıda basamak sayısını etkileyen duyarlık belirticisidir.</span><span class="sxs-lookup"><span data-stu-id="b42f8-144">`xx` is the precision specifier, which affects the number of digits in the formatted output.</span></span> <span data-ttu-id="b42f8-145">Duyarlık belirticisinin değeri, 0 ile 99 aralığındadır.</span><span class="sxs-lookup"><span data-stu-id="b42f8-145">The value of the precision specifier ranges from 0 to 99.</span></span>

<span data-ttu-id="b42f8-146">Ondalık ("D" veya "d") ve onaltılı ("X" veya "x") biçim belirticileri yalnızca integral türler için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b42f8-146">The decimal ("D" or "d") and hexadecimal ("X" or "x") format specifiers are supported only for integral types.</span></span> <span data-ttu-id="b42f8-147">Gidiş dönüş ("R" veya "r") Biçim belirleyicisi yalnızca <xref:System.Single>, <xref:System.Double>ve <xref:System.Numerics.BigInteger> türleri için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b42f8-147">The round-trip ("R" or "r") format specifier is supported only for <xref:System.Single>, <xref:System.Double>, and <xref:System.Numerics.BigInteger> types.</span></span>

<span data-ttu-id="b42f8-148">Standart sayısal biçim dizeleri şunları destekler:</span><span class="sxs-lookup"><span data-stu-id="b42f8-148">Standard numeric format strings are supported by:</span></span>

- <span data-ttu-id="b42f8-149">Tüm sayısal türlerde `ToString` yönteminin bazı aşırı yüklemeleri.</span><span class="sxs-lookup"><span data-stu-id="b42f8-149">Some overloads of the `ToString` method of all numeric types.</span></span> <span data-ttu-id="b42f8-150">Örneğin, <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> ve <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> yöntemlerine bir sayısal biçim dizesi sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42f8-150">For example, you can supply a numeric format string to the <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> and <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> methods.</span></span>

- <span data-ttu-id="b42f8-151">Örneğin <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemi tarafından desteklenen .NET [Bileşik biçimlendirme özelliği](../../../standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="b42f8-151">The .NET [composite formatting feature](../../../standard/base-types/composite-formatting.md), which is supported by the <xref:System.String.Format%2A?displayProperty=nameWithType> method, for example.</span></span>

- <span data-ttu-id="b42f8-152">[Enterpolasyonlu dizeler](../tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="b42f8-152">[Interpolated strings](../tokens/interpolated.md).</span></span>

<span data-ttu-id="b42f8-153">Daha fazla bilgi için bkz. [Standart sayısal biçim dizeleri](../../../standard/base-types/standard-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="b42f8-153">For more information, see [Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b42f8-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b42f8-154">See also</span></span>

- [<span data-ttu-id="b42f8-155">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="b42f8-155">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b42f8-156">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b42f8-156">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b42f8-157">Biçimlendirme türleri</span><span class="sxs-lookup"><span data-stu-id="b42f8-157">Formatting types</span></span>](../../../standard/base-types/formatting-types.md)
- [<span data-ttu-id="b42f8-158">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b42f8-158">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)
- [<span data-ttu-id="b42f8-159">Dize ilişkilendirme</span><span class="sxs-lookup"><span data-stu-id="b42f8-159">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="b42f8-160">string</span><span class="sxs-lookup"><span data-stu-id="b42f8-160">string</span></span>](../builtin-types/reference-types.md)
