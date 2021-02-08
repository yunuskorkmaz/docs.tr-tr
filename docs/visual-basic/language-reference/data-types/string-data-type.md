---
description: 'Daha fazla bilgi edinin: dize veri türü (Visual Basic)'
title: Dize Veri Türü
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
ms.openlocfilehash: 6597a5c4b8ee0eb961d3e33bee52ae493068da35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792121"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="443c8-103">Dize Veri Türü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="443c8-103">String Data Type (Visual Basic)</span></span>

<span data-ttu-id="443c8-104">0 ile 65535 arasında bir değer olarak aralıktaki işaretsiz 16 bit (2 baytlık) kod noktalarının dizilerini barındırır.</span><span class="sxs-lookup"><span data-stu-id="443c8-104">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="443c8-105">Her *kod noktası* veya karakter kodu, tek bir Unicode karakteri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="443c8-105">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="443c8-106">Dize, 0 ile yaklaşık 2.000.000.000 (2 ^ 31) Unicode karakter içerebilir.</span><span class="sxs-lookup"><span data-stu-id="443c8-106">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="443c8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="443c8-107">Remarks</span></span>  

 <span data-ttu-id="443c8-108">`String`Dizi yönetim ek yükü olmadan birden fazla karakter tutmak için veri türünü kullanın `Char()` , bir dizi `Char` öğe.</span><span class="sxs-lookup"><span data-stu-id="443c8-108">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="443c8-109">Öğesinin varsayılan değeri `String` `Nothing` (null başvurusu).</span><span class="sxs-lookup"><span data-stu-id="443c8-109">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="443c8-110">Bunun boş dize (değer) ile aynı olmadığına unutmayın `""` .</span><span class="sxs-lookup"><span data-stu-id="443c8-110">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="443c8-111">Unicode karakterler</span><span class="sxs-lookup"><span data-stu-id="443c8-111">Unicode Characters</span></span>  

 <span data-ttu-id="443c8-112">Unicode 'un ilk 128 kod noktası (0 – 127), standart bir ABD klavyesinde bulunan harflere ve simgelere karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="443c8-112">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="443c8-113">Bu ilk 128 kod noktası, ASCII karakter kümesi tarafından tanımlananlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="443c8-113">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="443c8-114">İkinci 128 kod noktaları (128 – 255) Latin tabanlı alfabe harfleri, vurgular, para birimi sembolleri ve kesirler gibi özel karakterleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="443c8-114">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="443c8-115">Unicode, çok çeşitli semboller için kalan kod noktalarını (256-65535) kullanır.</span><span class="sxs-lookup"><span data-stu-id="443c8-115">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="443c8-116">Bu, dünya genelindeki metinsel karakter, Aksanlar ve matematik ve teknik sembolleri içerir.</span><span class="sxs-lookup"><span data-stu-id="443c8-116">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="443c8-117"><xref:System.Char.IsDigit%2A> <xref:System.Char.IsPunctuation%2A> Unicode sınıflandırmasını belirleyebilmeniz için, ve gibi yöntemleri bir değişkende tek bir karakter olarak kullanabilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="443c8-117">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="443c8-118">Biçim gereksinimleri</span><span class="sxs-lookup"><span data-stu-id="443c8-118">Format Requirements</span></span>  

 <span data-ttu-id="443c8-119">Bir `String` sabit değer tırnak işaretleri () içine alınmalıdır `" "` .</span><span class="sxs-lookup"><span data-stu-id="443c8-119">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="443c8-120">Dizedeki karakterlerden biri olarak bir tırnak işareti eklemeniz gerekiyorsa, iki bitişik tırnak işareti ( `""` ) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="443c8-120">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="443c8-121">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="443c8-121">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="443c8-122">Dizedeki bir tırnak işaretini temsil eden bitişik tırnak işaretlerinin, sabit değerin başlangıç ve bitiş tırnak işaretleriyle bağımsız olduğunu unutmayın `String` .</span><span class="sxs-lookup"><span data-stu-id="443c8-122">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="443c8-123">Dize Işlemeleri</span><span class="sxs-lookup"><span data-stu-id="443c8-123">String Manipulations</span></span>  

 <span data-ttu-id="443c8-124">Bir değişkene bir dize atadıktan sonra `String` , bu dize *sabittir*, bu da uzunluğunu veya içeriğini değiştiremeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="443c8-124">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="443c8-125">Bir dizeyi dilediğiniz şekilde değiştirdiğinizde, Visual Basic yeni bir dize oluşturur ve öncekini terk ediyor.</span><span class="sxs-lookup"><span data-stu-id="443c8-125">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="443c8-126">`String`Değişken daha sonra yeni dizeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="443c8-126">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="443c8-127">Bir `String` değişkenin içeriğini çeşitli dize işlevleri kullanarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="443c8-127">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="443c8-128">Aşağıdaki örnekte <xref:Microsoft.VisualBasic.Strings.Left%2A> işlevi gösterilmektedir</span><span class="sxs-lookup"><span data-stu-id="443c8-128">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="443c8-129">Başka bir bileşen tarafından oluşturulan bir dize, başında veya sonunda boşluklarla doldurulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="443c8-129">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="443c8-130">Böyle bir dize alırsanız, <xref:Microsoft.VisualBasic.Strings.Trim%2A> <xref:Microsoft.VisualBasic.Strings.LTrim%2A> <xref:Microsoft.VisualBasic.Strings.RTrim%2A> bu boşlukları kaldırmak için,, ve işlevlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="443c8-130">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="443c8-131">Dize işlemeleri hakkında daha fazla bilgi için bkz. [dizeler](../../programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="443c8-131">For more information about string manipulations, see [Strings](../../programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="443c8-132">Programlama İpuçları</span><span class="sxs-lookup"><span data-stu-id="443c8-132">Programming Tips</span></span>  
  
- <span data-ttu-id="443c8-133">**Negatif sayılar.**</span><span class="sxs-lookup"><span data-stu-id="443c8-133">**Negative Numbers.**</span></span> <span data-ttu-id="443c8-134">Tarafından tutulan karakterlerin `String` işaretsiz olduğunu ve negatif değerleri temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="443c8-134">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="443c8-135">Herhangi bir durumda, `String` sayısal değerleri tutmak için kullanmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="443c8-135">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="443c8-136">**Birlikte çalışma konuları.**</span><span class="sxs-lookup"><span data-stu-id="443c8-136">**Interop Considerations.**</span></span> <span data-ttu-id="443c8-137">Otomasyon veya COM nesneleri gibi .NET Framework için yazılmayan bileşenlerle arabirimleriniz varsa, diğer ortamlarda dize karakterlerinin farklı bir veri genişliğine (8 bit) sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="443c8-137">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="443c8-138">Bu bileşene 8 bitlik karakterlerin dize bağımsız değişkenini geçirdiğinizden, bunu `Byte()` `Byte` Yeni Visual Basic kodunuzda değil, bir dizi öğe olarak bildirin `String` .</span><span class="sxs-lookup"><span data-stu-id="443c8-138">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="443c8-139">**Tür karakterleri.**</span><span class="sxs-lookup"><span data-stu-id="443c8-139">**Type Characters.**</span></span> <span data-ttu-id="443c8-140">Tanımlayıcı türü karakteri `$` herhangi bir tanımlayıcıya eklemek bunu `String` veri türüne zorlar.</span><span class="sxs-lookup"><span data-stu-id="443c8-140">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="443c8-141">`String` değişmez değer türü karakteri yok.</span><span class="sxs-lookup"><span data-stu-id="443c8-141">`String` has no literal type character.</span></span> <span data-ttu-id="443c8-142">Ancak derleyici, değişmez değerleri () olarak tırnak işaretleri içinde değerlendirir `" "` `String` .</span><span class="sxs-lookup"><span data-stu-id="443c8-142">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="443c8-143">**Çerçeve türü.**</span><span class="sxs-lookup"><span data-stu-id="443c8-143">**Framework Type.**</span></span> <span data-ttu-id="443c8-144">.NET Framework karşılık gelen tür <xref:System.String?displayProperty=nameWithType> sınıftır.</span><span class="sxs-lookup"><span data-stu-id="443c8-144">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443c8-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="443c8-145">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="443c8-146">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="443c8-146">Data Types</span></span>](index.md)
- [<span data-ttu-id="443c8-147">Char Veri Türü</span><span class="sxs-lookup"><span data-stu-id="443c8-147">Char Data Type</span></span>](char-data-type.md)
- [<span data-ttu-id="443c8-148">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="443c8-148">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="443c8-149">Dönüştürme Özeti</span><span class="sxs-lookup"><span data-stu-id="443c8-149">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="443c8-150">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma</span><span class="sxs-lookup"><span data-stu-id="443c8-150">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="443c8-151">Veri Türlerinin Etkili Kullanımı</span><span class="sxs-lookup"><span data-stu-id="443c8-151">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
