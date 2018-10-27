---
title: Ara değerli dizeler (Visual Basic)
ms.date: 10/31/2017
ms.openlocfilehash: 68194d4251f7057a070535531e0d4c1ad9154530
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50038467"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="39b09-102">Ara değerli dizeler (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="39b09-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="39b09-103">Dizeleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="39b09-103">Used to construct strings.</span></span>  <span data-ttu-id="39b09-104">İlişkilendirilmiş dize içeren bir şablon dize gibi görünüyor *ilişkilendirilmiş ifade*.</span><span class="sxs-lookup"><span data-stu-id="39b09-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="39b09-105">Bir aradeğerlendirme dizesinde içerdiği ilişkilendirilmiş ifadeler ile bunların dize temsilleri yerini alan bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="39b09-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="39b09-106">Bu özellik, Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39b09-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="39b09-107">İlişkilendirilmiş dize bağımsız değişkenleri daha anlamak daha kolay anlaşılır bir [bileşik biçimlendirme dizesi](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="39b09-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="39b09-108">Örneğin, ilişkilendirilmiş dize</span><span class="sxs-lookup"><span data-stu-id="39b09-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="39b09-109">'{name}', iki ilişkilendirilmiş ifadeler içerir ve '{saat: ss}'.</span><span class="sxs-lookup"><span data-stu-id="39b09-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="39b09-110">Eşdeğer bileşik biçimlendirme dizesi şöyle olur:</span><span class="sxs-lookup"><span data-stu-id="39b09-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="39b09-111">Bir aradeğerlendirme dizesinde yapısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="39b09-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="39b09-112">burada:</span><span class="sxs-lookup"><span data-stu-id="39b09-112">where:</span></span> 

- <span data-ttu-id="39b09-113">*Alan genişliği* alanında karakter sayısını belirten işaretli bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="39b09-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="39b09-114">Pozitif ise sağa hizalı alanıdır; negatif ise sola hizalıdır.</span><span class="sxs-lookup"><span data-stu-id="39b09-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="39b09-115">*Biçim dizesi* bir biçim dizesi, biçimlendirilen nesnenin türü için uygundur.</span><span class="sxs-lookup"><span data-stu-id="39b09-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="39b09-116">Örneğin, bir <xref:System.DateTime> değeri olabilir bir [standart tarih ve saat biçim dizesi](~/docs/standard/base-types/standard-date-and-time-format-strings.md) "D" veya "d" gibi.</span><span class="sxs-lookup"><span data-stu-id="39b09-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39b09-117">Arasında beyaz boşluk olamaz `$` ve `"` , dize başlar.</span><span class="sxs-lookup"><span data-stu-id="39b09-117">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="39b09-118">Bunun yapılması, bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="39b09-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="39b09-119">Bir aradeğerlendirme dizesinde kullanabileceğiniz bir dize sabit değeri her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39b09-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="39b09-120">İlişkilendirilmiş dize ile ilişkilendirilmiş dize kodu yürütür her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="39b09-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="39b09-121">Bu, bir aradeğerlendirme dizesinde değerlendirmesini ve tanımı ayırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="39b09-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="39b09-122">Küme ayracı içerecek şekilde ("{" veya "}") iki küme ayracı, bir aradeğerlendirme dizesinde kullanın "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="39b09-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="39b09-123">Daha fazla ayrıntı için örtülü dönüştürmeler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="39b09-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="39b09-124">İlişkilendirilmiş dize tırnak işareti ("), iki nokta üst üste (:) veya virgül (,) gibi bir aradeğerlendirme dizesinde özel bir anlamı olan diğer karakterler içeriyorsa bunlar değişmez değer metni ortaya ya da ayrılmış bir ifadede eklenmelidir Atlanan Dil öğeleri bir ilişkilendirilmiş ifadede dahil olmaları durumunda parantez.</span><span class="sxs-lookup"><span data-stu-id="39b09-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="39b09-125">Aşağıdaki örnek, tırnak işaretleri, sonuç dizesine eklemek çıkışları ve ifade sınırlandırmak için parantez kullanan `(age == 1 ? "" : "s")` böylece iki noktadan başlayarak bir biçim dizesi olarak yorumlanır değil.</span><span class="sxs-lookup"><span data-stu-id="39b09-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="39b09-126">Örtük dönüşümler</span><span class="sxs-lookup"><span data-stu-id="39b09-126">Implicit Conversions</span></span>  

<span data-ttu-id="39b09-127">Bir aradeğerlendirme dizesinde üç örtük tür dönüştürmelerinde vardır:</span><span class="sxs-lookup"><span data-stu-id="39b09-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="39b09-128">Bir araya alınmış dizeye dönüştürme bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="39b09-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="39b09-129">Aşağıdaki örnek, ilişkilendirilmiş dize ifadeleri ile bunların dize temsilleri değiştirilmiş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="39b09-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="39b09-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="39b09-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="39b09-131">Bir dize yorumu sonucunu budur.</span><span class="sxs-lookup"><span data-stu-id="39b09-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="39b09-132">Tüm oluşumlarını çift kaşlı ayraçlar ("{{" ve "}}") için tek bir küme ayracı dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="39b09-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="39b09-133">Bir araya alınmış dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanıza olanak değişkeni dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.</span><span class="sxs-lookup"><span data-stu-id="39b09-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="39b09-134">Bu, bağımsız kültür için doğru sayısal ve tarih biçimleri gibi şeyler dahil etmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="39b09-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="39b09-135">Tüm oluşumlarını çift kaşlı ayraçlar ("{{" ve "}}"), açıkça veya dolaylı olarak çağırarak biçim dizesi çift kaşlı ayraçlar ermesine <xref:System.Object.ToString> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39b09-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="39b09-136">Tüm kapsanan ilişkilendirme ifadeleri dönüştürülür {0}, {1}ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="39b09-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="39b09-137">Aşağıdaki örnek, üyeleri ve bunun yanı sıra alan ve özellik değerlerini görüntülemek için yansıtma kullanır. bir <xref:System.IFormattable> ilişkilendirilmiş bir dizeden oluşturulan değişken.</span><span class="sxs-lookup"><span data-stu-id="39b09-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="39b09-138">Bu işlem ayrıca geçirir <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="39b09-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="39b09-139">Yalnızca yansıma kullanarak ilişkilendirilmiş dize inceledi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="39b09-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="39b09-140">Aşağıdakiler gibi biçimlendirme yöntemi, bir dizeye geçip geçmediğini <xref:System.Console.WriteLine(System.String)>, biçim öğeleri çözümlendiği ve sonuç dizesi döndürdü.</span><span class="sxs-lookup"><span data-stu-id="39b09-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="39b09-141">Bir araya alınmış dizeye dönüştürme bir <xref:System.FormattableString> bir bileşik biçimlendirme dizesi temsil eden değişken.</span><span class="sxs-lookup"><span data-stu-id="39b09-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="39b09-142">Bileşik biçimlendirme dizesi ve sonuç olarak nasıl dize işleyen İnceleme Örneğin, bir sorgu oluşturuyorsanız bir ekleme saldırısına karşı korumanıza yardımcı.</span><span class="sxs-lookup"><span data-stu-id="39b09-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="39b09-143">A <xref:System.FormattableString> de içerir:</span><span class="sxs-lookup"><span data-stu-id="39b09-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="39b09-144">A <xref:System.FormattableString.ToString> için bir sonuç dizesi oluşturur aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="39b09-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="39b09-145">A <xref:System.FormattableString.Invariant%2A> için bir dize üreten yöntemi <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="39b09-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="39b09-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> yönteminin belirtilen kültür için bir sonuç dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="39b09-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="39b09-147">Tüm oluşumlarını çift kaşlı ayraçlar ("{{" ve "}}"), biçimlendirme kadar çift kaşlı ayraçlar kalır.</span><span class="sxs-lookup"><span data-stu-id="39b09-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="39b09-148">Tüm kapsanan ilişkilendirme ifadeleri dönüştürülür {0}, {1}ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="39b09-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="39b09-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39b09-149">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="39b09-150">Visual Basic Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="39b09-150">Visual Basic Language Reference</span></span>](index.md)  
 