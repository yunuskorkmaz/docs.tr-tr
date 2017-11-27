---
title: "Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 71ece18d4ce33b7b637410110e825b389affcd67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="b50d1-102">Dizeler ve Diğer Türleri Arasında Dönüştürmeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b50d1-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="b50d1-103">Bir sayısal dönüştürebilirsiniz `Boolean`, veya tarih/saat değerine bir `String`.</span><span class="sxs-lookup"><span data-stu-id="b50d1-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="b50d1-104">Ters yönde de dönüştürebilirsiniz — bir sayısal dize değerinden `Boolean`, veya `Date` — dize içeriği hedef veri türü geçerli bir değer yorumlanacak sağlanan.</span><span class="sxs-lookup"><span data-stu-id="b50d1-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="b50d1-105">Desteklemiyorlarsa, bir çalışma zamanı hatası oluşur.</span><span class="sxs-lookup"><span data-stu-id="b50d1-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="b50d1-106">Tüm bu atamaları herhangi bir yönde dönüştürmelerde daraltma dönüşümleri.</span><span class="sxs-lookup"><span data-stu-id="b50d1-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="b50d1-107">Tür Dönüşüm anahtar sözcükleri kullanması gereken (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, ve `CType`).</span><span class="sxs-lookup"><span data-stu-id="b50d1-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="b50d1-108"><xref:Microsoft.VisualBasic.Strings.Format%2A> Ve <xref:Microsoft.VisualBasic.Conversion.Val%2A> işlevleri dizeler ve sayılar arasında dönüştürmeler üzerinde ek denetim sunar.</span><span class="sxs-lookup"><span data-stu-id="b50d1-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="b50d1-109">Bir sınıf veya yapı tanımladıysanız, tür dönüştürme işleçleri arasında tanımlayabilirsiniz `String` ve sınıf veya yapı türü.</span><span class="sxs-lookup"><span data-stu-id="b50d1-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="b50d1-110">Daha fazla bilgi için bkz: [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b50d1-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="b50d1-111">Sayıların dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b50d1-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="b50d1-112">Kullanabileceğiniz `Format` yalnızca uygun rakam içerebilen biçimlendirilmiş bir dize için bir sayı dönüştürmek için çalışır ancak aynı zamanda bir para birimi oturum gibi semboller biçimlendirme (gibi `$`), binlik ayırıcı veya *basamak gruplandırma Simgeler* (gibi `,`) ve ondalık ayırıcı (gibi `.`).</span><span class="sxs-lookup"><span data-stu-id="b50d1-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="b50d1-113">`Format`otomatik olarak göre uygun simgeleri kullanır **Bölgesel Seçenekler** Windows belirtilen ayarları **Denetim Masası**.</span><span class="sxs-lookup"><span data-stu-id="b50d1-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="b50d1-114">Unutmayın birleştirme (`&`) işleci dönüştürebilir sayıyı dizeye örtük olarak, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="b50d1-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="b50d1-115">Dizeleri sayılara dönüştürme</span><span class="sxs-lookup"><span data-stu-id="b50d1-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="b50d1-116">Kullanabileceğiniz `Val` açıkça bir dize sayıları sayıya dönüştürme işlevi.</span><span class="sxs-lookup"><span data-stu-id="b50d1-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="b50d1-117">`Val`basamak, boşluk, sekme, satır besleme veya süresi dışında bir karakter bulduğu kadar dize okur.</span><span class="sxs-lookup"><span data-stu-id="b50d1-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="b50d1-118">Dizileri "& O" ve "& H" sayı sistemini tabanı alter ve tarama sonlanır.</span><span class="sxs-lookup"><span data-stu-id="b50d1-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="b50d1-119">Okuma, durduruluncaya kadar `Val` tüm uygun karakterleri sayısal bir değere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="b50d1-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="b50d1-120">Örneğin, aşağıdaki ifade değerini verir `141.825`.</span><span class="sxs-lookup"><span data-stu-id="b50d1-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="b50d1-121">Zaman [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sayısal bir değeri dizeye dönüştürür, kullandığı **Bölgesel Seçenekler** Windows belirtilen ayarları **Denetim Masası** binlerce yorumlamaya ayırıcı, ondalık ayırıcı, ve para birimi simgesi.</span><span class="sxs-lookup"><span data-stu-id="b50d1-121">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="b50d1-122">Başka bir deyişle, bir dönüştürme altında bir ancak başka ayarlama başarılı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b50d1-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="b50d1-123">Örneğin, `"$14.20"` kabul edilebilir İngilizce (ABD) yerel ancak Fransızca tüm yerel ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b50d1-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50d1-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b50d1-124">See Also</span></span>  
 [<span data-ttu-id="b50d1-125">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="b50d1-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="b50d1-126">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="b50d1-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="b50d1-127">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="b50d1-127">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="b50d1-128">Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür</span><span class="sxs-lookup"><span data-stu-id="b50d1-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="b50d1-129">Dizi dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="b50d1-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="b50d1-130">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b50d1-130">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="b50d1-131">Tür dönüşüm işlevleri</span><span class="sxs-lookup"><span data-stu-id="b50d1-131">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="b50d1-132">.NET Framework tabanlı Uluslararası uygulamalara giriş</span><span class="sxs-lookup"><span data-stu-id="b50d1-132">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
