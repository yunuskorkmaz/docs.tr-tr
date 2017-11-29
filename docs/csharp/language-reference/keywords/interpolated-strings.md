---
title: "Ara değerli dizeler (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b8a1fe0be82a0e09d61c66ed463199ff626c9faa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="32d00-102">Ara değerli dizeler (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="32d00-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="32d00-103">Dizeleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32d00-103">Used to construct strings.</span></span>  <span data-ttu-id="32d00-104">Ara değerli bir dize içeren bir şablon dize gibi görünüyor *Ara değerli ifadeleri*.</span><span class="sxs-lookup"><span data-stu-id="32d00-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="32d00-105">Ara değerli bir dize içeriyor Ara değerli ifadeleri kendi dize Beyanları ile değiştiren bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="32d00-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="32d00-106">Bu özellik, C# 6 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32d00-106">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="32d00-107">Ara değerli bir dize bağımsız değişkenleri daha anlamak daha kolay bir [bileşik biçim dizesi](../../../standard/base-types/composite-formatting.md#composite-format-string).</span><span class="sxs-lookup"><span data-stu-id="32d00-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="32d00-108">Örneğin, Ara değerli dize</span><span class="sxs-lookup"><span data-stu-id="32d00-108">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
<span data-ttu-id="32d00-109">'{name}', iki ara değerli ifadeleri içerir ve '{saat: ss}'.</span><span class="sxs-lookup"><span data-stu-id="32d00-109">contains two interpolated expressions, '{name}' and '{hour:hh}'.</span></span> <span data-ttu-id="32d00-110">Eşdeğer bileşik biçim dizesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="32d00-110">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="32d00-111">Ara değerli bir dize yapıdır:</span><span class="sxs-lookup"><span data-stu-id="32d00-111">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="32d00-112">burada:</span><span class="sxs-lookup"><span data-stu-id="32d00-112">where:</span></span> 

- <span data-ttu-id="32d00-113">*Alan genişliği* alanında karakter sayısını gösteren imzalı bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="32d00-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="32d00-114">Pozitif ise sağa hizalı alanıdır; negatifse, sola hizalı.</span><span class="sxs-lookup"><span data-stu-id="32d00-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="32d00-115">*Biçim dizesi* bir biçim dizesi biçimlendirilen nesne türü için uygundur.</span><span class="sxs-lookup"><span data-stu-id="32d00-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="32d00-116">Örneğin, bir <xref:System.DateTime> değeri, bir standart tarih ve saat biçim dizesi "D" veya "d" gibi olabilir.</span><span class="sxs-lookup"><span data-stu-id="32d00-116">For example, for a <xref:System.DateTime> value, it could be a standard date and time format string such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32d00-117">Arasında bir boşluk olamaz `$` ve `"` dize başlar.</span><span class="sxs-lookup"><span data-stu-id="32d00-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="32d00-118">Bunun yapılması, derleme zamanı hata neden olur.</span><span class="sxs-lookup"><span data-stu-id="32d00-118">Doing so causes a compile time error.</span></span>

 <span data-ttu-id="32d00-119">Ara değerli bir dize kullanabileceğiniz bir değişmez dize değeri her yerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32d00-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="32d00-120">Ara değerli dize ara değerli dizesiyle kodu yürütür her zaman değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="32d00-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="32d00-121">Bu, tanım ve Ara değerli bir dize değerlendirmesine ayırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="32d00-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="32d00-122">Süslü ayraç içerecek şekilde ("{" veya "}") iki süslü ayraçlar, bir ara değerli dizesinde kullanmak "{{" veya "}}".</span><span class="sxs-lookup"><span data-stu-id="32d00-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="32d00-123">Daha fazla ayrıntı için örtük dönüşümler bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32d00-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="32d00-124">Ara değerli dize tırnak işareti ("), iki nokta üst üste (:) veya virgül (,) gibi ara değerli bir dize olarak özel bir anlamı olan diğer karakterler içeriyorsa, bunlar değişmez değer metinde oluşma ya da virgülle ayrılan bir ifadede eklenmelidir kaçış Dil öğeleri ara değerli bir ifadede dahil olmaları durumunda parantez.</span><span class="sxs-lookup"><span data-stu-id="32d00-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="32d00-125">Aşağıdaki örnek sonuç dizesinde eklemek için tırnak işaretleri çıkışları ve ifade sınırlandırmak için parantez kullanır `(age == 1 ? "" : "s")` böylece iki nokta üst üste bir biçim dizesi başlayan olarak yorumlanır değil.</span><span class="sxs-lookup"><span data-stu-id="32d00-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

<span data-ttu-id="32d00-126">Harfi harfine dizeler Kullan'ı değiştirilmiş `$` karakter arkasından `@` karakter.</span><span class="sxs-lookup"><span data-stu-id="32d00-126">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="32d00-127">Harfi harfine dizeler hakkında daha fazla bilgi için bkz: [dize](string.md) konu.</span><span class="sxs-lookup"><span data-stu-id="32d00-127">For more information about verbatim strings, see the [string](string.md) topic.</span></span> <span data-ttu-id="32d00-128">Aşağıdaki kod verbatim Ara değerli bir dize kullanarak önceki kod parçacığında, değiştirilmiş bir sürümüdür:</span><span class="sxs-lookup"><span data-stu-id="32d00-128">The following code is a modified version of the previous snippet using a verbatim interpolated string:</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

<span data-ttu-id="32d00-129">Harfi harfine dizeler değil uyma biçimlendirme değişiklikleri gerekli olduğu `\` çıkış sıraları.</span><span class="sxs-lookup"><span data-stu-id="32d00-129">The formatting changes are necessary because verbatim strings do not obey `\` escape sequences.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32d00-130">`$` Belirteci önce görünmelidir `@` verbatim Ara değerli dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="32d00-130">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>


## <a name="implicit-conversions"></a><span data-ttu-id="32d00-131">Örtük dönüşümler</span><span class="sxs-lookup"><span data-stu-id="32d00-131">Implicit Conversions</span></span>  

<span data-ttu-id="32d00-132">Ara değerli bir dizeden üç örtük tür dönüşümleri vardır:</span><span class="sxs-lookup"><span data-stu-id="32d00-132">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="32d00-133">Ara değerli bir dizeye dönüştürme bir <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="32d00-133">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="32d00-134">Aşağıdaki örnek, Ara değerli dizesi ifadeleri kendi dize Beyanları ile değiştirilmiş bir dize döndürür.</span><span class="sxs-lookup"><span data-stu-id="32d00-134">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="32d00-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="32d00-135">For example:</span></span>

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   <span data-ttu-id="32d00-136">Bu dize yorumlama son sonucudur.</span><span class="sxs-lookup"><span data-stu-id="32d00-136">This is the final result of a string interpretation.</span></span> <span data-ttu-id="32d00-137">Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}") için tek bir büyük ayraç dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="32d00-137">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="32d00-138">Ara değerli bir dizeye dönüştürme bir <xref:System.IFormattable> birden çok sonuç oluşturmanıza olanak değişkeni dizeleri tek bir kültüre özgü içerikle <xref:System.IFormattable> örneği.</span><span class="sxs-lookup"><span data-stu-id="32d00-138">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="32d00-139">Bu, tek tek kültürler için doğru sayısal ve tarih biçimleri gibi şeyler dahil etmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="32d00-139">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="32d00-140">Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), açıkça veya örtük çağırarak biçim dizesi kadar çift ayraç kalır <xref:System.Object.ToString> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32d00-140">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="32d00-141">{0}, {1} ve benzeri için tüm kapsanan ilişkilendirme ifadeleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="32d00-141">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="32d00-142">Aşağıdaki örnek, alan ve özellik değerlerini yanı sıra üyeleri görüntülemek için yansıma kullanır. bir <xref:System.IFormattable> Ara değerli bir dizeden oluşturulmuş değişkeni.</span><span class="sxs-lookup"><span data-stu-id="32d00-142">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="32d00-143">Ayrıca geçirir <xref:System.IFormattable> değişkenini <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32d00-143">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   <span data-ttu-id="32d00-144">Ara değerli dize yalnızca yansıma kullanarak Denetlenmekte olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="32d00-144">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="32d00-145">Yöntemi, aşağıdaki gibi biçimlendirme dizeye geçip geçmediğini <xref:System.Console.WriteLine(System.String)>biçimi öğelerinden çözümlendiği ve sonucu dize döndürdü.</span><span class="sxs-lookup"><span data-stu-id="32d00-145">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="32d00-146">Ara değerli bir dizeye dönüştürme bir <xref:System.FormattableString> bileşik biçim dizesi gösteren değişkeni.</span><span class="sxs-lookup"><span data-stu-id="32d00-146">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="32d00-147">Bileşik biçim dizesi ve nasıl dizeyi sonucunda işler İnceleme Örneğin, bir sorgu oluşturuyorsanız ekleme saldırılara karşı korunmaya yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="32d00-147">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="32d00-148"><xref:System.FormattableString>Ayrıca içerir <xref:System.FormattableString.ToString> olanak tanıyan aşırı üretmek için sonuç dizeleri <xref:System.Globalization.CultureInfo.InvariantCulture> ve <xref:System.Globalization.CultureInfo.CurrentCulture>.</span><span class="sxs-lookup"><span data-stu-id="32d00-148"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the <xref:System.Globalization.CultureInfo.InvariantCulture> and <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>  <span data-ttu-id="32d00-149">Çift süslü ayraçlar tüm oluşumlarını ("{{" ve "}}"), format kadar çift süslü ayraçlar kalır.</span><span class="sxs-lookup"><span data-stu-id="32d00-149">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="32d00-150">{0}, {1} ve benzeri için tüm kapsanan ilişkilendirme ifadeleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="32d00-150">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a><span data-ttu-id="32d00-151">Dil belirtimi</span><span class="sxs-lookup"><span data-stu-id="32d00-151">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32d00-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32d00-152">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="32d00-153">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="32d00-153">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="32d00-154">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="32d00-154">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
