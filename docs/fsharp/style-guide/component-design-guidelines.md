---
title: F#Bileşen tasarım yönergeleri
description: Yazmak için kılavuzları edinin F# diğer çağıranlar tarafından tüketim için hazırlanmış bileşenleri.
ms.date: 05/14/2018
ms.openlocfilehash: c61e4cd9098388b356c71c325d66c760fa866cf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902167"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="97fcf-103">F#Bileşen tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-103">F# component design guidelines</span></span>

<span data-ttu-id="97fcf-104">Bu belge için bileşen tasarım yönergeleri kümesidir F# temel programlama, F# bileşen tasarım yönergeleri, v14, Microsoft Research ve [başka bir sürümü](https://fsharp.org/specs/component-design-guidelines/) başlangıçta seçkin ve destekleyen F# Yazılım Foundation.</span><span class="sxs-lookup"><span data-stu-id="97fcf-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="97fcf-105">Bu belge hakkında bilgi sahibi olduğunuz varsayılır F# programlama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="97fcf-106">Çoğu performanstan F# topluluk Katkıları ve bu kılavuz çeşitli sürümlerinde yararlı geri bildirim.</span><span class="sxs-lookup"><span data-stu-id="97fcf-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="97fcf-107">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="97fcf-107">Overview</span></span>

<span data-ttu-id="97fcf-108">Bu belge ilgili sorunlardan bazılarını bakar F# bileşen tasarım ve kodlama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="97fcf-109">Bir bileşen, aşağıdakilerden herhangi birini gelebilir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="97fcf-110">Bir katmana, F# dış tüketicileri bir proje olan proje.</span><span class="sxs-lookup"><span data-stu-id="97fcf-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="97fcf-111">Tüketimi yönelik bir kitaplık F# bütünleştirilmiş kod sınırları arasında kod.</span><span class="sxs-lookup"><span data-stu-id="97fcf-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="97fcf-112">Bütünleştirilmiş kod sınırları arasında herhangi bir .NET dil tarafından tüketim için hazırlanmış bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="97fcf-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="97fcf-113">Gibi bir paket deposu aracılığıyla dağıtım için hedeflenen bir kitaplık [NuGet](https://nuget.org).</span><span class="sxs-lookup"><span data-stu-id="97fcf-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="97fcf-114">Bu makalede açıklanan teknikleri izleyin [beş iyi prensipleri F# kod](index.md#five-principles-of-good-f-code), böylece her ikisi de işlevsel yazılımınız ve uygun şekilde programlama nesnesi.</span><span class="sxs-lookup"><span data-stu-id="97fcf-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="97fcf-115">Metodoloji bağımsız olarak, geliştiriciler tarafından kullanılabilen en kolay bir API'si çalışıyorlardı çalışırken bir dizi pratik ve prosaic soruna bileşen ve kitaplık Tasarımcı yüzler.</span><span class="sxs-lookup"><span data-stu-id="97fcf-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="97fcf-116">Sertifikasyonuna uygulamasının [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md) kullanmak eğlenceli API'lerden tutarlı özellik kümesi oluşturma doğrultusunda faaliyetidir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="97fcf-117">Genel yönergeler</span><span class="sxs-lookup"><span data-stu-id="97fcf-117">General guidelines</span></span>

<span data-ttu-id="97fcf-118">Geçerli birkaç Evrensel yönergeleri vardır F# kitaplıkları, kitaplığı için hedef kitle ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="97fcf-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="97fcf-119">.NET kitaplığı tasarım yönergeleri edinin</span><span class="sxs-lookup"><span data-stu-id="97fcf-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="97fcf-120">Türü ne olursa olsun, F# kodlama bilgisine sahip değerlidir, yapmakta olduğunuz [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="97fcf-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="97fcf-121">Çoğu diğer F# ve .NET programcıları bu yönergelere hakkında bilgi sahibi olmanız ve .NET kodu için uygun olması için bekler.</span><span class="sxs-lookup"><span data-stu-id="97fcf-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="97fcf-122">.NET kitaplığı tasarım yönergeleri adlandırma, sınıflar ve arabirimler, üye tasarım (Özellikler, yöntemler, olaylar, vb.) ve daha fazlasını tasarımı ile ilgili genel rehberlik sağlar ve tasarım kılavuzu çeşitli başvuru yararlı ilk noktası olan.</span><span class="sxs-lookup"><span data-stu-id="97fcf-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="97fcf-123">XML belge açıklamaları için kodunuzu ekleyin</span><span class="sxs-lookup"><span data-stu-id="97fcf-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="97fcf-124">XML belgeleri ortak API'lerde emin olmak için kitaplık dosyaları bu türleri ve üyeleri ve etkinleştirme yapı belgeleri kullanarak kullanıcıların harika IntelliSense ve Hızlıbilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fcf-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="97fcf-125">Bkz: [XML belgeleri](../language-reference/xml-documentation.md) xmldoc Açıklamalar içinde ek biçimlendirme için kullanılabilen çeşitli xml etiketleri hakkında.</span><span class="sxs-lookup"><span data-stu-id="97fcf-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="97fcf-126">Kısa form XML açıklamaları kullanabilirsiniz (`/// comment`), veya standart XML açıklamaları (`///<summary>comment</summary>`).</span><span class="sxs-lookup"><span data-stu-id="97fcf-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="97fcf-127">Kararlı kitaplığı ve bileşen API'leri için açık imza dosyalarını (.fsi) kullanmayı düşünün</span><span class="sxs-lookup"><span data-stu-id="97fcf-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="97fcf-128">Açık imzaları dosyalarını kullanan bir F# Kitaplığı hem tam genel kitaplığınızın, de yüzey gibi ortak belgeler arasında NET bir ayrım sağlar ve iç bildiğinizden emin olun yardımcı olan genel API birleştiren bir özetini sunar Uygulama Ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="97fcf-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="97fcf-129">Genel API değiştirmek için hem uygulama hem de imza dosyalarında yapılacak değişiklikler gerektirerek imza dosyalarını uyuşmazlıkları eklediğiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="97fcf-130">Bir API solidified haline gelir ve bundan böyle önemli bir değişiklik beklenen sonuç olarak, imza dosyalarını genellikle yalnızca tanıtılmak.</span><span class="sxs-lookup"><span data-stu-id="97fcf-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="97fcf-131">Her zaman .NET dizeleri kullanmak için en iyi uygulamaları izleyin</span><span class="sxs-lookup"><span data-stu-id="97fcf-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="97fcf-132">İzleyin [kullanarak dizeleri de .NET için en iyi](../../standard/base-types/best-practices-strings.md) Kılavuzu.</span><span class="sxs-lookup"><span data-stu-id="97fcf-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="97fcf-133">Özellikle, her zaman açık durum *kültürel hedefi* dönüştürme ve karşılaştırma dizeleri, (uygunsa).</span><span class="sxs-lookup"><span data-stu-id="97fcf-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="97fcf-134">Yönergeler için F#-karşılıklı kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="97fcf-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="97fcf-135">Bu bölümde genel geliştirmeye yönelik öneriler sunan F#-karşılıklı kitaplıkları; diğer bir deyişle, genel API tarafından tüketilmesi amaçlanan gösterme kitaplıkları F# geliştiriciler.</span><span class="sxs-lookup"><span data-stu-id="97fcf-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="97fcf-136">Kitaplık tasarım önerileri çeşitli özellikle ilgili F#.</span><span class="sxs-lookup"><span data-stu-id="97fcf-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="97fcf-137">Aşağıdaki öneriler olmaması durumunda .NET kitaplığı tasarım geri dönüş Kılavuzu yönergelerdir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="97fcf-138">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="97fcf-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="97fcf-139">.NET adlandırma ve büyük/küçük harf kuralları kullanma</span><span class="sxs-lookup"><span data-stu-id="97fcf-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="97fcf-140">Aşağıdaki tablo, .NET adlandırma ve büyük/küçük harf kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="97fcf-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="97fcf-141">Ayrıca içerecek şekilde küçük eklemeler yapılmıştır F# oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="97fcf-142">Oluştur</span><span class="sxs-lookup"><span data-stu-id="97fcf-142">Construct</span></span> | <span data-ttu-id="97fcf-143">Servis talebi</span><span class="sxs-lookup"><span data-stu-id="97fcf-143">Case</span></span> | <span data-ttu-id="97fcf-144">Bölümü</span><span class="sxs-lookup"><span data-stu-id="97fcf-144">Part</span></span> | <span data-ttu-id="97fcf-145">Örnekler</span><span class="sxs-lookup"><span data-stu-id="97fcf-145">Examples</span></span> | <span data-ttu-id="97fcf-146">Notlar</span><span class="sxs-lookup"><span data-stu-id="97fcf-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="97fcf-147">Somut türleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-147">Concrete types</span></span> | <span data-ttu-id="97fcf-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-148">PascalCase</span></span> | <span data-ttu-id="97fcf-149">İsim / sıfat</span><span class="sxs-lookup"><span data-stu-id="97fcf-149">Noun/ adjective</span></span> | <span data-ttu-id="97fcf-150">Liste, çift, karmaşık</span><span class="sxs-lookup"><span data-stu-id="97fcf-150">List, Double, Complex</span></span> | <span data-ttu-id="97fcf-151">Yapılar, sınıflar, numaralandırmalar, temsilciler, kayıtlar ve birleşimler bunun somut türleridir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="97fcf-152">Tür adları içinde OCaml, geleneksel olarak küçük olsa F# türleri için .NET adlandırma şeması BENİMSEDİ.</span><span class="sxs-lookup"><span data-stu-id="97fcf-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="97fcf-153">DLL'ler</span><span class="sxs-lookup"><span data-stu-id="97fcf-153">DLLs</span></span>           | <span data-ttu-id="97fcf-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-154">PascalCase</span></span> |                 | <span data-ttu-id="97fcf-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="97fcf-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="97fcf-156">Birleşim etiketleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-156">Union tags</span></span>     | <span data-ttu-id="97fcf-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-157">PascalCase</span></span> | <span data-ttu-id="97fcf-158">İsim</span><span class="sxs-lookup"><span data-stu-id="97fcf-158">Noun</span></span> | <span data-ttu-id="97fcf-159">Bazı, ekleme, başarılı</span><span class="sxs-lookup"><span data-stu-id="97fcf-159">Some, Add, Success</span></span> | <span data-ttu-id="97fcf-160">Bir ön ek, genel API'ler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="97fcf-161">İsteğe bağlı olarak bir önek gibi iç olduğunda kullanın `type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="97fcf-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="97fcf-162">Olay</span><span class="sxs-lookup"><span data-stu-id="97fcf-162">Event</span></span>          | <span data-ttu-id="97fcf-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-163">PascalCase</span></span> | <span data-ttu-id="97fcf-164">Fiili</span><span class="sxs-lookup"><span data-stu-id="97fcf-164">Verb</span></span> | <span data-ttu-id="97fcf-165">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="97fcf-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="97fcf-166">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="97fcf-166">Exceptions</span></span>     | <span data-ttu-id="97fcf-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-167">PascalCase</span></span> |      | <span data-ttu-id="97fcf-168">WebException ise</span><span class="sxs-lookup"><span data-stu-id="97fcf-168">WebException</span></span> | <span data-ttu-id="97fcf-169">Adı "Özel durum" ile bitmelidir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-169">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="97fcf-170">Alan</span><span class="sxs-lookup"><span data-stu-id="97fcf-170">Field</span></span>          | <span data-ttu-id="97fcf-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-171">PascalCase</span></span> | <span data-ttu-id="97fcf-172">İsim</span><span class="sxs-lookup"><span data-stu-id="97fcf-172">Noun</span></span> | <span data-ttu-id="97fcf-173">Geçerli ad</span><span class="sxs-lookup"><span data-stu-id="97fcf-173">CurrentName</span></span>  | |
| <span data-ttu-id="97fcf-174">Arabirim türleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-174">Interface types</span></span> |  <span data-ttu-id="97fcf-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-175">PascalCase</span></span> | <span data-ttu-id="97fcf-176">İsim / sıfat</span><span class="sxs-lookup"><span data-stu-id="97fcf-176">Noun/ adjective</span></span> | <span data-ttu-id="97fcf-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="97fcf-177">IDisposable</span></span> | <span data-ttu-id="97fcf-178">Adı "I" ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-178">Name should start with “I”.</span></span> |
| <span data-ttu-id="97fcf-179">Yöntem</span><span class="sxs-lookup"><span data-stu-id="97fcf-179">Method</span></span> |  <span data-ttu-id="97fcf-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-180">PascalCase</span></span> |  <span data-ttu-id="97fcf-181">Fiili</span><span class="sxs-lookup"><span data-stu-id="97fcf-181">Verb</span></span> | <span data-ttu-id="97fcf-182">ToString</span><span class="sxs-lookup"><span data-stu-id="97fcf-182">ToString</span></span> | |
| <span data-ttu-id="97fcf-183">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="97fcf-183">Namespace</span></span> | <span data-ttu-id="97fcf-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-184">PascalCase</span></span> | | <span data-ttu-id="97fcf-185">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="97fcf-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="97fcf-186">Genellikle kullanması `<Organization>.<Technology>[.<Subnamespace>]`, kuruluş teknolojisi organizasyonu bağımsız ise, ancak bırakın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="97fcf-187">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97fcf-187">Parameters</span></span> | <span data-ttu-id="97fcf-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-188">camelCase</span></span> | <span data-ttu-id="97fcf-189">İsim</span><span class="sxs-lookup"><span data-stu-id="97fcf-189">Noun</span></span> |  <span data-ttu-id="97fcf-190">typeName, dönüştürme ve aralığı</span><span class="sxs-lookup"><span data-stu-id="97fcf-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="97fcf-191">izin değerleri (iç)</span><span class="sxs-lookup"><span data-stu-id="97fcf-191">let values (internal)</span></span> | <span data-ttu-id="97fcf-192">camelCase veya PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-192">camelCase or PascalCase</span></span> | <span data-ttu-id="97fcf-193">İsim / fiili</span><span class="sxs-lookup"><span data-stu-id="97fcf-193">Noun/ verb</span></span> |  <span data-ttu-id="97fcf-194">getValue, myTable</span><span class="sxs-lookup"><span data-stu-id="97fcf-194">getValue, myTable</span></span> |
| <span data-ttu-id="97fcf-195">izin değerleri (Dış)</span><span class="sxs-lookup"><span data-stu-id="97fcf-195">let values (external)</span></span> | <span data-ttu-id="97fcf-196">camelCase veya PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-196">camelCase or PascalCase</span></span> | <span data-ttu-id="97fcf-197">İsim/fiili</span><span class="sxs-lookup"><span data-stu-id="97fcf-197">Noun/verb</span></span>  | <span data-ttu-id="97fcf-198">List.map, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="97fcf-198">List.map, Dates.Today</span></span> | <span data-ttu-id="97fcf-199">let bağlı değerleri genellikle geleneksel işlevsel tasarım desenleri izlerken ortaktır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="97fcf-200">Ancak, diğer .NET dillerinden tanımlayıcısı kullanılabilir olduğunda genellikle PascalCase kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="97fcf-201">Özellik</span><span class="sxs-lookup"><span data-stu-id="97fcf-201">Property</span></span>  | <span data-ttu-id="97fcf-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="97fcf-202">PascalCase</span></span>  | <span data-ttu-id="97fcf-203">İsim / sıfat</span><span class="sxs-lookup"><span data-stu-id="97fcf-203">Noun/ adjective</span></span>  | <span data-ttu-id="97fcf-204">IsEndOfFile, arka plan rengi</span><span class="sxs-lookup"><span data-stu-id="97fcf-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="97fcf-205">Boole özellikleri genellikle olduğu ve olabilir ve olumlu değil IsNotEndOfFile IsEndOfFile olduğu gibi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="97fcf-206">Kısaltmalar kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-206">Avoid abbreviations</span></span>

<span data-ttu-id="97fcf-207">.NET Kılavuzu kısaltmalar kullanımını engelleyin (örneğin, "kullanmak `OnButtonClick` yerine `OnBtnClick`").</span><span class="sxs-lookup"><span data-stu-id="97fcf-207">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="97fcf-208">Ortak kısaltmalar gibi `Async` "Zaman uyumsuz için", izin verilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-208">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="97fcf-209">Bu kılavuz, işlevsel programlama bazen yoksayıldı; Örneğin, `List.iter` "yinelemek için" bir kısaltma kullanır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="97fcf-210">İçinde büyük ölçüde edileceği kısaltmalar kullanarak bu nedenle, eğilimlidir F#- için -F# programlama, ancak genel bileşen tasarım hala genellikle kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="97fcf-211">Ad çakışması büyük/küçük harfleri kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-211">Avoid casing name collisions</span></span>

<span data-ttu-id="97fcf-212">.NET Kılavuzu, tek başına büyük/küçük harfleri bazı istemci dillerini (örneğin, Visual Basic) büyük/küçük harfe duyarsızdır beri ad çakışmalarını belirsizliğini ortadan kaldırmak için kullanılamayacağını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="97fcf-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="97fcf-213">Uygun yerlerde kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="97fcf-214">Kısaltmalar gibi XML kısaltmalar değildir ve .NET kitaplıkları eden formunda (Xml), yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="97fcf-215">Yalnızca bilinen, tanınmış kısaltmalar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="97fcf-216">Genel parametre adları için PascalCase kullanın</span><span class="sxs-lookup"><span data-stu-id="97fcf-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="97fcf-217">Genel parametre adları dahil olmak üzere, ortak API'lerde PascalCase kullanma F#-kitaplıkları karşılıklı.</span><span class="sxs-lookup"><span data-stu-id="97fcf-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="97fcf-218">Özellikle, adları gibi kullanın `T`, `U`, `T1`, `T2` rastgele genel parametreler için ve belirli adları, ardından mantıklı zaman F#-karşılıklı kitaplıklarını kullanma gibi adları `Key`, `Value`, `Arg` (ancak değil örneğin `TKey`).</span><span class="sxs-lookup"><span data-stu-id="97fcf-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="97fcf-219">Genel işlevler ve değerleri PascalCase ya da camelCase kullanılmaya F# modülleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="97fcf-220">camelCase kullanılmak üzere tasarlanmış genel işlevleri için kullanılan nitelenmemiş (örneğin, `invalidArg`) ve "standart toplama işlevleri için" (örneğin, List.map).</span><span class="sxs-lookup"><span data-stu-id="97fcf-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="97fcf-221">Her iki bu durumda, işlev adlarını çok dil anahtar sözcükleri gibi davranır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="97fcf-222">Nesne, türü ve modül tasarım</span><span class="sxs-lookup"><span data-stu-id="97fcf-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="97fcf-223">Türler ve modüller içerecek şekilde ad alanları veya modülleri kullanma</span><span class="sxs-lookup"><span data-stu-id="97fcf-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="97fcf-224">Her F# bir bileşen dosyasında, bir ad alanı bildirimi veya modül bildirimi ile başlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="97fcf-225">veya</span><span class="sxs-lookup"><span data-stu-id="97fcf-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="97fcf-226">Kod en üst düzeyde düzenlemek için modüller ve ad alanları'nı kullanarak arasındaki farklar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="97fcf-227">Ad alanlarında birden çok dosya yayılabilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="97fcf-228">Ad alanları içeremez F# içinde bir iç modül olmadıkları sürece işlevleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="97fcf-229">Herhangi bir modülden kodunu tek bir dosyada yer almalıdır</span><span class="sxs-lookup"><span data-stu-id="97fcf-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="97fcf-230">Üst düzey modüller içerebilir F# bir iç modül gerek kalmadan işlevleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="97fcf-231">Bir üst düzey ad alanında veya modülde arasında seçim kodun derlenmiş form etkiler ve bu nedenle diğer .NET dilleri görünümünden API'nizi sonunda kullanılması dışında etkiler F# kod.</span><span class="sxs-lookup"><span data-stu-id="97fcf-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="97fcf-232">Nesne türleri için iç işlemler için yöntemleri ve özellikleri kullanın</span><span class="sxs-lookup"><span data-stu-id="97fcf-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="97fcf-233">Nesneleriyle çalışırken tüketilebilir işlevselliği yöntemleri ve özellikleri türdeki olarak uygulandığından emin olmak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="97fcf-234">İşlevlerin toplu belirli bir üye için mutlaka bu üye uygulanmadı, ancak bu işlevsellik tüketilebilir parçası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="97fcf-235">Değişebilir durum kapsüllemek için sınıfları kullanma</span><span class="sxs-lookup"><span data-stu-id="97fcf-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="97fcf-236">İçinde F#, bu yalnızca bir durumu zaten bir kapanış, sıralama ifadesi veya zaman uyumsuz bir hesaplama gibi başka bir dil yapısı yalıtılan değil, yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="97fcf-237">Arabirimleri kullanın ilgili işlemler</span><span class="sxs-lookup"><span data-stu-id="97fcf-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="97fcf-238">Arabirim türlerinde işlemler kümesini temsil etmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="97fcf-239">Bu işlevlerin diziler veya işlevlerin kayıtlar gibi diğer seçenekleri için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="97fcf-240">Preference için:</span><span class="sxs-lookup"><span data-stu-id="97fcf-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="97fcf-241">Hangi işlev nesneleri normalde verirsiniz elde etmek için kullanabileceğiniz bir .NET birinci sınıf kavramları arabirimdir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="97fcf-242">Ayrıca, bunlar işlevlerin kayıtları olamaz, programa varlıksal türleri kodlamada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="97fcf-243">Koleksiyonlarda davranan grubun işlevleri için bir modül kullanma</span><span class="sxs-lookup"><span data-stu-id="97fcf-243">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="97fcf-244">Bir koleksiyon türü tanımladığınızda, standart bir dizi işlemlerini ister sağlamayı göz önüne alın `CollectionType.map` ve `CollectionType.iter`) için yeni koleksiyon türleri.</span><span class="sxs-lookup"><span data-stu-id="97fcf-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="97fcf-245">Böyle bir modül eklerseniz, FSharp.core'da bulunan işlevleri için standart adlandırma kurallarını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="97fcf-246">Matematik ve DSL kitaplıkları, özellikle ortak, kurallı işlevler için grubun işlevleri için bir modül kullanın</span><span class="sxs-lookup"><span data-stu-id="97fcf-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="97fcf-247">Örneğin, `Microsoft.FSharp.Core.Operators` en üst düzey işlevleri otomatik olarak açılan bir koleksiyonudur (gibi `abs` ve `sin`) FSharp.Core.dll tarafından sağlanan.</span><span class="sxs-lookup"><span data-stu-id="97fcf-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="97fcf-248">Benzer şekilde, istatistikleri kitaplığı işlevleri sahip bir modül içerebilir `erf` ve `erfc`, bu modül burada açıkça ya da otomatik olarak açılacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="97fcf-249">RequireQualifiedAccess kullanmayı göz önünde bulundurun ve dikkatli bir şekilde AutoOpen öznitelikleri uygulama</span><span class="sxs-lookup"><span data-stu-id="97fcf-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="97fcf-250">Ekleme `[<RequireQualifiedAccess>]` özniteliği bir modül için modülü açılamadı ve erişimi nitelenmiş modülünün öğelere başvurular açık gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="97fcf-251">Örneğin, `Microsoft.FSharp.Collections.List` modülü, bu öznitelik içeriyor.</span><span class="sxs-lookup"><span data-stu-id="97fcf-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="97fcf-252">İşlevleri ve değerleri modüldeki diğer modüllerin adlarla çakışma olasılığı adlara sahip olduğunda bu kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="97fcf-253">Koşullu erişim gerektiren bir kitaplığı geliştirilebilirlik ve uzun vadede sürdürülebilirliğini önemli ölçüde artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fcf-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="97fcf-254">Ekleme `[<AutoOpen>]` özniteliği bir modül için modülü içeren ad alanı açıldığında açılacak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="97fcf-255">`[<AutoOpen>]` Özniteliği da uygulanabilir olduğunda derlemeye başvurulduğundan otomatik olarak açıldığında bir modül belirtmek için bir derleme.</span><span class="sxs-lookup"><span data-stu-id="97fcf-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="97fcf-256">Örneğin, bir istatistik Kitaplığı **MathsHeaven.Statistics** içerebilir bir `module MathsHeaven.Statistics.Operators` işlevler içeren `erf` ve `erfc`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="97fcf-257">Bu modül olarak işaretlemek makul `[<AutoOpen>]`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="97fcf-258">Başka bir deyişle `open MathsHeaven.Statistics` Ayrıca bu modül açılacak ve adları Getir `erf` ve `erfc` kapsama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="97fcf-259">Başka bir iyi kullanımını `[<AutoOpen>]` için genişletme yöntemleri içeren modüllere.</span><span class="sxs-lookup"><span data-stu-id="97fcf-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="97fcf-260">Aşırı `[<AutoOpen>]` kirletilmiş ad alanları ve özniteliklerini müşteri adaylarını dikkatli kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="97fcf-261">Belirli alanlarında kullanmalıdır belirli kitaplıkları için `[<AutoOpen>]` için daha iyi kullanılabilirlik yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="97fcf-262">İyi bilinen işleçleri kullanarak uygun olduğu sınıflarında işleci üyelerini tanımlama göz önünde bulundurun</span><span class="sxs-lookup"><span data-stu-id="97fcf-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="97fcf-263">Bazen sınıfları, matematik yapıları vektörleri gibi model oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="97fcf-264">İyi bilinen işleçleri modellenmiş etki alanı varsa, bunları sınıfı iç üyeleri olarak tanımlama yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="97fcf-265">Bu kılavuz, bu tür için genel .NET rehberliği karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="97fcf-266">Ancak, ayrıca önemli olabilir F# ile birlikte kullanılmak üzere bu tür böylece olarak kodlama F# işlevlere ve metotlara List.sumBy gibi üye kısıtlamaları ile.</span><span class="sxs-lookup"><span data-stu-id="97fcf-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="97fcf-267">CompiledName sağlamak üzere kullanmayı göz önünde bulundurun bir. Diğer .NET dil Tüketiciler için NET kolay adı</span><span class="sxs-lookup"><span data-stu-id="97fcf-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="97fcf-268">Bazen bir stili için bir ad isteyebilirsiniz F# tüketiciler (gibi BT'nin görünecek şekilde küçük bir statik üye modülü bağlı işlevi gibi), ancak bütünleştirilmiş kod içine derlenmiş olan farklı bir stil adı vardır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="97fcf-269">Kullanabileceğiniz `[<CompiledName>]` için farklı bir stil sağlamak için özniteliği olmayan F# derlemenin tüketme kod.</span><span class="sxs-lookup"><span data-stu-id="97fcf-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="97fcf-270">Kullanarak `[<CompiledName>]`, .NET adlandırma kuralları için kullanabileceğiniz olmayan F# derlemenin tüketicileri.</span><span class="sxs-lookup"><span data-stu-id="97fcf-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="97fcf-271">Bunu yapmak, böylece daha basit bir API sağlar kullanırsanız, üye işlevleri için yöntemi aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="97fcf-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="97fcf-272">Yöntem aşırı yükü benzer işlevleri gerçekleştirmek için gereken API basitleştirmek için ancak farklı seçenekler ya da bağımsız değişkenler ile güçlü bir araç olan.</span><span class="sxs-lookup"><span data-stu-id="97fcf-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="97fcf-273">İçinde F#, bağımsız değişken türleri yerine bağımsız değişken sayısı aşırı daha yaygındır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="97fcf-274">Bu tür tasarım geliştirilebilen olasılığı varsa, kayıt ve birleşim türlerini temsillerini Gizle</span><span class="sxs-lookup"><span data-stu-id="97fcf-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="97fcf-275">Nesneleri somut temsillerini açıklanmaması</span><span class="sxs-lookup"><span data-stu-id="97fcf-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="97fcf-276">Örneğin, somut gösterimini <xref:System.DateTime> değerlerin değil .NET kitaplığı tasarım harici, genel API tarafından göstermiştir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="97fcf-277">Çalışma zamanında, ortak dil çalışma zamanı yürütme kullanılan taahhüt uygulama bilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="97fcf-278">Ancak, derlenmiş kod kendisini somut gösterimi bağımlılıkları yerden devam edebiliyorduk değil.</span><span class="sxs-lookup"><span data-stu-id="97fcf-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="97fcf-279">Uygulama devralma genişletilebilirliği için kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="97fcf-280">İçinde F#, uygulama devralma nadiren kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="97fcf-281">Ayrıca, devralma hiyerarşilerini çoğunlukla karmaşık ve yeni gereksinimleri geldiğinde değiştirmek zor olur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="97fcf-282">Devralma uygulama hala var F# uyumluluğu ve burada bir sorun için en iyi çözüm olduğundan, ancak diğer teknikleri Aranan nadir durumlarda, F# arabirimi gibi çok biçimlilik için tasarlarken programları uygulama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="97fcf-283">İşlev ve üyesi imzaları</span><span class="sxs-lookup"><span data-stu-id="97fcf-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="97fcf-284">Diziler için dönüş değerlerini, birden çok ilişkisiz değer az sayıda döndürülürken kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="97fcf-285">Bir dönüş türü bir tanımlama grubu kullanımı iyi bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="97fcf-286">İçin dönüş türleri birçok bileşen içeren veya bileşenleri tek bir tanımlanabilen varlıkla ilgili yerlerde, adlandırılmış tür yerine bir demet kullanmayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="97fcf-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="97fcf-287">Kullanım `Async<T>` için zaman uyumsuz programlama, F# API sınırları</span><span class="sxs-lookup"><span data-stu-id="97fcf-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="97fcf-288">Adlı karşılık gelen eşzamanlı bir işlem olup olmadığını `Operation` döndüren bir `T`, zaman uyumsuz işlem adlı sonra `AsyncOperation` döndürürse `Async<T>` veya `OperationAsync` döndürürse `Task<T>`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="97fcf-289">Başlangıç/bitiş yöntemleri açığa yaygın olarak kullanılan .NET türleri göz önünde bulundurun için kullanarak `Async.FromBeginEnd` genişletme yöntemleri sağlamak için bir cephe yazmak için F# bu .NET API'ları için zaman uyumsuz programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="97fcf-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

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

### <a name="exceptions"></a><span data-ttu-id="97fcf-290">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="97fcf-290">Exceptions</span></span>

<span data-ttu-id="97fcf-291">Bkz: [hata Yönetimi](conventions.md#error-management) özel durumlar, sonuçları ve seçenekleri uygun kullanımı hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="97fcf-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="97fcf-292">Uzantı üyeleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="97fcf-293">Dikkatli bir şekilde uygulama F# uzantı üyeleri F#- için -F# bileşenleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="97fcf-294">F#Uzantı üyeleri genellikle yalnızca bir türü modlarından kullanım çoğu ile ilişkili iç işlemlerinin kabini içinde işlemleri için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="97fcf-295">Yaygın olarak kullanıldığı olduğundan fazla deyimsel API'lerden sağlamak F# çeşitli .NET türleri için:</span><span class="sxs-lookup"><span data-stu-id="97fcf-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="97fcf-296">Birleşim türleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="97fcf-297">Ayrılmış birleşimler ağaç yapılandırılmış veriler için sınıf Hiyerarşiler yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="97fcf-298">Ağaç benzeri, yinelemeli olarak tanımlanan yapılardır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="97fcf-299">Devralma ile garip, ancak ayırt edici birleşimler ile Zarif budur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="97fcf-300">Ayırt edici birleşimler ağaç benzeri verileri temsil eden da Desen eşleştirme içinde exhaustiveness yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="97fcf-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="97fcf-301">Kullanım `[<RequireQualifiedAccess>]` adları büyük/küçük harf yeterince benzersiz olmayan birleşim türleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="97fcf-302">Bir etki alanında aynı adı ayrılmış birlik vakaları gibi farklı işlemler için en iyi ad olduğu kendinizi bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fcf-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="97fcf-303">Kullanabileceğiniz `[<RequireQualifiedAccess>]` gölgeleme nedeniyle kafa karıştırıcı hataları sıralamasını, bağımlı tetikleme önlemek için büyük/küçük harf adlarını ayırt etmek için `open` deyimleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="97fcf-304">Bu tür tasarım geliştirilebilen olasılığı varsa, ayrılmış birleşimler temsillerini ikili uyumlu API'leri için Gizle</span><span class="sxs-lookup"><span data-stu-id="97fcf-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="97fcf-305">Birleşimler türleri Bel F# desen eşleştirme forms birleştiren bir programlama modeli için.</span><span class="sxs-lookup"><span data-stu-id="97fcf-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="97fcf-306">Daha önce bahsedildiği gibi tasarım bu tür geliştirilebilen olasılığı varsa, somut veri gösterimleri devamlılığımız kaçınmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="97fcf-307">Örneğin, ayrılmış bir birleşim gösterimini kullanarak özel veya iç bildirimi gizlenebilir veya bir imza dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="97fcf-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="97fcf-308">Ayrılmış birleşimler incelemelerin çıkıyorsa, bu sürüm için sabit kitaplığınızı kullanıcı kodu bozmadan bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fcf-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="97fcf-309">Bunun yerine, değer türünüz üzerinde desen izin vermek için bir veya daha fazla Etkin desenler, devamlılığımız göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="97fcf-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="97fcf-310">Etkin desenler sağlamak için alternatif bir yolu sağlamak F# gösterme kaçınarak desen tüketicileriyle F# doğrudan birleşim türleri.</span><span class="sxs-lookup"><span data-stu-id="97fcf-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="97fcf-311">Satır içi işlevleri ve üye kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="97fcf-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="97fcf-312">Satır içi işlevleri statik olarak çözümlenmiş genel türler ve örtük üye kısıtlamaları ile kullanarak genel sayısal algoritmalarının tanımlayın</span><span class="sxs-lookup"><span data-stu-id="97fcf-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="97fcf-313">Aritmetik üye kısıtlamaları ve F# karşılaştırma kısıtlamaları için bir standart olan F# programlama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="97fcf-314">Örneğin, aşağıdaki kodu düşünün:</span><span class="sxs-lookup"><span data-stu-id="97fcf-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="97fcf-315">Bu işlev türü şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="97fcf-316">Bu, bir matematik Kitaplığı'ndaki Genel API için uygun bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="97fcf-317">Üye kısıtlamaları türü sınıfları ve yazmaya duck benzetimini yapmak için kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="97fcf-318">"Yazarak duck" kullanarak benzetimi mümkündür F# üye kısıtlamaları.</span><span class="sxs-lookup"><span data-stu-id="97fcf-318">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="97fcf-319">Ancak, olun üyeleri bu içinde olmayan genel kullanılması gerekir kullanın F#- için -F# kitaplığı tasarımları.</span><span class="sxs-lookup"><span data-stu-id="97fcf-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="97fcf-320">Bilinmeyen ya da standart dışı örtük kısıtlamalarına göre kitaplığı tasarımları eğilimindedir faaliyetini ve belirli bir framework desene bağlı olmak kullanıcı kodu neden olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="97fcf-321">Ayrıca, bu şekilde üye kısıtlamaları ağır olarak kullanan çok uzun derleme sürelerini sonuçlanabilen olasılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="97fcf-322">İşleç tanımları</span><span class="sxs-lookup"><span data-stu-id="97fcf-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="97fcf-323">Özel sembolik işleçleri tanımlamamaya özen gösterin</span><span class="sxs-lookup"><span data-stu-id="97fcf-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="97fcf-324">Özel işleçleri, bazı durumlarda gereklidir ve uygulama kodu büyük bir gövdesi içinde çok kullanışlı notational cihazlar.</span><span class="sxs-lookup"><span data-stu-id="97fcf-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="97fcf-325">Yeni bir kitaplık kullanıcıları için adlandırılan işlevlerin genellikle kullanımı daha kolay.</span><span class="sxs-lookup"><span data-stu-id="97fcf-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="97fcf-326">Ayrıca, özel sembolik işleçleri belgeye zor olabilir ve kullanıcılar IDE ve arama motorları mevcut kısıtlamalar nedeniyle, işleçler hakkında Yardım aramanızı daha zor bulur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="97fcf-327">Sonuç olarak, işlevinizi olarak adlandırılan işlevlerin ve üyeleri yayımlamak ve yalnızca notational belgeler ve bunları sahip bilişsel maliyeti basıyor, ayrıca işleçler için bu işlevi göstermek idealdir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="97fcf-328">Ölçü Birimleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="97fcf-329">Ölçü birimleri eklenen tür dikkatli bir şekilde kullanmak F# kod</span><span class="sxs-lookup"><span data-stu-id="97fcf-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="97fcf-330">Ölçü birimleri için ek çok yazma bilgilerini, diğer .NET dilleri ile görüntülendiğinde silinir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="97fcf-331">.NET bileşenleri, araçları ve yansıma türlerini SAN birimleri göreceği dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="97fcf-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="97fcf-332">Örneğin, C# tüketiciler görürsünüz `float` yerine `float<kg>`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="97fcf-333">Tür Kısaltmaları</span><span class="sxs-lookup"><span data-stu-id="97fcf-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="97fcf-334">Tür kısaltmaları'basitleştirmek için dikkatli kullanın F# kod</span><span class="sxs-lookup"><span data-stu-id="97fcf-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="97fcf-335">.NET bileşenleri, araçları ve yansıma kısaltılmış türleri tarafından görülmez.</span><span class="sxs-lookup"><span data-stu-id="97fcf-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="97fcf-336">Tür kısaltmaları önemli kullanımını daha karmaşık daha aslında, tüketicilerin karıştırır görünen bir etki alanı da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fcf-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="97fcf-337">Tür kısaltmaları genel türleri, üyeleri ve özellikler için kısaltılmış türünde mevcut kodlar doğası gereği farklı olmalıdır kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="97fcf-338">Bu durumda, tanımlanan asıl tür gösterimi hakkında çok fazla kısaltılmış türü ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="97fcf-339">Bunun yerine, bir sınıf türü ya da tek örneği ayrılmış bir birleşim kısaltması sarmalama göz önünde bulundurun (ya da performans gerekli olduğunda, bir yapı türü kısaltması sarmalamak için kullanmayı göz önünde bulundurun).</span><span class="sxs-lookup"><span data-stu-id="97fcf-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="97fcf-340">Örneğin, bir çoklu eşlem özel bir durum olarak tanımlamak için daha cazip bir F# eşleyin, örneğin:</span><span class="sxs-lookup"><span data-stu-id="97fcf-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="97fcf-341">Ancak, mantıksal nokta gösterimi işlemleri bu tür bir harita üzerindeki işlemler aynı değildir: Örneğin, arama işleci eşlendiğini makul. [Temel] anahtar sözlükte yerine bir özel durum oluşturma değilse boş liste döndürür.</span><span class="sxs-lookup"><span data-stu-id="97fcf-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="97fcf-342">Diğer .NET dilleri kullanımdan kitaplıkları için yönergeler</span><span class="sxs-lookup"><span data-stu-id="97fcf-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="97fcf-343">Diğer .NET dilleri kullanımdan kitaplıkları tasarlarken, bağlı kalacağını önemli olduğu [.NET kitaplığı tasarım yönergeleri](../../standard/design-guidelines/index.md).</span><span class="sxs-lookup"><span data-stu-id="97fcf-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="97fcf-344">Bu belgede, tersine, temel alınan .NET kitaplıkları Bu kitaplıklar etiketlenir F#-kullanan kitaplıkları karşılıklı F# kısıtlama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="97fcf-345">Temel alınan .NET kitaplıkları tasarlama anlamına gelir kullanımını en aza indirerek, tanıdık ve deyimsel API'ler .NET Framework geri kalanı ile tutarlı sağlama F#-Genel API belirli yapılardan.</span><span class="sxs-lookup"><span data-stu-id="97fcf-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="97fcf-346">Kurallar, aşağıdaki bölümlerde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="97fcf-347">Namespace ve türü tasarım (için diğer .NET dilleri kullanımdan kitaplıkları)</span><span class="sxs-lookup"><span data-stu-id="97fcf-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="97fcf-348">.NET adlandırma kuralları bileşenlerinizi Genel API için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="97fcf-349">Özel kısaltılmış ve .NET büyük/küçük harf kuralları kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="97fcf-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="97fcf-350">Ad alanları, türler ve üyeler birincil ait düzenlenmiş yapıyı bileşenleriniz için kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="97fcf-351">Genel işlevler içeren tüm dosyaları ile başlaması gereken bir `namespace` bildirimi ve yalnızca genel kullanıma yönelik varlıklar ad alanlarında türleri olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="97fcf-352">Kullanmayın F# modüller.</span><span class="sxs-lookup"><span data-stu-id="97fcf-352">Do not use F# modules.</span></span>

<span data-ttu-id="97fcf-353">Genel olmayan modülleri, uygulama kodu, yardımcı program türlerini ve yardımcı işlevlerini tutmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="97fcf-354">Statik türler olmalıdır tercih edilen modülleri, bunlar içinde kullanılamaz aşırı yüklerken ve diğer .NET API tasarım kavramları kullanılacak API gelecekteki evrimi izin F# modüller.</span><span class="sxs-lookup"><span data-stu-id="97fcf-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="97fcf-355">Örneğin, aşağıdaki genel API yerine:</span><span class="sxs-lookup"><span data-stu-id="97fcf-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="97fcf-356">Bunun yerine göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="97fcf-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="97fcf-357">Kullanım F# türlerinin tasarım evrim Geçiren kalmaz, .NET API vanilla içinde kayıt türleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="97fcf-358">F#kayıt türleri, basit bir .NET sınıfı için derleyin.</span><span class="sxs-lookup"><span data-stu-id="97fcf-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="97fcf-359">Bu, bazı API'leri basit, kararlı türler için uygundur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="97fcf-360">Kullanmayı düşünmelisiniz `[<NoEquality>]` ve `[<NoComparison>]` arabirimleri otomatik olarak oluşturulmasını engellemek için öznitelikler.</span><span class="sxs-lookup"><span data-stu-id="97fcf-360">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="97fcf-361">Ayrıca .NET API'lerini vanilla değişebilir kayıt alanları bu kullanıma sunan bir ortak alan kullanarak kaçının.</span><span class="sxs-lookup"><span data-stu-id="97fcf-361">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="97fcf-362">Her zaman bir sınıf gelecekteki gelişimine için daha esnek bir seçenek API'sinin sağlayacağını olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="97fcf-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="97fcf-363">Örneğin, aşağıdaki F# kod için genel API sunan bir C# tüketici:</span><span class="sxs-lookup"><span data-stu-id="97fcf-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="97fcf-364">F#:</span><span class="sxs-lookup"><span data-stu-id="97fcf-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="97fcf-365">C#:</span><span class="sxs-lookup"><span data-stu-id="97fcf-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="97fcf-366">Gösterimini Gizle F# birleşim türleri vanilla .NET API'leri</span><span class="sxs-lookup"><span data-stu-id="97fcf-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="97fcf-367">F#Birleşim türleri genellikle kullanılmaz bileşen sınırları boyunca için bile F#- için -F# kodlama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="97fcf-368">Bunlar, bileşenler ve kitaplıkları içinde dahili olarak kullanılan bir mükemmel uygulama cihazı.</span><span class="sxs-lookup"><span data-stu-id="97fcf-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="97fcf-369">Bir vanilla .NET API'si tasarlarken, özel bir bildirim ya da bir imza dosyası kullanarak bir birleşim türünün temsili gizleme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="97fcf-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="97fcf-370">Ayrıca, bir birleşim gösterimi üyeleriyle dahili olarak bir istenen sağlamak için kullandığınız türleri büyütmek. NET yönelik API.</span><span class="sxs-lookup"><span data-stu-id="97fcf-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="97fcf-371">Tasarım GUI ve diğer bileşenleri framework'ün tasarım desenlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="97fcf-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="97fcf-372">Birçok farklı çerçeveler, WinForms, WPF ve ASP.NET gibi .NET içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="97fcf-373">Bu çerçeveler kullanmak için bileşenleri tasarlıyorsanız adlandırma ve tasarım kuralları her biri için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="97fcf-374">Örneğin, WPF programlama WPF tasarlarken sınıfları için Tasarım desenleri benimseyin.</span><span class="sxs-lookup"><span data-stu-id="97fcf-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="97fcf-375">Kullanıcı arabirimi programlama modelleri için Tasarım desenleri gibi olayları kullanın ve bildirim tabanlı koleksiyonlar olanlar gibi bulunan <xref:System.Collections.ObjectModel>.</span><span class="sxs-lookup"><span data-stu-id="97fcf-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="97fcf-376">Nesne ve üye tasarımı (diğer .NET dilleri kullanımdan kitaplıkları)</span><span class="sxs-lookup"><span data-stu-id="97fcf-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="97fcf-377">CLIEvent özniteliği .NET olaylar oluşturmak için kullanın</span><span class="sxs-lookup"><span data-stu-id="97fcf-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="97fcf-378">Oluşturmak bir `DelegateEvent` belirli bir .NET ile temsilci türü bir nesneyi alır ve `EventArgs` (yerine `Event`, yalnızca kullanan `FSharpHandler` türü varsayılan olarak) ve böylece diğer .NET dilleri için benzer şekilde olayların yayımlandığı.</span><span class="sxs-lookup"><span data-stu-id="97fcf-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="97fcf-379">Zaman uyumsuz işlemler .NET görevleri döndüren yöntemler olarak kullanıma sunma</span><span class="sxs-lookup"><span data-stu-id="97fcf-379">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="97fcf-380">Görevler,. NET'te etkin zaman uyumsuz hesaplamalar temsil etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97fcf-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="97fcf-381">Genel olarak daha az bileşimsel görevleridir F# `Async<T>` nesneleri "zaten yürütülüyor." görevleri temsil eder ve paralel bileşim gerçekleştiren veya iptal etme sinyaller yayılmasını Gizle yollarla birlikte oluşturulan olamaz ve diğer bağlam parametreleri.</span><span class="sxs-lookup"><span data-stu-id="97fcf-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="97fcf-382">Ancak, bu rağmen görev döndüren zaman uyumsuz programlama .NET üzerinde standart gösterimi yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-382">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="97fcf-383">Sık olacaktır ayrıca bir açık iptal belirtecini kabul etmek istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="97fcf-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="97fcf-384">.NET temsilci türleri yerine kullanmak F# işlev türleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="97fcf-385">Burada "F# işlev türleri" ortalama "OK" türleri ister `int -> int`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-385">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="97fcf-386">Bunun yerine:</span><span class="sxs-lookup"><span data-stu-id="97fcf-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="97fcf-387">Bunu yapın:</span><span class="sxs-lookup"><span data-stu-id="97fcf-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="97fcf-388">F# İşlev türü olarak görünür `class FSharpFunc<T,U>` diğer .NET dilleri için dil özelliklerinin ve araçları için temsilci türleri anlayan daha az uygundur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="97fcf-389">.NET Framework 3.5 veya sonraki bir sürümünü hedefleyen bir daha yüksek sıralı yöntemi yazarken `System.Func` ve `System.Action` temsilcileri, doğru API'lerden bir düşük uyuşmazlıkları şekilde bu API'leri kullanmak, .NET geliştiricilerinin etkinleştirmek için yayımlayın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="97fcf-390">(.NET Framework 2.0 hedeflenirken sistem tarafından tanımlanan temsilci türleriyle daha sınırlıdır; gibi önceden tanımlanmış temsilci türleri kullanmayı düşünün `System.Converter<T,U>` veya belirli bir temsilci türü tanımlama.)</span><span class="sxs-lookup"><span data-stu-id="97fcf-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="97fcf-391">Diğer taraftan, .NET temsilciler için doğal olmayan F#-kitaplıkları'e yönelik (sonraki bölümüne F#-kitaplıkları'e yönelik).</span><span class="sxs-lookup"><span data-stu-id="97fcf-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="97fcf-392">Sonuç olarak, tüm uygulama kullanarak yazmak için temel alınan .NET kitaplıkları için daha yüksek sıralı yöntemleri geliştirirken yaygın bir uygulama stratejisi olan F# işlev türleri ve sonra gerçek F#uygulaması.</span><span class="sxs-lookup"><span data-stu-id="97fcf-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="97fcf-393">TryGetValue deseni döndürmek yerine kullanmak F# seçenek değerleri ve alma için yöntem aşırı yükü tercih F# seçenek değerleri bağımsız değişkenleri olarak</span><span class="sxs-lookup"><span data-stu-id="97fcf-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="97fcf-394">Kullanım için ortak desenler F# seçenek türünde API'leri daha iyi vanilla içinde uygulanan .NET standart .NET kullanarak API'leri teknikleri tasarlayın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="97fcf-395">Döndürmek yerine bir F# seçeneği değeri, dönüş türü bool artı out parametresi "TryGetValue" deseni olduğu gibi kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="97fcf-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="97fcf-396">Alma yerine F# seçenek değerleri parametre olarak, yöntem aşırı yüklerken veya isteğe bağlı bağımsız değişkenleri kullanmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="97fcf-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="97fcf-397">.NET koleksiyonu arabirimini kullanın türleri IEnumerable\<T\> ve IDictionary\<anahtar, değer\> için parametreler ve dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="97fcf-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="97fcf-398">.NET dizileri gibi somut koleksiyon türlerini kullanmaktan kaçının `T[]`, F# türleri `list<T>`, `Map<Key,Value>` ve `Set<T>`, ve .NET beton koleksiyon türleri gibi `Dictionary<Key,Value>`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="97fcf-399">.NET kitaplığı tasarım yönergeleri ile ilgili gibi çeşitli koleksiyon türlerini kullanmak iyi bir öneri sahip `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="97fcf-400">Diziler bazı kullanımını (`T[]`) grounds performans üzerinde bazı durumlarda, kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="97fcf-401">Özellikle dikkat `seq<T>` olduğundan yalnızca F# için diğer ad `IEnumerable<T>`, ve bu nedenle seq genellikle bir vanilla .NET API'si için uygun bir tür.</span><span class="sxs-lookup"><span data-stu-id="97fcf-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="97fcf-402">Yerine F# listeler:</span><span class="sxs-lookup"><span data-stu-id="97fcf-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="97fcf-403">Kullanım F# dizileri:</span><span class="sxs-lookup"><span data-stu-id="97fcf-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="97fcf-404">Birim türü sıfır bağımsız değişken yöntemi tanımlamak için bir yöntem yalnızca giriş türü olarak kullanmak ya da yalnızca dönüş türü void döndüren bir yöntemi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="97fcf-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="97fcf-405">Birim türü diğer kullanımları kaçının.</span><span class="sxs-lookup"><span data-stu-id="97fcf-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="97fcf-406">İyi şunlardır:</span><span class="sxs-lookup"><span data-stu-id="97fcf-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="97fcf-407">Bu hatalı.</span><span class="sxs-lookup"><span data-stu-id="97fcf-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="97fcf-408">Temel alınan .NET API sınırlarındaki null değerler olup olmadığını denetleyin</span><span class="sxs-lookup"><span data-stu-id="97fcf-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="97fcf-409">F#uygulama kodu eğilimlidir sabit tasarım desenleri ve kullanım kısıtlamaları için null değişmez değerlerinin nedeniyle daha az boş değerlerle sahip F# türleri.</span><span class="sxs-lookup"><span data-stu-id="97fcf-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="97fcf-410">Diğer .NET dilleri genellikle bir değer olarak null çok daha sık kullanın.</span><span class="sxs-lookup"><span data-stu-id="97fcf-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="97fcf-411">Bu nedenle, F# bir vanilla .NET API gösterme kod API sınırında null parametreleri denetleyin ve bu değerleri ile geçmesini engellemek F# uygulama kodu.</span><span class="sxs-lookup"><span data-stu-id="97fcf-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="97fcf-412">`isNull` İşlevi veya üzerinde desen `null` deseni kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="97fcf-413">Dönüş değerleri diziler kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="97fcf-414">Bunun yerine, toplama verileri tutan veya birden çok değerleri döndürülecek out parametreleri kullanarak adlandırılmış bir tür döndüren tercih eder.</span><span class="sxs-lookup"><span data-stu-id="97fcf-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="97fcf-415">Diziler ve yapı demetleri. NET'te mevcut olmasına karşın (C# dil desteği için çalışan yapı demetleri dahil), bunlar ideal ve beklenen API .NET geliştiricileri için sağlamaz çoğunlukla.</span><span class="sxs-lookup"><span data-stu-id="97fcf-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="97fcf-416">Parametreleri currying kullanmaktan kaçının</span><span class="sxs-lookup"><span data-stu-id="97fcf-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="97fcf-417">Bunun yerine, çağırma kuralları .NET kullanın `Method(arg1,arg2,…,argN)`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="97fcf-418">İpucu: Herhangi bir .NET dil kullanımdan kitaplıkları tasarladığınız sonra aslında hiçbir yerine bazı Deneysel C# ve Visual Basic Kitaplıklarınızı "Genel Görünüm hemen" Bu dillerin emin olmak için programlama.</span><span class="sxs-lookup"><span data-stu-id="97fcf-418">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="97fcf-419">Ayrıca, kitaplıkları, belgeleri geliştiricileri için beklendiği gibi göründüğünden emin olmak için .NET Reflector ve Visual Studio nesne tarayıcısı gibi araçları da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97fcf-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="97fcf-420">Ek</span><span class="sxs-lookup"><span data-stu-id="97fcf-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="97fcf-421">Uçtan uca örnek tasarlama F# diğer .NET dilleri ile kullanmak için kodu</span><span class="sxs-lookup"><span data-stu-id="97fcf-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="97fcf-422">Aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="97fcf-422">Consider the following class:</span></span>

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

<span data-ttu-id="97fcf-423">Çıkarsanan F# Bu sınıf türü şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-423">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="97fcf-424">Nasıl bir göz atalım bu F# başka bir .NET dilini kullanarak programcıya türü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-424">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="97fcf-425">Örneğin, yaklaşık C# "SIGNATURE" aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-425">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="97fcf-426">Hakkında dikkat edin gereken bazı önemli noktalar vardır F# burada yapıları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97fcf-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="97fcf-427">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="97fcf-427">For example:</span></span>

* <span data-ttu-id="97fcf-428">Bağımsız değişken adları gibi meta veriler korunur.</span><span class="sxs-lookup"><span data-stu-id="97fcf-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="97fcf-429">F#haline iki bağımsız değişken almaz yöntemleri C# iki bağımsız değişken almaz yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="97fcf-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="97fcf-430">İşlevler ve listeleri duruma karşılık gelen türler için başvuru F# kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="97fcf-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="97fcf-431">Aşağıdaki kod, bunları hesaba katması için bu kodu ayarlama konusunda gösterir.</span><span class="sxs-lookup"><span data-stu-id="97fcf-431">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="97fcf-432">Çıkarsanan F# kodun türünü şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="97fcf-432">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="97fcf-433">C# imza artık şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="97fcf-433">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="97fcf-434">Temel alınan bir .NET kitaplığının bir parçası olduğu gibi bu tür kullanıma hazırlamak düzeltmeler yaptınız:</span><span class="sxs-lookup"><span data-stu-id="97fcf-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="97fcf-435">Birden fazla ad ayarlanır: `Point1`, `n`, `l`, ve `f` dönüştü `RadialPoint`, `count`, `factor`, ve `transform`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="97fcf-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="97fcf-436">Dönüş türü kullanılan `seq<RadialPoint>` yerine `RadialPoint list` listesini kullanarak yapı değiştirerek `[ ... ]` sırası kullanarak oluşturma `IEnumerable<RadialPoint>`.</span><span class="sxs-lookup"><span data-stu-id="97fcf-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="97fcf-437">.NET temsilci türü kullanılan `System.Func` yerine bir F# işlev türü.</span><span class="sxs-lookup"><span data-stu-id="97fcf-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="97fcf-438">Bu, çok daha Hoş görünmesi C# kodunda kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="97fcf-438">This makes it far nicer to consume in C# code.</span></span>
