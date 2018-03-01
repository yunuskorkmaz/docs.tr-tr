---
title: "Char Veri Türü (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16ff547fccbf4481d31ca79537962cc7090fc9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="62da8-102">Char Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62da8-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="62da8-103">Değer 0 ile 65535 arasında değişen ayrı tutma imzasız 16-bit (2-bayt) kod noktaları.</span><span class="sxs-lookup"><span data-stu-id="62da8-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="62da8-104">Her *kod noktası*, veya karakter kodu, tek bir Unicode karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62da8-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62da8-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="62da8-105">Remarks</span></span>  
 <span data-ttu-id="62da8-106">Kullanım `Char` veri türü yalnızca tek bir tutmak gerektiğinde karakter ve yükü gerekmez `String`.</span><span class="sxs-lookup"><span data-stu-id="62da8-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="62da8-107">Bazı durumlarda kullandığınız `Char()`, bir dizi `Char` birden çok karakter tutmak için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="62da8-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="62da8-108">Varsayılan değer olan `Char` kod noktası 0 ile karakterdir.</span><span class="sxs-lookup"><span data-stu-id="62da8-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="62da8-109">Unicode karakterler</span><span class="sxs-lookup"><span data-stu-id="62da8-109">Unicode Characters</span></span>  
 <span data-ttu-id="62da8-110">Unicode ilk 128 kod noktası (0 – 127) harf ve sembol Standart ABD klavyedeki karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="62da8-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="62da8-111">Bu ilk 128 kod noktaları ASCII karakter kümesi tanımlar aynıdır.</span><span class="sxs-lookup"><span data-stu-id="62da8-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="62da8-112">İkinci 128 kod noktaları (128-255) Latin tabanlı alfabedeki harfleri, vurgular, para birimi simgeleri ve kesirler gibi özel karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62da8-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="62da8-113">Unicode için simgeler, dünya çapında metinsel karakter, Vurgu ve matematiksel ve teknik simgeleri de dahil olmak üzere çok çeşitli kalan kod noktaları (256-65535) kullanır.</span><span class="sxs-lookup"><span data-stu-id="62da8-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="62da8-114">Yöntemleri gibi kullanabilirsiniz <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> üzerinde bir `Char` kendi Unicode sınıflandırmasını belirlemek için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="62da8-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="62da8-115">Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="62da8-115">Type Conversions</span></span>  
 <span data-ttu-id="62da8-116">Visual Basic değil Dönüştür doğrudan arasında `Char` ve sayısal türler.</span><span class="sxs-lookup"><span data-stu-id="62da8-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="62da8-117">Kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Asc%2A> veya <xref:Microsoft.VisualBasic.Strings.AscW%2A> dönüştürmek için işlevi bir `Char` değeri bir `Integer` kod noktası temsil eden.</span><span class="sxs-lookup"><span data-stu-id="62da8-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="62da8-118">Kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Chr%2A> veya <xref:Microsoft.VisualBasic.Strings.ChrW%2A> dönüştürmek için işlevi bir `Integer` değeri bir `Char` Bu kod noktası vardır.</span><span class="sxs-lookup"><span data-stu-id="62da8-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="62da8-119">Tür denetleme geçiş yaparsanız ([Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)) olduğundan, gerekir eklediğiniz değişmez değer türü karakteri olarak tanımlamak için değişmez değer tek karakterli bir dize için `Char` veri türü.</span><span class="sxs-lookup"><span data-stu-id="62da8-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="62da8-120">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="62da8-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="62da8-121">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="62da8-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="62da8-122">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="62da8-122">**Negative Numbers.**</span></span> <span data-ttu-id="62da8-123">`Char`İmzasız bir tür olduğundan ve negatif bir değer temsil edilemez.</span><span class="sxs-lookup"><span data-stu-id="62da8-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="62da8-124">Her iki durumda da kullanılamaz `Char` sayısal değerleri tutmak için.</span><span class="sxs-lookup"><span data-stu-id="62da8-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="62da8-125">**Birlikte çalışma hakkında dikkat edilecek noktalar**</span><span class="sxs-lookup"><span data-stu-id="62da8-125">**Interop Considerations.**</span></span> <span data-ttu-id="62da8-126">.NET Framework için yazılmaz bileşenleriyle arabirim örnek otomasyon veya COM nesneleri için karakter türleri (8 bit) farklı veri genişliği sahip diğer ortamlarda unutmayın.</span><span class="sxs-lookup"><span data-stu-id="62da8-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="62da8-127">Bu tür bir bileşen için 8 bit bağımsız değişken geçirirseniz, olarak bildirme `Byte` yerine `Char` yeni Visual Basic kodunuzda.</span><span class="sxs-lookup"><span data-stu-id="62da8-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="62da8-128">**Genişletme.**</span><span class="sxs-lookup"><span data-stu-id="62da8-128">**Widening.**</span></span> <span data-ttu-id="62da8-129">`Char` Veri türü widens için `String`.</span><span class="sxs-lookup"><span data-stu-id="62da8-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="62da8-130">Bu dönüştürebilirsiniz anlamına gelir `Char` için `String` ve değil karşılaşır bir <xref:System.OverflowException?displayProperty=nameWithType> hata.</span><span class="sxs-lookup"><span data-stu-id="62da8-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="62da8-131">**Karakterleri yazın.**</span><span class="sxs-lookup"><span data-stu-id="62da8-131">**Type Characters.**</span></span> <span data-ttu-id="62da8-132">Değişmez değer türü karakteri ekleme `C` tek karakterli bir dize sabit değeri için zorlar `Char` veri türü.</span><span class="sxs-lookup"><span data-stu-id="62da8-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="62da8-133">`Char`hiçbir tanımlayıcı türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="62da8-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="62da8-134">**Framework türü.**</span><span class="sxs-lookup"><span data-stu-id="62da8-134">**Framework Type.**</span></span> <span data-ttu-id="62da8-135">.NET Framework'teki karşılık gelen tür <xref:System.Char?displayProperty=nameWithType> yapısı.</span><span class="sxs-lookup"><span data-stu-id="62da8-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62da8-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62da8-136">See Also</span></span>  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="62da8-137">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="62da8-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="62da8-138">Dize veri türü</span><span class="sxs-lookup"><span data-stu-id="62da8-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="62da8-139">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="62da8-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="62da8-140">Dönüştürme özeti</span><span class="sxs-lookup"><span data-stu-id="62da8-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="62da8-141">Nasıl yapılır: imzalanmamış türler isteyen bir Windows işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="62da8-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="62da8-142">Veri türlerinin etkili kullanımı</span><span class="sxs-lookup"><span data-stu-id="62da8-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
