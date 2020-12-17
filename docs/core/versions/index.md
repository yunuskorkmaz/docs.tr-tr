---
title: .NET çalışma zamanı ve SDK 'nın sürümü oluşturma
description: Bu makalede, .NET SDK ve çalışma zamanının nasıl sürümleneceği (anlamsal sürüm oluşturma ile benzerdir) açıklanmaktadır.
ms.date: 12/07/2020
ms.openlocfilehash: 2fbc2775f31b4eab1c9883282c58accd9bb2b9f5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633630"
---
# <a name="overview-of-how-net-is-versioned"></a><span data-ttu-id="7857b-103">.NET sürümünün sürümü oluşturma konusuna genel bakış</span><span class="sxs-lookup"><span data-stu-id="7857b-103">Overview of how .NET is versioned</span></span>

<span data-ttu-id="7857b-104">[.NET çalışma zamanı ve .NET SDK](../introduction.md#sdk-and-runtimes) , farklı sıklıklara yeni özellikler ekler.</span><span class="sxs-lookup"><span data-stu-id="7857b-104">The [.NET Runtime and the .NET SDK](../introduction.md#sdk-and-runtimes) add new features at different frequencies.</span></span> <span data-ttu-id="7857b-105">Genel olarak, SDK çalışma zamanından daha sık güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7857b-105">In general, the SDK is updated more frequently than the Runtime.</span></span> <span data-ttu-id="7857b-106">Bu makalede çalışma zamanı ve SDK sürüm numaraları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7857b-106">This article explains the runtime and the SDK version numbers.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="7857b-107">Sürüm oluşturma ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="7857b-107">Versioning details</span></span>

<span data-ttu-id="7857b-108">.NET çalışma zamanının, büyük/küçük ve düzeltme eki uygulama, [semantik sürümü oluşturma](#semantic-versioning)sonrasında sürüm oluşturma yaklaşımını vardır.</span><span class="sxs-lookup"><span data-stu-id="7857b-108">The .NET Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="7857b-109">.NET SDK, anlamsal sürüm oluşturmayı takip etmez.</span><span class="sxs-lookup"><span data-stu-id="7857b-109">The .NET SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="7857b-110">.NET SDK 'nın daha hızlı ve sürüm numaralarının her ikisi de hizalı çalışma zamanına ve SDK 'nın kendi alt ve düzeltme eki yayınlarına iletişim kurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7857b-110">The .NET SDK releases faster and its version numbers must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span>

<span data-ttu-id="7857b-111">.NET SDK sürüm numarasının ilk iki konumu ile yayınlanan .NET çalışma zamanı sürümüne kilitlidir.</span><span class="sxs-lookup"><span data-stu-id="7857b-111">The first two positions of the .NET SDK version number are locked to the .NET Runtime version it released with.</span></span> <span data-ttu-id="7857b-112">SDK 'nın her sürümü bu çalışma zamanına veya daha düşük bir sürüme yönelik uygulamalar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="7857b-112">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="7857b-113">SDK sürüm numarasının üçüncü konumu hem küçük hem de yayama numarasını iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="7857b-113">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="7857b-114">İkincil sürüm 100 ile çarpılır.</span><span class="sxs-lookup"><span data-stu-id="7857b-114">The minor version is multiplied by 100.</span></span> <span data-ttu-id="7857b-115">Son iki basamak, düzeltme eki numarasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7857b-115">The final two digits represent the patch number.</span></span> <span data-ttu-id="7857b-116">İkincil sürüm 1, düzeltme eki sürüm 2 102 olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7857b-116">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="7857b-117">Örneğin, bir çalışma zamanı ve SDK sürüm numarası sırası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7857b-117">For example, here's a possible sequence of runtime and SDK version numbers:</span></span>

| <span data-ttu-id="7857b-118">Değiştir</span><span class="sxs-lookup"><span data-stu-id="7857b-118">Change</span></span>                | <span data-ttu-id="7857b-119">.NET Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="7857b-119">.NET Runtime</span></span>      | <span data-ttu-id="7857b-120">.NET SDK ( \* )</span><span class="sxs-lookup"><span data-stu-id="7857b-120">.NET SDK (\*)</span></span>     |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="7857b-121">İlk yayın</span><span class="sxs-lookup"><span data-stu-id="7857b-121">Initial release</span></span>       | <span data-ttu-id="7857b-122">2.2.0</span><span class="sxs-lookup"><span data-stu-id="7857b-122">2.2.0</span></span>             | <span data-ttu-id="7857b-123">2.2.100</span><span class="sxs-lookup"><span data-stu-id="7857b-123">2.2.100</span></span>           |
| <span data-ttu-id="7857b-124">SDK Düzeltme Eki</span><span class="sxs-lookup"><span data-stu-id="7857b-124">SDK patch</span></span>             | <span data-ttu-id="7857b-125">2.2.0</span><span class="sxs-lookup"><span data-stu-id="7857b-125">2.2.0</span></span>             | <span data-ttu-id="7857b-126">2.2.101</span><span class="sxs-lookup"><span data-stu-id="7857b-126">2.2.101</span></span>           |
| <span data-ttu-id="7857b-127">Çalışma zamanı ve SDK Düzeltme Eki</span><span class="sxs-lookup"><span data-stu-id="7857b-127">Runtime and SDK patch</span></span> | <span data-ttu-id="7857b-128">2.2.1</span><span class="sxs-lookup"><span data-stu-id="7857b-128">2.2.1</span></span>             | <span data-ttu-id="7857b-129">2.2.102</span><span class="sxs-lookup"><span data-stu-id="7857b-129">2.2.102</span></span>           |
| <span data-ttu-id="7857b-130">SDK özelliği değişikliği</span><span class="sxs-lookup"><span data-stu-id="7857b-130">SDK feature change</span></span>    | <span data-ttu-id="7857b-131">2.2.1</span><span class="sxs-lookup"><span data-stu-id="7857b-131">2.2.1</span></span>             | <span data-ttu-id="7857b-132">2.2.200</span><span class="sxs-lookup"><span data-stu-id="7857b-132">2.2.200</span></span>           |

<span data-ttu-id="7857b-133">LARıNı</span><span class="sxs-lookup"><span data-stu-id="7857b-133">NOTES:</span></span>

- <span data-ttu-id="7857b-134">SDK 'nın, bir çalışma zamanı özelliği güncelleştirmesinden önce 10 Özellik Güncelleştirmesi varsa, sürüm numaraları 2.2.1000 gibi sayılarla 1000 serisine, 2.2.900 ' u takip eden özellik yayını olarak da.</span><span class="sxs-lookup"><span data-stu-id="7857b-134">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="7857b-135">Bu durumun gerçekleşmesi beklenmez.</span><span class="sxs-lookup"><span data-stu-id="7857b-135">This situation isn't expected to occur.</span></span>
- <span data-ttu-id="7857b-136">99 düzeltme eki sürümleri, özellik sürümü olmadan gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="7857b-136">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="7857b-137">Bir sürüm bu numaraya yaklaşırsa, bir özellik yayını zorlar.</span><span class="sxs-lookup"><span data-stu-id="7857b-137">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="7857b-138">[DotNet/Designs](https://github.com/dotnet/designs/pull/29) deposundaki ilk teklife daha fazla ayrıntı görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7857b-138">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="7857b-139">Anlamsal sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="7857b-139">Semantic versioning</span></span>

<span data-ttu-id="7857b-140">.NET *çalışma zamanı* kabaca, değişim kullanımını benimseme ve değişiklik türünü anlatmak için sürüm numarasının çeşitli kısımlarını kullanarak, daha önce [anlamsal sürüm oluşturma (semver)](https://semver.org/)kullanır `MAJOR.MINOR.PATCH` .</span><span class="sxs-lookup"><span data-stu-id="7857b-140">The .NET *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="7857b-141">İsteğe bağlı `PRERELEASE` ve `BUILDNUMBER` parçalar, Desteklenen sürümlerin hiçbir parçası değildir ve yalnızca gecelik derlemeler, kaynak hedeflerden yerel yapılar ve desteklenmeyen önizleme sürümleri üzerinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7857b-141">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="7857b-142">Çalışma zamanı sürüm numarası değişikliklerini anlama</span><span class="sxs-lookup"><span data-stu-id="7857b-142">Understand runtime version number changes</span></span>

<span data-ttu-id="7857b-143">`MAJOR` Şu durumlarda artırılır:</span><span class="sxs-lookup"><span data-stu-id="7857b-143">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="7857b-144">Üründe önemli değişiklikler veya yeni bir ürün yönü meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="7857b-144">Significant changes occur to the product, or a new product direction.</span></span>
- <span data-ttu-id="7857b-145">Son değişiklikler alındı.</span><span class="sxs-lookup"><span data-stu-id="7857b-145">Breaking changes were taken.</span></span> <span data-ttu-id="7857b-146">Son değişiklikleri kabul etmek için yüksek bir çubuk vardır.</span><span class="sxs-lookup"><span data-stu-id="7857b-146">There's a high bar to accepting breaking changes.</span></span>
- <span data-ttu-id="7857b-147">Eski sürüm artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7857b-147">An old version is no longer supported.</span></span>
- <span data-ttu-id="7857b-148">Mevcut bağımlılığın daha yeni bir `MAJOR` sürümü benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="7857b-148">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="7857b-149">`MINOR` Şu durumlarda artırılır:</span><span class="sxs-lookup"><span data-stu-id="7857b-149">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="7857b-150">Ortak API yüzey alanı eklendi.</span><span class="sxs-lookup"><span data-stu-id="7857b-150">Public API surface area is added.</span></span>
- <span data-ttu-id="7857b-151">Yeni bir davranış eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7857b-151">A new behavior is added.</span></span>
- <span data-ttu-id="7857b-152">Mevcut bağımlılığın daha yeni bir `MINOR` sürümü benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="7857b-152">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="7857b-153">Yeni bir bağımlılık ortaya çıkarılmıştır.</span><span class="sxs-lookup"><span data-stu-id="7857b-153">A new dependency is introduced.</span></span>

<span data-ttu-id="7857b-154">`PATCH` Şu durumlarda artırılır:</span><span class="sxs-lookup"><span data-stu-id="7857b-154">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="7857b-155">Hata düzeltmeleri yapılır.</span><span class="sxs-lookup"><span data-stu-id="7857b-155">Bug fixes are made.</span></span>
- <span data-ttu-id="7857b-156">Daha yeni bir platform için destek eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="7857b-156">Support for a newer platform is added.</span></span>
- <span data-ttu-id="7857b-157">Mevcut bağımlılığın daha yeni bir `PATCH` sürümü benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="7857b-157">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="7857b-158">Diğer herhangi bir değişiklik, önceki durumlardan birine uymuyor.</span><span class="sxs-lookup"><span data-stu-id="7857b-158">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="7857b-159">Birden çok değişiklik olduğunda, tek tek değişikliklerden etkilenen en üst öğe artırılır ve aşağıdakiler sıfıra sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="7857b-159">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="7857b-160">Örneğin, ne zaman `MAJOR` artırılır `MINOR` ve `PATCH` sıfıra sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="7857b-160">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="7857b-161">Ne zaman `MINOR` artırılır, `PATCH` `MAJOR` dokunulmadan sola sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="7857b-161">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="7857b-162">Dosya adlarındaki sürüm numaraları</span><span class="sxs-lookup"><span data-stu-id="7857b-162">Version numbers in file names</span></span>

<span data-ttu-id="7857b-163">.NET için indirilen dosyalar sürümü (örneğin,) taşır `dotnet-sdk-2.1.300-win10-x64.exe` .</span><span class="sxs-lookup"><span data-stu-id="7857b-163">The files downloaded for .NET carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="7857b-164">Önizleme sürümleri</span><span class="sxs-lookup"><span data-stu-id="7857b-164">Preview versions</span></span>

<span data-ttu-id="7857b-165">Önizleme sürümlerinin `-preview[number]-([build]|"final")` sürüm numarasına eklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7857b-165">Preview versions have a `-preview[number]-([build]|"final")` appended to the version number.</span></span> <span data-ttu-id="7857b-166">Örneğin, `2.0.0-preview1-final`.</span><span class="sxs-lookup"><span data-stu-id="7857b-166">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="7857b-167">Hizmet sürümleri</span><span class="sxs-lookup"><span data-stu-id="7857b-167">Servicing versions</span></span>

<span data-ttu-id="7857b-168">Bir sürüm kapatıldıktan sonra, yayın dalları genellikle günlük derlemeler üretmeden ve bunun yerine bakım yapıları üretmede başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7857b-168">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="7857b-169">Hizmet sürümlerinin bir `-servicing-[number]` sürümüne eklenmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7857b-169">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="7857b-170">Örneğin, `2.0.1-servicing-006924`.</span><span class="sxs-lookup"><span data-stu-id="7857b-170">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="7857b-171">.NET Standard sürümleriyle ilişki</span><span class="sxs-lookup"><span data-stu-id="7857b-171">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="7857b-172">.NET Standard bir .NET başvuru derlemesinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="7857b-172">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="7857b-173">Her platforma özel birden çok uygulama vardır.</span><span class="sxs-lookup"><span data-stu-id="7857b-173">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="7857b-174">Başvuru derlemesi, belirli bir .NET Standard sürümünün parçası olan .NET API 'lerinin tanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="7857b-174">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="7857b-175">Her uygulama, belirli bir platformda .NET Standard sözleşmesini yerine getirir.</span><span class="sxs-lookup"><span data-stu-id="7857b-175">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span>

<span data-ttu-id="7857b-176">.NET Standard Reference derlemesi bir `MAJOR.MINOR` sürüm oluşturma düzeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="7857b-176">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="7857b-177">`PATCH` düzey, yalnızca bir API belirtimi (uygulama olmadan) kullanıma sunduğundan ve tanıma göre API üzerinde yapılan herhangi bir değişiklik, özellik kümesindeki bir değişikliği ve bu nedenle yeni bir sürümü temsil ettiğinden .NET Standard için kullanışlı değildir `MINOR` .</span><span class="sxs-lookup"><span data-stu-id="7857b-177">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="7857b-178">Her platformdaki uygulamalar, genellikle platform sürümünün bir parçası olarak ve bu nedenle bu platformda .NET Standard kullanan programcılara yönelik olarak güncelleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="7857b-178">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="7857b-179">Daha fazla bilgi için bkz. [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="7857b-179">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7857b-180">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7857b-180">See also</span></span>

- [<span data-ttu-id="7857b-181">Hedef çerçeveler</span><span class="sxs-lookup"><span data-stu-id="7857b-181">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="7857b-182">.NET dağıtım paketleme</span><span class="sxs-lookup"><span data-stu-id="7857b-182">.NET distribution packaging</span></span>](../distribution-packaging.md)
- [<span data-ttu-id="7857b-183">.NET destek yaşam döngüsü olgu sayfası</span><span class="sxs-lookup"><span data-stu-id="7857b-183">.NET Support Lifecycle Fact Sheet</span></span>](https://dotnet.microsoft.com/platform/support/policy)
- [<span data-ttu-id="7857b-184">.NET için Docker görüntüleri</span><span class="sxs-lookup"><span data-stu-id="7857b-184">Docker images for .NET</span></span>](https://hub.docker.com/_/microsoft-dotnet/)
