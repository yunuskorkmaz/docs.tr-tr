---
title: Dize Veri Türü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842297"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="a31f9-102">Dize Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a31f9-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="a31f9-103">İmzasız 16-bit (2 baytlık) kod noktaları dizisi bu aralık 0 ile 65535 arasında bir değer tutar.</span><span class="sxs-lookup"><span data-stu-id="a31f9-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="a31f9-104">Her *kod noktası*, ya da karakter kodunu tek bir Unicode karakterini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a31f9-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="a31f9-105">Bir dize yaklaşık iki milyardan fazla 0'dan içerebilir (2 ^ 31) Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="a31f9-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a31f9-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a31f9-106">Remarks</span></span>  
 <span data-ttu-id="a31f9-107">Kullanım `String` birden çok karakter dizisi yönetim yükü olmadan tutmak için veri türü `Char()`, bir dizi `Char` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a31f9-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="a31f9-108">Varsayılan değer olan `String` olduğu `Nothing` (null bir başvuru).</span><span class="sxs-lookup"><span data-stu-id="a31f9-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="a31f9-109">Bu boş bir dize ile aynı olduğunu unutmayın (değer `""`).</span><span class="sxs-lookup"><span data-stu-id="a31f9-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="a31f9-110">Unicode karakterler</span><span class="sxs-lookup"><span data-stu-id="a31f9-110">Unicode Characters</span></span>  
 <span data-ttu-id="a31f9-111">Unicode ilk 128 kod noktası (0-127) harf ve sembol Standart ABD klavyedeki karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a31f9-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="a31f9-112">Bu ilk 128 kod noktaları ASCII karakter kümesi tanımlar aynıdır.</span><span class="sxs-lookup"><span data-stu-id="a31f9-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="a31f9-113">İkinci 128 kod noktası (128-255) Latin tabanlı alfabedeki harfleri, vurgular, para birimi simgeleri ve kesirli gibi özel karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a31f9-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="a31f9-114">Unicode çok çeşitli semboller için kalan kod noktası (256-65535) kullanır.</span><span class="sxs-lookup"><span data-stu-id="a31f9-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="a31f9-115">Bu, dünya çapında metinsel karakterler, aksanlar ve matematik ve teknik semboller içerir.</span><span class="sxs-lookup"><span data-stu-id="a31f9-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="a31f9-116">Gibi yöntemler kullanmanız <xref:System.Char.IsDigit%2A> ve <xref:System.Char.IsPunctuation%2A> tekil karakter, üzerinde bir `String` kendi Unicode sınıflandırmasını belirlemek için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a31f9-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="a31f9-117">Biçim gereksinimlerini</span><span class="sxs-lookup"><span data-stu-id="a31f9-117">Format Requirements</span></span>  
 <span data-ttu-id="a31f9-118">İçine almalısınız bir `String` tırnak işaretleri içindeki sabit değeri (`" "`).</span><span class="sxs-lookup"><span data-stu-id="a31f9-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="a31f9-119">Bir dizedeki karakter olarak bir tırnak işareti içermelidir, iki bitişik tırnak işareti kullanın (`""`).</span><span class="sxs-lookup"><span data-stu-id="a31f9-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="a31f9-120">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a31f9-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="a31f9-121">Bitişik dize bir tırnak işareti temsil eden tırnak başlayıp bitiş tırnak işareti bağımsız olduğunu unutmayın `String` değişmez.</span><span class="sxs-lookup"><span data-stu-id="a31f9-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="a31f9-122">Dize işlemeleri</span><span class="sxs-lookup"><span data-stu-id="a31f9-122">String Manipulations</span></span>  
 <span data-ttu-id="a31f9-123">Bir dizeye atadıktan sonra bir `String` değişken olduğundan, o dizeyi *değişmez*, anlamına gelir, uzunluk veya içeriği değiştiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a31f9-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="a31f9-124">Bir dizedeki herhangi bir şekilde değiştirdiğinizde, Visual Basic yeni bir dize oluşturur ve önceki bırakır.</span><span class="sxs-lookup"><span data-stu-id="a31f9-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="a31f9-125">`String` Değişkeni sonra yeni dizeye işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a31f9-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="a31f9-126">İçeriğini işleyebileceğiniz bir `String` değişken dize işlevleri çeşitli kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a31f9-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="a31f9-127">Aşağıdaki örnekte gösterilmiştir <xref:Microsoft.VisualBasic.Strings.Left%2A> işlevi</span><span class="sxs-lookup"><span data-stu-id="a31f9-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="a31f9-128">Başka bir bileşen tarafından oluşturulan bir dize, baştaki veya sondaki boşlukları ile sıfır.</span><span class="sxs-lookup"><span data-stu-id="a31f9-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="a31f9-129">Bu tür bir dize alırsanız, kullanabileceğiniz <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, ve <xref:Microsoft.VisualBasic.Strings.RTrim%2A> işlevleri bu boşlukları Kaldır.</span><span class="sxs-lookup"><span data-stu-id="a31f9-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="a31f9-130">Dize işlemeleri hakkında daha fazla bilgi için bkz: [dizeleri](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="a31f9-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="a31f9-131">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="a31f9-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="a31f9-132">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="a31f9-132">**Negative Numbers.**</span></span> <span data-ttu-id="a31f9-133">Karakter tarafından tutulan unutmayın `String` işaretsizdir ve negatif değerleri temsil edemez.</span><span class="sxs-lookup"><span data-stu-id="a31f9-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="a31f9-134">Her iki durumda da kullanmamalısınız `String` sayısal değerleri tutmak için.</span><span class="sxs-lookup"><span data-stu-id="a31f9-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="a31f9-135">**Birlikte çalışabilirlik değerlendirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="a31f9-135">**Interop Considerations.**</span></span> <span data-ttu-id="a31f9-136">.NET Framework yazılmaz bileşenleriyle arabirim örnek otomasyon ve COM nesneleri için dize karakterlerine farklı veri genişliği (8 bit) sahip diğer ortamlarda unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a31f9-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="a31f9-137">8 bitlik karakterleri bir dize bağımsız değişkeni böyle bir bileşene geçiriyorsanız, olarak bildirin `Byte()`, bir dizi `Byte` öğeleri yerine `String` yeni Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="a31f9-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="a31f9-138">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="a31f9-138">**Type Characters.**</span></span> <span data-ttu-id="a31f9-139">Tanımlayıcı türü karakteri ekleme `$` herhangi bir tanımlayıcı zorlar `String` veri türü.</span><span class="sxs-lookup"><span data-stu-id="a31f9-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="a31f9-140">`String` hiçbir değişmez değer türü karakteri var.</span><span class="sxs-lookup"><span data-stu-id="a31f9-140">`String` has no literal type character.</span></span> <span data-ttu-id="a31f9-141">Ancak, derleyici değişmez değerleri tırnak içine işler (`" "`) olarak `String`.</span><span class="sxs-lookup"><span data-stu-id="a31f9-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="a31f9-142">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="a31f9-142">**Framework Type.**</span></span> <span data-ttu-id="a31f9-143">.NET Framework içinde karşılık gelen türü <xref:System.String?displayProperty=nameWithType> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="a31f9-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a31f9-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a31f9-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="a31f9-145">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="a31f9-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a31f9-146">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a31f9-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="a31f9-147">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a31f9-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a31f9-148">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="a31f9-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="a31f9-149">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="a31f9-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="a31f9-150">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="a31f9-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
