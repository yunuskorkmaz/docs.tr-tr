---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi kullanım dışı API ve platform uyumluluğu sorunları algılayın nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.author: mairaw
ms.date: 05/31/2018
ms.technology: dotnet-standard
ms.openlocfilehash: d27e5299ad9b1a3dcd89d5a947d91f06a54549e2
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759138"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="35c93-103">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="35c93-103">.NET API analyzer</span></span>

<span data-ttu-id="35c93-104">.NET API Çözümleyicisi olası uyumluluk risk bulduğu Roslyn çözümleyicinizi olduğu C# farklı platformlarda API'leri ve kullanım dışı API'lere giden çağrıların algılar.</span><span class="sxs-lookup"><span data-stu-id="35c93-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="35c93-105">Tüm kullanıcılar için yararlı olabilir C# geliştiriciler geliştirme herhangi bir aşamasında.</span><span class="sxs-lookup"><span data-stu-id="35c93-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="35c93-106">API Çözümleyicisi bir NuGet paketi olarak gelir [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="35c93-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="35c93-107">Bir proje başvurusu sonra otomatik olarak kod izler ve sorunlu API kullanımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="35c93-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="35c93-108">Ampul üzerinde tıklayarak üzerinde olası düzeltmeleri önerileri de sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35c93-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="35c93-109">Aşağı açılan menüyü uyarıları bastırmak için bir seçenek içerir.</span><span class="sxs-lookup"><span data-stu-id="35c93-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="35c93-110">.NET API Çözümleyicisi hala bir yayın öncesi sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="35c93-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="35c93-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="35c93-111">Prerequisites</span></span>

* <span data-ttu-id="35c93-112">Visual Studio 2017 veya Visual Studio için Mac (tüm sürümler).</span><span class="sxs-lookup"><span data-stu-id="35c93-112">Visual Studio 2017 or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="35c93-113">Kullanım dışı API'lerini keşfetme</span><span class="sxs-lookup"><span data-stu-id="35c93-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="35c93-114">Hangi API'leri kullanım dışı?</span><span class="sxs-lookup"><span data-stu-id="35c93-114">What are deprecated APIs?</span></span>

<span data-ttu-id="35c93-115">.NET ailesi, sürekli daha iyi müşteri gereksinimlerini karşılamak için yükseltilen büyük ürünleri kümesidir.</span><span class="sxs-lookup"><span data-stu-id="35c93-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="35c93-116">Bazı API'leri kullanımdan kaldırma ve bunları yenileriyle değiştirme doğaldır.</span><span class="sxs-lookup"><span data-stu-id="35c93-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="35c93-117">Bir API, daha iyi bir alternatif varsa, kullanım dışı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="35c93-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="35c93-118">Bir API kullanım dışıdır ve kullanılmamalıdır bildiren bir yoludur kendisiyle işaretlemek için <xref:System.ObsoleteAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="35c93-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="35c93-119">Bu yaklaşımın bir dezavantajı, tüm eski API'ler için yalnızca bir tanılama kimliği olduğundan emin olup (için C#, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="35c93-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="35c93-120">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="35c93-120">This means that:</span></span>
- <span data-ttu-id="35c93-121">Her çalışması için belgelerin adanmış mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="35c93-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="35c93-122">Belirli kategori uyarıları bastırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="35c93-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="35c93-123">Tüm veya bunların hiçbiri gösterilmemesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35c93-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="35c93-124">Yeni bir kullanımdan kaldırılma kullanıcılara bildirmek için başvurulan bir derleme veya paket hedef güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="35c93-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="35c93-125">API Çözümleyicisi, tek tek uyarılar görünümünü denetime izin veren (hangi için kullanımdan kaldırma hatası anlamına gelir) DE ile başlayan API özgü hata kodları kullanır.</span><span class="sxs-lookup"><span data-stu-id="35c93-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="35c93-126">Kaldırılmış API'ler çözümleyici tarafından tanımlanan tanımlanan [platform/dotnet-compat](https://github.com/dotnet/platform-compat) depo.</span><span class="sxs-lookup"><span data-stu-id="35c93-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="35c93-127">API Çözümleyicisi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="35c93-127">Using the API Analyzer</span></span>

<span data-ttu-id="35c93-128">Kullanım dışı API, aşağıdakiler gibi <xref:System.Net.WebClient>, kullanılan bir kod içeren bir yeşil dalgalı satırı vurgular API Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="35c93-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="35c93-129">API çağrılarında geldiğinizde, aşağıdaki örnekte olduğu gibi API kullanımdan kaldırma hakkında bilgi içeren bir ampul görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="35c93-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Ekran, WebClient API'SİYLE yeşil dalgalı çizgi ve ampul sol taraftaki"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="35c93-131">**Hata listesi** penceresi, aşağıdaki örnekte gösterildiği gibi uyarılarla kullanım dışı API başına benzersiz bir kimlik içerir (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="35c93-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

!["Hata listesi penceresine uyarı'nın kimlik ve açıklama gösteren ekran görüntüsü"](media/api-analyzer/warnings.jpg)

<span data-ttu-id="35c93-133">Kimliğinde tıklayarak, API'nin neden kullanım dışı bırakıldı hakkında ayrıntılı bilgi ile bir Web sayfasına gidin ve kullanılabilecek diğer API'ler ile ilgili öneriler.</span><span class="sxs-lookup"><span data-stu-id="35c93-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="35c93-134">Tüm uyarılar vurgulanan üyesinde sağ tıklatıp seçerek gizlenebilir **bastır \<tanılama kimliği >**.</span><span class="sxs-lookup"><span data-stu-id="35c93-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="35c93-135">Uyarıları bastırmak için iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="35c93-135">There are two ways to suppress warnings:</span></span> 

* [<span data-ttu-id="35c93-136">yerel olarak (kaynak)</span><span class="sxs-lookup"><span data-stu-id="35c93-136">locally (in source)</span></span>](#suppressing-warnings-locally)
* <span data-ttu-id="35c93-137">[Genel (içinde bir gizleme dosyası)](#suppressing-warnings-globally) - önerilen</span><span class="sxs-lookup"><span data-stu-id="35c93-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="35c93-138">Yerel olarak uyarıları gizleme</span><span class="sxs-lookup"><span data-stu-id="35c93-138">Suppressing warnings locally</span></span>

<span data-ttu-id="35c93-139">Yerel olarak uyarıları bastırmak için için uyarıları gösterme ve ardından istediğiniz üyesinde sağ **hızlı Eylemler ve yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **kaynağındaki**.</span><span class="sxs-lookup"><span data-stu-id="35c93-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="35c93-140">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı önişlemci yönergesi, tanımlanan kapsam içinde kaynak kodunuza eklenir: !["Kod #pragma uyarı ile Çerçeveli ekran devre dışı bırak"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="35c93-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="35c93-141">Uyarıları gizleme genel</span><span class="sxs-lookup"><span data-stu-id="35c93-141">Suppressing warnings globally</span></span>

<span data-ttu-id="35c93-142">Bastırmak için uyarıları genel olarak, sağ için uyarıları gösterme ve ardından istediğiniz üyesinde **hızlı Eylemler ve yeniden düzenlemeler** > **bastır *tanılama kimliği* \<tanılama kimliği >** > **gizleme dosyasında**.</span><span class="sxs-lookup"><span data-stu-id="35c93-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Ekran, WebClient API'SİYLE yeşil dalgalı çizgi ve ampul sol taraftaki"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="35c93-144">A *GlobalSuppressions.cs* sonra ilk gizleme dosyası projenize eklenir.</span><span class="sxs-lookup"><span data-stu-id="35c93-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="35c93-145">Yeni genel gizlemeleri bu dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="35c93-145">New global suppressions are appended to this file.</span></span>

!["Ekran, WebClient API'SİYLE yeşil dalgalı çizgi ve ampul sol taraftaki"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="35c93-147">Genel gizlemeyi API kullanımı projeler arasında tutarlılığı için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="35c93-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="35c93-148">Platformlar arası sorunları bulma</span><span class="sxs-lookup"><span data-stu-id="35c93-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="35c93-149">Benzer şekilde kullanımdan kaldırılan API'leri, platformlar arası olmayan tüm API'leri Çözümleyicisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="35c93-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="35c93-150">Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows ancak Linux ve macOS üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="35c93-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="35c93-151">Tanılama kimliği gösterilen **hata listesi** penceresi.</span><span class="sxs-lookup"><span data-stu-id="35c93-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="35c93-152">Sağ tıklayarak bu uyarının gösterilmemesi tıklayıp **hızlı Eylemler ve yeniden düzenlemeler**.</span><span class="sxs-lookup"><span data-stu-id="35c93-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="35c93-153">İki seçenek olduğu kullanımdan kaldırma çalışmaları aksine (kullanım dışı üye kullanmaya devam edebilirsiniz ve Uyarıları bastırma ya da hiç kullanmayabilirsiniz), burada yalnızca belirli platformlar için kodunuzu geliştiriyorsanız, diğer tüm platformlar için tüm uyarıları sizin gösterilmemesini sağlayabilirsiniz kodunuzu çalıştırmayı planlayın.</span><span class="sxs-lookup"><span data-stu-id="35c93-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="35c93-154">Bunu yapmak için proje dosyanızı düzenlemeniz ve eklemeniz yeterlidir `PlatformCompatIgnore` yok sayılacak tüm platformları listeler özelliği.</span><span class="sxs-lookup"><span data-stu-id="35c93-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="35c93-155">Kabul edilen değerler şunlardır: `Linux`, `macOS`, ve `Windows`.</span><span class="sxs-lookup"><span data-stu-id="35c93-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="35c93-156">Kodunuzun birden çok platformu hedefleyen ve bunlardan bazıları üzerinde desteklenmeyen API yararlanmak istiyorsanız kodu ile bu bölümü önleyebilirsiniz bir `if` deyimi:</span><span class="sxs-lookup"><span data-stu-id="35c93-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="35c93-157">Hedef framework ve işletim sistemi da koşullu olarak derleyebilirsiniz, ancak şu anda, gerçekleştirmeniz gereken [el ile](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="35c93-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="35c93-158">Desteklenen tanılama</span><span class="sxs-lookup"><span data-stu-id="35c93-158">Supported diagnostics</span></span>

<span data-ttu-id="35c93-159">Şu anda Çözümleyicisi aşağıdaki durumlarda işler:</span><span class="sxs-lookup"><span data-stu-id="35c93-159">Currently, the analyzer handles the following cases:</span></span>

* <span data-ttu-id="35c93-160">.NET Standard oluşturan API'si kullanımı <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="35c93-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
* <span data-ttu-id="35c93-161">Bir .NET standart .NET Framework 4.6.1 (PC002) üzerinde bulunmayan API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="35c93-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
* <span data-ttu-id="35c93-162">UWP (PC003) mevcut olmayan bir yerel API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="35c93-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
* <span data-ttu-id="35c93-163">Kullanım dışı (DEXXXX) işaretlenmiş bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="35c93-163">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="35c93-164">CI makine</span><span class="sxs-lookup"><span data-stu-id="35c93-164">CI machine</span></span>

<span data-ttu-id="35c93-165">Bu tanılama yalnızca IDE içinde kullanılabilir, ancak ayrıca CI sunucu içeren projenizi oluşturma işleminin parçası olarak komut satırında.</span><span class="sxs-lookup"><span data-stu-id="35c93-165">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="35c93-166">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="35c93-166">Configuration</span></span>

<span data-ttu-id="35c93-167">Kullanıcı tanılama nasıl işleneceğini karar: uyarıları, hataları, önerileri olarak ya da devre dışı.</span><span class="sxs-lookup"><span data-stu-id="35c93-167">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="35c93-168">Örneğin, bir mimari, karar verebilirsiniz uyumluluk sorunları hata olarak işlem görecek, diğerleri yalnızca önerileri oluşturmak uyarıları, kullanım dışı bazı API'lere giden çağrıların oluşturmanız.</span><span class="sxs-lookup"><span data-stu-id="35c93-168">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="35c93-169">Bunu ayrı olarak tanılama kimliği ve proje göre yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35c93-169">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="35c93-170">Bu nedenle yapmak için **Çözüm Gezgini**, gitmek **bağımlılıkları** projenizi düğümünde.</span><span class="sxs-lookup"><span data-stu-id="35c93-170">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="35c93-171">Düğümleri genişletin **bağımlılıkları** > **Çözümleyicileri** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="35c93-171">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="35c93-172">Select tanılama kimliği sağ tıklayın **kural kümesi önem derecesini ayarlayın** ve istediğiniz seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="35c93-172">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Tanılama ve açılır iletişim kutusu ile kural kümesi önem derecesi gösteren çözüm Gezgini'nin ekran görüntüsü"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="35c93-174">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35c93-174">See also</span></span>

- <span data-ttu-id="35c93-175">[API Çözümleyicisi](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog gönderisi.</span><span class="sxs-lookup"><span data-stu-id="35c93-175">[Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="35c93-176">[API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) tanıtım YouTube video.</span><span class="sxs-lookup"><span data-stu-id="35c93-176">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
