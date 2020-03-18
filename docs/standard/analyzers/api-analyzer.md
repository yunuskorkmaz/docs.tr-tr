---
title: .NET API çözümleyicisi
description: .NET API Çözümleyicisinin amortismana alınan API'leri ve platform uyumluluk sorunlarını algılamaya nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: e214c91f2beebc7f3b3324f4879deba9a5623f86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156140"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="495ac-103">.NET API çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="495ac-103">.NET API analyzer</span></span>

<span data-ttu-id="495ac-104">.NET API Çözümleyicisi, farklı platformlarda C# API'leri için olası uyumluluk risklerini keşfeden ve amortismana alınan API'lere yönelik çağrıları algılayan bir Roslyn çözümleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="495ac-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="495ac-105">Geliştirmenin herhangi bir aşamasında tüm C# geliştiricileri için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="495ac-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="495ac-106">API Analyzer bir NuGet paketi [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="495ac-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="495ac-107">Bir projede başvuruyaptıktan sonra, kodu otomatik olarak izler ve sorunlu API kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="495ac-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="495ac-108">Ayrıca ampul tıklayarak olası düzeltmeleri hakkında öneriler alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="495ac-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="495ac-109">Açılır menü, uyarıları bastırmak için bir seçenek içerir.</span><span class="sxs-lookup"><span data-stu-id="495ac-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="495ac-110">.NET API çözümleyicisi hala bir ön sürüm sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="495ac-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="495ac-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="495ac-111">Prerequisites</span></span>

- <span data-ttu-id="495ac-112">Visual Studio 2017 ve sonraki sürümleri veya Mac için Visual Studio (tüm sürümler).</span><span class="sxs-lookup"><span data-stu-id="495ac-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discover-deprecated-apis"></a><span data-ttu-id="495ac-113">Amortismana kılan API'leri keşfedin</span><span class="sxs-lookup"><span data-stu-id="495ac-113">Discover deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="495ac-114">Amortismana uğran API'ler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="495ac-114">What are deprecated APIs?</span></span>

<span data-ttu-id="495ac-115">.NET ailesi, müşteri ihtiyaçlarına daha iyi hizmet vermek üzere sürekli olarak yükseltilen bir dizi büyük üründür.</span><span class="sxs-lookup"><span data-stu-id="495ac-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="495ac-116">Bazı API'leri amortismana tabi tarayıp yenileriyle değiştirmek doğaldır.</span><span class="sxs-lookup"><span data-stu-id="495ac-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="495ac-117">Daha iyi bir alternatif olduğunda API'nin amortismana ermiş olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="495ac-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="495ac-118">Bir API'nin amortismana erdiğini ve kullanılmaması gerektiğini bildirmenin <xref:System.ObsoleteAttribute> bir yolu, bu özelliği öznitelikle işaretlemektir.</span><span class="sxs-lookup"><span data-stu-id="495ac-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="495ac-119">Bu yaklaşımın dezavantajı, tüm eski API'ler için tek bir tanılama kimliği olmasıdır (C#, [CS0612](../../csharp/misc/cs0612.md)için).</span><span class="sxs-lookup"><span data-stu-id="495ac-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="495ac-120">Bu şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="495ac-120">This means that:</span></span>

- <span data-ttu-id="495ac-121">Her dava için özel belgelere sahip olmak imkansız.</span><span class="sxs-lookup"><span data-stu-id="495ac-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="495ac-122">Belirli uyarı kategorilerini bastırmak imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="495ac-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="495ac-123">Hepsini ya da hiçbirini bastırabilirsin.</span><span class="sxs-lookup"><span data-stu-id="495ac-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="495ac-124">Kullanıcıları yeni bir amortisman konusunda bilgilendirmek için, başvurulan bir derleme veya hedefleme paketinin güncellenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="495ac-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="495ac-125">API Analyzer, tek tek uyarıların görüntülenmesi üzerinde denetim sağlayan DE (Amortisman Hatası anlamına gelir) ile başlayan API'ye özgü hata kodları kullanır.</span><span class="sxs-lookup"><span data-stu-id="495ac-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="495ac-126">Çözümleyici tarafından tanımlanan amortismana lı API'ler [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo'da tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="495ac-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="add-the-api-analyzer-to-your-project"></a><span data-ttu-id="495ac-127">PROJENIZE API Çözümleyicisi ekleme</span><span class="sxs-lookup"><span data-stu-id="495ac-127">Add the API Analyzer to your project</span></span>

1. <span data-ttu-id="495ac-128">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="495ac-128">Open Visual Studio.</span></span>
2. <span data-ttu-id="495ac-129">Çözümleyiciyi çalıştırmak istediğiniz projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="495ac-129">Open the project you want to run the analyzer on.</span></span>
3. <span data-ttu-id="495ac-130">**Solution**Explorer'da, projenize sağ tıklayın ve **NuGet Paketlerini Yönet'i**seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-130">In **Solution Explorer**, right-click on your project and choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="495ac-131">(Bu seçenek **Proje** menüsünden de kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="495ac-131">(This option is also available from the **Project** menu.)</span></span>
4. <span data-ttu-id="495ac-132">NuGet Paket Yöneticisi sekmesinde:</span><span class="sxs-lookup"><span data-stu-id="495ac-132">On the NuGet Package Manager tab:</span></span>
   1. <span data-ttu-id="495ac-133">Paket kaynağı olarak "nuget.org" seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="495ac-133">Select "nuget.org" as the Package source.</span></span>
   2. <span data-ttu-id="495ac-134">**Gözat** sekmesine gidin.</span><span class="sxs-lookup"><span data-stu-id="495ac-134">Go to the **Browse** tab.</span></span>
   3. <span data-ttu-id="495ac-135">**Ön sürüm ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-135">Select **Include prerelease**.</span></span>
   4. <span data-ttu-id="495ac-136">**Microsoft.DotNet.Analyzers.Compatibility**için arama .</span><span class="sxs-lookup"><span data-stu-id="495ac-136">Search for **Microsoft.DotNet.Analyzers.Compatibility**.</span></span>
   5. <span data-ttu-id="495ac-137">Listedeki paketi seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-137">Select that package in the list.</span></span>
   6. <span data-ttu-id="495ac-138">**Yükle** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-138">Select the **Install** button.</span></span>
   7. <span data-ttu-id="495ac-139">**Değişiklikler Önizleme** iletişim kutusundaki **Tamam** düğmesini seçin ve listelenen paketlerin lisans koşullarını kabul ederseniz Lisans Kabul iletişim kutusundaki **Kabul** **Et** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="use-the-api-analyzer"></a><span data-ttu-id="495ac-140">API Çözümleyicisini Kullanma</span><span class="sxs-lookup"><span data-stu-id="495ac-140">Use the API Analyzer</span></span>

<span data-ttu-id="495ac-141">Bir kodda , bir kodda, amortismana uygun bir API <xref:System.Net.WebClient>kullanıldığında, API Çözümleyici squiggly satırı ile vurgular.</span><span class="sxs-lookup"><span data-stu-id="495ac-141">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="495ac-142">API çağrısının üzerinde gezinirken, aşağıdaki örnekte olduğu gibi, API amortismanı hakkında bilgi içeren bir ampul görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="495ac-142">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Soldaki yeşil kıvrımlı çizgi ve ampul ile WebClient API Ekran Görüntüsü"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="495ac-144">**Hata Listesi** penceresi, aşağıdaki örnekte gösterildiği gibi, amortismana alınan API`DE004`başına benzersiz bir kimlik içeren uyarılar içerir : :</span><span class="sxs-lookup"><span data-stu-id="495ac-144">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span>

<span data-ttu-id="495ac-145">!["Uyarının kimliğini ve açıklamasını gösteren Hata Listesi penceresinin ekran görüntüsü"](media/api-analyzer/warnings-id-and-descriptions.jpg "Uyarıları içeren Hata Listesi penceresi.")</span><span class="sxs-lookup"><span data-stu-id="495ac-145">!["Screenshot of the Error List window showing warning's ID and description"](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="495ac-146">Kimliği tıklayarak, API'nin neden küçümsendiğini ve kullanılabilen alternatif API'lerle ilgili önerileri içeren ayrıntılı bilgileri içeren bir web sayfasına gidersiniz.</span><span class="sxs-lookup"><span data-stu-id="495ac-146">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="495ac-147">Herhangi bir uyarı, vurgulanan üyeye sağ tıklayarak ve \*\* \<tanıtanı Kimliğini>Bastır'ı \*\*seçerek bastırılabilir.</span><span class="sxs-lookup"><span data-stu-id="495ac-147">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="495ac-148">Uyarıları bastırmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="495ac-148">There are two ways to suppress warnings:</span></span>

- [<span data-ttu-id="495ac-149">yerel (kaynakta)</span><span class="sxs-lookup"><span data-stu-id="495ac-149">locally (in source)</span></span>](#suppress-warnings-locally)
- <span data-ttu-id="495ac-150">[küresel olarak (bir bastırma dosyasında)](#suppress-warnings-globally) - önerilen</span><span class="sxs-lookup"><span data-stu-id="495ac-150">[globally (in a suppression file)](#suppress-warnings-globally) - recommended</span></span>

### <a name="suppress-warnings-locally"></a><span data-ttu-id="495ac-151">Uyarıları yerel olarak bastırma</span><span class="sxs-lookup"><span data-stu-id="495ac-151">Suppress warnings locally</span></span>

<span data-ttu-id="495ac-152">Uyarıları yerel olarak bastırmak için, uyarıları bastırmak istediğiniz üyeye sağ tıklayın ve ardından **Hızlı Eylemler ve Yeniden Faktörler'i** > seçin\*\* *Tanılama Kimliği Tanılama Kimliği'ni*\< \*\* **Kaynak'ta**> > bastırın.</span><span class="sxs-lookup"><span data-stu-id="495ac-152">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="495ac-153">[#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı önişlemci yönergesi tanımlanan kapsamda kaynak ![kodunuza eklenir: "#pragma uyarı devre dışı atılabilir" ile çerçevelenmiş kodun ekran görüntüsü](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="495ac-153">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppress-warnings-globally"></a><span data-ttu-id="495ac-154">Uyarıları genel olarak bastırma</span><span class="sxs-lookup"><span data-stu-id="495ac-154">Suppress warnings globally</span></span>

<span data-ttu-id="495ac-155">Uyarıları genel olarak bastırmak için, uyarıları bastırmak istediğiniz üyeye sağ tıklayın ve ardından **Hızlı Eylemler ve Yeniden Faktörler** >  \**bastırma dosyasında\*\*\*\*tanılama kimliği\<>*diagnostic ID\* \*\*  > bastırın'ı seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-155">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Soldaki yeşil kıvrımlı çizgi ve ampul ile WebClient API Ekran Görüntüsü"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="495ac-157">İlk bastırmadan sonra projenize *GlobalSuppressions.cs* bir dosya eklenir.</span><span class="sxs-lookup"><span data-stu-id="495ac-157">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="495ac-158">Bu dosyaya yeni genel bastırmalar eklenir.</span><span class="sxs-lookup"><span data-stu-id="495ac-158">New global suppressions are appended to this file.</span></span>

!["Soldaki yeşil kıvrımlı çizgi ve ampul ile WebClient API Ekran Görüntüsü"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="495ac-160">Küresel bastırma, PROJELER ARASıNDA API kullanımının tutarlılığını sağlamanın önerilen yoludur.</span><span class="sxs-lookup"><span data-stu-id="495ac-160">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discover-cross-platform-issues"></a><span data-ttu-id="495ac-161">Platformlar arası sorunları keşfedin</span><span class="sxs-lookup"><span data-stu-id="495ac-161">Discover cross-platform issues</span></span>

<span data-ttu-id="495ac-162">Amortismana yenik amorti edilen API'lere benzer şekilde, çözümleyici çapraz platform olmayan tüm API'leri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="495ac-162">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="495ac-163">Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows'da çalışır, ancak Linux ve macOS'ta çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="495ac-163">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="495ac-164">Tanılama kimliği Hata **Listesi** penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="495ac-164">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="495ac-165">Hızlı Eylemler ve **Yeniden Düzenleme'yi**sağ tıklayarak ve seçerek bu uyarıyı bastırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="495ac-165">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="495ac-166">İki seçeneğiniz olan (ya azalan üyeyi kullanmaya devam edin ve uyarıları bastırmaya devam edin ya da hiç kullanmadıysanız), burada kodunuzu yalnızca belirli platformlar için geliştiriyorsanız, olmadığınız diğer tüm platformlar için tüm uyarıları bastırabilirsiniz kodunuzu çalıştırmayı planlayın.</span><span class="sxs-lookup"><span data-stu-id="495ac-166">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="495ac-167">Bunu yapmak için proje dosyanızı düzenlemesi ve göz `PlatformCompatIgnore` ardı edilecek tüm platformları listeleyen özelliği eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="495ac-167">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="495ac-168">Kabul edilen değerler `Linux`şunlardır: , `macOS`, ve `Windows`.</span><span class="sxs-lookup"><span data-stu-id="495ac-168">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="495ac-169">Kodunuz birden çok platformu hedefliyorsa ve bazılarında desteklenmeyen bir API'den yararlanmak istiyorsanız, `if` kodun bu bölümünü bir deyimle koruyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="495ac-169">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="495ac-170">Ayrıca, hedef çerçevesi/işletim sistemi başına koşullu olarak derleyebilirsiniz, ancak şu anda bunu [el ile](../frameworks.md#how-to-specify-target-frameworks)yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="495ac-170">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="495ac-171">Desteklenen tanılama</span><span class="sxs-lookup"><span data-stu-id="495ac-171">Supported diagnostics</span></span>

<span data-ttu-id="495ac-172">Şu anda, çözümleyici aşağıdaki durumlarda işler:</span><span class="sxs-lookup"><span data-stu-id="495ac-172">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="495ac-173">Bir .NET Standart API kullanımı <xref:System.PlatformNotSupportedException> atar (PC001).</span><span class="sxs-lookup"><span data-stu-id="495ac-173">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="495ac-174">.NET Framework 4.6.1 (PC002) üzerinde bulunmayan bir .NET Standart API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="495ac-174">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="495ac-175">UWP(PC003) bulunmayan yerel bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="495ac-175">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
- <span data-ttu-id="495ac-176">Delegate.BeginInvoke ve EndInvoke API'lerinin (PC004) kullanımı.</span><span class="sxs-lookup"><span data-stu-id="495ac-176">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="495ac-177">Amortismana (DEXXXX) olarak işaretlenmiş bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="495ac-177">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="495ac-178">CI makinesi</span><span class="sxs-lookup"><span data-stu-id="495ac-178">CI machine</span></span>

<span data-ttu-id="495ac-179">Tüm bu tanılama, ci sunucuyu içeren projenizi oluşturmanın bir parçası olarak yalnızca IDE'de değil, komut satırında da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="495ac-179">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="495ac-180">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="495ac-180">Configuration</span></span>

<span data-ttu-id="495ac-181">Kullanıcı tanılamanın nasıl ele alınması gerektiğine karar verir: uyarılar, hatalar, öneriler veya kapatılacak gibi.</span><span class="sxs-lookup"><span data-stu-id="495ac-181">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="495ac-182">Örneğin, bir mimar olarak uyumluluk sorunlarının hata olarak ele alınmasına karar verebilirsiniz, bazı amortismana alınan API'lere yapılan çağrılar uyarılar oluştururken, diğerleri yalnızca öneriler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="495ac-182">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="495ac-183">Bunu tanılama kimliği ve proje ile ayrı ayrı yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="495ac-183">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="495ac-184">**Çözüm Gezgini'nde**bunu yapmak için projenizaltındaki **Bağımlılıklar** düğümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="495ac-184">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="495ac-185">Düğümleri Genişlet **Bağımlılıklar** > **Çözümleyiciler** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="495ac-185">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="495ac-186">Tanılama kimliğine sağ tıklayın, **Kural Kümesi Önem Ayarını seçin** ve istediğiniz seçeneği seçin.</span><span class="sxs-lookup"><span data-stu-id="495ac-186">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Çözüm Gezgini'nin Kural Kümesi Önem Derecesi ile tanılama ve açılır iletişim kutusunu gösteren ekran görüntüsü"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="495ac-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="495ac-188">See also</span></span>

- <span data-ttu-id="495ac-189">[API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog yazısı tanıtımı.</span><span class="sxs-lookup"><span data-stu-id="495ac-189">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="495ac-190">[YouTube'da API Analyzer](https://youtu.be/eeBEahYXGd0) demo video.</span><span class="sxs-lookup"><span data-stu-id="495ac-190">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
