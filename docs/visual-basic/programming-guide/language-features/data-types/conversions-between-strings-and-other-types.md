---
description: 'Hakkında daha fazla bilgi edinin: dizeler ve diğer türler arasında dönüştürmeler (Visual Basic)'
title: Dizeler ve Diğer Türler Arasında Dönüştürmeler
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: c0f7f7637d173d039d58b2516fba41ae55b990ac
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477222"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="5c439-103">Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c439-103">Conversions Between Strings and Other Types (Visual Basic)</span></span>

<span data-ttu-id="5c439-104">Bir sayısal, `Boolean` veya tarih/saat değerini bir olarak dönüştürebilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="5c439-104">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="5c439-105">Ters yönde, bir dize değerinden sayısal, `Boolean` , veya `Date` — dize içeriği belirtilen hedef veri türünün geçerli bir değeri olarak yorumlanabilecek şekilde de dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c439-105">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="5c439-106">Bu durumda, bir çalışma zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="5c439-106">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="5c439-107">Her iki yönde de tüm bu atamaların dönüştürmeleri daraltma dönüştürmelerinde.</span><span class="sxs-lookup"><span data-stu-id="5c439-107">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="5c439-108">Tür dönüştürme anahtar sözcüklerini ( `CBool` , `CByte` ,,,, `CDate` , `CDbl` , `CDec` `CInt` `CLng` `CSByte` , `CShort` , `CSng` , `CStr` ,,,, `CUInt` `CULng` `CUShort` ve `CType` ) kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5c439-108">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="5c439-109"><xref:Microsoft.VisualBasic.Strings.Format%2A>Ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> işlevleri, dizeler ve sayılar arasındaki dönüştürmeler üzerinde ek denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c439-109">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="5c439-110">Bir sınıf veya yapı tanımladıysanız, sınıf veya yapınızın türü dönüştürme işleçlerini tanımlayabilirsiniz `String` .</span><span class="sxs-lookup"><span data-stu-id="5c439-110">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="5c439-111">Daha fazla bilgi için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5c439-111">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="5c439-112">Sayıları dizelere dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5c439-112">Conversion of Numbers to Strings</span></span>  

 <span data-ttu-id="5c439-113">`Format`Bir sayıyı biçimlendirilmiş bir dizeye dönüştürmek için işlevini kullanabilirsiniz. Bu, yalnızca uygun basamakları değil, bir para birimi işareti (örneğin `$` ), binlik ayırıcıları veya *Basamak gruplama sembolleri* (gibi) `,` ve bir ondalık ayırıcısı (gibi) biçimlendirme gibi simgeleri de içerebilir `.` .</span><span class="sxs-lookup"><span data-stu-id="5c439-113">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="5c439-114">`Format`, Windows **Denetim Masası**'Nda belirtilen **Bölgesel Seçenekler** ayarlarına göre otomatik olarak uygun sembolleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c439-114">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="5c439-115">`&`Aşağıdaki örnekte gösterildiği gibi, birleştirme () işlecinin bir sayıyı örtük olarak bir dizeye dönüştürebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5c439-115">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="5c439-116">Dizelerin sayılara dönüştürülmesi</span><span class="sxs-lookup"><span data-stu-id="5c439-116">Conversion of Strings to Numbers</span></span>  

 <span data-ttu-id="5c439-117">`Val`Bir dizedeki rakamları bir sayıya açıkça dönüştürmek için işlevini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5c439-117">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="5c439-118">`Val` bir rakam, boşluk, sekme, satır akışı veya nokta dışında bir karakterle karşılaşana kadar dizeyi okur.</span><span class="sxs-lookup"><span data-stu-id="5c439-118">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="5c439-119">"&O" ve "&H" dizileri, sayı sisteminin temelini değiştirir ve taramayı sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="5c439-119">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="5c439-120">Okumayı durdurmadan, `Val` tüm uygun karakterleri sayısal bir değere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5c439-120">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="5c439-121">Örneğin, aşağıdaki ifade değeri döndürür `141.825` .</span><span class="sxs-lookup"><span data-stu-id="5c439-121">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="5c439-122">Visual Basic bir dizeyi sayısal bir değere dönüştürdüğünde, binlik ayırıcısını, ondalık ayırıcıyı ve para birimi simgesini yorumlamak için Windows **Denetim Masası** 'Nda belirtilen **Bölgesel Seçenekler** ayarlarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5c439-122">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="5c439-123">Bu, dönüştürmenin bir ayar altında başarılı olabileceği ancak başka bir şekilde başarısız olabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5c439-123">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="5c439-124">Örneğin, `"$14.20"` İngilizce (Birleşik Devletler) yerel ayarında kabul edilebilir, ancak herhangi bir Fransızca yerel ayarda yoktur.</span><span class="sxs-lookup"><span data-stu-id="5c439-124">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c439-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c439-125">See also</span></span>

- [<span data-ttu-id="5c439-126">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="5c439-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5c439-127">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="5c439-127">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5c439-128">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="5c439-128">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5c439-129">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="5c439-129">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="5c439-130">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="5c439-130">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="5c439-131">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="5c439-131">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="5c439-132">Tür Dönüştürme İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5c439-132">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5c439-133">Genelleştirilmiş ve yerelleştirilmiş uygulamalar geliştirin</span><span class="sxs-lookup"><span data-stu-id="5c439-133">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)
