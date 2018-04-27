---
title: Genel adlandırma kuralları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 87f866210667905566d75bfed22ba7b9a521abdc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="general-naming-conventions"></a><span data-ttu-id="ab882-102">Genel adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="ab882-102">General Naming Conventions</span></span>
<span data-ttu-id="ab882-103">Bu bölümde, sözcük seçimi için ilgili genel adlandırma kuralları kısaltmalar ve kısaltmalar ve öneriler dile özel adlar kullanmaktan kaçının nasıl kullanma hakkında yönergeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab882-103">This section describes general naming conventions that relate to word choice, guidelines on using abbreviations and acronyms, and recommendations on how to avoid using language-specific names.</span></span>  
  
## <a name="word-choice"></a><span data-ttu-id="ab882-104">Sözcük seçimi</span><span class="sxs-lookup"><span data-stu-id="ab882-104">Word Choice</span></span>  
 <span data-ttu-id="ab882-105">**✓ YAPMAK** kolay okunabilir tanımlayıcı adlarını seçin.</span><span class="sxs-lookup"><span data-stu-id="ab882-105">**✓ DO** choose easily readable identifier names.</span></span>  
  
 <span data-ttu-id="ab882-106">Örneğin, adında bir özellik `HorizontalAlignment` daha İngilizce-okunamaz daha `AlignmentHorizontal`.</span><span class="sxs-lookup"><span data-stu-id="ab882-106">For example, a property named `HorizontalAlignment` is more English-readable than `AlignmentHorizontal`.</span></span>  
  
 <span data-ttu-id="ab882-107">**✓ YAPMAK** okunabilirlik kısaltma ayrıcalık tanıma.</span><span class="sxs-lookup"><span data-stu-id="ab882-107">**✓ DO** favor readability over brevity.</span></span>  
  
 <span data-ttu-id="ab882-108">Özellik adı `CanScrollHorizontally` daha iyidir `ScrollableX` (x ekseni belirsiz bir referansı).</span><span class="sxs-lookup"><span data-stu-id="ab882-108">The property name `CanScrollHorizontally` is better than `ScrollableX` (an obscure reference to the X-axis).</span></span>  
  
 <span data-ttu-id="ab882-109">**X yok** alt çizgi, kısa çizgi veya herhangi bir alfasayısal olmayan karakterler kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-109">**X DO NOT** use underscores, hyphens, or any other nonalphanumeric characters.</span></span>  
  
 <span data-ttu-id="ab882-110">**X yok** Macarca gösterimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-110">**X DO NOT** use Hungarian notation.</span></span>  
  
 <span data-ttu-id="ab882-111">**KAÇININ x** kullanılan programlama dilleri anahtar sözcükleriyle yaygın olarak çakışma kimlikleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ab882-111">**X AVOID** using identifiers that conflict with keywords of widely used programming languages.</span></span>  
  
 <span data-ttu-id="ab882-112">Ortak dil belirtimi (CLS), kural 4 göre tüm uyumlu diller söz konusu dilin anahtar sözcüğü bir tanımlayıcı olarak kullanmak adlandırılmış öğelere erişime izin veren bir mekanizma sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ab882-112">According to Rule 4 of the Common Language Specification (CLS), all compliant languages must provide a mechanism that allows access to named items that use a keyword of that language as an identifier.</span></span> <span data-ttu-id="ab882-113">Örneğin, C# ' ta, kullanır @ işareti bu durumda kaçış mekanizması olarak.</span><span class="sxs-lookup"><span data-stu-id="ab882-113">C#, for example, uses the @ sign as an escape mechanism in this case.</span></span> <span data-ttu-id="ab882-114">Ancak, ortak anahtar sözcükleri olmadan birden kaçış sırası içeren bir yöntem kullanmak çok daha zor olduğundan önlemek için iyi bir fikir hala olduğu.</span><span class="sxs-lookup"><span data-stu-id="ab882-114">However, it is still a good idea to avoid common keywords because it is much more difficult to use a method with the escape sequence than one without it.</span></span>  
  
## <a name="using-abbreviations-and-acronyms"></a><span data-ttu-id="ab882-115">Kısaltmalar ve kısaltmalar kullanma</span><span class="sxs-lookup"><span data-stu-id="ab882-115">Using Abbreviations and Acronyms</span></span>  
 <span data-ttu-id="ab882-116">**X yok** kısaltmalar veya kısaltmalar tanımlayıcı adları bir parçası olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-116">**X DO NOT** use abbreviations or contractions as part of identifier names.</span></span>  
  
 <span data-ttu-id="ab882-117">Örneğin, `GetWindow` yerine `GetWin`.</span><span class="sxs-lookup"><span data-stu-id="ab882-117">For example, use `GetWindow` rather than `GetWin`.</span></span>  
  
 <span data-ttu-id="ab882-118">**X yok** yaygın olarak kabul edilen ve, yalnızca gerekli olduğunda olmaları durumunda bile olmayan kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-118">**X DO NOT** use any acronyms that are not widely accepted, and even if they are, only when necessary.</span></span>  
  
## <a name="avoiding-language-specific-names"></a><span data-ttu-id="ab882-119">Dile özgü adları önleme</span><span class="sxs-lookup"><span data-stu-id="ab882-119">Avoiding Language-Specific Names</span></span>  
 <span data-ttu-id="ab882-120">**✓ YAPMAK** dile özgü anahtar sözcükler yerine anlamsal olarak ilginç adları için tür adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-120">**✓ DO** use semantically interesting names rather than language-specific keywords for type names.</span></span>  
  
 <span data-ttu-id="ab882-121">Örneğin, `GetLength` daha iyi bir adı `GetInt`.</span><span class="sxs-lookup"><span data-stu-id="ab882-121">For example, `GetLength` is a better name than `GetInt`.</span></span>  
  
 <span data-ttu-id="ab882-122">**✓ YAPMAK** bir tanımlayıcı türü ötesinde anlamsal anlamı olduğunda nadir durumlarda dile özgü adı yerine bir genel CLR türü adı kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-122">**✓ DO** use a generic CLR type name, rather than a language-specific name, in the rare cases when an identifier has no semantic meaning beyond its type.</span></span>  
  
 <span data-ttu-id="ab882-123">Örneğin, dönüştürülürken bir yöntem <xref:System.Int64> adlı olmalıdır `ToInt64`değil `ToLong` (çünkü <xref:System.Int64> için C# bir CLR ad-belirli diğer `long`).</span><span class="sxs-lookup"><span data-stu-id="ab882-123">For example, a method converting to <xref:System.Int64> should be named `ToInt64`, not `ToLong` (because <xref:System.Int64> is a CLR name for the C#-specific alias `long`).</span></span> <span data-ttu-id="ab882-124">Aşağıdaki tabloda, CLR türü adları (C#, Visual Basic ve C++ için karşılık gelen tür adları için olduğu gibi) kullanarak birden fazla temel veri türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ab882-124">The following table presents several base data types using the CLR type names (as well as the corresponding type names for C#, Visual Basic, and C++).</span></span>  
  
|<span data-ttu-id="ab882-125">C#</span><span class="sxs-lookup"><span data-stu-id="ab882-125">C#</span></span>|<span data-ttu-id="ab882-126">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab882-126">Visual Basic</span></span>|<span data-ttu-id="ab882-127">C++</span><span class="sxs-lookup"><span data-stu-id="ab882-127">C++</span></span>|<span data-ttu-id="ab882-128">CLR</span><span class="sxs-lookup"><span data-stu-id="ab882-128">CLR</span></span>|  
|---------|------------------|-----------|---------|  
|<span data-ttu-id="ab882-129">**sbyte**</span><span class="sxs-lookup"><span data-stu-id="ab882-129">**sbyte**</span></span>|<span data-ttu-id="ab882-130">**SByte**</span><span class="sxs-lookup"><span data-stu-id="ab882-130">**SByte**</span></span>|<span data-ttu-id="ab882-131">**char**</span><span class="sxs-lookup"><span data-stu-id="ab882-131">**char**</span></span>|<span data-ttu-id="ab882-132">**SByte**</span><span class="sxs-lookup"><span data-stu-id="ab882-132">**SByte**</span></span>|  
|<span data-ttu-id="ab882-133">**byte**</span><span class="sxs-lookup"><span data-stu-id="ab882-133">**byte**</span></span>|<span data-ttu-id="ab882-134">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="ab882-134">**Byte**</span></span>|<span data-ttu-id="ab882-135">**İmzasız char**</span><span class="sxs-lookup"><span data-stu-id="ab882-135">**unsigned char**</span></span>|<span data-ttu-id="ab882-136">**Bayt**</span><span class="sxs-lookup"><span data-stu-id="ab882-136">**Byte**</span></span>|  
|<span data-ttu-id="ab882-137">**short**</span><span class="sxs-lookup"><span data-stu-id="ab882-137">**short**</span></span>|<span data-ttu-id="ab882-138">**kısa**</span><span class="sxs-lookup"><span data-stu-id="ab882-138">**Short**</span></span>|<span data-ttu-id="ab882-139">**short**</span><span class="sxs-lookup"><span data-stu-id="ab882-139">**short**</span></span>|<span data-ttu-id="ab882-140">**Int16**</span><span class="sxs-lookup"><span data-stu-id="ab882-140">**Int16**</span></span>|  
|<span data-ttu-id="ab882-141">**ushort**</span><span class="sxs-lookup"><span data-stu-id="ab882-141">**ushort**</span></span>|<span data-ttu-id="ab882-142">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="ab882-142">**UInt16**</span></span>|<span data-ttu-id="ab882-143">**İmzasız short**</span><span class="sxs-lookup"><span data-stu-id="ab882-143">**unsigned short**</span></span>|<span data-ttu-id="ab882-144">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="ab882-144">**UInt16**</span></span>|  
|<span data-ttu-id="ab882-145">**int**</span><span class="sxs-lookup"><span data-stu-id="ab882-145">**int**</span></span>|<span data-ttu-id="ab882-146">**tamsayı**</span><span class="sxs-lookup"><span data-stu-id="ab882-146">**Integer**</span></span>|<span data-ttu-id="ab882-147">**int**</span><span class="sxs-lookup"><span data-stu-id="ab882-147">**int**</span></span>|<span data-ttu-id="ab882-148">**Int32**</span><span class="sxs-lookup"><span data-stu-id="ab882-148">**Int32**</span></span>|  
|<span data-ttu-id="ab882-149">**uint**</span><span class="sxs-lookup"><span data-stu-id="ab882-149">**uint**</span></span>|<span data-ttu-id="ab882-150">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="ab882-150">**UInt32**</span></span>|<span data-ttu-id="ab882-151">**İmzasız int**</span><span class="sxs-lookup"><span data-stu-id="ab882-151">**unsigned int**</span></span>|<span data-ttu-id="ab882-152">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="ab882-152">**UInt32**</span></span>|  
|<span data-ttu-id="ab882-153">**long**</span><span class="sxs-lookup"><span data-stu-id="ab882-153">**long**</span></span>|<span data-ttu-id="ab882-154">**uzun**</span><span class="sxs-lookup"><span data-stu-id="ab882-154">**Long**</span></span>|<span data-ttu-id="ab882-155">**__int64**</span><span class="sxs-lookup"><span data-stu-id="ab882-155">**__int64**</span></span>|<span data-ttu-id="ab882-156">**Int64**</span><span class="sxs-lookup"><span data-stu-id="ab882-156">**Int64**</span></span>|  
|<span data-ttu-id="ab882-157">**ulong**</span><span class="sxs-lookup"><span data-stu-id="ab882-157">**ulong**</span></span>|<span data-ttu-id="ab882-158">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="ab882-158">**UInt64**</span></span>|<span data-ttu-id="ab882-159">**İmzasız __int64**</span><span class="sxs-lookup"><span data-stu-id="ab882-159">**unsigned __int64**</span></span>|<span data-ttu-id="ab882-160">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="ab882-160">**UInt64**</span></span>|  
|<span data-ttu-id="ab882-161">**float**</span><span class="sxs-lookup"><span data-stu-id="ab882-161">**float**</span></span>|<span data-ttu-id="ab882-162">**Tek**</span><span class="sxs-lookup"><span data-stu-id="ab882-162">**Single**</span></span>|<span data-ttu-id="ab882-163">**float**</span><span class="sxs-lookup"><span data-stu-id="ab882-163">**float**</span></span>|<span data-ttu-id="ab882-164">**Tek**</span><span class="sxs-lookup"><span data-stu-id="ab882-164">**Single**</span></span>|  
|<span data-ttu-id="ab882-165">**double**</span><span class="sxs-lookup"><span data-stu-id="ab882-165">**double**</span></span>|<span data-ttu-id="ab882-166">**Çift**</span><span class="sxs-lookup"><span data-stu-id="ab882-166">**Double**</span></span>|<span data-ttu-id="ab882-167">**double**</span><span class="sxs-lookup"><span data-stu-id="ab882-167">**double**</span></span>|<span data-ttu-id="ab882-168">**Çift**</span><span class="sxs-lookup"><span data-stu-id="ab882-168">**Double**</span></span>|  
|<span data-ttu-id="ab882-169">**bool**</span><span class="sxs-lookup"><span data-stu-id="ab882-169">**bool**</span></span>|<span data-ttu-id="ab882-170">**Boole değeri**</span><span class="sxs-lookup"><span data-stu-id="ab882-170">**Boolean**</span></span>|<span data-ttu-id="ab882-171">**bool**</span><span class="sxs-lookup"><span data-stu-id="ab882-171">**bool**</span></span>|<span data-ttu-id="ab882-172">**Boole değeri**</span><span class="sxs-lookup"><span data-stu-id="ab882-172">**Boolean**</span></span>|  
|<span data-ttu-id="ab882-173">**char**</span><span class="sxs-lookup"><span data-stu-id="ab882-173">**char**</span></span>|<span data-ttu-id="ab882-174">**char**</span><span class="sxs-lookup"><span data-stu-id="ab882-174">**Char**</span></span>|<span data-ttu-id="ab882-175">**wchar_t**</span><span class="sxs-lookup"><span data-stu-id="ab882-175">**wchar_t**</span></span>|<span data-ttu-id="ab882-176">**char**</span><span class="sxs-lookup"><span data-stu-id="ab882-176">**Char**</span></span>|  
|<span data-ttu-id="ab882-177">**string**</span><span class="sxs-lookup"><span data-stu-id="ab882-177">**string**</span></span>|<span data-ttu-id="ab882-178">**Dize**</span><span class="sxs-lookup"><span data-stu-id="ab882-178">**String**</span></span>|<span data-ttu-id="ab882-179">**Dize**</span><span class="sxs-lookup"><span data-stu-id="ab882-179">**String**</span></span>|<span data-ttu-id="ab882-180">**Dize**</span><span class="sxs-lookup"><span data-stu-id="ab882-180">**String**</span></span>|  
|<span data-ttu-id="ab882-181">**object**</span><span class="sxs-lookup"><span data-stu-id="ab882-181">**object**</span></span>|<span data-ttu-id="ab882-182">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="ab882-182">**Object**</span></span>|<span data-ttu-id="ab882-183">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="ab882-183">**Object**</span></span>|<span data-ttu-id="ab882-184">**Nesne**</span><span class="sxs-lookup"><span data-stu-id="ab882-184">**Object**</span></span>|  
  
 <span data-ttu-id="ab882-185">**✓ YAPMAK** gibi ortak bir ad kullanın `value` veya `item`, tür adı bir tanımlayıcı bir anlam anlamı yoktur ve parametresinin türü önemli olmadığında nadir durumlarda yinelenen yerine.</span><span class="sxs-lookup"><span data-stu-id="ab882-185">**✓ DO**  use a common name, such as `value` or `item`, rather than repeating the type name, in the rare cases when an identifier has no semantic meaning and the type of the parameter is not important.</span></span>  
  
## <a name="naming-new-versions-of-existing-apis"></a><span data-ttu-id="ab882-186">Mevcut API'lerini yeni sürümlerini adlandırma</span><span class="sxs-lookup"><span data-stu-id="ab882-186">Naming New Versions of Existing APIs</span></span>  
 <span data-ttu-id="ab882-187">**✓ YAPMAK** var olan bir API yeni sürümlerini oluştururken eski API için benzer bir ad kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-187">**✓ DO** use a name similar to the old API when creating new versions of an existing API.</span></span>  
  
 <span data-ttu-id="ab882-188">Bu API'ları arasındaki ilişkiyi vurgulamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ab882-188">This helps to highlight the relationship between the APIs.</span></span>  
  
 <span data-ttu-id="ab882-189">**✓ YAPMAK** var olan bir API yeni bir sürümünü belirtmek için bir önek yerine bir sonek ekleme tercih eder.</span><span class="sxs-lookup"><span data-stu-id="ab882-189">**✓ DO** prefer adding a suffix rather than a prefix to indicate a new version of an existing API.</span></span>  
  
 <span data-ttu-id="ab882-190">Bu belge, göz atarken bulma yardımcı olur veya IntelliSense kullanma.</span><span class="sxs-lookup"><span data-stu-id="ab882-190">This will assist discovery when browsing documentation, or using Intellisense.</span></span> <span data-ttu-id="ab882-191">Çoğu tarayıcılar ve IntelliSense tanımlayıcıları alfabetik olarak göstermek için API eski sürümü yeni API'leri yakın düzenleneceğini.</span><span class="sxs-lookup"><span data-stu-id="ab882-191">The old version of the API will be organized close to the new APIs, because most browsers and Intellisense show identifiers in alphabetical order.</span></span>  
  
 <span data-ttu-id="ab882-192">**✓ DÜŞÜNÜN** sonek veya bir önek eklemek yerine yepyeni, ancak anlamlı tanımlayıcısını kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ab882-192">**✓ CONSIDER** using a brand new, but meaningful identifier, instead of adding a suffix or a prefix.</span></span>  
  
 <span data-ttu-id="ab882-193">**✓ YAPMAK** sayısal bir sonek özellikle, API varolan adı (yani, sektör standardı ise) mantıklı yalnızca bir ad ve her anlamlı ekleme soneki (veya adının değiştirilmesi) bir uygulama değilse varolan bir API yeni bir sürümünü belirtmek için kullanın ropriate seçeneği.</span><span class="sxs-lookup"><span data-stu-id="ab882-193">**✓ DO** use a numeric suffix to indicate a new version of an existing API, particularly if the existing name of the API is the only name that makes sense (i.e., if it is an industry standard) and if adding any meaningful suffix (or changing the name) is not an appropriate option.</span></span>  
  
 <span data-ttu-id="ab882-194">**X yok** "Eski" (veya benzeri) kullanmak aynı API önceki bir sürümünden ayırt etmek bir tanımlayıcı için soneki.</span><span class="sxs-lookup"><span data-stu-id="ab882-194">**X DO NOT** use the "Ex" (or a similar) suffix for an identifier to distinguish it from an earlier version of the same API.</span></span>  
  
 <span data-ttu-id="ab882-195">**✓ YAPMAK** 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümleri Tanıtımı "64" soneki kullanın.</span><span class="sxs-lookup"><span data-stu-id="ab882-195">**✓ DO** use the "64" suffix when introducing versions of APIs that operate on a 64-bit integer (a long integer) instead of a 32-bit integer.</span></span> <span data-ttu-id="ab882-196">Varolan 32-bit API varsa bu yaklaşımı benimsemeye yeterlidir; yapma, yalnızca 64-bit sürümü ile yepyeni API'leri için.</span><span class="sxs-lookup"><span data-stu-id="ab882-196">You only need to take this approach when the existing 32-bit API exists; don’t do it for brand new APIs with only a 64-bit version.</span></span>  
  
 <span data-ttu-id="ab882-197">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="ab882-197">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ab882-198">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="ab882-198">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab882-199">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab882-199">See Also</span></span>  
 [<span data-ttu-id="ab882-200">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="ab882-200">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="ab882-201">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="ab882-201">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
