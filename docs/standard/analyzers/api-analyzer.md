---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi kullanım dışı API ve platform uyumluluğu sorunları algılamak nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 4394bc77b499db1960d61bad5e828f77f1144c65
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696890"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="66da0-103">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="66da0-103">.NET API analyzer</span></span>

<span data-ttu-id="66da0-104">.NET API Çözümleyicisi olası uyumluluk için C# API'leri farklı platformlarda risklerini ve kullanım dışı API çağrıları algılar bulur Roslyn Çözümleyicisi ' dir.</span><span class="sxs-lookup"><span data-stu-id="66da0-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="66da0-105">Bu geliştirme herhangi bir aşamasında tüm C# geliştiricileri için faydalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="66da0-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="66da0-106">API Çözümleyicisi bir NuGet paketi olarak gelir [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="66da0-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="66da0-107">Projede başvuru sonra otomatik olarak kod izler ve sorunlu API kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="66da0-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="66da0-108">Ampul üzerinde tıklayarak olası düzeltmeler hakkında öneriler de alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66da0-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="66da0-109">Aşağı açılan menüden uyarıları gizlemek için bir seçenek içerir.</span><span class="sxs-lookup"><span data-stu-id="66da0-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="66da0-110">.NET API Çözümleyicisi hala bir yayın öncesi sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="66da0-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66da0-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="66da0-111">Prerequisites</span></span>

* <span data-ttu-id="66da0-112">Visual Studio 2017 veya Mac (tüm sürümler) için Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66da0-112">Visual Studio 2017 or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="66da0-113">Kullanım dışı API'leri keşfetme</span><span class="sxs-lookup"><span data-stu-id="66da0-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="66da0-114">Hangi API'leri kullanım?</span><span class="sxs-lookup"><span data-stu-id="66da0-114">What are deprecated APIs?</span></span>

<span data-ttu-id="66da0-115">.NET ailesi, müşteri gereksinimlerini daha iyi karşılamak için sürekli olarak yükseltme büyük ürünleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="66da0-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="66da0-116">Bazı API'leri Kaldır ve yenileriyle değiştirme için doğal.</span><span class="sxs-lookup"><span data-stu-id="66da0-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="66da0-117">Bir API daha iyi bir alternatif mevcut olduğunda kullanım dışı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="66da0-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="66da0-118">Bir API kullanım dışıdır ve kullanılmaması bilgilendirmek için bir yoldur ile işaretlemek için <xref:System.ObsoleteAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="66da0-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="66da0-119">Bu yaklaşımın bir dezavantajı tüm eski API'leri için yalnızca bir tanılama kimliği olmasıdır (C# ' ta, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="66da0-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="66da0-120">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="66da0-120">This means that:</span></span>
- <span data-ttu-id="66da0-121">Belgeleri her örneği için ayrılmış mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="66da0-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="66da0-122">Belirli kategorisini uyarıları gizlemek mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="66da0-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="66da0-123">Tüm ya da bunların hiçbiri gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66da0-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="66da0-124">Yeni bir kullanımdan kaldırma kullanıcıları bilgilendirmek için başvurulan bir derleme veya paket hedefleme güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="66da0-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="66da0-125">API Çözümleyicisi bireysel uyarılar görünümünü denetime izin veren (hangi kullanımdan kaldırma hatası için anlamına gelir) DE ile başlayan API özgü hata kodları kullanır.</span><span class="sxs-lookup"><span data-stu-id="66da0-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="66da0-126">Çözümleyicisi tarafından tanımlanan kullanım dışı API'leri tanımlanan [platform/dotnet-compat](https://github.com/dotnet/platform-compat) deposu.</span><span class="sxs-lookup"><span data-stu-id="66da0-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="66da0-127">API Çözümleyicisi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="66da0-127">Using the API Analyzer</span></span>

<span data-ttu-id="66da0-128">Kullanım dışı bir API, gibi <xref:System.Net.WebClient>, kullanılan bir kod yeşil dalgalı çizgi ile vurgular API Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="66da0-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="66da0-129">Üzerinden API çağrısı geldiğinizde, bir ampul API kullanımdan aşağıdaki örnekteki gibi bilgiler görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="66da0-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Ekran WebClient API yeşil dalgalı çizgi ve ampul soldaki"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="66da0-131">**Hata listesi** penceresi, aşağıdaki örnekte gösterildiği gibi kullanım dışı API başına benzersiz bir kimliği uyarılarla içerir (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="66da0-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

!["Uyarı'nin kimlik ve açıklama gösteren Hata Listesi penceresi ekran görüntüsü"](media/api-analyzer/warnings.jpg)

<span data-ttu-id="66da0-133">Kimliği temel tıklayarak neden API kullanım dışı hakkında ayrıntılı bilgi içeren bir Web sayfası gitmeniz ve kullanılabilir alternatif API'leri ile ilgili öneriler.</span><span class="sxs-lookup"><span data-stu-id="66da0-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="66da0-134">Tüm uyarılar vurgulanan üyesinde sağ tıklayıp seçerek gizlenebilir **bastır \<tanılama kimliği >**.</span><span class="sxs-lookup"><span data-stu-id="66da0-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="66da0-135">Uyarıları gizlemek için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="66da0-135">There are two ways to suppress warnings:</span></span> 

* [<span data-ttu-id="66da0-136">yerel olarak (kaynak)</span><span class="sxs-lookup"><span data-stu-id="66da0-136">locally (in source)</span></span>](#suppressing-warnings-locally)
* <span data-ttu-id="66da0-137">[Genel (dosyasındaki bir gizleme)](#suppressing-warnings-globally) - önerilen</span><span class="sxs-lookup"><span data-stu-id="66da0-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="66da0-138">Yerel olarak uyarıları gizleme</span><span class="sxs-lookup"><span data-stu-id="66da0-138">Suppressing warnings locally</span></span>

<span data-ttu-id="66da0-139">Yerel olarak uyarıları gizlemek için için uyarıları bastırma ve ardından istediğiniz üyesinde sağ **hızlı Eylemler ve yapan yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **kaynağındaki**.</span><span class="sxs-lookup"><span data-stu-id="66da0-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="66da0-140">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) önişlemci yönergesi kaynak kodunuzda tanımlanan kapsam eklenen uyarı: !["Kod ekran Çerçeveli ile #pragma uyarısı devre dışı bırak"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="66da0-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="66da0-141">Uyarıları gizleme genel</span><span class="sxs-lookup"><span data-stu-id="66da0-141">Suppressing warnings globally</span></span>

<span data-ttu-id="66da0-142">Gizlemek için uyarılar için uyarıları bastırma ve ardından istediğiniz üyesinde genel olarak, sağ **hızlı Eylemler ve yapan yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **gizleme dosyasında**.</span><span class="sxs-lookup"><span data-stu-id="66da0-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Ekran WebClient API yeşil dalgalı çizgi ve ampul soldaki"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="66da0-144">A *GlobalSuppressions.cs* dosya sonra ilk gizleme projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="66da0-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="66da0-145">Yeni genel suppressions bu dosyaya eklenir.</span><span class="sxs-lookup"><span data-stu-id="66da0-145">New global suppressions are appended to this file.</span></span>

!["Ekran WebClient API yeşil dalgalı çizgi ve ampul soldaki"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="66da0-147">Genel gizleme, projeler arasında tutarlılığı API kullanımı için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="66da0-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="66da0-148">Platformlar arası sorunları bulma</span><span class="sxs-lookup"><span data-stu-id="66da0-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="66da0-149">Benzer şekilde kullanım dışı API'leri, platformlar arası olmayan tüm API'leri Çözümleyicisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66da0-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="66da0-150">Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows ancak Linux ve macOS çalışır.</span><span class="sxs-lookup"><span data-stu-id="66da0-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="66da0-151">Tanılama kimliği gösterilen **hata listesi** penceresi.</span><span class="sxs-lookup"><span data-stu-id="66da0-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="66da0-152">Sağ tıklayarak bu uyarı gizleyebilirsiniz ve seçerek **hızlı Eylemler ve yapan yeniden düzenlemeler**.</span><span class="sxs-lookup"><span data-stu-id="66da0-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="66da0-153">Burada iki seçeneğiniz kullanımdan durumlarda aksine (kullanım dışı üye kullanmaya devam et ve Uyarıları bastırma ya da hiç kullanmayabilirsiniz), burada yalnızca belirli platformlar için kodunuzu geliştiriyorsanız, diğer tüm platformlar için tüm uyarıları sizin gizleyebilirsiniz kodunuzu çalıştırmayı planlayın.</span><span class="sxs-lookup"><span data-stu-id="66da0-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="66da0-154">Bunu yapmak için proje dosyanızı düzenleyin ve eklemek yeterlidir `PlatformCompatIgnore` yok sayılacak tüm platformlar listeler özelliği.</span><span class="sxs-lookup"><span data-stu-id="66da0-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="66da0-155">Kabul edilen değerler şunlardır: `Linux`, `macOS`, ve `Windows`.</span><span class="sxs-lookup"><span data-stu-id="66da0-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="66da0-156">Kodunuzu birden çok platformu hedefleyen ve bunların bazıları üzerinde desteklenmeyen bir API yararlanmak isterseniz koduyla kısmı önleyebilirsiniz bir `if` deyimi:</span><span class="sxs-lookup"><span data-stu-id="66da0-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="66da0-157">Hedef framework ve işletim sistemi ayrıca koşullu derleyebilir, ancak şu anda, gerçekleştirmeniz gereken [el ile](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="66da0-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="66da0-158">Desteklenen tanılama</span><span class="sxs-lookup"><span data-stu-id="66da0-158">Supported diagnostics</span></span>

<span data-ttu-id="66da0-159">Şu anda Çözümleyicisi aşağıdaki durumlarda işler:</span><span class="sxs-lookup"><span data-stu-id="66da0-159">Currently, the analyzer handles the following cases:</span></span>

* <span data-ttu-id="66da0-160">Bir .NET standart oluşturur API kullanımı <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="66da0-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
* <span data-ttu-id="66da0-161">Bir .NET standart .NET Framework 4.6.1 (PC002) kullanılabilir olmayan API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="66da0-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
* <span data-ttu-id="66da0-162">UWP (PC003) mevcut olmayan yerel bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="66da0-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
* <span data-ttu-id="66da0-163">Kullanım dışı (DEXXXX) işaretlenmiş bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="66da0-163">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="66da0-164">CI makine</span><span class="sxs-lookup"><span data-stu-id="66da0-164">CI machine</span></span>

<span data-ttu-id="66da0-165">Bu tanılama yalnızca IDE'de kullanılabilir, ancak ayrıca projenizi oluşturmanın bir parçası olarak komut satırında, CI sunucunun içerir.</span><span class="sxs-lookup"><span data-stu-id="66da0-165">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="66da0-166">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="66da0-166">Configuration</span></span>

<span data-ttu-id="66da0-167">Tanılama nasıl değerlendirilmelidir kullanıcı karar: uyarılar, hatalar, öneriler olarak ya da devre dışı bırakılmış.</span><span class="sxs-lookup"><span data-stu-id="66da0-167">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="66da0-168">Örneğin, bir mimari, karar verebilirsiniz uyumluluk sorunları hata olarak ele alınması gerektiğini, diğerleri yalnızca önerileri oluşturmak karşın bazı kullanım dışı API çağrıları uyarılar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="66da0-168">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="66da0-169">Bunu ayrı olarak tanılama kimliği ve proje tarafından yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66da0-169">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="66da0-170">Bu nedenle yapmak için **Çözüm Gezgini**, gitmek **bağımlılıkları** projenizi düğümünde.</span><span class="sxs-lookup"><span data-stu-id="66da0-170">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="66da0-171">Düğümleri genişletin **bağımlılıkları** > **çözümleyiciler** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="66da0-171">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="66da0-172">Select tanılama kimliği sağ tıklayın **kural kümesi önem derecesi ayarlanmıştır** ve istediğiniz seçeneği seçin.</span><span class="sxs-lookup"><span data-stu-id="66da0-172">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Tanılama ve açılan iletişim kuralı önem derecesi ayarlanmıştır gösteren çözüm Gezgini'nin ekran"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="66da0-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66da0-174">See also</span></span>

* <span data-ttu-id="66da0-175">[API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog postası.</span><span class="sxs-lookup"><span data-stu-id="66da0-175">[Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog post.</span></span>
* <span data-ttu-id="66da0-176">[API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) gösteri video YouTube'da.</span><span class="sxs-lookup"><span data-stu-id="66da0-176">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
