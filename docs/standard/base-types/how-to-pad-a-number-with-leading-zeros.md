---
title: 'Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma'
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
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131982"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="b6eb3-102">Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma</span><span class="sxs-lookup"><span data-stu-id="b6eb3-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="b6eb3-103">"D" [standart sayısal biçim dizesini](../../../docs/standard/base-types/standard-numeric-format-strings.md) hassas bir belirtimle kullanarak bir tamsayıya satır aralığı sıfırları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="b6eb3-104">[Özel bir sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md)kullanarak hem tamsayı hem de kayan nokta numaralarına satır aralığı sıfırları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="b6eb3-105">Bu makalede, önde gelen sıfırlar ile bir sayı pad için her iki yöntem nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="b6eb3-106">Belirli bir uzunluğa giden sıfırları içeren bir tamsayıyı deftere</span><span class="sxs-lookup"><span data-stu-id="b6eb3-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="b6eb3-107">Tümsek değerinin görüntülenmesini istediğiniz en az basamak sayısını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="b6eb3-108">Bu sayıya herhangi bir satır basamağı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="b6eb3-109">Tamsayıyı ondalık değer mi yoksa hexadecimal değer olarak mı görüntülemek istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="b6eb3-110">Tamsayıyı `ToString(String)` ondalık değer olarak görüntülemek için, yöntemini çağırın ve *"D* *n"* dizesini, n dizesinin minimum uzunluğunu temsil eden `format` parametrenin değeri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="b6eb3-111">Tamsayıyı hexadecimal değer olarak görüntülemek için, yöntemini `ToString(String)` çağırın ve *"X* *n"* dizesini, n dizesinin minimum uzunluğunu temsil eden biçim parametresinin değeri olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="b6eb3-112">Biçim dizesini hem [C#](../../csharp/language-reference/tokens/interpolated.md) hem de [Visual Basic'te](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)enterpolasyonlu bir dizede <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>de kullanabilirsiniz veya bileşik [biçimlendirme](../../../docs/standard/base-types/composite-formatting.md)kullanan bir yöntem <xref:System.String.Format%2A?displayProperty=nameWithType> çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>

<span data-ttu-id="b6eb3-113">Aşağıdaki örnek, biçimlendirilmiş sayının toplam uzunluğunun en az sekiz karakter olması için satır aralığı sıfırlarla birkaç tamsayı değerini biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="b6eb3-114">Belirli sayıda satır aralığı sıfıriçeren bir tamsayıyı deftere almak için</span><span class="sxs-lookup"><span data-stu-id="b6eb3-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="b6eb3-115">Tümsek değerinin kaç tane satır aralığını görüntülemesini istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="b6eb3-116">Tamsayıyı ondalık değer mi yoksa hexadecimal değer olarak mı görüntülemek istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="b6eb3-117">Ondalık değer olarak biçimlendirmek için "D" standart biçim belirticisini kullanmanız gerekmektedir.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="b6eb3-118">Bir hexadecimal değer olarak biçimlendirme "X" standart biçim belirtici kullanmanız gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="b6eb3-119">Toplam değerin `ToString("D").Length` veya `ToString("X").Length` yöntemi çağırarak eklenmemiş sayısal dizenin uzunluğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="b6eb3-120">Biçimlendirilmiş dizeye eklemek istediğiniz satır aralığı sıfırlarının sayısını, eklenmemiş sayısal dize uzunluğuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="b6eb3-121">Satır aralığı sıfırların sayısı nın eklenmesi, dolgulu dizenin toplam uzunluğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="b6eb3-122">Tamsayı `ToString(String)` değerinin yöntemini çağırın ve ondalık dizeler için "D*n"* ve *n'nin* yastıklı dizenin toplam uzunluğunu temsil ettiği hexadecimal dizeler için "X*n"* dizesini geçirin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="b6eb3-123">"D*n"* veya "X*n*" biçimdize, bileşik biçimlendirmeyi destekleyen bir yöntemde de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="b6eb3-124">Aşağıdaki örnek, beş satır sıfıriçeren bir bir bir veyaslama değerini pedleri.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="b6eb3-125">Belirli bir uzunluğa giden sıfırlarla sayısal bir değer emetmek için</span><span class="sxs-lookup"><span data-stu-id="b6eb3-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="b6eb3-126">Ondalık sayı nın solunda kaç basamaklı olmasını istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="b6eb3-127">Bu toplam basamak sayısına önde gelen sıfırları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="b6eb3-128">En az sıfır sayısını temsil etmek için sıfır yer tutucu "0"ı kullanan özel bir sayısal biçim dizesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="b6eb3-129">Numaranın `ToString(String)` yöntemini çağırın ve özel biçim dizesini geçirin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="b6eb3-130">Ayrıca dize enterpolasyonu veya bileşik biçimlendirme destekleyen bir yöntem ile özel biçim dizek kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="b6eb3-131">Aşağıdaki örnek, önde gelen sıfırlarla birkaç sayısal değeri biçimlendirür.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="b6eb3-132">Sonuç olarak, biçimlendirilmiş sayının toplam uzunluğu ondalık adın solunda en az sekiz basamaktır.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="b6eb3-133">Belirli sayıda satır aralığı sıfıriçeren sayısal bir değere sahip olmak için</span><span class="sxs-lookup"><span data-stu-id="b6eb3-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="b6eb3-134">Sayısal değerin kaç satır önde gelen sıfıra sahip olmasını istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="b6eb3-135">Ondalık basamak ların solundaki basamak sayısını, eklenmemiş sayısal dizede belirleyin:</span><span class="sxs-lookup"><span data-stu-id="b6eb3-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="b6eb3-136">Bir sayının dize gösteriminin ondalık nokta simgesi ni içerip içermediğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="b6eb3-137">Ondalık nokta simgesi içeriyorsa, ondalık noktanın solundaki karakter sayısını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="b6eb3-138">-veya-</span><span class="sxs-lookup"><span data-stu-id="b6eb3-138">-or-</span></span>

         <span data-ttu-id="b6eb3-139">Ondalık nokta simgesi içermiyorsa, dizenin uzunluğunu belirleyin.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="b6eb3-140">Aşağıdakileri kullanan özel bir biçim dizesi oluşturun:</span><span class="sxs-lookup"><span data-stu-id="b6eb3-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="b6eb3-141">Önde gelen sıfırların her biri için dizegörünmesi için sıfır yer tutucu "0"</span><span class="sxs-lookup"><span data-stu-id="b6eb3-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="b6eb3-142">Varsayılan dizedeki her rakamı temsil edecek sıfır yer tutucu veya basamak yer tutucusu "#" olur.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="b6eb3-143">Özel biçim dizesini parametre olarak sayının `ToString(String)` yöntemine veya bileşik biçimlendirmeyi destekleyen bir yönteme ver.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="b6eb3-144">Aşağıdaki örnek, beş <xref:System.Double> satır sıfırile iki değer pads.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="b6eb3-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6eb3-145">See also</span></span>

- [<span data-ttu-id="b6eb3-146">Özel Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="b6eb3-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="b6eb3-147">Standart Sayısal Biçim Dizeleri</span><span class="sxs-lookup"><span data-stu-id="b6eb3-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="b6eb3-148">Bileşik Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="b6eb3-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
