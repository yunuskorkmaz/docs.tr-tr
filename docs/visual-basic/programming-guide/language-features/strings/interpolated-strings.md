---
title: "Ara değerli dizeler (Visual Basic)"
ms.date: 10/31/2017
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f865d5a7167847bf869d70a39570413dac271a2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="4de26-102">Ara değerli dizeler (Visual Basic Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4de26-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="4de26-103">Dizeleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4de26-103">Used to construct strings.</span></span>  <span data-ttu-id="4de26-104">Ara değerli bir dize içeren bir şablon dize gibi görünüyor *Ara değerli ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="4de26-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="4de26-105">Ara değerli bir dize içeriyor Ara değerli ifadeleri kendi dize Beyanları ile değiştiren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="4de26-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="4de26-106">Bu özellik, Visual Basic 14 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4de26-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="4de26-107">Ara değerli bir dize bağımsız değişkenleri daha anlamak daha kolay bir [bileşik biçim dizesi](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="4de26-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="4de26-108">Örneğin, Ara değerli dize</span><span class="sxs-lookup"><span data-stu-id="4de26-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="4de26-109">'{name}', iki ara değerli ifadeleri içerir ve '{saatleri: ss}'.</span><span class="sxs-lookup"><span data-stu-id="4de26-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="4de26-110">Eşdeğer bileşik biçim dizesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="4de26-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="4de26-111">Ara değerli bir dize yapıdır:</span><span class="sxs-lookup"><span data-stu-id="4de26-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="4de26-112">burada:</span><span class="sxs-lookup"><span data-stu-id="4de26-112">where:</span></span> 

- <span data-ttu-id="4de26-113">*Alan genişliği* alanında karakter sayısını gösteren imzalı bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="4de26-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="4de26-114">Pozitif ise sağa hizalı alanıdır; negatifse, sola hizalı.</span><span class="sxs-lookup"><span data-stu-id="4de26-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="4de26-115">*Biçim dizesi* bir biçim dizesi biçimlendirilen nesne türü için uygundur.</span><span class="sxs-lookup"><span data-stu-id="4de26-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="4de26-116">Örneğin, bir <xref:System.DateTime> değeri, onu olabilir bir [standart tarih ve saat biçim dizesi](~/docs/standard/base-types/standard-date-and-time-format-strings.md) "D" veya "d" gibi.</span><span class="sxs-lookup"><span data-stu-id="4de26-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4de26-117">Arasında bir boşluk olamaz `$` ve `"` dize başlar.</span><span class="sxs-lookup"><span data-stu-id="4de26-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="4de26-118">Bunun yapılması bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4de26-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="4de26-119">Ara değerli bir dize kullanabileceğiniz bir değişmez dize değeri her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4de26-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="4de26-120">Ara değerli dize ara değerli dizesiyle kodu yürütür her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="4de26-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="4de26-121">Bu, tanım ve Ara değerli bir dize değerlendirmesine ayırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4de26-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="4de26-122">Süslü ayraç içerecek şekilde ("{" veya "}") iki süslü ayraçlar, bir ara değerli dizesinde kullanmak "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="4de26-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="4de26-123">Daha fazla ayrıntı için örtük dönüşümler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4de26-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="4de26-124">Ara değerli dize tırnak işareti ("), iki nokta üst üste (:) veya virgül (,) gibi ara değerli bir dize olarak özel bir anlamı olan diğer karakterler içeriyorsa, bunlar değişmez değer metinde oluşma ya da virgülle ayrılan bir ifadede eklenmelidir kaçış Dil öğeleri ara değerli bir ifadede dahil olmaları durumunda parantez.</span><span class="sxs-lookup"><span data-stu-id="4de26-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="4de26-125">Aşağıdaki örnek sonuç dizesinde eklemek için tırnak işaretleri çıkışları ve ifade sınırlandırmak için parantez kullanır `(age == 1 ? "" : "s")` böylece iki nokta üst üste bir biçim dizesi başlayan olarak yorumlanır değil.</span><span class="sxs-lookup"><span data-stu-id="4de26-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="4de26-126">Örtük dönüşümler</span><span class="sxs-lookup"><span data-stu-id="4de26-126">Implicit Conversions</span></span>  

<span data-ttu-id="4de26-127">Ara değerli bir dizeden üç örtük tür dönüşümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="4de26-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="4de26-128">Ara değerli bir dizeye dönüştürme bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4de26-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="4de26-129">Aşağıdaki örnek, Ara değerli dizesi ifadeleri kendi dize Beyanları ile değiştirilmiş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="4de26-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="4de26-130">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4de26-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="4de26-131">Bu dize yorumlama son sonucudur.</span><span class="sxs-lookup"><span data-stu-id="4de26-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="4de26-132">Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}") için tek bir büyük ayraç dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="4de26-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="4de26-133">Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanıza olanak değişkeni dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.</span><span class="sxs-lookup"><span data-stu-id="4de26-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="4de26-134">Bu, tek tek kültürler için doğru sayısal ve tarih biçimleri gibi şeyler dahil etmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="4de26-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="4de26-135">Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), açıkça veya örtük çağırarak biçim dizesi kadar çift ayraç kalır <xref:System.Object.ToString> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4de26-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="4de26-136">{0}, {1} ve benzeri için tüm kapsanan ilişkilendirme ifadeleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="4de26-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="4de26-137">Aşağıdaki örnek, alan ve özellik değerlerini yanı sıra üyeleri görüntülemek için yansıma kullanır. bir <xref:System.IFormattable> Ara değerli bir dizeden oluşturulmuş değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4de26-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="4de26-138">Ayrıca geçirir <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4de26-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="4de26-139">Ara değerli dize yalnızca yansıma kullanarak Denetlenmekte olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4de26-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="4de26-140">Yöntemi, aşağıdaki gibi biçimlendirme dizeye geçip geçmediğini <xref:System.Console.WriteLine(System.String)>biçimi öğelerinden çözümlendiği ve sonucu dize döndürdü.</span><span class="sxs-lookup"><span data-stu-id="4de26-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="4de26-141">Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> bileşik biçim dizesi gösteren değişkeni.</span><span class="sxs-lookup"><span data-stu-id="4de26-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="4de26-142">Bileşik biçim dizesi ve nasıl dizeyi sonucunda işler İnceleme Örneğin, bir sorgu oluşturuyorsanız ekleme saldırılara karşı korunmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4de26-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="4de26-143">A <xref:System.FormattableString> de içerir:</span><span class="sxs-lookup"><span data-stu-id="4de26-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="4de26-144">A <xref:System.FormattableString.ToString> için bir sonuç dize üreten aşırı <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="4de26-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="4de26-145">A <xref:System.FormattableString.Invariant%2A> için bir dize üreten yöntem <xref:System.Globalization.CultureInfo.InvariantCulture>.</span><span class="sxs-lookup"><span data-stu-id="4de26-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="4de26-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> belirtilen kültür için bir sonuç dize üreten yöntem.</span><span class="sxs-lookup"><span data-stu-id="4de26-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="4de26-147">Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), format kadar çift ayraç kalır.</span><span class="sxs-lookup"><span data-stu-id="4de26-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="4de26-148">{0}, {1} ve benzeri için tüm kapsanan ilişkilendirme ifadeleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="4de26-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="4de26-149">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4de26-149">See Also</span></span>  
<span data-ttu-id="4de26-150">f<xref:System.IFormattable?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4de26-150">f <xref:System.IFormattable?displayProperty=nameWithType></span></span>   
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="4de26-151">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="4de26-151">Visual Basic Language Reference</span></span>](index.md)  
 