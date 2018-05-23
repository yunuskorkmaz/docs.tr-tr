---
title: 'F # bileşen tasarım yönergeleri'
description: 'Tüketim için diğer arayanlar tarafından kullanılmaya F # bileşenlerini yazmak için kılavuzları hakkında bilgi edinin.'
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="a90aa-103">F # bileşen tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-103">F# component design guidelines</span></span>

<span data-ttu-id="a90aa-104">Bu belge bileşen tasarım yönergeleri F programlama, F # bileşen tasarım yönergeleri, v14, Microsoft Research dayalı # kümesidir ve [başka bir sürümü](https://fsharp.org/specs/component-design-guidelines/) başlangıçta seçkin ve F # yazılım Foundation tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="a90aa-105">Bu belge, F # programlama ile bildiğinizi varsayar.</span><span class="sxs-lookup"><span data-stu-id="a90aa-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="a90aa-106">Çok F # topluluk katkılarına ve bu kılavuz çeşitli sürümlerinde yararlı geri bildirim teşekkür ederiz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="a90aa-107">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a90aa-107">Overview</span></span>

<span data-ttu-id="a90aa-108">Bu belge, F # bileşen tasarım ve kodlama ilgili sorunlardan bazıları bakar.</span><span class="sxs-lookup"><span data-stu-id="a90aa-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="a90aa-109">Bir bileşenin aşağıdakilerden herhangi birini anlamına gelebilir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="a90aa-110">Bu proje dış tüketicileri sahip F # projenize bir katmanı.</span><span class="sxs-lookup"><span data-stu-id="a90aa-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="a90aa-111">Derleme sınırlarında F # koduna göre tüketimi için amaçlanan bir kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="a90aa-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="a90aa-112">Tüketimi için derleme sınırları ötesinde herhangi bir .NET dil tarafından kullanılmaya kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="a90aa-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="a90aa-113">Bir paket deposu aracılığıyla dağıtım gibi yönelik bir kitaplık [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="a90aa-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="a90aa-114">Bu makalede açıklanan teknikleri izleyin [iyi F # kodu beş ilkeleri](index.md#five-principles-of-good-f-code), dolayısıyla her ikisi de işlevsel kullanmasına ve uygun şekilde programlama nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a90aa-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="a90aa-115">Yönteme bağımsız olarak bileşeni ve kitaplık Tasarımcısı geliştiriciler tarafından en kolay kullanılabilir bir API hazırlanması çalışırken bir dizi pratik ve prosaic sorununu yüzler.</span><span class="sxs-lookup"><span data-stu-id="a90aa-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="a90aa-116">Sertifikasyonuna uygulamasının [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md) tutarlı bir dizi tüketmeye eğlenceli API oluşturma doğrultusunda ilerletebilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="a90aa-117">Genel yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-117">General guidelines</span></span>

<span data-ttu-id="a90aa-118">Kitaplık için hedef kitle bağımsız olarak F # kitaplıkları, uygulamak birkaç Evrensel yönergeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="a90aa-119">.NET kitaplığı tasarım yönergeleri öğrenin</span><span class="sxs-lookup"><span data-stu-id="a90aa-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="a90aa-120">Kodlama F #, gittiğini türü ne olursa olsun, bir bilgiye sahip değerli [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="a90aa-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="a90aa-121">Çoğu diğer F # .NET programcıları bu yönergelere hakkında bilgi sahibi olmanız ve .NET kodu için uygun olması için bekler.</span><span class="sxs-lookup"><span data-stu-id="a90aa-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="a90aa-122">.NET kitaplığı tasarım yönergeleri adlandırma, sınıflar ve arabirimler, üye tasarım (özellikleri, yöntemleri, olaylar, vb.) ve daha fazlasını tasarımı ile ilgili genel rehberlik sağlar ve Tasarım Kılavuzu, çeşitli başvurusunu yararlı bir ilk noktası.</span><span class="sxs-lookup"><span data-stu-id="a90aa-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="a90aa-123">XML belge açıklamaları için kodunuzu ekleyin</span><span class="sxs-lookup"><span data-stu-id="a90aa-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="a90aa-124">XML belgeleri ortak API'ler üzerinde olun bu türleri ve üyeleri ve etkinleştir yapı belgelerinin kullanarak kitaplık için dosyaları, kullanıcıların harika IntelliSense ve Quıckınfo alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="a90aa-125">Bkz: [XML belgeleri](../language-reference/xml-documentation.md) xmldoc açıklamaları içinde ek biçimlendirme için kullanılan çeşitli xml etiketleri hakkında.</span><span class="sxs-lookup"><span data-stu-id="a90aa-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="a90aa-126">Kısa form XML açıklamaları kullanabilirsiniz (`/// comment`), veya standart XML yorum (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="a90aa-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="a90aa-127">Kararlı kitaplığı ve bileşen API'leri için açık imza dosyalarını (.fsi) kullanmayı düşünün</span><span class="sxs-lookup"><span data-stu-id="a90aa-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="a90aa-128">Bir F # kitaplığı açık imza dosyalarını kullanarak her iki, tam ortak yüzeyini kitaplığınızın bilmeniz yanı sıra, ortak belgeler arasında iç temiz bir ayrımı sağlar sağlamaya yardımcı olan genel API'si kısa bir özetini sunar Uygulama Ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="a90aa-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="a90aa-129">Genel API uygulaması ve imza dosyalarında yapılacak değişiklikler gerektirerek değiştirmeye imza dosyalarını uyuşmazlık eklediğiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="a90aa-130">Bir API solidified haline gelir ve artık önemli ölçüde değişiklik bekleniyor olduğunda sonuç olarak, imza dosyalarını genellikle yalnızca ortaya çıkan.</span><span class="sxs-lookup"><span data-stu-id="a90aa-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="a90aa-131">Her zaman .NET dizeleri kullanmak için en iyi uygulamaları izleyin</span><span class="sxs-lookup"><span data-stu-id="a90aa-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="a90aa-132">İzleyin [.NET kullanarak dizelerde için en iyi uygulamaları](../../standard/base-types/best-practices-strings.md) Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="a90aa-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="a90aa-133">Özellikle, her zaman açıkça durum *kültürel hedefi* dönüştürme ve dizeleri karşılaştırma (uygunsa).</span><span class="sxs-lookup"><span data-stu-id="a90aa-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="a90aa-134">F # için yönergeler-kitaplıkları karşılıklı</span><span class="sxs-lookup"><span data-stu-id="a90aa-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="a90aa-135">Bu bölüm ortak F # geliştirme için öneriler sunar-kitaplıkları; karşılıklı diğer bir deyişle, F # geliştiriciler tarafından kullanılması amaçlanan ortak API'ler gösterme kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="a90aa-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="a90aa-136">Kitaplık tasarım önerilerini çeşitli özellikle F # için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="a90aa-137">İzleyin belirli öneriler olmaması durumunda, .NET kitaplığı tasarım geri dönüş Kılavuzu yönergelerdir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="a90aa-138">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="a90aa-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="a90aa-139">.NET adlandırma ve büyük/küçük harf kuralları kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="a90aa-140">Aşağıdaki tabloda .NET adlandırma ve büyük/küçük harf kuralları izler.</span><span class="sxs-lookup"><span data-stu-id="a90aa-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="a90aa-141">F # yapılarını de içerecek şekilde küçük eklemeler vardır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="a90aa-142">Oluştur</span><span class="sxs-lookup"><span data-stu-id="a90aa-142">Construct</span></span> | <span data-ttu-id="a90aa-143">Durumu</span><span class="sxs-lookup"><span data-stu-id="a90aa-143">Case</span></span> | <span data-ttu-id="a90aa-144">Bölümü</span><span class="sxs-lookup"><span data-stu-id="a90aa-144">Part</span></span> | <span data-ttu-id="a90aa-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a90aa-145">Examples</span></span> | <span data-ttu-id="a90aa-146">Notlar</span><span class="sxs-lookup"><span data-stu-id="a90aa-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="a90aa-147">Somut türleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-147">Concrete types</span></span> | <span data-ttu-id="a90aa-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-148">PascalCase</span></span> | <span data-ttu-id="a90aa-149">İsim / sıfat</span><span class="sxs-lookup"><span data-stu-id="a90aa-149">Noun/ adjective</span></span> | <span data-ttu-id="a90aa-150">Liste, Double, karmaşık</span><span class="sxs-lookup"><span data-stu-id="a90aa-150">List, Double, Complex</span></span> | <span data-ttu-id="a90aa-151">Yapılar, sınıflar, numaralandırmalar, temsilciler, kaydeder ve birleşimleri bunun somut türleridir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="a90aa-152">Tür adları OCaml geleneksel olarak küçük olmakla birlikte, F # türleri için .NET adlandırma şeması benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="a90aa-153">DLL'ler</span><span class="sxs-lookup"><span data-stu-id="a90aa-153">DLLs</span></span>           | <span data-ttu-id="a90aa-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-154">PascalCase</span></span> |                 | <span data-ttu-id="a90aa-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="a90aa-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="a90aa-156">Birleşim etiketleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-156">Union tags</span></span>     | <span data-ttu-id="a90aa-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-157">PascalCase</span></span> | <span data-ttu-id="a90aa-158">isim</span><span class="sxs-lookup"><span data-stu-id="a90aa-158">Noun</span></span> | <span data-ttu-id="a90aa-159">Bazı, ekleme, başarılı</span><span class="sxs-lookup"><span data-stu-id="a90aa-159">Some, Add, Success</span></span> | <span data-ttu-id="a90aa-160">Bir önek ortak API'leri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="a90aa-161">İsteğe bağlı olarak bir önek gibi iç olduğunda kullanın ''' takımlar yazın TAlpha =</span><span class="sxs-lookup"><span data-stu-id="a90aa-161">Optionally use a prefix when internal, such as \`\`\`type Teams = TAlpha</span></span> | <span data-ttu-id="a90aa-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="a90aa-162">TBeta</span></span> | <span data-ttu-id="a90aa-163">TDelta.'' '</span><span class="sxs-lookup"><span data-stu-id="a90aa-163">TDelta.\`\`\`</span></span> |
| <span data-ttu-id="a90aa-164">Olay</span><span class="sxs-lookup"><span data-stu-id="a90aa-164">Event</span></span>          | <span data-ttu-id="a90aa-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-165">PascalCase</span></span> | <span data-ttu-id="a90aa-166">Fiil</span><span class="sxs-lookup"><span data-stu-id="a90aa-166">Verb</span></span> | <span data-ttu-id="a90aa-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="a90aa-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="a90aa-168">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a90aa-168">Exceptions</span></span>     | <span data-ttu-id="a90aa-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-169">PascalCase</span></span> |      | <span data-ttu-id="a90aa-170">WebException</span><span class="sxs-lookup"><span data-stu-id="a90aa-170">WebException</span></span> | <span data-ttu-id="a90aa-171">Adı "Özel durum" ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="a90aa-172">Alan</span><span class="sxs-lookup"><span data-stu-id="a90aa-172">Field</span></span>          | <span data-ttu-id="a90aa-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-173">PascalCase</span></span> | <span data-ttu-id="a90aa-174">isim</span><span class="sxs-lookup"><span data-stu-id="a90aa-174">Noun</span></span> | <span data-ttu-id="a90aa-175">Geçerli ad</span><span class="sxs-lookup"><span data-stu-id="a90aa-175">CurrentName</span></span>  | |
| <span data-ttu-id="a90aa-176">Arabirim türleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-176">Interface types</span></span> |  <span data-ttu-id="a90aa-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-177">PascalCase</span></span> | <span data-ttu-id="a90aa-178">İsim / sıfat</span><span class="sxs-lookup"><span data-stu-id="a90aa-178">Noun/ adjective</span></span> | <span data-ttu-id="a90aa-179">IDisposable</span><span class="sxs-lookup"><span data-stu-id="a90aa-179">IDisposable</span></span> | <span data-ttu-id="a90aa-180">Adı "T" ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="a90aa-181">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a90aa-181">Method</span></span> |  <span data-ttu-id="a90aa-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-182">PascalCase</span></span> |  <span data-ttu-id="a90aa-183">Fiil</span><span class="sxs-lookup"><span data-stu-id="a90aa-183">Verb</span></span> | <span data-ttu-id="a90aa-184">ToString</span><span class="sxs-lookup"><span data-stu-id="a90aa-184">ToString</span></span> | |
| <span data-ttu-id="a90aa-185">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a90aa-185">Namespace</span></span> | <span data-ttu-id="a90aa-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-186">PascalCase</span></span> | | <span data-ttu-id="a90aa-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="a90aa-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="a90aa-188">Genellikle kullanması `<Organization>.<Technology>[.<Subnamespace>]`, teknolojisi organizasyonu bağımsızsa ancak kuruluş bırakın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="a90aa-189">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a90aa-189">Parameters</span></span> | <span data-ttu-id="a90aa-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-190">camelCase</span></span> | <span data-ttu-id="a90aa-191">isim</span><span class="sxs-lookup"><span data-stu-id="a90aa-191">Noun</span></span> |  <span data-ttu-id="a90aa-192">typeName, dönüştürme ve aralığı</span><span class="sxs-lookup"><span data-stu-id="a90aa-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="a90aa-193">let değerleri (iç)</span><span class="sxs-lookup"><span data-stu-id="a90aa-193">let values (internal)</span></span> | <span data-ttu-id="a90aa-194">camelCase veya PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-194">camelCase or PascalCase</span></span> | <span data-ttu-id="a90aa-195">İsim / fiil</span><span class="sxs-lookup"><span data-stu-id="a90aa-195">Noun/ verb</span></span> |  <span data-ttu-id="a90aa-196">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="a90aa-196">getValue, myTable</span></span> |
| <span data-ttu-id="a90aa-197">let değerleri (harici)</span><span class="sxs-lookup"><span data-stu-id="a90aa-197">let values (external)</span></span> | <span data-ttu-id="a90aa-198">camelCase veya PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-198">camelCase or PascalCase</span></span> | <span data-ttu-id="a90aa-199">İsim/fiil</span><span class="sxs-lookup"><span data-stu-id="a90aa-199">Noun/verb</span></span>  | <span data-ttu-id="a90aa-200">List.map, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="a90aa-200">List.map, Dates.Today</span></span> | <span data-ttu-id="a90aa-201">let bağlı genellikle geleneksel işlevsel tasarım desenleri aşağıdaki durumlarda ortak değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="a90aa-202">Ancak, diğer .NET dillerinden tanımlayıcı kullanılabilir olduğunda genellikle PascalCase kullanın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="a90aa-203">Özellik</span><span class="sxs-lookup"><span data-stu-id="a90aa-203">Property</span></span>  | <span data-ttu-id="a90aa-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="a90aa-204">PascalCase</span></span>  | <span data-ttu-id="a90aa-205">İsim / sıfat</span><span class="sxs-lookup"><span data-stu-id="a90aa-205">Noun/ adjective</span></span>  | <span data-ttu-id="a90aa-206">IsEndOfFile, arka plan rengi</span><span class="sxs-lookup"><span data-stu-id="a90aa-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="a90aa-207">Boole özellikleri genellikle olduğu ve olabilir ve IsEndOfFile olduğu gibi yok IsNotEndOfFile ileticiden onaylama olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="a90aa-208">Kısaltmalar kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-208">Avoid abbreviations</span></span>

<span data-ttu-id="a90aa-209">.NET yönergeleri kısaltmalar kullanımı önerilmemektedir (örneğin, "kullanmak `OnButtonClick` yerine `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="a90aa-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="a90aa-210">Ortak kısaltmalar gibi `Async` "Zaman uyumsuz için", izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="a90aa-211">Bu kılavuz için işlevsel programlama bazen göz ardı edilir; Örneğin, `List.iter` "yinelemek için" kısaltma kullanır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="a90aa-212">F # daha büyük ölçüde kabul edileceği kısaltmalar kullanarak bu nedenle, eğilimlidir-için-F # programlama, ancak hala genellikle ortak bileşen tasarımında kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="a90aa-213">Ad çakışmaları büyük/küçük harfleri kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-213">Avoid casing name collisions</span></span>

<span data-ttu-id="a90aa-214">Tek başına büyük/küçük harfleri bazı istemci dillerini (örneğin, Visual Basic) büyük/küçük harfe duyarsızdır sonra ad çakışması belirsizliğini ortadan kaldırmak için kullanılamayacağını .NET yönergeleri söyleyin.</span><span class="sxs-lookup"><span data-stu-id="a90aa-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="a90aa-215">Uygun olan yerlerde kısaltmalar kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="a90aa-216">Kısaltmalar XML gibi kısaltmalar değildir ve .NET kitaplıklarına eden formunda (Xml) yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="a90aa-217">Yalnızca iyi bilinen, tanınmış kısaltmalar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="a90aa-218">Genel parametre adları için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="a90aa-219">PascalCase genel API'leri, F #'de dahil olmak üzere genel parametre adlarında kullanma-kitaplıkları karşılıklı.</span><span class="sxs-lookup"><span data-stu-id="a90aa-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="a90aa-220">Özellikle, adları gibi kullanın `T`, `U`, `T1`, `T2` rasgele genel parametreler için ve belirli adları, sonra F # için anlamlı-karşılıklı kitaplıklarını kullanma gibi adları `Key`, `Value`, `Arg`(ancak olmayan örneğin `TKey`).</span><span class="sxs-lookup"><span data-stu-id="a90aa-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="a90aa-221">Genel işlevler ve F # modülleri değerleri için PascalCase veya camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="a90aa-222">camelCase kullanılmak üzere tasarlanmış ortak işlevleri için kullanılan nitelenmemiş (örneğin, `invalidArg`) ve "standart toplama işlevleri için" (örneğin, List.map).</span><span class="sxs-lookup"><span data-stu-id="a90aa-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="a90aa-223">Her iki bu durumda işlev adları çok dilindeki anahtar sözcükler gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="a90aa-224">Nesne, türü ve modül tasarım</span><span class="sxs-lookup"><span data-stu-id="a90aa-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="a90aa-225">Ad alanları veya modülleri türleri ve modülleri içerecek şekilde kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="a90aa-226">Her F # dosyasında bir bileşeni, bir ad alanı bildirimini veya bir modül bildirimi ile başlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="a90aa-227">veya</span><span class="sxs-lookup"><span data-stu-id="a90aa-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="a90aa-228">Modülleri ve ad alanlarını kullanarak en üst düzeyinde kod düzenleme arasındaki farklar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="a90aa-229">Ad alanları, birden çok dosya yayılabilir</span><span class="sxs-lookup"><span data-stu-id="a90aa-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="a90aa-230">Bir iç modülü içinde olmadığı sürece ad alanları F # işlevleri içeremez.</span><span class="sxs-lookup"><span data-stu-id="a90aa-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="a90aa-231">Kod belirli herhangi bir modül için tek bir dosyada yer almalıdır</span><span class="sxs-lookup"><span data-stu-id="a90aa-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="a90aa-232">Üst düzey modüller F # işlevleri iç modül gerek kalmadan içerebilir</span><span class="sxs-lookup"><span data-stu-id="a90aa-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="a90aa-233">En üst düzey ad veya modülü arasında seçim derlenmiş formun kodunun etkiler ve böylece diğer .NET dilleri görünümünden API'nizi sonunda F # kodu dışında kullanılması etkileyecektir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="a90aa-234">Nesne türlerine iç işlemleri için yöntemlerini ve özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="a90aa-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="a90aa-235">Nesneler ile çalışırken, kaynaklarda işlevselliği yöntemleri ve özellikleri ilgili türdeki olarak uygulanır sağlamak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="a90aa-236">İşlevselliği toplu belirli bir üye için mutlaka bu üyede uygulanmadı, ancak bu işlevselliği tüketilebilir parçası olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="a90aa-237">Değişebilir durumu kapsülleyen sınıflarını kullanma</span><span class="sxs-lookup"><span data-stu-id="a90aa-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="a90aa-238">F #'ta bu yalnızca durum zaten kapatılmak üzere, dizisi ifade veya zaman uyumsuz hesaplama gibi başka bir dil yapısı yalıtılan değil, yerine getirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="a90aa-239">Grubuna arabirimler kullanacak ilgili işlemler</span><span class="sxs-lookup"><span data-stu-id="a90aa-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="a90aa-240">Bir işlemler kümesini temsil eden arabirim türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="a90aa-241">Bu işlevlerin diziler veya işlevlerin kayıtları gibi diğer seçenekleri için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="a90aa-242">İçinde preference için:</span><span class="sxs-lookup"><span data-stu-id="a90aa-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="a90aa-243">İlk sınıf kavramları ne Functors normalde verirsiniz elde etmek için kullanabileceğiniz .NET içinde arabirimlerdir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="a90aa-244">Ayrıca, bunlar işlevlerin kayıtları olamaz, programa varlıksal türleri kodlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="a90aa-245">Bir modül davranan Grup işlevlere koleksiyonlarında kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="a90aa-246">Koleksiyon türü tanımladığınızda, standart bir işlemler kümesini ister sağlamayı düşünün `CollectionType.map` ve `CollectionType.iter`) için yeni koleksiyon türleri.</span><span class="sxs-lookup"><span data-stu-id="a90aa-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="a90aa-247">Bu tür bir modül eklerseniz, FSharp.Core içinde bulunan işlevleri için standart adlandırma kuralları izleyin.</span><span class="sxs-lookup"><span data-stu-id="a90aa-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="a90aa-248">Ortak, kurallı işlevlerde, özellikle matematik ve DSL kitaplıkları için Grup işlevleri bir modüle kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="a90aa-249">Örneğin, `Microsoft.FSharp.Core.Operators` en üst düzey işlevleri otomatik olarak açılan bir koleksiyonudur (gibi `abs` ve `sin`) FSharp.Core.dll tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="a90aa-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="a90aa-250">Benzer şekilde, bir istatistik kitaplık işlevleri sahip bir modül içerebilir `erf` ve `erfc`, bu modül burada açıkça veya otomatik olarak açılacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="a90aa-251">RequireQualifiedAccess kullanmayı düşünün ve dikkatle AutoOpen öznitelikleri uygulama</span><span class="sxs-lookup"><span data-stu-id="a90aa-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="a90aa-252">Ekleme `[<RequireQualifiedAccess>]` öznitelik bir modüle, modül açılmamış ve koşullu erişim modülü öğelere başvurular açık gerektirir gösterir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="a90aa-253">Örneğin, `Microsoft.FSharp.Collections.List` modülü bu öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="a90aa-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="a90aa-254">Bu, İşlevler ve değerleri modüldeki diğer modüllerdeki adlarıyla çakışma olasılığı adlara sahip durumunda faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="a90aa-255">Koşullu erişim gerektiren bir kitaplık evolvability ve uzun süreli bakım önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="a90aa-256">Ekleme `[<AutoOpen>]` özniteliği bir modüle anlamına gelir içeren ad alanı açıldığında modülü açılacak.</span><span class="sxs-lookup"><span data-stu-id="a90aa-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="a90aa-257">`[<AutoOpen>]` Özniteliği de uygulanabilir bir derlemeye derlemesi başvurulduğunda otomatik olarak açılan bir modülü belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a90aa-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="a90aa-258">Örneğin, bir istatistik Kitaplığı **MathsHeaven.Statistics** içerebilecek bir `module MathsHeaven.Statistics.Operators` işlevleri içeren `erf` ve `erfc`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="a90aa-259">Bu modül olarak işaretlemek makul `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="a90aa-260">Yani `open MathsHeaven.Statistics` de bu modül açılır ve adlarını Getir `erf` ve `erfc` kapsam içine.</span><span class="sxs-lookup"><span data-stu-id="a90aa-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="a90aa-261">Başka bir iyi kullanımını `[<AutoOpen>]` genişletme yöntemleri içeren modüller için değil.</span><span class="sxs-lookup"><span data-stu-id="a90aa-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="a90aa-262">Aşırı `[<AutoOpen>]` müşteri adayları polluted ad alanları ve öznitelik dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="a90aa-263">Belirli alanlarında kullanmalıdır belirli kitaplıkları için `[<AutoOpen>]` daha iyi kullanılabilirlik yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="a90aa-264">İyi bilinen işleçleri kullanarak uygun olduğu sınıflarında işleci üyelerini tanımlama göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="a90aa-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="a90aa-265">Bazen sınıfları vektörlerinin gibi matematiksel yapıları model oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="a90aa-266">İyi bilinen işleçleri Modellenen etki alanı sahip olduğunda, onları sınıfa iç üye olarak tanımlayarak yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="a90aa-267">Bu kılavuz, bu tür için genel .NET Kılavuzu karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="a90aa-268">Ancak, bu F # işlevleri ile birlikte ve yöntemleri List.sumBy gibi üye kısıtlamaları ile kullanılmak üzere bu tür verdiğinden F # kodlama Ayrıca önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="a90aa-269">CompiledName sağlamak için kullanmayı bir. Diğer .NET dil müşterileri için NET kolay ad</span><span class="sxs-lookup"><span data-stu-id="a90aa-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="a90aa-270">Bazen bir stilinde bir şey F # Tüketiciler için ad isteyebilirsiniz (statik bir üyenin alt şekilde görünmesi durumda gibi bir modül bağlı işlevi değilmiş gibi), ancak bütünleştirilmiş koda derlenmemiş adı için farklı bir stil vardır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="a90aa-271">Kullanabileceğiniz `[<CompiledName>]` özniteliği için derleme tüketen olmayan F # kodu farklı bir stil sağlayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="a90aa-272">Kullanarak `[<CompiledName>]`, .NET adlandırma kuralları olmayan F # tüketiciler derlemenin için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="a90aa-273">Bunun yapılması, yöntemi kullanmak için üye işlevleri, aşırı daha basit bir API sağlar</span><span class="sxs-lookup"><span data-stu-id="a90aa-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="a90aa-274">Yöntemi aşırı yüklemesi güçlü benzer işlevleri gerçekleştirmek için gereken bir API basitleştirmek için ancak farklı seçenekler veya bağımsız bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="a90aa-275">F #'ta bağımsız değişken türleri yerine bağımsız değişken sayısı aşırı yüklemeyi daha yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="a90aa-276">Bu tür tasarım gelişmesi olasılığı varsa kayıt ve birleşim türlerini gösterimlerini Gizle</span><span class="sxs-lookup"><span data-stu-id="a90aa-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="a90aa-277">Nesneleri somut gösterimlerini ortaya kaçının.</span><span class="sxs-lookup"><span data-stu-id="a90aa-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="a90aa-278">Örneğin, somut gösterimini <xref:System.DateTime> .NET kitaplığı tasarım dış, ortak API'si tarafından değerleri ortaya değil.</span><span class="sxs-lookup"><span data-stu-id="a90aa-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="a90aa-279">Çalışma zamanında, ortak dil çalışma zamanı yürütme kullanılan kaydedilmiş uygulama bilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="a90aa-280">Ancak, derlenmiş kod kendisini somut gösterimi bağımlılıkları alması değil.</span><span class="sxs-lookup"><span data-stu-id="a90aa-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="a90aa-281">Uygulama devralma genişletilebilirliği için kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="a90aa-282">F #'ta uygulama devralma nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="a90aa-283">Ayrıca, devralma hiyerarşileri genellikle karmaşık ve zordur yeni gereksinimleri geldiğinde değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="a90aa-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="a90aa-284">Devralma uygulamasında hala F #'de uyumluluk ve burada bir sorun için en iyi çözüm olduğunu, ancak alternatif teknikleri, F # programlarında arabirim uygulaması gibi çok biçimlilik için tasarlarken Aranan nadiren bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="a90aa-285">İşlev ve üye imzaları</span><span class="sxs-lookup"><span data-stu-id="a90aa-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="a90aa-286">Birden çok ilişkisiz değerleri az sayıda döndürülürken diziler için dönüş değerlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="a90aa-287">Aşağıda, bir dönüş türü bir tanımlama grubu kullanmak iyi bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="a90aa-288">Dönüş türleri birçok bileşen içeren veya bileşenleri tek bir kişisel varlık ilişkili olduğunda, bir tanımlama grubu yerine bir adlandırılmış türü kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a90aa-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="a90aa-289">Kullanım `Async<T>` F # API sınırlarında zaman uyumsuz programlama için</span><span class="sxs-lookup"><span data-stu-id="a90aa-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="a90aa-290">Adlı karşılık gelen eşzamanlı bir işlem olup olmadığını `Operation` döndüren bir `T`, zaman uyumsuz işlemi adlı sonra `AsyncOperation` döndürürse `Async<T>` veya `OperationAsync` döndürürse `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="a90aa-291">Başlangıç/bitiş yöntemleri kullanıma yaygın olarak kullanılan .NET türleri göz önünde bulundurun için kullanarak `Async.FromBeginEnd` F # zaman uyumsuz programlama modeli bu .NET API'lerini sağlamak için bir cephesi olarak genişletme yöntemleri yazma.</span><span class="sxs-lookup"><span data-stu-id="a90aa-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="a90aa-292">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a90aa-292">Exceptions</span></span>

<span data-ttu-id="a90aa-293">Özel durumları .NET olağanüstü; diğer bir deyişle, bunlar çalışma zamanında sık oluşmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-293">Exceptions are exceptional in .NET; that is, they should not occur frequently at runtime.</span></span> <span data-ttu-id="a90aa-294">Bunu yaptıklarında, içerdikleri bilgi faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-294">When they do, the information they contain is valuable.</span></span> <span data-ttu-id="a90aa-295">Özel durumlar çekirdek .NET birinci sınıf kavramını; yine de uygun istiyor musunuz? Bu nedenle BT özel durumların uygulama uygun aşağıdaki arabirimi bileşeninin tasarımının bir parçası kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-295">Exceptions are a core first class concept of .NET; it hence follows that appropriate application of the Exceptions should be used as part of the design of the interface of a component.</span></span>

#### <a name="follow-the-net-guidelines-for-exceptions"></a><span data-ttu-id="a90aa-296">Özel durumlar için .NET yönergeleri izleyin</span><span class="sxs-lookup"><span data-stu-id="a90aa-296">Follow the .NET guidelines for exceptions</span></span>

<span data-ttu-id="a90aa-297">[.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/exceptions.md) bağlamında tüm .NET programlama özel durumları kullanımını mükemmel önerileri verin.</span><span class="sxs-lookup"><span data-stu-id="a90aa-297">The [.NET Library Design Guidelines](../../standard/design-guidelines/exceptions.md) give excellent advice on the use of exceptions in the context of all .NET programming.</span></span> <span data-ttu-id="a90aa-298">Bu yönergeleri bazıları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a90aa-298">Some of these guidelines are as follows:</span></span>

* <span data-ttu-id="a90aa-299">Özel durumlar için normal denetim akışı kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-299">Do not use exceptions for normal flow of control.</span></span> <span data-ttu-id="a90aa-300">Bu teknik genellikle OCaml gibi dillerde kullanılsa da hataya yatkın ve .NET verimsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-300">Although this technique is often used in languages such as OCaml, it is bug-prone and can be inefficient on .NET.</span></span> <span data-ttu-id="a90aa-301">Bunun yerine, döndürme göz önünde bulundurun bir `None` seçeneği ortak veya beklenen oluşum bir hata belirten değer.</span><span class="sxs-lookup"><span data-stu-id="a90aa-301">Instead, consider returning a `None` option value to indicate a failure that is a common or expected occurrence.</span></span>

* <span data-ttu-id="a90aa-302">Bir işlevin yanlış kullanıldığında, bileşenler tarafından oluşturulan özel durumları belge.</span><span class="sxs-lookup"><span data-stu-id="a90aa-302">Document exceptions thrown by your components when a function is used incorrectly.</span></span>

* <span data-ttu-id="a90aa-303">Mümkünse, varolan özel durumlar sistemi ad alanları kullanın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-303">Where possible, employ existing exceptions from the System namespaces.</span></span> <span data-ttu-id="a90aa-304">Kaçının <xref:System.ApplicationException>ancak.</span><span class="sxs-lookup"><span data-stu-id="a90aa-304">Avoid <xref:System.ApplicationException>, though.</span></span>

* <span data-ttu-id="a90aa-305">Değil throw <xref:System.Exception> zaman onu kaçınmak için kullanıcı kodu.</span><span class="sxs-lookup"><span data-stu-id="a90aa-305">Do not throw <xref:System.Exception> when it will escape to user code.</span></span> <span data-ttu-id="a90aa-306">Bu kullanımını önleme içerir `failwith`, `failwithf`, hangi geliştirme altında kod ve komut dosyası kullanımı için kullanışlı işlevleri ancak kodundan daha belirli bir özel durum türü atma lehinde F # kitaplığı kaldırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-306">This includes avoiding the use of `failwith`, `failwithf`, which are handy functions for use in scripting and for code under development, but should be removed from F# library code in favor of throwing a more specific exception type.</span></span>

* <span data-ttu-id="a90aa-307">Kullanım `nullArg`, `invalidArg`, ve `invalidOp` throw mekanizması olarak <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, ve <xref:System.InvalidOperationException> uygun olduğunda.</span><span class="sxs-lookup"><span data-stu-id="a90aa-307">Use `nullArg`, `invalidArg`, and `invalidOp` as the mechanism to throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, and <xref:System.InvalidOperationException> when appropriate.</span></span>

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a><span data-ttu-id="a90aa-308">Seçenek değerleri hatası olağanüstü bir senaryo değildir dönüş türleri için kullandığınızda göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="a90aa-308">Consider using option values for return types when failure is not an exceptional scenario</span></span>

<span data-ttu-id="a90aa-309">.NET özel durumlara bunlar "olağanüstü"; olacağını yaklaşımdır diğer bir deyişle, nispeten nadir oluşma.</span><span class="sxs-lookup"><span data-stu-id="a90aa-309">The .NET approach to exceptions is that they should be “exceptional”; that is, they should occur relatively infrequently.</span></span> <span data-ttu-id="a90aa-310">Ancak, bazı işlemler (örneğin, bir tablo arama) sık sık başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-310">However, some operations (for example, searching a table) may fail frequently.</span></span> <span data-ttu-id="a90aa-311">F # seçenek değerleri, bu işlemlerin dönüş türleri temsil etmek için mükemmel bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-311">F# option values are an excellent way to represent the return types of these operations.</span></span> <span data-ttu-id="a90aa-312">Bu işlemler, işleme, genel "deneyin" adı öneki ile başlatın:</span><span class="sxs-lookup"><span data-stu-id="a90aa-312">These operations conventionally start with the name prefix “try”:</span></span>

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a><span data-ttu-id="a90aa-313">Uzantı üyeleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-313">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="a90aa-314">F # uzantısı üyeleri F # dikkatle geçerli-için-F # bileşenleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-314">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="a90aa-315">F # uzantı üyeleri genellikle yalnızca modlarından kullanım çoğunluğu bir türü ile ilişkili iç işlemleri kapatması bulunan işlemler için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-315">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="a90aa-316">Bir ortak çeşitli .NET türleri için F # için daha fazla kullanılan deyimsel API'leri sağlamak için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="a90aa-316">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="a90aa-317">Birleşim türleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-317">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="a90aa-318">Ayrılmış birleşimler sınıf hiyerarşileri yerine ağacında yapılandırılmış veri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-318">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="a90aa-319">Ağaç benzeri yapıları yinelemeli olarak tanımlanmış olan.</span><span class="sxs-lookup"><span data-stu-id="a90aa-319">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="a90aa-320">Devralma ile garip ancak ayrılmış birleşimler ile Zarif budur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-320">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="a90aa-321">Ayrılmış birleşimler ağaç benzeri verilerle temsil eden desen eşleştirme içinde exhaustiveness yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a90aa-321">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="a90aa-322">Kullanım `[<RequireQualifiedAccess>]` örneği adları yeterince benzersiz olmayan birleşim türleri hakkında</span><span class="sxs-lookup"><span data-stu-id="a90aa-322">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="a90aa-323">Kendinizi aynı adı ayrılmış birleşim durumları gibi farklı işlemler için en iyi adı olduğu bir etki alanında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-323">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="a90aa-324">Kullanabileceğiniz `[<RequireQualifiedAccess>]` gölgeleme nedeniyle kafa karıştırıcı hataları sıralamasını üzerinde bağımlı tetikleme önlemek için büyük/küçük harfe adlarını ayırt etmek için `open` deyimleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-324">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="a90aa-325">Bu tür tasarım gelişmesi olasılığı varsa ikili uyumlu API'leri için ayrılmış birleşimler gösterimlerini Gizle</span><span class="sxs-lookup"><span data-stu-id="a90aa-325">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="a90aa-326">Birleşimler türleri F # desen eşleştirme formlar için kısa bir programlama modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-326">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="a90aa-327">Daha önce belirtildiği gibi bu tür tasarım gelişmesi olasılığı olan somut veri Beyanları ortaya kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="a90aa-327">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="a90aa-328">Örneğin, ayrılmış bir birleşim gösterimini bir özel veya dahili bildirimi kullanarak gizlenebilir veya bir imza dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a90aa-328">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="a90aa-329">Ayrılmış birleşimler ölçüsüzce ortaya çıkıyorsa, bu sürüm için sabit kitaplığınızın kullanıcı kodu bozmadan bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-329">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="a90aa-330">Bunun yerine, türünüz değerleri desen eşlemeyi izin vermek için bir veya daha fazla Etkin desenler ortaya göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a90aa-330">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="a90aa-331">Etkin desenler F # tüketicileri F # birleşim türlerini doğrudan gösterme kaçınarak eşleşen kalıbı sağlamak için alternatif bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a90aa-331">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="a90aa-332">Satır içi işlevler ve üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="a90aa-332">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="a90aa-333">Satır içi işlevler zımni üye kısıtlamaları ve statik olarak çözümlenmiş genel türler ile kullanarak genel sayısal algoritmaları tanımlayın</span><span class="sxs-lookup"><span data-stu-id="a90aa-333">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="a90aa-334">Aritmetik üye kısıtlamaları ve F # karşılaştırma kısıtlamaları F # programlama için bir standart mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-334">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="a90aa-335">Örneğin, aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a90aa-335">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="a90aa-336">Bu işlev türü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-336">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="a90aa-337">Bu bir matematik kitaplığında ortak bir API uygun bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-337">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="a90aa-338">Türü sınıfları ve yazarak duck benzetimini yapmak için üye kısıtlamaları kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-338">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="a90aa-339">"Yazarak duck" benzetimini mümkündür F # üye kısıtlamaları kullanma.</span><span class="sxs-lookup"><span data-stu-id="a90aa-339">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="a90aa-340">Ancak, olun üyeleri, bunun içinde değil genel kullanılmalıdır F #'ta kullanın-için-F # kitaplığı tasarımları.</span><span class="sxs-lookup"><span data-stu-id="a90aa-340">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="a90aa-341">Kitaplık tasarımları bilmediğiniz veya standart örtük kısıtlamalarına göre esnek olmayan ve bir belirli framework desene bağlı olmasını kullanıcı kodu neden eğilimindedir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-341">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="a90aa-342">Ayrıca, bu şekilde üye kısıtlamaları kullanımına ağırlık çok uzun derleme sürelerini sonuçlanabilir şansı yoktur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-342">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="a90aa-343">İşleç tanımları</span><span class="sxs-lookup"><span data-stu-id="a90aa-343">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="a90aa-344">Özel simgesel işleçler tanımlamaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-344">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="a90aa-345">Özel işleçleri bazı durumlarda gereklidir ve uygulama kodu büyük gövdesi içinde çok yararlı notational aygıtlar.</span><span class="sxs-lookup"><span data-stu-id="a90aa-345">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="a90aa-346">Bir kitaplık yeni kullanıcılar adlandırılmış işlevleri genellikle kullanmak daha kolay içindir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-346">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="a90aa-347">Ayrıca, özel simgesel işleçler belgeye zor olabilir ve kullanıcılar IDE ve arama altyapılarındaki varolan sınırlamaları nedeniyle işleçler hakkında yardım aramak daha zor bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-347">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="a90aa-348">Sonuç olarak, işlevselliği adlandırılmış işlevler ve üyeleri olarak yayımlamak ve yalnızca belgeleri ve bunları sahip bilişsel maliyetini notational ağır basıyor varsa bu işlevler operatörleri ayrıca kullanıma sunmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-348">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="a90aa-349">Ölçü Birimleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-349">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="a90aa-350">F # kodunda eklenen tür güvenliği için ölçü dikkatli kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-350">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="a90aa-351">Ölçü birimleri için ek çok yazarak bilgilerini diğer .NET dilleri tarafından görüntülendiğinde silinir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-351">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="a90aa-352">.NET bileşenleri, araçları ve yansıma birimleri sans türleri görürsünüz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-352">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="a90aa-353">Örneğin, C# tüketicileri görürsünüz `float` yerine `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-353">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="a90aa-354">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="a90aa-354">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="a90aa-355">Tür kısaltmaları F # kodu basitleştirmek için dikkatli kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-355">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="a90aa-356">.NET bileşenleri, araçları ve yansıma türleri için kısaltılmış adları görmez.</span><span class="sxs-lookup"><span data-stu-id="a90aa-356">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="a90aa-357">Tür kısaltmaları önemli kullanımını daha daha karmaşık gerçekte, Tüketicileri karıştırır olduğu görünür bir etki alanı de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-357">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="a90aa-358">Tür kısaltmaları, üyeleri ve Özellikler kısaltılmış türüne kullanılabilir kişilere doğası gereği farklı olmalıdır genel türleri için kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-358">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="a90aa-359">Bu durumda, kısaltılmış türü çok tanımlanmakta gerçek tür gösterimini hakkında ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-359">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="a90aa-360">Bunun yerine, bir sınıf türü ya da tek durumda ayrılmış birleşim kısaltması kaydırma göz önünde bulundurun (ya da performans gerekli olduğunda, bir yapı türü kısaltması sarmalamak kullanmayı göz önünde bulundurun).</span><span class="sxs-lookup"><span data-stu-id="a90aa-360">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="a90aa-361">Örneğin, bir çok harita örneğin özel bir F # eşlemesi, durum olarak tanımlamak için tempting şöyledir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-361">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="a90aa-362">Ancak, bu tür mantıksal noktalı gösterim işlemlerde bir harita üzerinde işlemler aynı değildir – Örneğin, arama işleci eşleme uygun olur. [anahtar] return anahtar sözlük yerine bir özel durum yükseltme değilse boş liste.</span><span class="sxs-lookup"><span data-stu-id="a90aa-362">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="a90aa-363">Diğer .NET dilleri kullanımdan için kitaplıkları için yönergeler</span><span class="sxs-lookup"><span data-stu-id="a90aa-363">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="a90aa-364">Diğer .NET dilleri kullanımdan için kitaplıkları tasarlarken, uygun daha önemlidir [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="a90aa-364">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="a90aa-365">Bu belgede, bu kitaplıklar aksine F # temel alınan .NET kitaplıklarına olarak etiketlenir-F # kullanan kitaplıkları karşılıklı kısıtlama olmaksızın oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-365">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="a90aa-366">Temel alınan .NET kitaplıklarına tasarlama anlamına gelir F # kullanımını en aza indirerek tanıdık ve kullanılan deyimsel API'leri .NET Framework geri kalanı ile tutarlı sağlama-genel API'si belirli yapılardan.</span><span class="sxs-lookup"><span data-stu-id="a90aa-366">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="a90aa-367">Kurallar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-367">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="a90aa-368">Namespace ve türü sesign (için diğer .NET dilleri kullanımdan kitaplıklar)</span><span class="sxs-lookup"><span data-stu-id="a90aa-368">Namespace and Type sesign (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="a90aa-369">Bileşenlerinizi ortak API için .NET adlandırma kuralları uygula</span><span class="sxs-lookup"><span data-stu-id="a90aa-369">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="a90aa-370">Özel kısaltılmış adları ve .NET büyük/küçük harf yönergeleri kullanımını dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a90aa-370">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="a90aa-371">Ad alanları, türleri ve üyeleri birincil kuruluş yapısı bileşenleriniz için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-371">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="a90aa-372">Ortak işlevsellik içeren tüm dosyaları ile başlaması gereken bir `namespace` bildirimi ve yalnızca genel kullanıma yönelik varlıkları ad alanlarında türleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-372">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="a90aa-373">F # modülleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-373">Do not use F# modules.</span></span>

<span data-ttu-id="a90aa-374">Uygulama kodu, yardımcı program türlerini ve yardımcı işlevlerini tutmak için genel olmayan modüller kullanın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-374">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="a90aa-375">F # modülleri içinde kullanılamaz. tekrar yüklemesi ve diğer .NET API tasarım kavramları kullanmak için API gelecekteki evrimi sağlarlar statik türler modülleri, tercih edilen olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-375">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="a90aa-376">Örneğin, aşağıdaki genel API yerine:</span><span class="sxs-lookup"><span data-stu-id="a90aa-376">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="a90aa-377">Bunun yerine göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a90aa-377">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="a90aa-378">F # kayıt türleri türlerinin tasarım gelişmesi olmaz vanilla .NET API'lerini kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-378">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="a90aa-379">F # kayıt türleri için basit bir .NET sınıfı derleyin.</span><span class="sxs-lookup"><span data-stu-id="a90aa-379">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="a90aa-380">Bunlar, API'lerde bazı basit, kararlı türleri için uygundur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-380">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="a90aa-381">Kullanmayı düşünmelisiniz `[<NoEquality>]` ve `[<NoComparison>]` arabirimleri otomatik olarak oluşturulmasını gizlemek için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="a90aa-381">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="a90aa-382">Ayrıca vanilla .NET API'lerini değişebilir kayıt alanlarında bu çıkarır ortak alan kullanarak kaçının.</span><span class="sxs-lookup"><span data-stu-id="a90aa-382">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="a90aa-383">Her zaman bir sınıf gelecekteki evrimi için daha esnek bir seçenek API sağlayacak olup olmadığını düşünün.</span><span class="sxs-lookup"><span data-stu-id="a90aa-383">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="a90aa-384">Örneğin, aşağıdaki F # kodu Genel API'si bir C# tüketiciye sunar:</span><span class="sxs-lookup"><span data-stu-id="a90aa-384">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="a90aa-385">F #'TA:</span><span class="sxs-lookup"><span data-stu-id="a90aa-385">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="a90aa-386">C# ' TA:</span><span class="sxs-lookup"><span data-stu-id="a90aa-386">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="a90aa-387">F # birleşim türlerinde vanilla .NET API'lerini gösterimini Gizle</span><span class="sxs-lookup"><span data-stu-id="a90aa-387">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="a90aa-388">F # birleşim türleri yaygın olarak kullanılmaz bileşen sınırlarında bile F # '-için-F # kodlama.</span><span class="sxs-lookup"><span data-stu-id="a90aa-388">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="a90aa-389">Bileşenleri ve kitaplıkları içinde dahili olarak kullanılan bir mükemmel uygulama aygıt oldukları.</span><span class="sxs-lookup"><span data-stu-id="a90aa-389">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="a90aa-390">Vanilla .NET API tasarlarken, özel bir bildirim veya bir imza dosyası kullanarak bir birleşim türü gösterimini gizleme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a90aa-390">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="a90aa-391">Ayrıca bir birleşim gösterimi üyeleriyle bir istenen sağlamak için dahili olarak kullanan türlerden büyütmek. NET dönük API.</span><span class="sxs-lookup"><span data-stu-id="a90aa-391">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="a90aa-392">Tasarım GUI ve framework'ün tasarım desenleri kullanarak diğer bileşenleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-392">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="a90aa-393">Birçok farklı çerçeveleri WinForms, WPF ve ASP.NET gibi .NET içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-393">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="a90aa-394">Bu çerçeveleri kullanmak için bileşenleri tanımlıyorsanız adlandırma ve tasarım kuralları her kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-394">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="a90aa-395">Örneğin, programlama WPF için WPF tasarım desenleri tasarlarken sınıfları için benimser.</span><span class="sxs-lookup"><span data-stu-id="a90aa-395">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="a90aa-396">Kullanıcı arabirimi programlamada modelleri için Tasarım desenleri olayları gibi kullanın ve bildirim tabanlı koleksiyonlar olanlar gibi bulunan <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="a90aa-396">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="a90aa-397">Nesne ve üye tasarım (için diğer .NET dilleri kullanımdan kitaplıklar)</span><span class="sxs-lookup"><span data-stu-id="a90aa-397">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="a90aa-398">CLIEvent özniteliği .NET olaylar oluşturmak için kullanın</span><span class="sxs-lookup"><span data-stu-id="a90aa-398">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="a90aa-399">Oluşturmak bir `DelegateEvent` belirli bir .NET ile temsilci bir nesne alan türü ve `EventArgs` (yerine bir `Event`, yalnızca kullanan `FSharpHandler` türü varsayılan olarak) diğer .NET dilleri benzer şekilde olayların yayımlandığı böylece.</span><span class="sxs-lookup"><span data-stu-id="a90aa-399">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="a90aa-400">Zaman uyumsuz işlemleri .NET görevleri döndürmesi yöntemleri olarak kullanıma sunma</span><span class="sxs-lookup"><span data-stu-id="a90aa-400">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="a90aa-401">Görevler .NET etkin zaman uyumsuz hesapları temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-401">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="a90aa-402">Görevlerdir genel F # daha az compositional `Async<T>` nesneleri "zaten Yürütülüyor" görevleri temsil eder ve birlikte paralel birleşim gerçekleştirmek ya da iptal sinyalleri ve diğer yayılmasını Gizle yollarla oluşamaz Bağlam parametreleri.</span><span class="sxs-lookup"><span data-stu-id="a90aa-402">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="a90aa-403">Ancak, bu rağmen görevleri döndürmesi yöntemleri zaman uyumsuz programlama .NET üzerinde standart temsili değildir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-403">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="a90aa-404">Sık olur da açık iptal belirteci kabul etmek isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a90aa-404">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="a90aa-405">F # işlev türleri yerine .NET temsilci türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a90aa-405">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="a90aa-406">Burada "F # işlev türleri", "OK" türleri ister anlamına gelir `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-406">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="a90aa-407">Bunun yerine:</span><span class="sxs-lookup"><span data-stu-id="a90aa-407">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="a90aa-408">Bunu yapın:</span><span class="sxs-lookup"><span data-stu-id="a90aa-408">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="a90aa-409">F # işlev türü olarak görünür `class FSharpFunc<T,U>` diğer .NET dilleri için ve dil özellikleri ve araçları için temsilci türleri anlamak daha az uygundur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-409">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="a90aa-410">.NET Framework 3.5 veya daha yüksek hedefleme daha yüksek sıralı yöntemi yazarken `System.Func` ve `System.Action` temsilciler olan bir düşük uyuşmazlık şekilde bu API'leri kullanmak .NET geliştiricilerin yayımlamak için doğru API'leri.</span><span class="sxs-lookup"><span data-stu-id="a90aa-410">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="a90aa-411">(.NET Framework 2.0 hedeflerken sistem tarafından tanımlanan temsilci türleri daha sınırlıdır; önceden tanımlanmış temsilci türleri gibi kullanmayı `System.Converter<T,U>` veya belirli bir temsilci türü tanımlama.)</span><span class="sxs-lookup"><span data-stu-id="a90aa-411">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="a90aa-412">Çevir tarafında .NET temsilciler F # için doğal olmayan-kitaplıkları karşılıklı (F # sonraki bölüme bakın-kitaplıkları karşılıklı).</span><span class="sxs-lookup"><span data-stu-id="a90aa-412">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="a90aa-413">Sonuç olarak, tüm F # işlev türleri kullanarak uygulama yazmak ve temsilciler üzerinde gerçek F # ince cephesi kullanarak genel API'si oluşturmak için temel alınan .NET kitaplıkları için daha yüksek sıralı yöntemleri geliştirirken, ortak bir uygulama stratejisi olduğu uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a90aa-413">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="a90aa-414">F # seçeneği değerler döndüren yerine TryGetValue deseni kullanılacak ve F # seçenek değerleri bağımsız değişken olarak alan için yöntem aşırı yükleme tercih</span><span class="sxs-lookup"><span data-stu-id="a90aa-414">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="a90aa-415">F # seçenek türü için API kullanımı ortak desenler daha iyi vanilla içinde uygulanan standart .NET kullanarak .NET API'lerini teknikleri tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="a90aa-415">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="a90aa-416">Bir F # seçeneği değer döndürme yerine bool dönüş türü artı out parametresi "TryGetValue" deseni olduğu gibi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a90aa-416">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="a90aa-417">Ve F # seçeneği değerleri parametre olarak ayırdığınız yerine yöntemi aşırı yüklenmesi veya isteğe bağlı bağımsız değişkenler kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="a90aa-417">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="a90aa-418">.NET koleksiyonu arabirimini kullanın türleri IEnumerable\<T\> ve IDictionary\<anahtar, değer\> için parametreler ve dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="a90aa-418">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="a90aa-419">.NET diziler gibi somut koleksiyon türleri kullanmaktan kaçının `T[]`, F # türleri `list<T>`, `Map<Key,Value>` ve `Set<T>`, ve .NET somut koleksiyon türleri gibi `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-419">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="a90aa-420">.NET kitaplığı tasarım yönergeleri ile ilgili çeşitli koleksiyon türleri gibi kullanmak iyi öneriler sahip `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-420">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="a90aa-421">Diziler bazı kullanımını (`T[]`) performans işe son verme üzerinde bazı durumlarda, kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-421">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="a90aa-422">Özellikle dikkat edin `seq<T>` yalnızca F # için diğer ad olduğu `IEnumerable<T>`, ve bunun sonucunda seq genellikle vanilla .NET API için uygun bir tür.</span><span class="sxs-lookup"><span data-stu-id="a90aa-422">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="a90aa-423">F # yerine listeler:</span><span class="sxs-lookup"><span data-stu-id="a90aa-423">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="a90aa-424">F # dizileri kullanın:</span><span class="sxs-lookup"><span data-stu-id="a90aa-424">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="a90aa-425">Bir bağımsız değişkeni sıfır yöntemi tanımlamak için bir yöntem yalnızca girdi türü olarak birim türünü kullanın ya da yalnızca dönüş türü void döndüren bir yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="a90aa-425">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="a90aa-426">Diğer kullanımlar birim türü kaçının.</span><span class="sxs-lookup"><span data-stu-id="a90aa-426">Avoid other uses of the unit type.</span></span> <span data-ttu-id="a90aa-427">Bunlar iyi şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a90aa-427">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="a90aa-428">Bu bozuk.</span><span class="sxs-lookup"><span data-stu-id="a90aa-428">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="a90aa-429">Temel alınan .NET API sınırları null değerler denetleyin</span><span class="sxs-lookup"><span data-stu-id="a90aa-429">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="a90aa-430">F # uygulama kodu değişmez tasarım desenleri ve F # türleri için null değişmez değerleri kullanma kısıtlamaları nedeniyle daha az boş değerlere sahip eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-430">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="a90aa-431">Diğer .NET dilleri genellikle bir değer olarak null çok daha sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-431">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="a90aa-432">Bu nedenle, vanilla .NET API gösterme F # kodu API sınırlar null parametreleri denetleyin ve bu değerleri daha derin F # uygulama koduna akan engelleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-432">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="a90aa-433">`isNull` İşlevi veya desen üzerinde eşleştirme `null` düzeni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-433">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="a90aa-434">Dönüş değerleri olarak diziler kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-434">Avoid using tuples as return values</span></span>

<span data-ttu-id="a90aa-435">Bunun yerine, veri toplama tutarak veya birden çok değer döndürmek için out parametreleri kullanarak adlandırılmış bir tür döndüren tercih eder.</span><span class="sxs-lookup"><span data-stu-id="a90aa-435">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="a90aa-436">Diziler ve yapı diziler .NET içinde mevcut olmasına karşın (C# dil desteğini yapısı başlıkları dahil), bunlar ideal ve beklenen API .NET geliştiricileri için sağlamaz çoğunlukla.</span><span class="sxs-lookup"><span data-stu-id="a90aa-436">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="a90aa-437">Parametreleri currying kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="a90aa-437">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="a90aa-438">Bunun yerine, .NET çağırma kuralları kullanın ``Method(arg1,arg2,…,argN)``.</span><span class="sxs-lookup"><span data-stu-id="a90aa-438">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="a90aa-439">İpucu: kitaplıkları için herhangi bir .NET dil kullanımdan tasarlarken, ardından yoktur gerçekte bazı Deneysel C# ve Visual Basic Kitaplıklarınızı "kullanımında sağ" Bu dillerdeki emin olmak için programlama yapmak için hiçbir yedek.</span><span class="sxs-lookup"><span data-stu-id="a90aa-439">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="a90aa-440">.NET Reflector ve Visual Studio nesne tarayıcısı gibi araçlar, kitaplıklar ve kendi belgelerine geliştiricilerine beklendiği gibi göründüğünden emin olmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a90aa-440">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="a90aa-441">Ek</span><span class="sxs-lookup"><span data-stu-id="a90aa-441">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="a90aa-442">Uçtan uca örnek F # kodu kullanmak için diğer .NET dilleri tarafından tasarlama</span><span class="sxs-lookup"><span data-stu-id="a90aa-442">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="a90aa-443">Aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="a90aa-443">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="a90aa-444">Bu sınıf oluşturulursa F # türü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-444">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="a90aa-445">Bu F # tür başka bir .NET dilini kullanarak bir programcı görünme bir bakalım.</span><span class="sxs-lookup"><span data-stu-id="a90aa-445">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="a90aa-446">Örneğin, yaklaşık C# "imza" aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-446">For example, the approximate C# “signature” is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="a90aa-447">Nasıl F # burada yapıları temsil eden hakkında fark edilecek bazı önemli noktalar vardır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-447">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="a90aa-448">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a90aa-448">For example:</span></span>

* <span data-ttu-id="a90aa-449">Bağımsız değişken adları gibi meta veriler korunur.</span><span class="sxs-lookup"><span data-stu-id="a90aa-449">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="a90aa-450">İki bağımsız değişkenler almayan F # yöntemleri iki bağımsız değişkenler almayan C# yöntemleri haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-450">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="a90aa-451">İşlevler ve listeleri karşılık gelen türlerine F # Kitaplığı'nda başvurular haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-451">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="a90aa-452">Aşağıdaki kod bu konuları dikkate almanız için bu kodu ayarlama konusunda gösterir.</span><span class="sxs-lookup"><span data-stu-id="a90aa-452">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="a90aa-453">Çıkarılan F # türü kod aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-453">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="a90aa-454">C# imza şimdi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="a90aa-454">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="a90aa-455">Temel alınan bir .NET kitaplığı bir parçası olarak aşağıdaki gibi bu tür kullanıma hazırlamak düzeltmeleri yaptık:</span><span class="sxs-lookup"><span data-stu-id="a90aa-455">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="a90aa-456">Birden fazla ad ayarlandı: `Point1`, `n`, `l`, ve `f` hale geldi `RadialPoint`, `count`, `factor`, ve `transform`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="a90aa-456">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="a90aa-457">Dönüş türü kullanılan `seq<RadialPoint>` yerine `RadialPoint list` listesini kullanarak yapım değiştirerek `[ ... ]` dizisi kullanılarak yapımı için `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="a90aa-457">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="a90aa-458">.NET temsilci türü kullanılan `System.Func` yerine bir F # işlev türü.</span><span class="sxs-lookup"><span data-stu-id="a90aa-458">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="a90aa-459">Bu, çok daha Hoş görünmesi C# kodunda tüketmeye kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="a90aa-459">This makes it far nicer to consume in C# code.</span></span>
