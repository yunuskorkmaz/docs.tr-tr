---
title: 'Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma'
description: Bir sayıyı baştaki sıfırlarla doldurma hakkında bilgi edinin. Tamsayıları veya sayısal değerleri, belirli bir toplam uzunluğa veya belirli bir satır başına sıfırlar için öndeki sıfırlar ekleyin.
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
ms.openlocfilehash: 6ef0ddb37f1bc73254aa639d7c018ec6a01abd9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447192"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="4809a-104">Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma</span><span class="sxs-lookup"><span data-stu-id="4809a-104">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="4809a-105">"D" [Standart sayısal biçim dizesini](standard-numeric-format-strings.md) bir duyarlık belirticisiyle kullanarak bir tamsayıya önde gelen sıfırlar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4809a-105">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="4809a-106">[Özel bir sayısal biçim dizesi](custom-numeric-format-strings.md)kullanarak, hem tamsayı hem de kayan nokta numaralarına önde sıfır ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4809a-106">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="4809a-107">Bu makalede, her iki yöntemin de bir sayıyı baştaki sıfırlarla doldurma yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4809a-107">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4809a-108">Bir tamsayıyı önünde sıfır ile belirli bir uzunluğa göre doldurma</span><span class="sxs-lookup"><span data-stu-id="4809a-108">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="4809a-109">Tamsayı değerinin görüntülenmesini istediğiniz en az basamak sayısını belirleme.</span><span class="sxs-lookup"><span data-stu-id="4809a-109">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="4809a-110">Bu numaraya öndeki rakamları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4809a-110">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="4809a-111">Tamsayıyı ondalık değer veya onaltılık bir değer olarak göstermek isteyip istemediğinizi belirleme.</span><span class="sxs-lookup"><span data-stu-id="4809a-111">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="4809a-112">Tamsayıyı bir ondalık değer olarak göstermek için `ToString(String)` metodunu çağırın ve "D*n*" dizesini parametresinin değeri olarak geçirin `format` ; burada *n* , dizenin minimum uzunluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4809a-112">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="4809a-113">Tamsayıyı onaltılık bir değer olarak göstermek için `ToString(String)` metodunu çağırın ve "X*n*" dizesini biçim parametresinin değeri olarak geçirin; burada *n* , dizenin minimum uzunluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4809a-113">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="4809a-114">Ayrıca, biçim dizesini hem [C#](../../csharp/language-reference/tokens/interpolated.md) hem de [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)enterpolasyonlu bir dizedeki de kullanabilirsiniz ya da <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> [Bileşik biçimlendirme](composite-formatting.md)kullanan veya gibi bir yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4809a-114">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="4809a-115">Aşağıdaki örnek, biçimlendirilen sayının toplam uzunluğu en az sekiz karakter olacak şekilde, bazı tamsayı değerlerini öndeki sıfırlar ile biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="4809a-115">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4809a-116">Bir tamsayıyı belirli bir baştaki sıfır sayısıyla doldurma</span><span class="sxs-lookup"><span data-stu-id="4809a-116">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="4809a-117">Tamsayı değerinin kaç tane önde görüntülenmesini istediğinizi saptayın.</span><span class="sxs-lookup"><span data-stu-id="4809a-117">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="4809a-118">Tamsayıyı ondalık değer veya onaltılık bir değer olarak göstermek isteyip istemediğinizi belirleme.</span><span class="sxs-lookup"><span data-stu-id="4809a-118">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="4809a-119">Bunu bir ondalık değer olarak biçimlendirmek için "D" standart biçim belirticisini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4809a-119">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="4809a-120">Onaltılık değer olarak biçimlendirmek için "X" Standart Biçim belirleyicisi kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4809a-120">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="4809a-121">Tamsayı değerinin veya metodunu çağırarak, unununnumeric dizenin uzunluğunu belirleme `ToString("D").Length` `ToString("X").Length` .</span><span class="sxs-lookup"><span data-stu-id="4809a-121">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="4809a-122">Sayısal olmayan dizenin uzunluğuna göre biçimlendirilen dizeye eklemek istediğiniz öndeki sıfırlar sayısını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4809a-122">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="4809a-123">Baştaki sıfırların sayısını eklemek, doldurulmuş dizenin toplam uzunluğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4809a-123">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="4809a-124">Tamsayı değerinin `ToString(String)` metodunu çağırın ve "D*n*" dizesini ondalık dizeler Için ve "X*n*" dizesini, onaltılık dizeler için geçirin; burada *n* , doldurulmuş dizenin toplam uzunluğunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4809a-124">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="4809a-125">Bileşik biçimlendirmeyi destekleyen bir yöntemde "D*n*" veya "X*n*" biçim dizesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4809a-125">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="4809a-126">Aşağıdaki örnek, beş önde sıfır ile bir tamsayı değeri alt Pad.</span><span class="sxs-lookup"><span data-stu-id="4809a-126">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="4809a-127">Sayısal bir değeri öndeki sıfırlar ile belirli bir uzunluğa göre doldurma</span><span class="sxs-lookup"><span data-stu-id="4809a-127">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="4809a-128">Sayının dize gösteriminin kaç basamak olmasını istediğinizi belirleme.</span><span class="sxs-lookup"><span data-stu-id="4809a-128">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="4809a-129">Bu toplam basamak sayısında öndeki sıfırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4809a-129">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="4809a-130">En az sıfır sayısını temsil etmek için sıfır "0" yer tutucusunu kullanan özel bir sayısal biçim dizesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="4809a-130">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="4809a-131">Sayının `ToString(String)` metodunu çağırın ve özel biçim dizesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="4809a-131">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="4809a-132">Dize ilişkilendirme ile veya bileşik biçimlendirmeyi destekleyen bir yöntemle özel biçim dizesini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4809a-132">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="4809a-133">Aşağıdaki örnek, öndeki sıfırlar ile birkaç sayısal değeri biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="4809a-133">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="4809a-134">Sonuç olarak, biçimlendirilen sayının toplam uzunluğu, ondalık ayırıcının solunda en az sekiz haneye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4809a-134">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="4809a-135">Sayısal bir değeri belirli bir satır başına sıfır sayısıyla doldurma</span><span class="sxs-lookup"><span data-stu-id="4809a-135">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="4809a-136">Sayısal değerin kaç tane önde olacağını istediğinizi belirleme.</span><span class="sxs-lookup"><span data-stu-id="4809a-136">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="4809a-137">Undoldurulmuş sayısal dizedeki Decimal öğesinin solundaki basamak sayısını belirleme:</span><span class="sxs-lookup"><span data-stu-id="4809a-137">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="4809a-138">Bir sayının dize temsilinin bir Decimal Point simgesi içerip içermediğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="4809a-138">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="4809a-139">Bir ondalık nokta sembolü içeriyorsa, ondalık noktanın solundaki karakter sayısını saptayın.</span><span class="sxs-lookup"><span data-stu-id="4809a-139">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="4809a-140">-veya-</span><span class="sxs-lookup"><span data-stu-id="4809a-140">-or-</span></span>

         <span data-ttu-id="4809a-141">Bir ondalık nokta simgesi içermiyorsa, dizenin uzunluğunu saptayın.</span><span class="sxs-lookup"><span data-stu-id="4809a-141">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="4809a-142">Şunu kullanan bir özel biçim dizesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4809a-142">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="4809a-143">Baştaki sıfırların her biri için dizede görünecek sıfır yer tutucusu "0".</span><span class="sxs-lookup"><span data-stu-id="4809a-143">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="4809a-144">Varsayılan dizedeki her basamağı temsil eden sıfır yer tutucusu veya "#" basamak yer tutucusu.</span><span class="sxs-lookup"><span data-stu-id="4809a-144">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="4809a-145">Özel biçim dizesini, sayının `ToString(String)` yöntemine ya da bileşik biçimlendirmeyi destekleyen bir yönteme parametre olarak sağlayın.</span><span class="sxs-lookup"><span data-stu-id="4809a-145">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="4809a-146">Aşağıdaki örnek, <xref:System.Double> beş öndeki sıfırlar ile iki değeri alt Pad.</span><span class="sxs-lookup"><span data-stu-id="4809a-146">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="4809a-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4809a-147">See also</span></span>

- [<span data-ttu-id="4809a-148">Özel sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="4809a-148">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="4809a-149">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="4809a-149">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="4809a-150">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="4809a-150">Composite Formatting</span></span>](composite-formatting.md)
