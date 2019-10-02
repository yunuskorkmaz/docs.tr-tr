---
title: Dize veri türü (Visual Basic)
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
ms.openlocfilehash: 6d2fd226735622de5cd7197060c05b8ac12b69f1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696838"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="66b3d-102">Dize veri türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66b3d-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="66b3d-103">0 ile 65535 arasında bir değer olarak aralıktaki işaretsiz 16 bit (2 baytlık) kod noktalarının dizilerini barındırır.</span><span class="sxs-lookup"><span data-stu-id="66b3d-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="66b3d-104">Her *kod noktası*veya karakter kodu, tek bir Unicode karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="66b3d-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="66b3d-105">Dize, 0 ile yaklaşık 2.000.000.000 (2 ^ 31) Unicode karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66b3d-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66b3d-106">Remarks</span></span>  
 <span data-ttu-id="66b3d-107">@No__t-2 öğelerinden oluşan bir dizi olan `Char()` dizi Yönetimi ek yükü olmadan birden çok karakteri tutmak için `String` veri türünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="66b3d-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="66b3d-108">@No__t-0 ' ın varsayılan değeri, `Nothing` ' dir (null bir başvurudur).</span><span class="sxs-lookup"><span data-stu-id="66b3d-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="66b3d-109">Bunun boş dize (değer `""`) ile aynı olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66b3d-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="66b3d-110">Unicode karakterler</span><span class="sxs-lookup"><span data-stu-id="66b3d-110">Unicode Characters</span></span>  
 <span data-ttu-id="66b3d-111">Unicode 'un ilk 128 kod noktası (0 – 127), standart bir ABD klavyesinde bulunan harflere ve simgelere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="66b3d-112">Bu ilk 128 kod noktası, ASCII karakter kümesi tarafından tanımlananlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="66b3d-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="66b3d-113">İkinci 128 kod noktaları (128 – 255) Latin tabanlı alfabe harfleri, vurgular, para birimi sembolleri ve kesirler gibi özel karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="66b3d-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="66b3d-114">Unicode, çok çeşitli semboller için kalan kod noktalarını (256-65535) kullanır.</span><span class="sxs-lookup"><span data-stu-id="66b3d-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="66b3d-115">Bu, dünya genelindeki metinsel karakter, Aksanlar ve matematik ve teknik sembolleri içerir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="66b3d-116">@No__t-0 ve <xref:System.Char.IsPunctuation%2A> gibi yöntemleri, bir `String` değişkeninde tek bir karakter üzerinde, Unicode sınıflandırmasını belirleyebilmeniz için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b3d-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="66b3d-117">Biçim gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="66b3d-117">Format Requirements</span></span>  
 <span data-ttu-id="66b3d-118">@No__t-0 sabit değerini tırnak işaretleri içine almalısınız (`" "`).</span><span class="sxs-lookup"><span data-stu-id="66b3d-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="66b3d-119">Dizedeki karakterlerden biri olarak bir tırnak işareti eklemeniz gerekiyorsa, iki bitişik tırnak işareti (`""`) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="66b3d-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="66b3d-120">Aşağıdaki örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-120">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="66b3d-121">Dizedeki bir tırnak işaretini temsil eden bitişik tırnak işaretlerinin, `String` sabit değerinin başlayacağı ve sonundaki tırnak işaretlerinden bağımsız olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66b3d-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="66b3d-122">Dize Işlemeleri</span><span class="sxs-lookup"><span data-stu-id="66b3d-122">String Manipulations</span></span>  
 <span data-ttu-id="66b3d-123">Bir `String` değişkenine bir dize atadıktan sonra, bu dize *sabittir*, bu da uzunluğunu veya içeriğini değiştiremeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="66b3d-124">Bir dizeyi dilediğiniz şekilde değiştirdiğinizde, Visual Basic yeni bir dize oluşturur ve öncekini terk ediyor.</span><span class="sxs-lookup"><span data-stu-id="66b3d-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="66b3d-125">@No__t-0 değişkeni daha sonra yeni dizeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="66b3d-126">@No__t-0 değişkeninin içeriğini çeşitli dize işlevleri kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b3d-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="66b3d-127">Aşağıdaki örnekte <xref:Microsoft.VisualBasic.Strings.Left%2A> işlevi gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="66b3d-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="66b3d-128">Başka bir bileşen tarafından oluşturulan bir dize, başında veya sonunda boşluklarla doldurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="66b3d-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="66b3d-129">Böyle bir dize alırsanız, bu boşlukları kaldırmak için <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A> ve <xref:Microsoft.VisualBasic.Strings.RTrim%2A> işlevlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66b3d-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="66b3d-130">Dize işlemeleri hakkında daha fazla bilgi için bkz. [dizeler](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="66b3d-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="66b3d-131">Programlama Ipuçları</span><span class="sxs-lookup"><span data-stu-id="66b3d-131">Programming Tips</span></span>  
  
- <span data-ttu-id="66b3d-132">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="66b3d-132">**Negative Numbers.**</span></span> <span data-ttu-id="66b3d-133">@No__t-0 tarafından tutulan karakterlerin işaretsiz olduğunu ve negatif değerleri temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66b3d-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="66b3d-134">Herhangi bir durumda, sayısal değerleri tutmak için `String` kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="66b3d-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="66b3d-135">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="66b3d-135">**Interop Considerations.**</span></span> <span data-ttu-id="66b3d-136">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlarda dize karakterlerinin farklı bir veri genişliğine (8 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66b3d-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="66b3d-137">Bu bileşene 8 bitlik karakterlerin dize bağımsız değişkenini geçirdiğinizden, yeni Visual Basic kodunuzda `String` yerine `Byte` öğelerinden oluşan bir dizi olan `Byte()` olarak bildirin.</span><span class="sxs-lookup"><span data-stu-id="66b3d-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="66b3d-138">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="66b3d-138">**Type Characters.**</span></span> <span data-ttu-id="66b3d-139">Tanımlayıcı türü karakterini herhangi bir tanımlayıcıya eklemek @no__t `String` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="66b3d-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="66b3d-140">`String` ' ın değişmez değer türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="66b3d-140">`String` has no literal type character.</span></span> <span data-ttu-id="66b3d-141">Ancak derleyici, sabit değerleri (`" "`) `String` olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="66b3d-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="66b3d-142">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="66b3d-142">**Framework Type.**</span></span> <span data-ttu-id="66b3d-143">.NET Framework karşılık gelen tür <xref:System.String?displayProperty=nameWithType> sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="66b3d-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b3d-144">Ayrıca bkz:</span><span class="sxs-lookup"><span data-stu-id="66b3d-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="66b3d-145">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="66b3d-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="66b3d-146">Char veri türü</span><span class="sxs-lookup"><span data-stu-id="66b3d-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="66b3d-147">Tür dönüştürme Işlevleri</span><span class="sxs-lookup"><span data-stu-id="66b3d-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="66b3d-148">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="66b3d-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="66b3d-149">Nasıl yapılır: Imzasız türleri alan bir Windows Işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="66b3d-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="66b3d-150">Veri türlerinin etkili kullanımı</span><span class="sxs-lookup"><span data-stu-id="66b3d-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
