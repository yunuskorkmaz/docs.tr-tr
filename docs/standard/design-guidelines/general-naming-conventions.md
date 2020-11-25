---
title: Genel Adlandırma Kuralları
description: Sözcük seçimiyle ilgili genel adlandırma kurallarını, kısaltmaların ve kısaltmaların kullanımıyla ilgili yönergeleri ve dile özgü adlardan kaçınmayla ilgili yönergeleri kullanın.
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: 60832e823ed2f51fdd13c467dbbef4378de27885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706716"
---
# <a name="general-naming-conventions"></a><span data-ttu-id="27b23-103">Genel Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="27b23-103">General Naming Conventions</span></span>

<span data-ttu-id="27b23-104">Bu bölümde, Word seçimiyle ilgili genel adlandırma kuralları, kısaltmalar ve kısaltmalar kullanma yönergeleri ve dile özgü adların kullanılmasıyla ilgili öneriler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="27b23-104">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>

## <a name="word-choice"></a><span data-ttu-id="27b23-105">Sözcük seçimi</span><span class="sxs-lookup"><span data-stu-id="27b23-105">Word Choice</span></span>

 <span data-ttu-id="27b23-106">✔️ kolayca okunabilir tanımlayıcı adlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="27b23-106">✔️ DO choose easily readable identifier names.</span></span>

 <span data-ttu-id="27b23-107">Örneğin, adlı bir özellik, `HorizontalAlignment` daha fazla İngilizce-okunabilir `AlignmentHorizontal` .</span><span class="sxs-lookup"><span data-stu-id="27b23-107">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>

 <span data-ttu-id="27b23-108">✔️, kısaltma üzerinde okunabilirliğini tercih edin.</span><span class="sxs-lookup"><span data-stu-id="27b23-108">✔️ DO favor readability over brevity.</span></span>

 <span data-ttu-id="27b23-109">Özellik adı `CanScrollHorizontally` şundan daha iyidir `ScrollableX` (X eksenine yönelik bir tam başvuru).</span><span class="sxs-lookup"><span data-stu-id="27b23-109">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>

 <span data-ttu-id="27b23-110">❌ Alt çizgi, kısa çizgi veya alfasayısal olmayan karakterler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27b23-110">❌ DO NOT use underscores, hyphens, or any other nonalphanumeric characters.</span></span>

 <span data-ttu-id="27b23-111">❌ Macarca gösterimini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27b23-111">❌ DO NOT use Hungarian notation.</span></span>

 <span data-ttu-id="27b23-112">❌ Yaygın olarak kullanılan programlama dillerinin anahtar sözcükleriyle çakışan tanımlayıcılar kullanmaktan KAÇıNıN.</span><span class="sxs-lookup"><span data-stu-id="27b23-112">❌ AVOID using identifiers that conflict with keywords of widely used programming languages.</span></span>

 <span data-ttu-id="27b23-113">Ortak dil belirtiminin (CLS) kural 4 ' e göre, tüm uyumlu dillerin, söz konusu dilin anahtar sözcüğünü tanımlayıcı olarak kullanan adlandırılmış öğelere erişime izin veren bir mekanizma sağlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="27b23-113">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="27b23-114">Örneğin, C#, bu durumda @ Sign 'ı kaçış mekanizması olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="27b23-114">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="27b23-115">Ancak, bir yöntemi kaçış sırası olmadan kullanmak çok daha zor olduğundan ortak anahtar sözcüklerden kaçınmak iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="27b23-115">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>

## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="27b23-116">Kısaltmalar ve kısaltmalar kullanma</span><span class="sxs-lookup"><span data-stu-id="27b23-116">Using Abbreviations and Acronyms</span></span>

 <span data-ttu-id="27b23-117">❌ Tanımlayıcı adlarının parçası olarak kısaltmalar veya aykırılıkları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27b23-117">❌ DO NOT use abbreviations or contractions as part of identifier names.</span></span>

 <span data-ttu-id="27b23-118">Örneğin, yerine kullanın `GetWindow` `GetWin` .</span><span class="sxs-lookup"><span data-stu-id="27b23-118">For example, use `GetWindow` rather than `GetWin`.</span></span>

 <span data-ttu-id="27b23-119">❌ Yaygın olarak kabul edilmeyen ve yalnızca gerekli olduğunda bile olmayan kısaltmalar kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27b23-119">❌ DO NOT use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>

## <a name="avoiding-language-specific-names"></a><span data-ttu-id="27b23-120">Language-Specific adlarından kaçınma</span><span class="sxs-lookup"><span data-stu-id="27b23-120">Avoiding Language-Specific Names</span></span>

 <span data-ttu-id="27b23-121">✔️, tür adları için dile özgü anahtar sözcükler yerine anlam açısından ilginç adlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="27b23-121">✔️ DO use semantically interesting names rather than language-specific keywords for type names.</span></span>

 <span data-ttu-id="27b23-122">Örneğin, `GetLength` daha iyi bir addır `GetInt` .</span><span class="sxs-lookup"><span data-stu-id="27b23-122">For example, `GetLength` is a better name than `GetInt`.</span></span>

 <span data-ttu-id="27b23-123">✔️, bir tanımlayıcının türünün ötesinde anlam anlamı olmadığında nadir durumlarda, dile özgü bir ad yerine genel CLR türü adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="27b23-123">✔️ DO use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>

 <span data-ttu-id="27b23-124">Örneğin, öğesine dönüştürme yöntemi <xref:System.Int64> `ToInt64` , değil, olarak adlandırılmalıdır `ToLong` (çünkü <xref:System.Int64> C# özel DIĞER adı için bir clr adıdır `long` ).</span><span class="sxs-lookup"><span data-stu-id="27b23-124">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="27b23-125">Aşağıdaki tabloda, CLR tür adlarını (Ayrıca C#, Visual Basic ve C++ için karşılık gelen tür adlarını) kullanan çeşitli temel veri türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="27b23-125">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>

|<span data-ttu-id="27b23-126">C#</span><span class="sxs-lookup"><span data-stu-id="27b23-126">C#</span></span>|<span data-ttu-id="27b23-127">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27b23-127">Visual Basic</span></span>|<span data-ttu-id="27b23-128">C++</span><span class="sxs-lookup"><span data-stu-id="27b23-128">C++</span></span>|<span data-ttu-id="27b23-129">CLR</span><span class="sxs-lookup"><span data-stu-id="27b23-129">CLR</span></span>|
|---------|------------------|-----------|---------|
|<span data-ttu-id="27b23-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="27b23-130">**sbyte**</span></span>|<span data-ttu-id="27b23-131">**SByte**</span><span class="sxs-lookup"><span data-stu-id="27b23-131">**SByte**</span></span>|<span data-ttu-id="27b23-132">**char**</span><span class="sxs-lookup"><span data-stu-id="27b23-132">**char**</span></span>|<span data-ttu-id="27b23-133">**SByte**</span><span class="sxs-lookup"><span data-stu-id="27b23-133">**SByte**</span></span>|
|<span data-ttu-id="27b23-134">**bayt**</span><span class="sxs-lookup"><span data-stu-id="27b23-134">**byte**</span></span>|<span data-ttu-id="27b23-135">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="27b23-135">**Byte**</span></span>|<span data-ttu-id="27b23-136">**unsigned char**</span><span class="sxs-lookup"><span data-stu-id="27b23-136">**unsigned char**</span></span>|<span data-ttu-id="27b23-137">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="27b23-137">**Byte**</span></span>|
|<span data-ttu-id="27b23-138">**short**</span><span class="sxs-lookup"><span data-stu-id="27b23-138">**short**</span></span>|<span data-ttu-id="27b23-139">**Kısadır**</span><span class="sxs-lookup"><span data-stu-id="27b23-139">**Short**</span></span>|<span data-ttu-id="27b23-140">**short**</span><span class="sxs-lookup"><span data-stu-id="27b23-140">**short**</span></span>|<span data-ttu-id="27b23-141">**Int16**</span><span class="sxs-lookup"><span data-stu-id="27b23-141">**Int16**</span></span>|
|<span data-ttu-id="27b23-142">**ushort**</span><span class="sxs-lookup"><span data-stu-id="27b23-142">**ushort**</span></span>|<span data-ttu-id="27b23-143">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="27b23-143">**UInt16**</span></span>|<span data-ttu-id="27b23-144">**imzasız short**</span><span class="sxs-lookup"><span data-stu-id="27b23-144">**unsigned short**</span></span>|<span data-ttu-id="27b23-145">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="27b23-145">**UInt16**</span></span>|
|<span data-ttu-id="27b23-146">**int**</span><span class="sxs-lookup"><span data-stu-id="27b23-146">**int**</span></span>|<span data-ttu-id="27b23-147">**Tamsayı**</span><span class="sxs-lookup"><span data-stu-id="27b23-147">**Integer**</span></span>|<span data-ttu-id="27b23-148">**int**</span><span class="sxs-lookup"><span data-stu-id="27b23-148">**int**</span></span>|<span data-ttu-id="27b23-149">**Int32**</span><span class="sxs-lookup"><span data-stu-id="27b23-149">**Int32**</span></span>|
|<span data-ttu-id="27b23-150">**uint**</span><span class="sxs-lookup"><span data-stu-id="27b23-150">**uint**</span></span>|<span data-ttu-id="27b23-151">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="27b23-151">**UInt32**</span></span>|<span data-ttu-id="27b23-152">**unsigned int**</span><span class="sxs-lookup"><span data-stu-id="27b23-152">**unsigned int**</span></span>|<span data-ttu-id="27b23-153">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="27b23-153">**UInt32**</span></span>|
|<span data-ttu-id="27b23-154">**long**</span><span class="sxs-lookup"><span data-stu-id="27b23-154">**long**</span></span>|<span data-ttu-id="27b23-155">**Kalacağını**</span><span class="sxs-lookup"><span data-stu-id="27b23-155">**Long**</span></span>|<span data-ttu-id="27b23-156">**__int64**</span><span class="sxs-lookup"><span data-stu-id="27b23-156">**__int64**</span></span>|<span data-ttu-id="27b23-157">**Tutulamaz**</span><span class="sxs-lookup"><span data-stu-id="27b23-157">**Int64**</span></span>|
|<span data-ttu-id="27b23-158">**ulong**</span><span class="sxs-lookup"><span data-stu-id="27b23-158">**ulong**</span></span>|<span data-ttu-id="27b23-159">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="27b23-159">**UInt64**</span></span>|<span data-ttu-id="27b23-160">**imzasız __int64**</span><span class="sxs-lookup"><span data-stu-id="27b23-160">**unsigned __int64**</span></span>|<span data-ttu-id="27b23-161">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="27b23-161">**UInt64**</span></span>|
|<span data-ttu-id="27b23-162">**float**</span><span class="sxs-lookup"><span data-stu-id="27b23-162">**float**</span></span>|<span data-ttu-id="27b23-163">**Tek**</span><span class="sxs-lookup"><span data-stu-id="27b23-163">**Single**</span></span>|<span data-ttu-id="27b23-164">**float**</span><span class="sxs-lookup"><span data-stu-id="27b23-164">**float**</span></span>|<span data-ttu-id="27b23-165">**Tek**</span><span class="sxs-lookup"><span data-stu-id="27b23-165">**Single**</span></span>|
|<span data-ttu-id="27b23-166">**double**</span><span class="sxs-lookup"><span data-stu-id="27b23-166">**double**</span></span>|<span data-ttu-id="27b23-167">**Çift**</span><span class="sxs-lookup"><span data-stu-id="27b23-167">**Double**</span></span>|<span data-ttu-id="27b23-168">**double**</span><span class="sxs-lookup"><span data-stu-id="27b23-168">**double**</span></span>|<span data-ttu-id="27b23-169">**Çift**</span><span class="sxs-lookup"><span data-stu-id="27b23-169">**Double**</span></span>|
|<span data-ttu-id="27b23-170">**bool**</span><span class="sxs-lookup"><span data-stu-id="27b23-170">**bool**</span></span>|<span data-ttu-id="27b23-171">**Boole**</span><span class="sxs-lookup"><span data-stu-id="27b23-171">**Boolean**</span></span>|<span data-ttu-id="27b23-172">**bool**</span><span class="sxs-lookup"><span data-stu-id="27b23-172">**bool**</span></span>|<span data-ttu-id="27b23-173">**Boole**</span><span class="sxs-lookup"><span data-stu-id="27b23-173">**Boolean**</span></span>|
|<span data-ttu-id="27b23-174">**char**</span><span class="sxs-lookup"><span data-stu-id="27b23-174">**char**</span></span>|<span data-ttu-id="27b23-175">**Char**</span><span class="sxs-lookup"><span data-stu-id="27b23-175">**Char**</span></span>|<span data-ttu-id="27b23-176">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="27b23-176">**wchar_t**</span></span>|<span data-ttu-id="27b23-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="27b23-177">**Char**</span></span>|
|<span data-ttu-id="27b23-178">**string**</span><span class="sxs-lookup"><span data-stu-id="27b23-178">**string**</span></span>|<span data-ttu-id="27b23-179">**Dize**</span><span class="sxs-lookup"><span data-stu-id="27b23-179">**String**</span></span>|<span data-ttu-id="27b23-180">**Dize**</span><span class="sxs-lookup"><span data-stu-id="27b23-180">**String**</span></span>|<span data-ttu-id="27b23-181">**Dize**</span><span class="sxs-lookup"><span data-stu-id="27b23-181">**String**</span></span>|
|<span data-ttu-id="27b23-182">**object**</span><span class="sxs-lookup"><span data-stu-id="27b23-182">**object**</span></span>|<span data-ttu-id="27b23-183">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="27b23-183">**Object**</span></span>|<span data-ttu-id="27b23-184">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="27b23-184">**Object**</span></span>|<span data-ttu-id="27b23-185">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="27b23-185">**Object**</span></span>|

 <span data-ttu-id="27b23-186">✔️, tür adını yinelemek yerine veya gibi ortak bir ad kullanın, `value` `item` nadir olarak bir tanımlayıcının anlam anlamı yoktur ve parametre türü önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="27b23-186">✔️ DO  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>

## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="27b23-187">Mevcut API 'lerin yeni sürümlerini adlandırma</span><span class="sxs-lookup"><span data-stu-id="27b23-187">Naming New Versions of Existing APIs</span></span>

 <span data-ttu-id="27b23-188">✔️ var olan bir API 'nin yeni sürümlerini oluştururken eski API 'ye benzer bir ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="27b23-188">✔️ DO use a name similar to the old API when creating new versions of an existing API.</span></span>

 <span data-ttu-id="27b23-189">Bu, API 'Ler arasındaki ilişkiyi vurgulamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="27b23-189">This helps to highlight the relationship between the APIs.</span></span>

 <span data-ttu-id="27b23-190">✔️ var olan bir API 'nin yeni bir sürümünü göstermek için önek yerine bir sonek eklemeyi tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27b23-190">✔️ DO prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>

 <span data-ttu-id="27b23-191">Bu, belgelere gözatarken veya IntelliSense kullanılırken bulmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="27b23-191">This will assist discovery when browsing documentation, or using IntelliSense.</span></span> <span data-ttu-id="27b23-192">Çoğu tarayıcı ve IntelliSense tanımlayıcıları alfabetik sırada göstertiğinden, API 'nin eski sürümü yeni API 'lere yakın şekilde düzenlenir.</span><span class="sxs-lookup"><span data-stu-id="27b23-192">The old version of the API will be organized close to the new APIs, because most browsers and IntelliSense show identifiers in alphabetical order.</span></span>

 <span data-ttu-id="27b23-193">✔️, bir sonek veya ön ek eklemek yerine yeni bir yepyeni, ancak anlamlı bir tanımlayıcı kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="27b23-193">✔️ CONSIDER using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>

 <span data-ttu-id="27b23-194">✔️ var olan bir API 'nin yeni bir sürümünü göstermek için sayısal bir sonek kullanın, özellikle de var olan API 'nin adı anlamlı olan tek addır (yani, bir sektör standardı ise) ve anlamlı bir sonek eklemek (veya adı değiştirmek) uygun bir seçenek değildir.</span><span class="sxs-lookup"><span data-stu-id="27b23-194">✔️ DO use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>

 <span data-ttu-id="27b23-195">❌ Aynı API 'nin önceki bir sürümünden ayırt etmek için bir tanımlayıcı için "Ex" (ya da benzer) sonekini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="27b23-195">❌ DO NOT use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>

 <span data-ttu-id="27b23-196">✔️, 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümlerini ("64" sonekini) kullanıma sunuyor.</span><span class="sxs-lookup"><span data-stu-id="27b23-196">✔️ DO use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="27b23-197">Yalnızca var olan 32 bitlik API olduğunda bu yaklaşımı uygulamanız gerekir; Bunu yalnızca 64 bitlik bir sürümle yepyeni yeni API 'Ler için yapmayın.</span><span class="sxs-lookup"><span data-stu-id="27b23-197">You only need to take this approach when the existing 32-bit API exists; don't do it for brand new APIs with only a 64-bit version.</span></span>

 <span data-ttu-id="27b23-198">*Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="27b23-198">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="27b23-199">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="27b23-199">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="27b23-200">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27b23-200">See also</span></span>

- [<span data-ttu-id="27b23-201">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="27b23-201">Framework design guidelines</span></span>](index.md)
- [<span data-ttu-id="27b23-202">Adlandırma yönergeleri</span><span class="sxs-lookup"><span data-stu-id="27b23-202">Naming guidelines</span></span>](naming-guidelines.md)
- [<span data-ttu-id="27b23-203">EditorConfig için .NET adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="27b23-203">.NET naming conventions for EditorConfig</span></span>](/visualstudio/ide/editorconfig-naming-conventions)
