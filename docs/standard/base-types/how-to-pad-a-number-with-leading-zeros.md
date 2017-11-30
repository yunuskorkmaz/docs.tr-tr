---
title: "Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="d9420-102">Nasıl yapılır: Bir Sayıyı Baştaki Sıfırlarla Doldurma</span><span class="sxs-lookup"><span data-stu-id="d9420-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="d9420-103">"D" kullanarak bir tamsayı baştaki sıfırlarla ekleyebilirsiniz [standart sayısal biçim dizesi](../../../docs/standard/base-types/standard-numeric-format-strings.md) duyarlık Belirleyicisi ile.</span><span class="sxs-lookup"><span data-stu-id="d9420-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="d9420-104">Tamsayı ve kayan nokta sayıları baştaki sıfırlarla kullanarak ekleyebileceğiniz bir [özel sayısal biçim dizesi](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="d9420-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="d9420-105">Bu konu, her iki yöntem sayıyı baştaki sıfırlarla paneli için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9420-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="d9420-106">Baştaki sıfırlarla belirli bir süre için bir tamsayı doldurulacak</span><span class="sxs-lookup"><span data-stu-id="d9420-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="d9420-107">Tamsayı değeri görüntülemek istediğiniz basamak sayısı alt sınırını belirler.</span><span class="sxs-lookup"><span data-stu-id="d9420-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="d9420-108">Tüm önde gelen basamak bu numarayı içerir.</span><span class="sxs-lookup"><span data-stu-id="d9420-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="d9420-109">Tamsayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d9420-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="d9420-110">Tamsayı ondalık bir değeri görüntülemek için arama kendi `ToString(String)` yöntemi ve geçişi dizesi "D*n*" değeri olarak `format` parametresi, burada  *n*  en az dize uzunluğu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9420-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="d9420-111">Tamsayı bir onaltılık değer olarak görüntülemek için arama kendi `ToString(String)` yöntemi ve geçişi dizesi "X*n*" değeri olarak `format` parametresi, burada  *n*  en az dize uzunluğu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9420-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="d9420-112">Biçim dizesi bir yöntemde gibi kullanabilirsiniz <xref:System.String.Format%2A> veya <xref:System.Console.WriteLine%2A>, kullanan [bileşik biçimlendirme](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="d9420-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="d9420-113">Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz karakter sıfırları ile birkaç tamsayı değerlerini biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="d9420-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="d9420-114">Öndeki sıfırların belirli bir sayısı bir tamsayı doldurulacak</span><span class="sxs-lookup"><span data-stu-id="d9420-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="d9420-115">Kaç tane öndeki sıfırların istediğiniz görüntülemek için tamsayı değeri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d9420-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="d9420-116">Tamsayı ondalık bir değer veya bir onaltılık değer olarak görüntülemek isteyip istemediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d9420-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="d9420-117">Ondalık değer olarak biçimlendirme "D" standart biçim belirticisi kullanmanızı gerektirir; bir onaltılık değer olarak biçimlendirme "X" standart biçim belirticisi kullanmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d9420-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="d9420-118">Tamsayı değerinin çağırarak unpadded sayısal dize uzunluğu belirlemek `ToString("D").Length` veya `ToString("X").Length` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d9420-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="d9420-119">Unpadded sayısal dize uzunluğu biçimlendirilmiş dizeye dahil etmek istediğiniz öndeki sıfırların sayısı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d9420-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="d9420-120">Bu, toplam doldurulan dize uzunluğu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d9420-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="d9420-121">Tamsayı değerinin çağrısı `ToString(String)` yöntemi ve geçişi dizesi "D*n*" ondalık dizeleri ve "X*n*" onaltılık dizeler için burada  *n*  doldurulan dize toplam uzunluğu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d9420-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="d9420-122">Aynı zamanda "D*n*" veya "X*n*" format dize bileşik biçimlendirme destekleyen bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="d9420-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="d9420-123">Aşağıdaki örnek, bir tamsayı değeri beş baştaki sıfırlarla pads.</span><span class="sxs-lookup"><span data-stu-id="d9420-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="d9420-124">Baştaki sıfırlarla belirli bir süre için sayısal bir değer yazma</span><span class="sxs-lookup"><span data-stu-id="d9420-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="d9420-125">Ondalık konumun soluna kaç basamağa sahip üzere numarasını dize gösterimini istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d9420-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="d9420-126">Bu toplam basamak sayısı önde gelen tüm sıfırları içerir.</span><span class="sxs-lookup"><span data-stu-id="d9420-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="d9420-127">En az sayıda sıfır göstermek için sıfır yer tutucusu ("0") kullanan bir özel sayısal biçim dizesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d9420-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="d9420-128">Sayının çağrı `ToString(String)` yöntemi ve özel biçim dizesi geçirin.</span><span class="sxs-lookup"><span data-stu-id="d9420-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="d9420-129">Bileşik biçimlendirme destekleyen bir yöntemle özel biçim dizesi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9420-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="d9420-130">Aşağıdaki örnek, böylece biçimlendirilmiş sayısının toplam uzunluğu en az sekiz basamağa ondalık konumun soluna sıfırları ile birkaç sayısal değerleri biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="d9420-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="d9420-131">Öndeki sıfırların belirli sayıda sayısal bir değer yazma</span><span class="sxs-lookup"><span data-stu-id="d9420-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="d9420-132">Kaç tane öndeki sıfırların sayısal değerin olmasını istediğinizi belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d9420-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="d9420-133">Sol tarafındaki unpadded sayısal dize ondalık basamak sayısını belirler.</span><span class="sxs-lookup"><span data-stu-id="d9420-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="d9420-134">Bunu yapmak için:</span><span class="sxs-lookup"><span data-stu-id="d9420-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="d9420-135">Bir sayı dize gösterimini bir ondalık ayırıcısı simge içerip içermediğini belirler.</span><span class="sxs-lookup"><span data-stu-id="d9420-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="d9420-136">Bir ondalık ayırıcısı simge dahil ederseniz, Ondalık ayırıcının solundaki karakter sayısını belirler.</span><span class="sxs-lookup"><span data-stu-id="d9420-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="d9420-137">veya</span><span class="sxs-lookup"><span data-stu-id="d9420-137">-or-</span></span>  
  
         <span data-ttu-id="d9420-138">Bir ondalık ayırıcısı simge içermiyorsa dizenin uzunluğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="d9420-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="d9420-139">Her basamakta varsayılan dizesini temsil etmek için sıfır yer tutucusu veya basamak yer tutucusu ("#") kullanan ve sıfır yer tutucusu ("0") her öndeki sıfırların dizesinde görünmesi kullanan özel bir biçim dizesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d9420-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="d9420-140">Özel biçim dizesi parametre olarak ya da sayının tedarik `ToString(String)` yöntemi veya bileşik biçimlendirme destekleyen bir yöntem.</span><span class="sxs-lookup"><span data-stu-id="d9420-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="d9420-141">Aşağıdaki örnekte iki pads <xref:System.Double> beş baştaki sıfırlarla değerleri.</span><span class="sxs-lookup"><span data-stu-id="d9420-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d9420-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9420-142">See Also</span></span>  
 [<span data-ttu-id="d9420-143">Özel sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="d9420-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="d9420-144">Standart sayısal biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="d9420-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="d9420-145">Bileşik biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="d9420-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
