---
title: F# bileşen tasarımı yönergeleri
description: 'Diğer çağıranlar tarafından tüketim için tasarlanan F # bileşenlerini yazma yönergelerini öğrenin.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209142"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="fe470-103">F# bileşen tasarımı yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fe470-103">F# component design guidelines</span></span>

<span data-ttu-id="fe470-104">Bu belge f # programlamasında, f # bileşeni tasarım yönergeleri, v14, Microsoft Research ve F # Software Foundation tarafından oluşturulan ve korunan bir sürümü temel alan bir bileşen tasarım yönergeleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="fe470-105">Bu belge, F # programlama hakkında bilgi sahibi olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="fe470-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="fe470-106">Birçok, bu kılavuzun çeşitli sürümleriyle ilgili katkılarına ve yararlı bildirimlere yönelik olarak F # topluluğu için teşekkürler.</span><span class="sxs-lookup"><span data-stu-id="fe470-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="fe470-107">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fe470-107">Overview</span></span>

<span data-ttu-id="fe470-108">Bu belge F # bileşen tasarımı ve kodlama ile ilgili bazı sorunları inceler.</span><span class="sxs-lookup"><span data-stu-id="fe470-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="fe470-109">Bir bileşen, aşağıdakilerden herhangi biri anlamına gelebilir:</span><span class="sxs-lookup"><span data-stu-id="fe470-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="fe470-110">F # projenizdeki, bu proje içinde harici tüketicilerle olan bir katman.</span><span class="sxs-lookup"><span data-stu-id="fe470-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="fe470-111">Derleme sınırları genelinde F # kodu tarafından tüketime için tasarlanan bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="fe470-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="fe470-112">Derleme sınırları genelinde herhangi bir .NET dili tarafından tüketimine yönelik bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="fe470-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="fe470-113">[NuGet](https://nuget.org)gibi bir paket deposu aracılığıyla dağıtıma yönelik bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="fe470-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="fe470-114">Bu makalede açıklanan teknikler, [Iyi F # kodunun beş prensipini](index.md#five-principles-of-good-f-code)izler ve bu nedenle hem işlevsel hem de nesne programlamayı uygun şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="fe470-115">Metodolojiden bağımsız olarak, bileşen ve kitaplık Tasarımcısı, geliştiriciler tarafından en kolay şekilde kullanılabilen bir API 'yi oluşturmaya çalışırken bir dizi pratik ve prosaic sorunu ortaya yayınlar.</span><span class="sxs-lookup"><span data-stu-id="fe470-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="fe470-116">[.NET kitaplığı tasarım yönergelerinden](../../standard/design-guidelines/index.md) oluşan yarışma, kullanım açısından uygun olan tutarlı bir API kümesi oluşturmak için size yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="fe470-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="fe470-117">Genel yönergeler</span><span class="sxs-lookup"><span data-stu-id="fe470-117">General guidelines</span></span>

<span data-ttu-id="fe470-118">Kitaplık için amaçlanan kitleden bağımsız olarak F # kitaplıkları için uygulanan birkaç evrensel yönerge vardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="fe470-119">.NET kitaplığı tasarım yönergelerini öğrenin</span><span class="sxs-lookup"><span data-stu-id="fe470-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="fe470-120">Yaptığınız F # kodlamasının türü ne olursa olsun, [.NET kitaplığı tasarım yönergeleriyle](../../standard/design-guidelines/index.md)çalışan bir bilgiye sahip olmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="fe470-121">Diğer tüm F # ve .NET programcılarının çoğu bu kılavuzla tanıdık gelecektir ve .NET kodunun bunlara uymasını bekler.</span><span class="sxs-lookup"><span data-stu-id="fe470-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="fe470-122">.NET kitaplığı tasarım yönergeleri, adlandırma, sınıfları ve arabirimleri tasarlama, üye tasarımı (özellikler, Yöntemler, olaylar, vb.) ve daha fazlası ile ilgili genel yönergeler sağlar ve çeşitli tasarım kılavuzlarından oluşan yararlı bir ilk başvuru noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="fe470-123">Kodunuza XML belge açıklamaları ekleme</span><span class="sxs-lookup"><span data-stu-id="fe470-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="fe470-124">Ortak API 'lerde XML belgeleri, kullanıcıların bu türleri ve üyeleri kullanırken harika IntelliSense ve QuickInfo almasını ve kitaplık için belge dosyaları oluşturmayı etkinleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe470-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="fe470-125">XmlDoc açıklamaları içinde ek biçimlendirme için kullanılabilecek çeşitli XML etiketleri hakkında [XML belgelerine](../language-reference/xml-documentation.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="fe470-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="fe470-126">Kısa form XML açıklamalarını ( `/// comment` ) ya da standart XML açıklamalarını ( `///<summary>comment</summary>` ) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="fe470-127">Kararlı kitaplık ve bileşen API 'Leri için açık imza dosyaları (. fsi) kullanmayı düşünün</span><span class="sxs-lookup"><span data-stu-id="fe470-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="fe470-128">Bir F # kitaplığındaki açık imzalar dosyalarının kullanılması, genel API 'nin kısa bir özetini sağlar. Bu, kitaplığınızın tam genel yüzeyini bilmenizi sağlamaya yardımcı olur ve ortak belgeler ile iç uygulama ayrıntıları arasında temiz bir ayrım sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe470-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="fe470-129">İmza dosyaları, hem uygulama hem de imza dosyalarında değişiklik yapılmasını gerektiren ortak API 'yi değiştirmeye yönelik uçuşmayı ekler.</span><span class="sxs-lookup"><span data-stu-id="fe470-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="fe470-130">Sonuç olarak, imza dosyaları genellikle yalnızca bir API 'nin tahmin edildiğinde ve önemli ölçüde değişmemesi beklendiğinde tanıtılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="fe470-131">.NET 'teki dizeleri kullanmak için her zaman en iyi uygulamaları izleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="fe470-132">[.Net Kılavuzu 'Nda dizeleri kullanmak Için En Iyi uygulamaları](../../standard/base-types/best-practices-strings.md) izleyin.</span><span class="sxs-lookup"><span data-stu-id="fe470-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="fe470-133">Özellikle, dizelerin dönüştürülmesine ve karşılaştırmasına göre (uygulanabilir olduğunda) her zaman açık bir *şekilde eyalet.*</span><span class="sxs-lookup"><span data-stu-id="fe470-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="fe470-134">F # ile bağlantılı kitaplıklar için yönergeler</span><span class="sxs-lookup"><span data-stu-id="fe470-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="fe470-135">Bu bölümde, genel F # ile ilgili kitaplıkların geliştirilmesi için öneriler sunulmaktadır; diğer bir deyişle, F # geliştiricileri tarafından tüketilmesi amaçlanan genel API 'Leri kullanıma sunan kitaplıklardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="fe470-136">Özellikle F # için geçerli olan çok sayıda kitaplık tasarımı önerisi vardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="fe470-137">Aşağıdaki belirli önerilerin yokluğunda, .NET kitaplığı tasarım yönergeleri, geri dönüş kılavuzluğu ' dir.</span><span class="sxs-lookup"><span data-stu-id="fe470-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="fe470-138">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="fe470-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="fe470-139">.NET adlandırma ve büyük/küçük harf kuralları kullanma</span><span class="sxs-lookup"><span data-stu-id="fe470-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="fe470-140">Aşağıdaki tabloda .NET adlandırma ve büyük/küçük harf kuralları yer verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe470-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="fe470-141">F # yapılarını da içeren küçük eklemeler vardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="fe470-142">Oluştur</span><span class="sxs-lookup"><span data-stu-id="fe470-142">Construct</span></span> | <span data-ttu-id="fe470-143">Case (Olay)</span><span class="sxs-lookup"><span data-stu-id="fe470-143">Case</span></span> | <span data-ttu-id="fe470-144">Bölüm</span><span class="sxs-lookup"><span data-stu-id="fe470-144">Part</span></span> | <span data-ttu-id="fe470-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fe470-145">Examples</span></span> | <span data-ttu-id="fe470-146">Notlar</span><span class="sxs-lookup"><span data-stu-id="fe470-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="fe470-147">Somut türler</span><span class="sxs-lookup"><span data-stu-id="fe470-147">Concrete types</span></span> | <span data-ttu-id="fe470-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-148">PascalCase</span></span> | <span data-ttu-id="fe470-149">Ad/sıfatıcı</span><span class="sxs-lookup"><span data-stu-id="fe470-149">Noun/ adjective</span></span> | <span data-ttu-id="fe470-150">List, Double, Complex</span><span class="sxs-lookup"><span data-stu-id="fe470-150">List, Double, Complex</span></span> | <span data-ttu-id="fe470-151">Somut türler yapılar, sınıflar, numaralandırmalar, temsilciler, kayıtlar ve birleşimler.</span><span class="sxs-lookup"><span data-stu-id="fe470-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="fe470-152">Tür adları OCaml 'de geleneksel olarak küçük olsa da, F # türler için .NET adlandırma şemasını benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="fe470-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="fe470-153">DLL'ler</span><span class="sxs-lookup"><span data-stu-id="fe470-153">DLLs</span></span>           | <span data-ttu-id="fe470-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-154">PascalCase</span></span> |                 | <span data-ttu-id="fe470-155">Fabrikam. Core. dll</span><span class="sxs-lookup"><span data-stu-id="fe470-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="fe470-156">Birleşim etiketleri</span><span class="sxs-lookup"><span data-stu-id="fe470-156">Union tags</span></span>     | <span data-ttu-id="fe470-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-157">PascalCase</span></span> | <span data-ttu-id="fe470-158">İsim</span><span class="sxs-lookup"><span data-stu-id="fe470-158">Noun</span></span> | <span data-ttu-id="fe470-159">Bazıları, ekleme, başarı</span><span class="sxs-lookup"><span data-stu-id="fe470-159">Some, Add, Success</span></span> | <span data-ttu-id="fe470-160">Genel API 'lerde bir ön ek kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="fe470-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="fe470-161">İsteğe bağlı olarak, iç zaman bir önek kullanın, örneğin`type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="fe470-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="fe470-162">Olay</span><span class="sxs-lookup"><span data-stu-id="fe470-162">Event</span></span>          | <span data-ttu-id="fe470-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-163">PascalCase</span></span> | <span data-ttu-id="fe470-164">Fiil</span><span class="sxs-lookup"><span data-stu-id="fe470-164">Verb</span></span> | <span data-ttu-id="fe470-165">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="fe470-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="fe470-166">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="fe470-166">Exceptions</span></span>     | <span data-ttu-id="fe470-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-167">PascalCase</span></span> |      | <span data-ttu-id="fe470-168">Gönderdi</span><span class="sxs-lookup"><span data-stu-id="fe470-168">WebException</span></span> | <span data-ttu-id="fe470-169">Ad "Exception" ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="fe470-170">Alan</span><span class="sxs-lookup"><span data-stu-id="fe470-170">Field</span></span>          | <span data-ttu-id="fe470-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-171">PascalCase</span></span> | <span data-ttu-id="fe470-172">İsim</span><span class="sxs-lookup"><span data-stu-id="fe470-172">Noun</span></span> | <span data-ttu-id="fe470-173">CurrentName</span><span class="sxs-lookup"><span data-stu-id="fe470-173">CurrentName</span></span>  | |
| <span data-ttu-id="fe470-174">Arabirim türleri</span><span class="sxs-lookup"><span data-stu-id="fe470-174">Interface types</span></span> |  <span data-ttu-id="fe470-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-175">PascalCase</span></span> | <span data-ttu-id="fe470-176">Ad/sıfatıcı</span><span class="sxs-lookup"><span data-stu-id="fe470-176">Noun/ adjective</span></span> | <span data-ttu-id="fe470-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="fe470-177">IDisposable</span></span> | <span data-ttu-id="fe470-178">Ad "I" ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-178">Name should start with "I".</span></span> |
| <span data-ttu-id="fe470-179">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fe470-179">Method</span></span> |  <span data-ttu-id="fe470-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-180">PascalCase</span></span> |  <span data-ttu-id="fe470-181">Fiil</span><span class="sxs-lookup"><span data-stu-id="fe470-181">Verb</span></span> | <span data-ttu-id="fe470-182">ToString</span><span class="sxs-lookup"><span data-stu-id="fe470-182">ToString</span></span> | |
| <span data-ttu-id="fe470-183">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="fe470-183">Namespace</span></span> | <span data-ttu-id="fe470-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-184">PascalCase</span></span> | | <span data-ttu-id="fe470-185">Microsoft. FSharp. Core</span><span class="sxs-lookup"><span data-stu-id="fe470-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="fe470-186">Genellikle `<Organization>.<Technology>[.<Subnamespace>]` teknolojisini kullanır, ancak teknolojinin kuruluştan bağımsız olması halinde organizasyonu bırakın.</span><span class="sxs-lookup"><span data-stu-id="fe470-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="fe470-187">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe470-187">Parameters</span></span> | <span data-ttu-id="fe470-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="fe470-188">camelCase</span></span> | <span data-ttu-id="fe470-189">İsim</span><span class="sxs-lookup"><span data-stu-id="fe470-189">Noun</span></span> |  <span data-ttu-id="fe470-190">typeName, Transform, Aralık</span><span class="sxs-lookup"><span data-stu-id="fe470-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="fe470-191">izin ver (iç)</span><span class="sxs-lookup"><span data-stu-id="fe470-191">let values (internal)</span></span> | <span data-ttu-id="fe470-192">camelCase veya PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-192">camelCase or PascalCase</span></span> | <span data-ttu-id="fe470-193">Ad/fiil</span><span class="sxs-lookup"><span data-stu-id="fe470-193">Noun/ verb</span></span> |  <span data-ttu-id="fe470-194">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="fe470-194">getValue, myTable</span></span> |
| <span data-ttu-id="fe470-195">değerlere izin ver (dış)</span><span class="sxs-lookup"><span data-stu-id="fe470-195">let values (external)</span></span> | <span data-ttu-id="fe470-196">camelCase veya PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-196">camelCase or PascalCase</span></span> | <span data-ttu-id="fe470-197">Ad/fiil</span><span class="sxs-lookup"><span data-stu-id="fe470-197">Noun/verb</span></span>  | <span data-ttu-id="fe470-198">List. map, tarihlere. bugün</span><span class="sxs-lookup"><span data-stu-id="fe470-198">List.map, Dates.Today</span></span> | <span data-ttu-id="fe470-199">daha geleneksel işlevsel tasarım desenleri aşağıdaki durumlarda, izin-bağlanacak değerler genellikle genel kullanıma açıktır.</span><span class="sxs-lookup"><span data-stu-id="fe470-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="fe470-200">Ancak, tanımlayıcı diğer .NET dillerinden kullanılabilecek şekilde genellikle PascalCase kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe470-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="fe470-201">Özellik</span><span class="sxs-lookup"><span data-stu-id="fe470-201">Property</span></span>  | <span data-ttu-id="fe470-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="fe470-202">PascalCase</span></span>  | <span data-ttu-id="fe470-203">Ad/sıfatıcı</span><span class="sxs-lookup"><span data-stu-id="fe470-203">Noun/ adjective</span></span>  | <span data-ttu-id="fe470-204">Ienddoffile, BackColor</span><span class="sxs-lookup"><span data-stu-id="fe470-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="fe470-205">Boolean özellikleri genellikle ' dir ve ' in IsNotEndOfFile değil, ıenddoffile dosyasında olduğu gibi, bunun da bir değerlendirme olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe470-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="fe470-206">Kısaltmaların önleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-206">Avoid abbreviations</span></span>

<span data-ttu-id="fe470-207">.NET yönergeleri kısaltmaların kullanımını önleyin (örneğin, " `OnButtonClick` yerine kullanın `OnBtnClick` ").</span><span class="sxs-lookup"><span data-stu-id="fe470-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="fe470-208">`Async`"Zaman uyumsuz" gibi yaygın kısaltmalar toleranslı olarak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="fe470-209">Bu kılavuz bazen işlevsel programlama için yok sayılır; Örneğin, `List.iter` "ITERATE" için bir kısaltma kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="fe470-210">Bu nedenle, kısaltmaların kullanılması F #-to-F # programlamada daha büyük bir ölçüde toleranslı hale gelmelidir, ancak genel bileşen tasarımında yine de kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="fe470-211">Büyük küçük harf çakışmalarını önleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-211">Avoid casing name collisions</span></span>

<span data-ttu-id="fe470-212">.NET yönergeleri, bazı istemci dilleri (örneğin, Visual Basic) büyük/küçük harfe duyarsız olduğundan, tek başına büyük küçük harf olarak ad çakışmalarını ortadan kaldırmak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fe470-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="fe470-213">Uygun yerlerde kısaltmalar kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="fe470-214">XML gibi kısaltmalar kısaltmalar değildir ve .NET kitaplıklarında büyük harfli olmayan biçimde (XML) yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe470-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="fe470-215">Yalnızca iyi bilinen, yaygın olarak tanınan kısaltmalar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="fe470-216">Genel parametre adları için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="fe470-217">F # kullanan kitaplıklar dahil genel API 'lerde genel parametre adları için PascalCase kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe470-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="fe470-218">Özellikle,,,,, `T` `U` `T1` `T2` rastgele genel parametreler için, ve belirli adların anlamlı olduğu durumlarda gibi adları kullanın, F # ile bağlantılı kitaplıklar için `Key` , `Value` `Arg` (örneğin, değil) adlarını kullanın `TKey` .</span><span class="sxs-lookup"><span data-stu-id="fe470-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="fe470-219">F # modüllerinde ortak işlevler ve değerler için PascalCase ya da camelCase kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="fe470-220">camelCase, nitelenmemiş kullanılacak şekilde tasarlanan (örneğin, `invalidArg` ) ve "Standart koleksiyon işlevleri" (örneğin, List. Map) için kullanılan genel işlevler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe470-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="fe470-221">Bu iki durumda da işlev adları, dildeki anahtar sözcüklere çok benzer şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="fe470-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="fe470-222">Nesne, tür ve modül tasarımı</span><span class="sxs-lookup"><span data-stu-id="fe470-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="fe470-223">Türlerinizi ve modüllerinizi içerecek şekilde ad alanlarını veya modülleri kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="fe470-224">Bir bileşendeki her F # dosyası, bir ad alanı bildirimiyle veya bir modül bildirimiyle başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="fe470-225">veya</span><span class="sxs-lookup"><span data-stu-id="fe470-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="fe470-226">En üst düzeyde kod düzenlemek için modüller ve ad alanları kullanma arasındaki farklar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="fe470-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="fe470-227">Ad alanları birden çok dosyaya yayılabilir</span><span class="sxs-lookup"><span data-stu-id="fe470-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="fe470-228">Ad alanları, bir iç modül içinde olmadıkları müddetçe F # işlevleri içeremez</span><span class="sxs-lookup"><span data-stu-id="fe470-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="fe470-229">Belirli bir modülün kodu tek bir dosya içinde bulunmalıdır</span><span class="sxs-lookup"><span data-stu-id="fe470-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="fe470-230">Üst düzey modüller, bir iç modüle gerek olmadan F # işlevleri içerebilir</span><span class="sxs-lookup"><span data-stu-id="fe470-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="fe470-231">Üst düzey bir ad alanı veya modül arasındaki seçim, kodun derlenmiş biçimini etkiler ve bu nedenle API 'nizin sonunda F # kodu dışında tüketilmesi için diğer .NET dillerinden görünümü etkiler.</span><span class="sxs-lookup"><span data-stu-id="fe470-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="fe470-232">Nesne türlerine yönelik işlemler için yöntemleri ve özellikleri kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="fe470-233">Nesnelerle çalışırken, tüketilebilir işlevselliğin bu tür üzerinde Yöntemler ve özellikler olarak uygulandığından emin olmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="fe470-234">Belirli bir üye için işlevselliğin toplu olması, söz konusu üyeye uygulanmamalıdır, ancak söz konusu işlevin tüketilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe470-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="fe470-235">Kesilebilir durumu kapsüllemek için sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="fe470-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="fe470-236">F # ' da, bu durumun yalnızca bir kapanış, sıra ifadesi veya zaman uyumsuz hesaplama gibi başka bir dil yapısı tarafından kapsüllenmediğinden yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe470-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="fe470-237">İlgili işlemleri gruplamak için arabirimler kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="fe470-238">Bir dizi işlemi temsil etmek için arabirim türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe470-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="fe470-239">Bu, işlevlerin veya işlev kayıtlarının başlıkları gibi diğer seçeneklere tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="fe470-240">Tercihe göre:</span><span class="sxs-lookup"><span data-stu-id="fe470-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="fe470-241">Arabirimler, .NET 'teki birinci sınıf kavramlardır ve bu sayede, Funların normalde size nasıl sağlayabileceklerini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="fe470-242">Ayrıca, varlıksal türlerini programınıza kodlamak için kullanılabilirler, bu da işlev kayıtları olamaz.</span><span class="sxs-lookup"><span data-stu-id="fe470-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="fe470-243">Koleksiyonlar üzerinde hareket eden işlevleri gruplandırmak için bir modül kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="fe470-244">Bir koleksiyon türü tanımladığınızda, `CollectionType.map` `CollectionType.iter` Yeni koleksiyon türleri için ve gibi standart bir işlem kümesi sağlamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="fe470-245">Böyle bir modül eklerseniz, FSharp. Core 'da bulunan işlevler için standart adlandırma kurallarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="fe470-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="fe470-246">Özellikle matematik ve DSL kitaplıklarında ortak, kurallı işlevler için işlevleri gruplamak üzere bir modül kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="fe470-247">Örneğin, `Microsoft.FSharp.Core.Operators` `abs` `sin` FSharp. Core. dll tarafından belirtilen en üst düzey işlevlerin (ve gibi) otomatik olarak açılmış bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="fe470-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="fe470-248">Benzer şekilde, bir istatistik kitaplığı işlevleri olan bir modül içerebilir `erf` ve `erfc` Bu modül açıkça veya otomatik olarak açılacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe470-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="fe470-249">RequireQualifiedAccess kullanmayı düşünün ve oto aç özniteliklerini dikkatle uygulayın</span><span class="sxs-lookup"><span data-stu-id="fe470-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="fe470-250">`[<RequireQualifiedAccess>]`Özniteliği bir modüle eklemek, modülün açılamayabilir ve modülün öğelerine yapılan başvuruların açık nitelikli erişim gerektirdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe470-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="fe470-251">Örneğin, `Microsoft.FSharp.Collections.List` modülün bu özniteliği vardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="fe470-252">Bu, modüldeki işlevlerin ve değerlerin diğer modüllerdeki adlarla çakışabilecek adlara sahip olduğu durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="fe470-253">Tam erişim gerektirmek, bir kitaplığın uzun süreli bakım ve gelişmesini büyük ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="fe470-254">`[<AutoOpen>]`Özniteliği bir modüle eklemek, kapsayan ad alanı açıldığında modülün açılıp açılmayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fe470-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="fe470-255">`[<AutoOpen>]`Özniteliği, derlemeye başvuruluyorsa otomatik olarak açılan bir modülü göstermek için bir derlemeye de uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="fe470-256">Örneğin, bir istatistik Kitaplığı **MathsHeaven. STATISTICS** bir `module MathsHeaven.Statistics.Operators` kapsayan işlevler `erf` ve içerebilir `erfc` .</span><span class="sxs-lookup"><span data-stu-id="fe470-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="fe470-257">Bu modülün olarak işaretlenmesi mantıklıdır `[<AutoOpen>]` .</span><span class="sxs-lookup"><span data-stu-id="fe470-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="fe470-258">Bu, `open MathsHeaven.Statistics` Ayrıca bu modülün açılacağı ve adları ve kapsamına getirecek anlamına gelir `erf` `erfc` .</span><span class="sxs-lookup"><span data-stu-id="fe470-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="fe470-259">Uygulamasının başka bir kullanımı `[<AutoOpen>]` , uzantı yöntemleri içeren modüller içindir.</span><span class="sxs-lookup"><span data-stu-id="fe470-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="fe470-260">`[<AutoOpen>]`Kirletilmişti ad alanlarına müşteri adayları fazla kullanımı ve özniteliği dikkatli olarak kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="fe470-261">Belirli etki alanlarındaki belirli kitaplıklar için, imdicemlik kullanımı `[<AutoOpen>]` daha iyi kullanılabilirlik elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="fe470-262">İyi bilinen işleçlerin kullanılması uygun olan sınıflarda işleç üyelerini tanımlamayı düşünün</span><span class="sxs-lookup"><span data-stu-id="fe470-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="fe470-263">Bazen sınıflar, vektör gibi matematik yapılarını modellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe470-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="fe470-264">Modellenen etki alanının iyi bilinen işleçleri olduğunda, bunları sınıfa iç üye olarak tanımlamak faydalı olur.</span><span class="sxs-lookup"><span data-stu-id="fe470-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="fe470-265">Bu kılavuz, bu türler için genel .NET yönergelerine karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="fe470-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="fe470-266">Bununla birlikte, F # kodlamasına ek olarak da önemli olabilir. Bu, bu türlerin F # işlevleriyle ve List. sumBy gibi üye kısıtlamalarına sahip yöntemlerle birlikte kullanılmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="fe470-267">Bir sağlamak için CompiledName kullanmayı düşünün. Diğer .NET dil tüketicileri için NET-kolay ad</span><span class="sxs-lookup"><span data-stu-id="fe470-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="fe470-268">Bazen F # tüketicilerinin (modül bağlantılı işlevmiş gibi görünmesi için bir statik üye gibi) bir stili bir stil olarak adlandırmak isteyebilirsiniz, ancak bir derlemeye derlendiğinde ad için farklı bir stile sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="fe470-269">`[<CompiledName>]`Derlemeyi kullanan F # olmayan kod için farklı bir stil sağlamak üzere özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="fe470-270">Kullanarak `[<CompiledName>]` , derlemenin F # tüketicilerine yönelik .net adlandırma kurallarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="fe470-271">Daha basit bir API sağlayan üye işlevleri için yöntem aşırı yüklemesini kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="fe470-272">Yöntem aşırı yüklemesi, farklı seçeneklerle veya bağımsız değişkenlerle benzer işlevler gerçekleştirmesi gerekebilecek bir API 'YI basitleştirmek için güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="fe470-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="fe470-273">F # ' da, bağımsız değişken türleri yerine bağımsız değişken sayısında aşırı yükleme daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="fe470-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="fe470-274">Bu türlerin tasarımı gelişmeye olasılığı varsa, kayıt ve birleşim türlerinin temsillerini gizleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="fe470-275">Nesnelerin somut gösterimlerini göstermeden kaçının.</span><span class="sxs-lookup"><span data-stu-id="fe470-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="fe470-276">Örneğin, değerlerin somut gösterimi <xref:System.DateTime> .NET kitaplığı tasarımının dış, ortak API 'si tarafından görünmez.</span><span class="sxs-lookup"><span data-stu-id="fe470-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="fe470-277">Çalışma zamanında, ortak dil çalışma zamanı yürütme sırasında kullanılacak kaydedilmiş uygulamayı bilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="fe470-278">Ancak, derlenmiş kod kendisi somut gösterimdeki bağımlılıkları almaz.</span><span class="sxs-lookup"><span data-stu-id="fe470-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="fe470-279">Genişletilebilirlik için uygulama devralmanın kullanılmasını önleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="fe470-280">F # ' da, uygulama devralma nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe470-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="fe470-281">Ayrıca, devralma hiyerarşileri genellikle karmaşık ve yeni gereksinimler geldiğinde değişme zor olur.</span><span class="sxs-lookup"><span data-stu-id="fe470-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="fe470-282">Devralma işlemi, uyumluluk için F # içinde ve soruna en iyi çözüm olduğu nadir durumlar için de mevcuttur, ancak arabirim uygulama gibi çok biçimlilik için tasarlanırken alternatif teknikler, F # programlarınızda elde edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="fe470-283">İşlev ve üye imzaları</span><span class="sxs-lookup"><span data-stu-id="fe470-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="fe470-284">Çok sayıda ilişkisiz değer döndürürken dönüş değerleri için tanımlama grupları kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="fe470-285">Aşağıda, bir dönüş türünde tanımlama grubu kullanmanın iyi bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fe470-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="fe470-286">Birçok bileşeni içeren dönüş türleri veya bileşenlerin tek bir tanınabilir varlıkla ilişkili olduğu durumlarda, tanımlama grubu yerine adlandırılmış bir tür kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="fe470-287">`Async<T>`F # API sınırlarında zaman uyumsuz programlama için kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="fe470-288">' I döndüren karşılık gelen bir zaman uyumlu işlem varsa `Operation` `T` , zaman uyumsuz işlem, döndürürse veya döndürürse adlandırılmış olmalıdır `AsyncOperation` `Async<T>` `OperationAsync` `Task<T>` .</span><span class="sxs-lookup"><span data-stu-id="fe470-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="fe470-289">Başlangıç/bitiş yöntemlerini ortaya çıkaran yaygın olarak kullanılan .NET türleri için, `Async.FromBeginEnd` F # Async programlama modelini bu .NET API 'lerine sağlamak üzere bir façlade olarak uzantı yöntemleri yazmak için kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="fe470-290">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="fe470-290">Exceptions</span></span>

<span data-ttu-id="fe470-291">Özel durumların, sonuçların ve seçeneklerin uygun kullanımı hakkında bilgi edinmek için bkz. [hata yönetimi](conventions.md#error-management) .</span><span class="sxs-lookup"><span data-stu-id="fe470-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="fe470-292">Uzantı üyeleri</span><span class="sxs-lookup"><span data-stu-id="fe470-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="fe470-293">F #-to-F # bileşenlerinde F # uzantı üyelerini dikkatle uygulama</span><span class="sxs-lookup"><span data-stu-id="fe470-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="fe470-294">F # uzantısı üyeleri genellikle yalnızca kullanım modlarının çoğunluğunda bulunan bir türle ilişkili iç işlemleri kapanışdaki işlemler için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="fe470-295">Yaygın olarak kullanılan bir kullanım, çeşitli .NET türleri için F # ile daha fazla deyim içeren API 'Ler sağlamaktır:</span><span class="sxs-lookup"><span data-stu-id="fe470-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="fe470-296">Birleşim türleri</span><span class="sxs-lookup"><span data-stu-id="fe470-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="fe470-297">Ağaç yapılandırılmış veriler için sınıf hiyerarşileri yerine ayrılmış birleşimler kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="fe470-298">Ağaç benzeri yapılar yinelemeli olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="fe470-299">Bu, devralmayla birlikte, ayırt edici birleşimler ile zarif.</span><span class="sxs-lookup"><span data-stu-id="fe470-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="fe470-300">Ayrılmış birleşimlerle ağaç benzeri verilerin temsil edilmesi, aynı zamanda, model eşleştirme sırasında tüketme özelliğinden faydalanabilmeniz de sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe470-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="fe470-301">`[<RequireQualifiedAccess>]`Büyük/küçük harf adları yeterince benzersiz olmayan birleşim türlerinde kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="fe470-302">Kendinizi, ayırt edici birleşim durumları gibi farklı şeyler için aynı adın en iyi adı olduğu bir etki alanında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="fe470-303">`[<RequireQualifiedAccess>]`Deyimlerin sıralamasına bağlı olarak gölgeleme nedeniyle karışık hataları tetiklememeniz için büyük/küçük harf adlarını ayırt etmek için kullanabilirsiniz `open`</span><span class="sxs-lookup"><span data-stu-id="fe470-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="fe470-304">Bu türlerin tasarımı gelişmeye olasılığı varsa, ikili uyumlu API 'Ler için ayrılmış birleşimlerin sunumlarını gizleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="fe470-305">Birleşimler türleri bir kısa programlama modeli için F # örüntü eşleşen formları kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="fe470-306">Daha önce bahsedildiği gibi, bu türlerin tasarımı gelişdiğinde somut veri gösterimlerini önlemeyi kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="fe470-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="fe470-307">Örneğin, ayrılmış bir birleşimin temsili özel veya iç bildirim kullanılarak veya bir imza dosyası kullanılarak gizlenebilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="fe470-308">Ayrılmış birleşimler sayısının fark gözetmeden ortaya çıkardıysanız, kitaplığınızı Kullanıcı kodunu bozmadan sürüm olarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="fe470-309">Bunun yerine, bir veya daha fazla etkin deseni, bu türden değerler üzerinde desen eşleştirmeye izin vermek için kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="fe470-310">Etkin desenler, f # tüketicilerini doğrudan gösterme sırasında desen eşleştirme ile F # tüketicilerinin sağlanması için alternatif bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe470-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="fe470-311">Satır içi Işlevler ve üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="fe470-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="fe470-312">Örtülü üye kısıtlamaları ve statik olarak çözümlenen genel türler içeren satır içi işlevleri kullanarak genel sayısal algoritmaları tanımlayın</span><span class="sxs-lookup"><span data-stu-id="fe470-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="fe470-313">Aritmetik üye kısıtlamaları ve F # karşılaştırma kısıtlamaları F # programlama için standarttır.</span><span class="sxs-lookup"><span data-stu-id="fe470-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="fe470-314">Örneğin, aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fe470-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="fe470-315">Bu işlevin türü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fe470-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="fe470-316">Bu, bir matematik kitaplığındaki ortak API için uygun bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="fe470-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="fe470-317">Tür sınıflarının benzetimini yapmak için üye kısıtlamalarını kullanmaktan kaçının ve Duck yazma</span><span class="sxs-lookup"><span data-stu-id="fe470-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="fe470-318">F # üye kısıtlamaları kullanılarak "Duck yazma" benzetimi yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="fe470-319">Ancak, bunu kullanan Üyeler F #-to-F # kitaplığı tasarımlarında genel olarak kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="fe470-320">Bunun nedeni, bilmediğiniz veya standart olmayan örtük kısıtlamaları temel alan kitaplık tasarımlarının, Kullanıcı kodu ile belirli bir çerçeve düzenine bağlı olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="fe470-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="fe470-321">Ayrıca, üye kısıtlamalarının bu şekilde büyük bir şekilde kullanılması çok uzun derleme sürelerine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="fe470-322">İşleç tanımları</span><span class="sxs-lookup"><span data-stu-id="fe470-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="fe470-323">Özel sembolik işleçler tanımlamayı önleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="fe470-324">Özel işleçler bazı durumlarda gereklidir ve büyük bir uygulama kodu gövdesinde çok yararlı notational cihazlarıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="fe470-325">Bir kitaplığın yeni kullanıcıları için, adlandırılmış işlevlerin kullanımı genellikle daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="fe470-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="fe470-326">Buna ek olarak, özel sembolik operatörler belge açısından zor olabilir ve kullanıcılar, IDE ve arama altyapılarındaki mevcut sınırlamalar nedeniyle, operatörlerle ilgili yardım aramak daha zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="fe470-327">Sonuç olarak, işlevlerinizi adlandırılmış işlevler ve Üyeler olarak yayımlamak en iyisidir ve ayrıca, notational avantajları bu işlevselliğe sahip olan belge ve bilişsel maliyetlerini açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="fe470-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="fe470-328">Ölçü Birimleri</span><span class="sxs-lookup"><span data-stu-id="fe470-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="fe470-329">F # kodunda eklenen tür güvenliği için ölçü birimlerini dikkatle kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="fe470-330">Ölçü birimleri için ek yazma bilgileri, diğer .NET dilleri tarafından görüntülendiklerinde silinir.</span><span class="sxs-lookup"><span data-stu-id="fe470-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="fe470-331">.NET bileşenlerinin, araçların ve yansımanın türler-sans-units olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fe470-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="fe470-332">Örneğin, C# tüketicileri yerine burada görünür `float` `float<kg>` .</span><span class="sxs-lookup"><span data-stu-id="fe470-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="fe470-333">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="fe470-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="fe470-334">F # kodunu basitleştirmek için tür kısaltmalarını dikkatle kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="fe470-335">.NET bileşenleri, araçları ve Reflection türler için kısaltılmış adları görmez.</span><span class="sxs-lookup"><span data-stu-id="fe470-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="fe470-336">Tür kısaltmalarının önemli kullanımları, bir etki alanının gerçekten olduğu kadar karmaşık görünmesini sağlayabilir ve bu da tüketicileri karıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="fe470-337">Üyeleri ve özellikleri, kısaltılmakta olan türden bulunanlarla farklı doğası gereği olması gereken genel türlerin tür kısaltmalarını önleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="fe470-338">Bu durumda, kısaltılmakta olan tür, tanımlanmakta olan gerçek türün temsili hakkında çok fazla görünür.</span><span class="sxs-lookup"><span data-stu-id="fe470-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="fe470-339">Bunun yerine, kısaltmayı bir sınıf türü veya tek büyük harf ayrılmış bir Union içinde sarmalayın (ya da performans önemli olduğunda, kısaltmayı kaydırmak için bir struct türü kullanmayı düşünün).</span><span class="sxs-lookup"><span data-stu-id="fe470-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="fe470-340">Örneğin, bir F # eşlemesinin özel durumu olarak çok eşleme tanımlamak, örneğin:</span><span class="sxs-lookup"><span data-stu-id="fe470-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="fe470-341">Ancak, bu tür üzerindeki mantıksal nokta gösterimi işlemleri bir haritadaki işlemlerle aynı değildir. Örneğin, arama işlecinin eşleşmesi mantıklı değildir. [key] anahtar sözlükte değilse, bir özel durumu yükseltmek yerine boş listeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe470-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="fe470-342">Diğer .NET dillerinden kullanım için kitaplıklara yönelik yönergeler</span><span class="sxs-lookup"><span data-stu-id="fe470-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="fe470-343">Kitaplıkları diğer .NET dillerinden kullanılmak üzere tasarlarken, [.NET kitaplığı tasarım yönergelerine](../../standard/design-guidelines/index.md)uymamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="fe470-344">Bu belgede, kısıtlama olmadan F # yapılarını kullanan F # temelli kitaplıkların aksine, bu kitaplıklar Vanilla .NET kitaplıkları olarak etiketlenir.</span><span class="sxs-lookup"><span data-stu-id="fe470-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="fe470-345">Vanilla .NET kitaplıklarını tasarlamak, genel API 'de F # özel yapıların kullanımını en aza indirerek, .NET Framework geri kalanı ile tutarlı tanıdık ve idmatik API 'Lerin sağlanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fe470-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="fe470-346">Kurallar aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fe470-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="fe470-347">Ad alanı ve tür tasarımı (diğer .NET dillerinden kullanılacak kitaplıklar için)</span><span class="sxs-lookup"><span data-stu-id="fe470-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="fe470-348">Bileşenlerinizin genel API 'sine .NET adlandırma kuralları uygulayın</span><span class="sxs-lookup"><span data-stu-id="fe470-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="fe470-349">Kısaltılmış adların kullanımı ve .NET büyük/küçük harf yönergeleri için özel dikkat ödeyin.</span><span class="sxs-lookup"><span data-stu-id="fe470-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="fe470-350">Bileşenleriniz için birincil kuruluş yapısı olarak ad alanları, türler ve Üyeler kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="fe470-351">Ortak işlevselliği içeren tüm dosyalar bir `namespace` bildirimle başlamalıdır ve ad alanlarındaki genel kullanıma yönelik varlıkların türleri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="fe470-352">F # modülleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="fe470-352">Do not use F# modules.</span></span>

<span data-ttu-id="fe470-353">Uygulama kodu, yardımcı program türleri ve yardımcı program işlevlerini barındırmak için ortak olmayan modüller kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe470-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="fe470-354">Statik türler, API 'nin gelecekteki gelişiminde ve F # modülleri içinde kullanılamayan diğer .NET API tasarımı kavramlarını kullanmasına izin verdiklerinden, modüller üzerinden tercih edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="fe470-355">Örneğin, aşağıdaki ortak API 'nin yerine:</span><span class="sxs-lookup"><span data-stu-id="fe470-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="fe470-356">Bunun yerine göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fe470-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="fe470-357">Türlerin tasarımı geliştirimayacaksa, Vanilla .NET API 'Lerinde F # kayıt türlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="fe470-358">F # kayıt türleri basit bir .NET sınıfına derlenir.</span><span class="sxs-lookup"><span data-stu-id="fe470-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="fe470-359">Bunlar, API 'lerde bazı basit ve kararlı türler için uygundur.</span><span class="sxs-lookup"><span data-stu-id="fe470-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="fe470-360">`[<NoEquality>]` `[<NoComparison>]` Arabirimlerin otomatik olarak oluşturulmasını engellemek için ve özniteliklerini kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="fe470-361">Ayrıca, Vanilla .NET API 'Lerinde kesilebilir kayıt alanlarını kullanmaktan kaçının, bunlar ortak bir alanı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="fe470-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="fe470-362">Her zaman bir sınıfın, API 'nin gelecekteki gelişiminde daha esnek bir seçenek sağlayıp sağlamamadığını düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="fe470-363">Örneğin, aşağıdaki F # kodu bir C# tüketicisi için ortak API 'yi kullanıma sunar:</span><span class="sxs-lookup"><span data-stu-id="fe470-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="fe470-364">F#:</span><span class="sxs-lookup"><span data-stu-id="fe470-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="fe470-365">C#:</span><span class="sxs-lookup"><span data-stu-id="fe470-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="fe470-366">Vanilla .NET API 'Lerinde F # birleşim türlerinin gösterimini gizleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="fe470-367">F # birleşim türleri, F #-F # kodlaması için bile bileşen sınırları boyunca yaygın olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="fe470-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="fe470-368">Bunlar, dahili olarak bileşenler ve kitaplıklar içinde kullanıldığında harika bir uygulama cihazlarıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="fe470-369">Bir Vanilla .NET API 'SI tasarlarken, bir özel bildirim veya imza dosyası kullanarak bir birleşim türü gösterimini gizlemeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="fe470-370">Ayrıca, istenen bir birleşim temsili olan türleri, Üyeler ile dahili olarak kullanarak da genişletebilirsiniz. NET 'e yönelik API.</span><span class="sxs-lookup"><span data-stu-id="fe470-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="fe470-371">Framework 'ün tasarım düzenlerini kullanarak GUI ve diğer bileşenleri tasarlama</span><span class="sxs-lookup"><span data-stu-id="fe470-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="fe470-372">.NET içinde WinForms, WPF ve ASP.NET gibi birçok farklı çerçeve mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="fe470-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="fe470-373">Her birinin adlandırma ve tasarım kuralları, bu çerçevelerde kullanılmak üzere bileşen tasarlıyorsanız kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fe470-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="fe470-374">Örneğin, WPF programlama için, tasarlamakta olduğunuz sınıflar için WPF tasarım düzenlerini benimseyin.</span><span class="sxs-lookup"><span data-stu-id="fe470-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="fe470-375">Kullanıcı arabirimi programlamadaki modeller için, içinde bulunan olaylar ve bildirim tabanlı Koleksiyonlar gibi tasarım düzenlerini kullanın <xref:System.Collections.ObjectModel> .</span><span class="sxs-lookup"><span data-stu-id="fe470-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="fe470-376">Nesne ve üye tasarımı (diğer .NET dillerinden kullanılacak kitaplıklar için)</span><span class="sxs-lookup"><span data-stu-id="fe470-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="fe470-377">.NET olaylarını göstermek için CLIEvent özniteliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="fe470-378">Bir `DelegateEvent` nesnesi alan ve `EventArgs` (yalnızca türü varsayılan olarak kullanan) belirli bir .NET temsilci türüyle oluşturun `Event` , `FSharpHandler` böylece olaylar diğer .NET dillerine tanıdık bir şekilde yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="fe470-379">Zaman uyumsuz işlemleri .NET görevleri döndüren yöntemler olarak kullanıma sunma</span><span class="sxs-lookup"><span data-stu-id="fe470-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="fe470-380">Görevler, .NET 'te etkin zaman uyumsuz hesaplamaları göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe470-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="fe470-381">Görevler `Async<T>` , "zaten yürütülmekte olan" görevleri temsil ettiğinden ve paralel bileşim yapan ya da iptal sinyallerinin ve diğer bağlamsal parametrelerin yayılmasını gizleyemediğinden, F # nesnelerinden genel olarak daha az bileşimdir.</span><span class="sxs-lookup"><span data-stu-id="fe470-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="fe470-382">Ancak, bu şekilde, görevleri döndüren yöntemler .NET üzerinde zaman uyumsuz programlama için standart gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="fe470-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="fe470-383">Ayrıca, açık bir iptal belirtecini de kabul etmek isteyeceksiniz:</span><span class="sxs-lookup"><span data-stu-id="fe470-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="fe470-384">F # işlev türleri yerine .NET temsilci türlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="fe470-385">Burada "F # işlev türleri", gibi "ok" türler anlamına gelir `int -> int` .</span><span class="sxs-lookup"><span data-stu-id="fe470-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="fe470-386">Bunun yerine:</span><span class="sxs-lookup"><span data-stu-id="fe470-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="fe470-387">Bunu yapın:</span><span class="sxs-lookup"><span data-stu-id="fe470-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="fe470-388">F # işlev türü `class FSharpFunc<T,U>` diğer .NET dilleri gibi görünür ve temsilci türlerini anlayan dil özellikleri ve araçlar için daha az uygundur.</span><span class="sxs-lookup"><span data-stu-id="fe470-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="fe470-389">.NET Framework 3,5 veya üzeri bir şekilde hedef alan daha yüksek sıralı bir yöntem yazarken, `System.Func` ve `System.Action` temsilcileri, .NET geliştiricilerinin bu API 'leri düşük bir şekilde kullanmasını sağlamak için yayımlanacak doğru API 'lardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="fe470-390">(.NET Framework 2,0 ' i hedeflerken, sistem tarafından tanımlanan temsilci türleri daha sınırlıdır; gibi önceden tanımlanmış temsilci türlerini kullanmayı düşünün `System.Converter<T,U>` veya belirli bir temsilci türü tanımlar.)</span><span class="sxs-lookup"><span data-stu-id="fe470-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="fe470-391">Ters çevir tarafında, F # ile bağlantılı kitaplıklar için .NET temsilcileri doğal değildir (F # ile bağlantılı kitaplıkların sonraki bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="fe470-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="fe470-392">Sonuç olarak, Vanilla .NET kitaplıkları için daha yüksek sıralı Yöntemler geliştirilirken yaygın bir uygulama stratejisi, F # işlev türlerini kullanarak tüm uygulamayı yazar ve ardından temsilcileri kullanarak ortak API 'yi bir ince façlade üzerine gerçek F # uygulamasını olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe470-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="fe470-393">F # seçenek değerlerini döndürmek yerine TryGetValue modelini kullanın ve F # seçenek değerlerini bağımsız değişken olarak almak için yöntem aşırı yüklemesini tercih edin</span><span class="sxs-lookup"><span data-stu-id="fe470-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="fe470-394">API 'lerde F # seçenek türü için kullanılan yaygın kullanım desenleri, standart .NET tasarım teknikleri kullanılarak Vanilla .NET API 'Lerinde daha iyi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="fe470-395">Bir F # seçenek değeri döndürmek yerine, bool dönüş türünü ve "TryGetValue" düzeninde olduğu gibi bir out parametresini kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="fe470-396">F # seçenek değerlerini parametre olarak almak yerine, yöntem aşırı yüklemesini veya isteğe bağlı bağımsız değişkenleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="fe470-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="fe470-397">.NET koleksiyon arabirim türleri IEnumerable \< T \> ve IDictionary \< anahtarı, \> Parametreler ve dönüş değerleri için değer kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="fe470-398">.NET dizileri, F # türleri ve gibi somut koleksiyon türlerinin kullanılmasını önleyin `T[]` ve gibi `list<T>` `Map<Key,Value>` `Set<T>` .net somut koleksiyon türleri `Dictionary<Key,Value>` .</span><span class="sxs-lookup"><span data-stu-id="fe470-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="fe470-399">.NET kitaplığı tasarım yönergeleri, gibi çeşitli koleksiyon türlerinin ne zaman kullanılacağı konusunda iyi öneriler sağlar `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="fe470-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="fe470-400">Bazı durumlarda dizilerin () bazı kullanımı, performans miktarı ' nda `T[]` bazı koşullarda kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="fe470-401">Özellikle `seq<T>` için yalnızca F # diğer adı olduğunu unutmayın `IEnumerable<T>` ve bu nedenle, bir Vanilla .NET API 'si için sıra, genellikle uygun bir türdür.</span><span class="sxs-lookup"><span data-stu-id="fe470-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="fe470-402">F # listeleri yerine:</span><span class="sxs-lookup"><span data-stu-id="fe470-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="fe470-403">F # dizilerini kullan:</span><span class="sxs-lookup"><span data-stu-id="fe470-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="fe470-404">Sıfır değişkenli bir yöntemi tanımlamak için bir metodun tek giriş türü olarak veya void döndüren bir yöntemi tanımlamak için tek dönüş türü olarak birim türünü kullanın</span><span class="sxs-lookup"><span data-stu-id="fe470-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="fe470-405">Birim türünün diğer kullanımkullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="fe470-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="fe470-406">Bunlar iyidir:</span><span class="sxs-lookup"><span data-stu-id="fe470-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="fe470-407">Bu hatalı:</span><span class="sxs-lookup"><span data-stu-id="fe470-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="fe470-408">Vanilla .NET API sınırları üzerinde null değerleri denetle</span><span class="sxs-lookup"><span data-stu-id="fe470-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="fe470-409">F # uygulama kodu, sabit tasarım desenleri ve F # türleri için null sabit değerler kullanımıyla ilgili kısıtlamalar nedeniyle daha az null değere sahip olacak şekilde eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="fe470-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="fe470-410">Diğer .NET dilleri genellikle null değeri çok daha sık kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe470-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="fe470-411">Bu nedenle, bir Vanilla .NET API 'sini kullanıma sunan F # kodu, API sınırında null için parametreleri denetlemelidir ve bu değerlerin F # uygulama koduna daha derin akmasını önler.</span><span class="sxs-lookup"><span data-stu-id="fe470-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="fe470-412">`isNull`Düzende eşleşen işlev veya desenler `null` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe470-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="fe470-413">Bir dönüş değeri olarak tanımlama gruplarını kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="fe470-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="fe470-414">Bunun yerine, Birleşik verileri tutan adlandırılmış bir tür döndürmeyi veya birden çok değer döndürmek için out parametrelerini kullanmayı tercih edin.</span><span class="sxs-lookup"><span data-stu-id="fe470-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="fe470-415">Tanımlama grupları ve yapı tanımlama grupları .NET 'te bulunmasına rağmen (struct tanımlama grupları için C# dil desteği dahil), en sık, .NET geliştiricileri için ideal ve beklenen API 'YI sağlamayacak.</span><span class="sxs-lookup"><span data-stu-id="fe470-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="fe470-416">Parametrelerin currying kullanımını önleyin</span><span class="sxs-lookup"><span data-stu-id="fe470-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="fe470-417">Bunun yerine, .NET çağırma kurallarını kullanın `Method(arg1,arg2,…,argN)` .</span><span class="sxs-lookup"><span data-stu-id="fe470-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="fe470-418">İpucu: kitaplıkları herhangi bir .NET dilinden kullanılmak üzere tasarlıyorsanız, kitaplıklarınızın bu dillerden "doğru" olduğundan emin olmak için bazı deneysel C# ve Visual Basic programlamasına yönelik bir yedek yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe470-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="fe470-419">Ayrıca, kitaplıkların ve belgelerinin geliştiriciler tarafından beklendiği gibi göründüğünden emin olmak için .NET yansıtıcısı ve Visual Studio Nesne Tarayıcısı gibi araçları da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe470-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="fe470-420">Ek</span><span class="sxs-lookup"><span data-stu-id="fe470-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="fe470-421">Diğer .NET dilleri tarafından kullanılmak üzere F # kodu tasarlamaya yönelik uçtan uca örnek</span><span class="sxs-lookup"><span data-stu-id="fe470-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="fe470-422">Aşağıdaki sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fe470-422">Consider the following class:</span></span>

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

<span data-ttu-id="fe470-423">Bu sınıfın çıkarılan F # türü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fe470-423">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="fe470-424">Bu F # türünün başka bir .NET dilini kullanarak bir programcıya nasıl göründüğüne göz atalım.</span><span class="sxs-lookup"><span data-stu-id="fe470-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="fe470-425">Örneğin, yaklaşık C# "imza" şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fe470-425">For example, the approximate C# "signature" is as follows:</span></span>

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

<span data-ttu-id="fe470-426">Burada F # yapıları nasıl temsil ettiğini fark eden bazı önemli noktaları vardır.</span><span class="sxs-lookup"><span data-stu-id="fe470-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="fe470-427">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fe470-427">For example:</span></span>

* <span data-ttu-id="fe470-428">Bağımsız değişken adları gibi meta veriler korunur.</span><span class="sxs-lookup"><span data-stu-id="fe470-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="fe470-429">İki bağımsız değişken alan F # yöntemleri iki bağımsız değişken içeren C# yöntemi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="fe470-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="fe470-430">İşlevler ve listeler, F # kitaplığındaki ilgili türlere başvuru haline gelir.</span><span class="sxs-lookup"><span data-stu-id="fe470-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="fe470-431">Aşağıdaki kod, bu kodun bu işlemleri hesaba çekmek için nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe470-431">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="fe470-432">Kodun çıkarılan F # türü aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fe470-432">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="fe470-433">C# imzası artık şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="fe470-433">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="fe470-434">Bu tür bir Vanilla .NET kitaplığının parçası olarak kullanılmak üzere hazırlanmaya yapılan düzeltmeler aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="fe470-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="fe470-435">Birkaç ad düzeltildi: `Point1` , `n` , `l` , ve `f` sırasıyla,, `RadialPoint` `count` `factor` , ve `transform` .</span><span class="sxs-lookup"><span data-stu-id="fe470-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="fe470-436">Kullanarak bir `seq<RadialPoint>` `RadialPoint list` liste oluşturmayı kullanarak bir sıra oluşturma için kullanarak bir liste oluşturma yerine bir dönüş türü kullandınız `[ ... ]` `IEnumerable<RadialPoint>` .</span><span class="sxs-lookup"><span data-stu-id="fe470-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="fe470-437">`System.Func`F # işlev türü yerine .NET temsilci türü kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="fe470-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="fe470-438">Bu, C# kodunda tüketilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe470-438">This makes it far nicer to consume in C# code.</span></span>
