---
title: Char Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 8313c2282a3b4b7b035f9f3b685a786c4471f53a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630148"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="98f44-102">Char Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98f44-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="98f44-103">0 ile 65535 arasında değer değişen işaretsiz 16 bit (2 baytlık) kod noktalarını tutar.</span><span class="sxs-lookup"><span data-stu-id="98f44-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="98f44-104">Her *kod noktası*veya karakter kodu, tek bir Unicode karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98f44-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="98f44-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98f44-105">Remarks</span></span>

<span data-ttu-id="98f44-106">Yalnızca tek bir karakter tutmanız gerektiğinde ve `String`ek yüküne ihtiyaç duymadığınızda veritürünükullanın.`Char`</span><span class="sxs-lookup"><span data-stu-id="98f44-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="98f44-107">Bazı durumlarda, birden çok karakteri `Char()`tutmak için bir `Char` dizi öğe kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98f44-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="98f44-108">Varsayılan değeri `Char` , bir kod noktası 0 olan karakterdir.</span><span class="sxs-lookup"><span data-stu-id="98f44-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="98f44-109">Unicode karakterler</span><span class="sxs-lookup"><span data-stu-id="98f44-109">Unicode Characters</span></span>

<span data-ttu-id="98f44-110">Unicode 'un ilk 128 kod noktası (0 – 127), standart bir ABD klavyesinde bulunan harflere ve simgelere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="98f44-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="98f44-111">Bu ilk 128 kod noktası, ASCII karakter kümesi tarafından tanımlananlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="98f44-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="98f44-112">İkinci 128 kod noktaları (128 – 255) Latin tabanlı alfabe harfleri, vurgular, para birimi sembolleri ve kesirler gibi özel karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98f44-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="98f44-113">Unicode, dünya çapındaki metin karakterleri, Aksanlar ve matematik ve teknik semboller dahil olmak üzere çok çeşitli semboller için kalan kod noktalarını (256-65535) kullanır.</span><span class="sxs-lookup"><span data-stu-id="98f44-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="98f44-114">Unicode sınıflandırmasını belirleyebilmeniz için <xref:System.Char.IsDigit%2A> bir <xref:System.Char.IsPunctuation%2A> `Char` değişkende ve gibi yöntemleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98f44-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="98f44-115">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="98f44-115">Type Conversions</span></span>

<span data-ttu-id="98f44-116">Visual Basic, ve sayısal türler arasında `Char` doğrudan dönüştürmez.</span><span class="sxs-lookup"><span data-stu-id="98f44-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="98f44-117">Ya <xref:Microsoft.VisualBasic.Strings.Asc%2A> `Char` `Integer` da işlevini, kod noktasını temsil eden bir değere dönüştürmek için kullanabilirsiniz. <xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="98f44-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="98f44-118">Veya <xref:Microsoft.VisualBasic.Strings.Chr%2A> `Integer` `Char` işlevini, bu kod noktasına sahip bir değeri öğesine dönüştürmek için kullanabilirsiniz. <xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="98f44-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="98f44-119">Tür denetimi anahtarı ( [katı ifade seçeneği](../../../visual-basic/language-reference/statements/option-strict-statement.md)) açık ise, `Char` veri türü olarak tanımlamak için, değişmez değer türü karakterini tek karakterli bir dize sabit değerine eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="98f44-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="98f44-120">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="98f44-120">The following example illustrates this.</span></span> <span data-ttu-id="98f44-121">`charVar` Değişkene ilk atama, açık olduğu için derleyici hatası [BC30512](../../misc/bc30512.md) `Option Strict` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98f44-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="98f44-122">`c` Sabit değer türü karakteri değeri bir `Char` değer olarak tanımladığı için ikinci derleme başarıyla derlenir.</span><span class="sxs-lookup"><span data-stu-id="98f44-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="98f44-123">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="98f44-123">Programming Tips</span></span>

- <span data-ttu-id="98f44-124">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="98f44-124">**Negative Numbers.**</span></span> <span data-ttu-id="98f44-125">`Char`işaretsiz bir tür ve negatif bir değer temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="98f44-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="98f44-126">Herhangi bir durumda, sayısal değerleri tutmak için `Char` kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="98f44-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="98f44-127">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="98f44-127">**Interop Considerations.**</span></span> <span data-ttu-id="98f44-128">Örneğin Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabiriminiz varsa, başka ortamlarda karakter türlerinin farklı bir veri genişliğine (8 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="98f44-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="98f44-129">Böyle bir bileşene 8 bitlik bir bağımsız değişken geçirirseniz, bunu yeni Visual Basic kodunuzda `Byte` `Char` değil olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="98f44-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="98f44-130">**Kan.**</span><span class="sxs-lookup"><span data-stu-id="98f44-130">**Widening.**</span></span> <span data-ttu-id="98f44-131">`Char` Widens`String`veri türü.</span><span class="sxs-lookup"><span data-stu-id="98f44-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="98f44-132">Bu, `Char` `String` ' a <xref:System.OverflowException?displayProperty=nameWithType>dönüştürebileceğiniz ve ile karşılaşmayacak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="98f44-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="98f44-133">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="98f44-133">**Type Characters.**</span></span> <span data-ttu-id="98f44-134">Değişmez değer türü karakterini `C` tek karakterli bir dize değişmez değerine eklemek, `Char` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="98f44-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="98f44-135">`Char`tanımlayıcı türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="98f44-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="98f44-136">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="98f44-136">**Framework Type.**</span></span> <span data-ttu-id="98f44-137">.NET Framework karşılık gelen tür <xref:System.Char?displayProperty=nameWithType> yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="98f44-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="98f44-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98f44-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="98f44-139">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="98f44-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="98f44-140">String Veri Türü</span><span class="sxs-lookup"><span data-stu-id="98f44-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="98f44-141">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="98f44-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="98f44-142">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="98f44-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="98f44-143">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="98f44-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="98f44-144">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="98f44-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
