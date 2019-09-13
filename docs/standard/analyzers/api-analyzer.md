---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi 'nin kullanım dışı API 'Leri ve platform uyumluluk sorunlarını algılamaya nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.author: mairaw
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 584f9f952148ebf72c5d5aaed64a2a078be00ce5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929362"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="48205-103">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="48205-103">.NET API analyzer</span></span>

<span data-ttu-id="48205-104">.NET API Çözümleyicisi, farklı platformlarda API 'ler için C# olası uyumluluk risklerini bulan ve kullanım dışı API 'leri çağrılarını algılayan bir Roslyn çözümleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="48205-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="48205-105">Herhangi bir geliştirme aşamasında tüm C# geliştiriciler için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="48205-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="48205-106">API Çözümleyicisi, [Microsoft. DotNet. çözümleyiciler. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)bir NuGet paketi olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="48205-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="48205-107">Bir projede başvurulduktan sonra kodu otomatik olarak izler ve sorunlu API kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="48205-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="48205-108">Hafif ampul ' i tıklatarak olası düzeltmeler hakkında öneriler de alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48205-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="48205-109">Açılan menü, uyarıları gösterme seçeneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="48205-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="48205-110">.NET API Çözümleyicisi, hala yayın öncesi bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="48205-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48205-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="48205-111">Prerequisites</span></span>

- <span data-ttu-id="48205-112">Visual Studio 2017 ve üzeri sürümleri veya Mac için Visual Studio (tüm sürümler).</span><span class="sxs-lookup"><span data-stu-id="48205-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="48205-113">Kullanımdan kaldırılan API 'Ler bulunuyor</span><span class="sxs-lookup"><span data-stu-id="48205-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="48205-114">Kullanımdan kaldırılan API 'Ler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="48205-114">What are deprecated APIs?</span></span>

<span data-ttu-id="48205-115">.NET ailesi, müşteri ihtiyaçlarını daha iyi karşılamak üzere sürekli olarak yükseltilen büyük ürünlerden oluşan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="48205-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="48205-116">Bazı API 'Leri kullanımdan kaldırma ve yenilerini yenisiyle değiştirme doğal bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="48205-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="48205-117">Daha iyi bir alternatif olduğunda bir API kullanım dışı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="48205-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="48205-118">Bir API 'nin kullanım dışı olduğunu ve kullanılması gerekmemesi gerektiğini bildirmek için bir yol, <xref:System.ObsoleteAttribute> özniteliği ile işaretmektir.</span><span class="sxs-lookup"><span data-stu-id="48205-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="48205-119">Bu yaklaşımın dezavantajı, artık kullanılmayan tüm API 'ler için yalnızca bir tanılama kimliği (for C#, [CS0612](../../csharp/misc/cs0612.md)) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="48205-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="48205-120">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="48205-120">This means that:</span></span>

- <span data-ttu-id="48205-121">Her durum için adanmış belgeler olması olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="48205-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="48205-122">Belirli uyarı kategorisini bastırmak imkansız olabilir.</span><span class="sxs-lookup"><span data-stu-id="48205-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="48205-123">Bunlardan hiçbirini veya hiçbirini gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48205-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="48205-124">Kullanıcıları yeni bir kullanımdan kaldırma hakkında bilgilendirmek için, başvurulan bir derleme veya hedefleme paketi güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="48205-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="48205-125">API Çözümleyicisi, tek tek uyarıların görüntülenmesi üzerinde denetime izin veren, DE (kullanımdan kaldırma hatası anlamına gelir) ile başlayan API 'ye özel hata kodları kullanır.</span><span class="sxs-lookup"><span data-stu-id="48205-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="48205-126">Çözümleyici tarafından tanımlanan kullanım dışı API 'Ler [DotNet/platform-COMPAT](https://github.com/dotnet/platform-compat) deposunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="48205-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="48205-127">API Çözümleyicisi 'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="48205-127">Using the API Analyzer</span></span>

<span data-ttu-id="48205-128"><xref:System.Net.WebClient>, Gibi kullanım dışı bırakılmış bir API bir kodda kullanıldığında, API Çözümleyicisi bunu yeşil dalgalı çizgi ile vurgular.</span><span class="sxs-lookup"><span data-stu-id="48205-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="48205-129">API çağrısının üzerine geldiğinizde, aşağıdaki örnekte olduğu gibi, API 'nin kullanımdan kaldırılması hakkında bilgiler içeren bir ampul görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="48205-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Yeşil dalgalı çizgili ve sol tarafta açık ampul içeren WebClient API ekran görüntüsü"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="48205-131">**Hata listesi** penceresinde, aşağıdaki örnekte gösterildiği gibi, kullanım dışı API başına BENZERSIZ bir kimliğe sahip uyarılar bulunur (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="48205-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

<span data-ttu-id="48205-132">!["UYARıNıN kimliğini ve açıklamasını gösteren hata listesi penceresinin ekran görüntüsü"](media/api-analyzer/warnings-id-and-descriptions.jpg "Uyarıları içeren hata listesi pencere.")</span><span class="sxs-lookup"><span data-stu-id="48205-132">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="48205-133">KIMLIĞE tıkladığınızda, API 'nin neden kullanım dışı olduğuna ilişkin ayrıntılı bilgiler ve kullanılabilecek alternatif API 'Ler ile ilgili öneriler içeren bir Web sayfasına gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48205-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="48205-134">Vurgulanan üyeye sağ tıklayıp, **Tanılama kimliğini gizle \<>** ' yi seçerek herhangi bir uyarı gizlenebilir.</span><span class="sxs-lookup"><span data-stu-id="48205-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="48205-135">Uyarıları basmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="48205-135">There are two ways to suppress warnings:</span></span> 

- [<span data-ttu-id="48205-136">Yerel olarak (kaynakta)</span><span class="sxs-lookup"><span data-stu-id="48205-136">locally (in source)</span></span>](#suppressing-warnings-locally)
- <span data-ttu-id="48205-137">[küresel olarak (bir gizleme dosyasında)](#suppressing-warnings-globally) önerilir</span><span class="sxs-lookup"><span data-stu-id="48205-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="48205-138">Uyarıları yerel olarak gizleme</span><span class="sxs-lookup"><span data-stu-id="48205-138">Suppressing warnings locally</span></span>

<span data-ttu-id="48205-139">Uyarıları yerel olarak gizlemek için uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler** >  \***Tanılama kimliği\*\<tanılama kimliğini Gizle > seçin**  >   **Kaynak içinde**.</span><span class="sxs-lookup"><span data-stu-id="48205-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="48205-140">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı ön işlemci yönergesi, tanımlanan kapsamdaki kaynak kodunuza eklenir: !["#Pragma uyarı devre dışı bırakarak çerçeveli kodun ekran görüntüsü"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="48205-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="48205-141">Uyarıları küresel olarak gizleme</span><span class="sxs-lookup"><span data-stu-id="48205-141">Suppressing warnings globally</span></span>

<span data-ttu-id="48205-142">Uyarıları küresel olarak gizlemek için uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler** >  \***Tanılama kimliği\*\<tanılama kimliğini Gizle > seçin**  >  **gizleme dosyası içinde**.</span><span class="sxs-lookup"><span data-stu-id="48205-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Yeşil dalgalı çizgili ve sol tarafta açık ampul içeren WebClient API ekran görüntüsü"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="48205-144">İlk göstermeme sonrasında projenize bir *GlobalSuppressions.cs* dosyası eklenir.</span><span class="sxs-lookup"><span data-stu-id="48205-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="48205-145">Bu dosyanın yeni genel gizlemeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="48205-145">New global suppressions are appended to this file.</span></span>

!["Yeşil dalgalı çizgili ve sol tarafta açık ampul içeren WebClient API ekran görüntüsü"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="48205-147">Genel gizleme, projeler genelinde API kullanımının tutarlılığını sağlamak için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="48205-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="48205-148">Platformlar arası sorunları keşfetme</span><span class="sxs-lookup"><span data-stu-id="48205-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="48205-149">Kullanım dışı olan API 'Lerle benzer şekilde, çözümleyici platformlar arası olmayan tüm API 'Leri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="48205-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="48205-150">Örneğin, Windows <xref:System.Console.WindowWidth?displayProperty=nameWithType> 'da, Linux ve MacOS 'ta değil, üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="48205-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="48205-151">Tanılama KIMLIĞI **hata listesi** penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="48205-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="48205-152">Sağ tıklayıp **Hızlı Eylemler ve yeniden düzenlemeler '** i seçerek bu uyarının görüntülenmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48205-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="48205-153">İki seçeneğe sahip olduğunuz kullanım dışı durumların aksine (kullanımdan kaldırılan üyeyi kullanmaya devam edin, uyarıları gizleyin veya hiç kullanmayın), burada kodunuzu yalnızca belirli platformlar için geliştiriyorsanız, tüm diğer platformlar için tüm uyarıları gizleyebilirsiniz kodunuzu üzerinde çalıştırmayı planlayın.</span><span class="sxs-lookup"><span data-stu-id="48205-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="48205-154">Bunu yapmak için yalnızca proje dosyanızı düzenlemeniz ve tüm platformları listeleyen `PlatformCompatIgnore` özelliği yok sayılacak şekilde eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="48205-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="48205-155">Kabul edilen değerler şunlardır: `Linux`, `macOS`, ve `Windows`.</span><span class="sxs-lookup"><span data-stu-id="48205-155">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="48205-156">Kodunuz birden çok platformu hedefliyorsa ve bazılarında desteklenmeyen bir API 'nin avantajlarından yararlanmak istiyorsanız kodun bu bölümünü bir `if` ifadesiyle koryükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="48205-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="48205-157">Ayrıca, hedef çerçeve/işletim sistemi için koşullu olarak derleyebilirsiniz, ancak şu anda [el ile](../frameworks.md#how-to-specify-target-frameworks)yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48205-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="48205-158">Desteklenen Tanılamalar</span><span class="sxs-lookup"><span data-stu-id="48205-158">Supported diagnostics</span></span>

<span data-ttu-id="48205-159">Şu anda, çözümleyici aşağıdaki durumları işler:</span><span class="sxs-lookup"><span data-stu-id="48205-159">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="48205-160"><xref:System.PlatformNotSupportedException> (PC001) oluşturan .NET Standard API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="48205-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="48205-161">.NET Framework 4.6.1 (PC002) üzerinde kullanılamayan bir .NET Standard API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="48205-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="48205-162">UWP 'de mevcut olmayan bir yerel API kullanımı (PC003).</span><span class="sxs-lookup"><span data-stu-id="48205-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="48205-163">Delegate. BeginInvoke ve EndInvoke API 'Leri (PC004) kullanımı.</span><span class="sxs-lookup"><span data-stu-id="48205-163">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="48205-164">Kullanım dışı (DEXXXX) olarak işaretlenen bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="48205-164">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="48205-165">CI makinesi</span><span class="sxs-lookup"><span data-stu-id="48205-165">CI machine</span></span>

<span data-ttu-id="48205-166">Tüm bu Tanılamalar yalnızca IDE 'de değil, aynı zamanda, CI sunucusunu içeren projenizi oluşturmanın bir parçası olarak komut satırında de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="48205-166">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="48205-167">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="48205-167">Configuration</span></span>

<span data-ttu-id="48205-168">Kullanıcı, tanılama nasıl ele alınacağına karar verir: uyarılar, hatalar, öneriler veya kapatılacak.</span><span class="sxs-lookup"><span data-stu-id="48205-168">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="48205-169">Örneğin, bir mimari olarak uyumluluk sorunlarının hata olarak değerlendirilip bazı kullanım dışı API 'lere yapılan çağrılar uyarı üretirken, diğerleri yalnızca öneriler üretmeye karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48205-169">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="48205-170">Bunu, tanılama KIMLIĞI ve proje tarafından ayrı ayrı yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48205-170">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="48205-171">**Çözüm Gezgini**için, projenizin altındaki **Bağımlılıklar** düğümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="48205-171">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="48205-172">**Microsoft. DotNet. çözümleyiciler. uyumluluğu** **çözümleyicilerinin** > düğümleri **bağımlılıklarını** > genişletin.</span><span class="sxs-lookup"><span data-stu-id="48205-172">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="48205-173">Tanılama KIMLIĞI ' ne sağ tıklayın, **kural kümesi önem derecesini ayarla** ' yı seçin ve istediğiniz seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="48205-173">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Kural kümesi önem derecesine sahip tanılama ve açılır iletişim iletişimini gösteren Çözüm Gezgini ekran görüntüsü"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="48205-175">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48205-175">See also</span></span>

- <span data-ttu-id="48205-176">[API Çözümleyicisi blog gönderisine giriş](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .</span><span class="sxs-lookup"><span data-stu-id="48205-176">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="48205-177">YouTube 'da [API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) tanıtım videosu.</span><span class="sxs-lookup"><span data-stu-id="48205-177">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
