---
title: 'Nasıl yapılır: Bir sayı önünde sıfır ile doldurur.'
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54c3eb734184adf5168607cfc8bcbf6c17ea493a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678902"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="493a9-102">Nasıl yapılır: Bir sayı önünde sıfır ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="493a9-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="493a9-103">"D"'ı kullanarak bir tamsayıya baştaki sıfırlar ekleyebilirsiniz [standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md) bir duyarlık belirtici ile.</span><span class="sxs-lookup"><span data-stu-id="493a9-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="493a9-104">Tamsayı ve kayan nokta sayıları baştaki sıfırlar ekleyebilirsiniz bir [özel sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="493a9-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="493a9-105">Bu makalede, bir sayı sıfırları ile doldurulacak iki yöntem de kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="493a9-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="493a9-106">Bir tamsayı, belirli bir süre için sıfırları ile doldurulacak</span><span class="sxs-lookup"><span data-stu-id="493a9-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="493a9-107">Tamsayı değeri görüntülemek istediğiniz basamak sayısı alt sınırını belirler.</span><span class="sxs-lookup"><span data-stu-id="493a9-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="493a9-108">Bu sayıda önde gelen tüm basamaklar içerir.</span><span class="sxs-lookup"><span data-stu-id="493a9-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="493a9-109">Tam sayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="493a9-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="493a9-110">Tam sayı ondalık bir değeri görüntülemek için arama, `ToString(String)` yöntemi ve pass dize "D*n*" değeri olarak `format` parametresi, burada *n* dize en küçük uzunluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="493a9-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="493a9-111">Tamsayı bir onaltılık değer görüntülemek için çağrı kendi `ToString(String)` yöntemi ve pass dize "X*n*" biçim parametresinin değeri olarak burada *n* dize en küçük uzunluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="493a9-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="493a9-112">Biçim dizesi bir aradeğerlendirme dizesinde hem de kullanabilirsiniz [ C# ](../../csharp/language-reference/tokens/interpolated.md) ve [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), veya gibi bir yöntem çağırabilirsiniz <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, kullanan [ Bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="493a9-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>

<span data-ttu-id="493a9-113">Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz karakter ile sıfırları birkaç tamsayı değeri biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="493a9-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="493a9-114">Belirli sayıda önünde sıfır ile tamsayı yazma</span><span class="sxs-lookup"><span data-stu-id="493a9-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="493a9-115">Kaç tane baştaki sıfırlar istediğiniz görüntülemek için tamsayı değeri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="493a9-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="493a9-116">Tam sayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="493a9-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="493a9-117">Ondalık değer olarak biçimlendirme "D" standart biçim tanımlayıcısı kullanmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="493a9-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="493a9-118">Bir onaltılık değer biçimlendirme "X" standart biçim tanımlayıcısı kullanmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="493a9-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="493a9-119">Tamsayı değerinin çağırarak unpadded sayısal dize uzunluğunu belirlemek `ToString("D").Length` veya `ToString("X").Length` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="493a9-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="493a9-120">Biçimlendirilen dizesinde unpadded sayısal dize uzunluğu dahil etmek istediğiniz baştaki sıfırlar sayısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="493a9-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="493a9-121">Baştaki sıfırlar sayısını ekleyerek toplam doldurulan bir dizenin uzunluğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="493a9-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="493a9-122">Tamsayı değerinin çağrı `ToString(String)` yöntemi ve pass dize "D*n*" ondalık dizeleri ve "X*n*" onaltılık dizeler için burada *n* toplam temsil eder doldurulan dize uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="493a9-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="493a9-123">Ayrıca "D*n*" veya "X*n*" biçimlendirme dizesi bileşik biçimlendirmeyi destekleyen bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="493a9-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="493a9-124">Aşağıdaki örnek bir tamsayı değeri beş önünde sıfır ile sıfır ekleyerek doldurur.</span><span class="sxs-lookup"><span data-stu-id="493a9-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="493a9-125">Belirli bir süre için sıfırları ile sayısal bir değer yazma</span><span class="sxs-lookup"><span data-stu-id="493a9-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="493a9-126">Küsur işaretinin solundaki kaç basamağa sahip bir sayının dize gösterimini istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="493a9-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="493a9-127">Bu basamakların toplam sayısı, baştaki sıfırları içerir.</span><span class="sxs-lookup"><span data-stu-id="493a9-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="493a9-128">Sıfır en az sayısını temsil etmek için sıfır yer tutucu "0" kullanan bir özel sayısal biçim dizesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="493a9-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="493a9-129">Sayının çağrı `ToString(String)` yöntemi ve özel biçim dizesi geçirin.</span><span class="sxs-lookup"><span data-stu-id="493a9-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="493a9-130">Özel biçim dizesi, dize ilişkilendirme ile veya bileşik biçimlendirmeyi destekleyen bir yöntemle de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="493a9-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="493a9-131">Aşağıdaki örnek, öndeki ile birkaç sayısal değeri biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="493a9-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="493a9-132">Sonuç olarak, biçimlendirilen sayı toplam uzunluğu en az sekiz küsur işaretinin solundaki basamak olabilir.</span><span class="sxs-lookup"><span data-stu-id="493a9-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="493a9-133">Baştaki sıfırlar, belirli bir değere sahip bir sayısal değer yazma</span><span class="sxs-lookup"><span data-stu-id="493a9-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="493a9-134">Kaç tane baştaki sıfırlar sayısal bir değer olmasını istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="493a9-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="493a9-135">Sol tarafındaki unpadded sayısal dizesindeki ondalık basamak sayısını belirler:</span><span class="sxs-lookup"><span data-stu-id="493a9-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="493a9-136">Bir sayının dize gösterimini bir ondalık noktası simgesi içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="493a9-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="493a9-137">Ondalık noktası simgesi dahil ederseniz, Ondalık ayırıcının solundaki karakter sayısını belirler.</span><span class="sxs-lookup"><span data-stu-id="493a9-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="493a9-138">-veya-</span><span class="sxs-lookup"><span data-stu-id="493a9-138">-or-</span></span>

         <span data-ttu-id="493a9-139">Ondalık noktası simgesi içermiyorsa, dizenin uzunluğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="493a9-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="493a9-140">Kullanan bir özel biçim dizesinde oluşturun:</span><span class="sxs-lookup"><span data-stu-id="493a9-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="493a9-141">Dizesinde görünmesi için sıfır için yer tutucu "0" her baştaki sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="493a9-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="493a9-142">Sıfır yer tutucu ya da basmak yer tutucusu "#" varsayılan dizedeki her basamak gösterecek.</span><span class="sxs-lookup"><span data-stu-id="493a9-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="493a9-143">Özel biçim dizesi bir parametre olarak ya da sayının tedarik `ToString(String)` yöntemi veya bileşik biçimlendirmeyi destekleyen bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="493a9-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="493a9-144">Aşağıdaki örnek iki sıfır ekleyerek doldurur <xref:System.Double> değerlerle beş baştaki sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="493a9-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="493a9-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="493a9-145">See also</span></span>

- [<span data-ttu-id="493a9-146">Özel Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="493a9-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="493a9-147">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="493a9-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="493a9-148">Bileşik Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="493a9-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
