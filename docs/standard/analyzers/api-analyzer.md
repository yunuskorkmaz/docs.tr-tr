---
title: .NET API Çözümleyicisi
description: .NET API Çözümleyicisi 'nin kullanım dışı API 'Leri ve platform uyumluluk sorunlarını algılamaya nasıl yardımcı olabileceğini öğrenin.
author: oliag
ms.date: 02/20/2020
ms.technology: dotnet-standard
ms.openlocfilehash: a689ae347efbc8c2dd933b2f6920ac6cc06cda7d
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756201"
---
# <a name="net-api-analyzer"></a><span data-ttu-id="af79e-103">.NET API Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="af79e-103">.NET API analyzer</span></span>

<span data-ttu-id="af79e-104">.NET API Çözümleyicisi, farklı platformlarda C# API 'Leri için olası uyumluluk risklerini bulan ve kullanım dışı API 'leri çağrılarını algılayan bir Roslyn çözümleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="af79e-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="af79e-105">Tüm geliştirme aşamalarında tüm C# geliştiricileri için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="af79e-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="af79e-106">API Çözümleyicisi, [Microsoft. DotNet. çözümleyiciler. Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/)bir NuGet paketi olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="af79e-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="af79e-107">Bir projede başvurulduktan sonra kodu otomatik olarak izler ve sorunlu API kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af79e-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="af79e-108">Hafif ampul ' i tıklatarak olası düzeltmeler hakkında öneriler de alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="af79e-109">Açılan menü, uyarıları gösterme seçeneğini içerir.</span><span class="sxs-lookup"><span data-stu-id="af79e-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="af79e-110">.NET API Çözümleyicisi, hala yayın öncesi bir sürümdür.</span><span class="sxs-lookup"><span data-stu-id="af79e-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="af79e-111">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="af79e-111">Prerequisites</span></span>

- <span data-ttu-id="af79e-112">Visual Studio 2017 ve üzeri sürümleri veya Mac için Visual Studio (tüm sürümler).</span><span class="sxs-lookup"><span data-stu-id="af79e-112">Visual Studio 2017 and later versions, or Visual Studio for Mac (all versions).</span></span>

## <a name="discover-deprecated-apis"></a><span data-ttu-id="af79e-113">Kullanımdan kaldırılan API 'Leri bul</span><span class="sxs-lookup"><span data-stu-id="af79e-113">Discover deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="af79e-114">Kullanımdan kaldırılan API 'Ler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="af79e-114">What are deprecated APIs?</span></span>

<span data-ttu-id="af79e-115">.NET ailesi, müşteri ihtiyaçlarını daha iyi karşılamak üzere sürekli olarak yükseltilen büyük ürünlerden oluşan bir kümesidir.</span><span class="sxs-lookup"><span data-stu-id="af79e-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="af79e-116">Bazı API 'Leri kullanımdan kaldırma ve yenilerini yenisiyle değiştirme doğal bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="af79e-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="af79e-117">Daha iyi bir alternatif olduğunda bir API kullanım dışı olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="af79e-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="af79e-118">Bir API 'nin kullanım dışı olduğunu ve kullanılması gerekmemesi gerektiğini bildirmek için bir yol, özniteliği ile işaretmektir <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="af79e-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="af79e-119">Bu yaklaşımın dezavantajı, artık kullanılmayan tüm API 'Ler için yalnızca bir tanılama KIMLIĞI (C#, [CS0612](../../csharp/misc/cs0612.md)için) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="af79e-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="af79e-120">Bunun anlamı:</span><span class="sxs-lookup"><span data-stu-id="af79e-120">This means that:</span></span>

- <span data-ttu-id="af79e-121">Her durum için adanmış belgeler olması olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="af79e-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="af79e-122">Belirli uyarı kategorisini bastırmak imkansız olabilir.</span><span class="sxs-lookup"><span data-stu-id="af79e-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="af79e-123">Bunlardan hiçbirini veya hiçbirini gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="af79e-124">Kullanıcıları yeni bir kullanımdan kaldırma hakkında bilgilendirmek için, başvurulan bir derleme veya hedefleme paketi güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="af79e-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="af79e-125">API Çözümleyicisi, tek tek uyarıların görüntülenmesi üzerinde denetime izin veren, DE (kullanımdan kaldırma hatası anlamına gelir) ile başlayan API 'ye özel hata kodları kullanır.</span><span class="sxs-lookup"><span data-stu-id="af79e-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="af79e-126">Çözümleyici tarafından tanımlanan kullanım dışı API 'Ler [DotNet/platform-COMPAT](https://github.com/dotnet/platform-compat) deposunda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="af79e-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="add-the-api-analyzer-to-your-project"></a><span data-ttu-id="af79e-127">Projenize API Çözümleyicisi ekleme</span><span class="sxs-lookup"><span data-stu-id="af79e-127">Add the API Analyzer to your project</span></span>

1. <span data-ttu-id="af79e-128">Visual Studio'yu açın.</span><span class="sxs-lookup"><span data-stu-id="af79e-128">Open Visual Studio.</span></span>
2. <span data-ttu-id="af79e-129">Çözümleyiciyi çalıştırmak istediğiniz projeyi açın.</span><span class="sxs-lookup"><span data-stu-id="af79e-129">Open the project you want to run the analyzer on.</span></span>
3. <span data-ttu-id="af79e-130">**Çözüm Gezgini**, projenize sağ tıklayın ve **NuGet Paketlerini Yönet**' i seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-130">In **Solution Explorer**, right-click on your project and choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="af79e-131">(Bu seçenek, **Proje** menüsünden de kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="af79e-131">(This option is also available from the **Project** menu.)</span></span>
4. <span data-ttu-id="af79e-132">NuGet Paket Yöneticisi sekmesinde:</span><span class="sxs-lookup"><span data-stu-id="af79e-132">On the NuGet Package Manager tab:</span></span>
   1. <span data-ttu-id="af79e-133">Paket kaynağı olarak "nuget.org" öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-133">Select "nuget.org" as the Package source.</span></span>
   2. <span data-ttu-id="af79e-134">**Araştır** sekmesine gidin.</span><span class="sxs-lookup"><span data-stu-id="af79e-134">Go to the **Browse** tab.</span></span>
   3. <span data-ttu-id="af79e-135">**Yayın öncesi Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-135">Select **Include prerelease**.</span></span>
   4. <span data-ttu-id="af79e-136">**Microsoft. DotNet. çözümleyiciler**için arama yapın. uyumluluk.</span><span class="sxs-lookup"><span data-stu-id="af79e-136">Search for **Microsoft.DotNet.Analyzers.Compatibility**.</span></span>
   5. <span data-ttu-id="af79e-137">Listeden bu paketi seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-137">Select that package in the list.</span></span>
   6. <span data-ttu-id="af79e-138">**Install** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-138">Select the **Install** button.</span></span>
   7. <span data-ttu-id="af79e-139">**Değişiklikleri Önizle** Iletişim kutusunda **Tamam** düğmesini seçin ve ardından listelenen paketlerin lisans koşullarını kabul ediyorsanız **Lisans kabulü** iletişim kutusunda **kabul ediyorum** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="use-the-api-analyzer"></a><span data-ttu-id="af79e-140">API Çözümleyicisi 'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="af79e-140">Use the API Analyzer</span></span>

<span data-ttu-id="af79e-141">, Gibi kullanım dışı bırakılmış bir API <xref:System.Net.WebClient> bir kodda kullanıldığında, API Çözümleyicisi bunu yeşil dalgalı çizgi ile vurgular.</span><span class="sxs-lookup"><span data-stu-id="af79e-141">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="af79e-142">API çağrısının üzerine geldiğinizde, aşağıdaki örnekte olduğu gibi, API 'nin kullanımdan kaldırılması hakkında bilgiler içeren bir ampul görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="af79e-142">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

![Sol tarafta yeşil dalgalı çizgi ve ampul ile WebClient API ekran görüntüsü.](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="af79e-144">**Hata listesi** penceresinde, aşağıdaki örnekte gösterildiği gibi, kullanım dışı API başına BENZERSIZ bir kimliğe sahip uyarılar bulunur ( `DE004` ):</span><span class="sxs-lookup"><span data-stu-id="af79e-144">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span>

<span data-ttu-id="af79e-145">![Uyarının KIMLIĞINI ve açıklamasını gösteren Hata Listesi penceresinin ekran görüntüsü.](media/api-analyzer/warnings-id-and-descriptions.jpg "Uyarıları içeren Hata Listesi pencere.")</span><span class="sxs-lookup"><span data-stu-id="af79e-145">![Screenshot of the Error List window showing warning's ID and description.](media/api-analyzer/warnings-id-and-descriptions.jpg "Error List window that includes warnings.")</span></span>

<span data-ttu-id="af79e-146">KIMLIĞE tıkladığınızda, API 'nin neden kullanım dışı olduğuna ilişkin ayrıntılı bilgiler ve kullanılabilecek alternatif API 'Ler ile ilgili öneriler içeren bir Web sayfasına gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-146">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="af79e-147">Vurgulanan üyeye sağ tıklayıp \*\*Gizle \<diagnostic ID> \*\*' yi seçerek herhangi bir uyarı bastırılabilir.</span><span class="sxs-lookup"><span data-stu-id="af79e-147">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="af79e-148">Uyarıları basmanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="af79e-148">There are two ways to suppress warnings:</span></span>

- [<span data-ttu-id="af79e-149">Yerel olarak (kaynakta)</span><span class="sxs-lookup"><span data-stu-id="af79e-149">locally (in source)</span></span>](#suppress-warnings-locally)
- <span data-ttu-id="af79e-150">[küresel olarak (bir gizleme dosyasında)](#suppress-warnings-globally) önerilir</span><span class="sxs-lookup"><span data-stu-id="af79e-150">[globally (in a suppression file)](#suppress-warnings-globally) - recommended</span></span>

### <a name="suppress-warnings-locally"></a><span data-ttu-id="af79e-151">Uyarıları yerel olarak gösterme</span><span class="sxs-lookup"><span data-stu-id="af79e-151">Suppress warnings locally</span></span>

<span data-ttu-id="af79e-152">Uyarıları yerel olarak gizlemek için uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler**  >  \*\* *Tanılama kimliğini* \<diagnostic ID> \*\*  >  **kaynak bölümünde**göster ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="af79e-152">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="af79e-153">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) uyarı ön işlemci yönergesi, tanımlanan kapsamdaki kaynak kodunuza eklenir: ![ #pragma uyarı devre dışı ile çerçeveli kodun ekran görüntüsü.](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="af79e-153">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: ![Screenshot of code framed with #pragma warning disable.](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppress-warnings-globally"></a><span data-ttu-id="af79e-154">Uyarıları küresel olarak gösterme</span><span class="sxs-lookup"><span data-stu-id="af79e-154">Suppress warnings globally</span></span>

<span data-ttu-id="af79e-155">Uyarıları küresel olarak gizlemek için uyarıları gizlemek istediğiniz üyeye sağ tıklayın ve sonra **Hızlı Eylemler ve yeniden düzenlemeler**  >  gizleme dosyasında\*\* *Tanılama kimliğini* \<diagnostic ID> Gizle\*\*' yi seçin  >  **in Suppression File**.</span><span class="sxs-lookup"><span data-stu-id="af79e-155">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

![Visual Studio 'da bir uyarıyı gösterme seçeneklerini gösteren sağ tıklama menüsünün ekran görüntüsü.](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="af79e-157">İlk göstermeme sonrasında projenize bir *GlobalSuppressions.cs* dosyası eklenir.</span><span class="sxs-lookup"><span data-stu-id="af79e-157">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="af79e-158">Bu dosyanın yeni genel gizlemeleri eklenir.</span><span class="sxs-lookup"><span data-stu-id="af79e-158">New global suppressions are appended to this file.</span></span>

![Çözüm Gezgini içindeki GlobalSuppressions.cs dosyasının ekran görüntüsü.](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="af79e-160">Genel gizleme, projeler genelinde API kullanımının tutarlılığını sağlamak için önerilen yoldur.</span><span class="sxs-lookup"><span data-stu-id="af79e-160">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discover-cross-platform-issues"></a><span data-ttu-id="af79e-161">Platformlar arası sorunları bulma</span><span class="sxs-lookup"><span data-stu-id="af79e-161">Discover cross-platform issues</span></span>

> [!NOTE]
> <span data-ttu-id="af79e-162">.NET 5,0, bu özelliğin yerini alacak şekilde [platform uyumluluğu Çözümleyicisi](platform-compat-analyzer.md) 'ni tanıtır.</span><span class="sxs-lookup"><span data-stu-id="af79e-162">.NET 5.0 introduces the [Platform compatibility analyzer](platform-compat-analyzer.md) as a replacement of this feature.</span></span> <span data-ttu-id="af79e-163">Platform uyumluluğu Çözümleyicisi, .NET SDK 'ya dahildir (Bu uygulamayı ayrı olarak yüklemeniz gerekmez) ve varsayılan olarak açık olur.</span><span class="sxs-lookup"><span data-stu-id="af79e-163">The platform compatibility analyzer is included in the .NET SDK (no need to install it separately) and is on by default.</span></span>

<span data-ttu-id="af79e-164">Kullanım dışı olan API 'Lerle benzer şekilde, çözümleyici platformlar arası olmayan tüm API 'Leri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="af79e-164">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="af79e-165">Örneğin, <xref:System.Console.WindowWidth?displayProperty=nameWithType> Windows 'da, Linux ve macOS 'ta değil, üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="af79e-165">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="af79e-166">Tanılama KIMLIĞI **hata listesi** penceresinde gösterilir.</span><span class="sxs-lookup"><span data-stu-id="af79e-166">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="af79e-167">Sağ tıklayıp **Hızlı Eylemler ve yeniden düzenlemeler '** i seçerek bu uyarının görüntülenmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-167">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="af79e-168">İki seçeneğe sahip olduğunuz kullanım dışı durumların aksine (kullanımdan kaldırılan üyeyi kullanmaya devam edin, uyarıları gizleyin veya hiç kullanmayın), burada kodunuzu yalnızca belirli platformlar için geliştiriyorsanız, kodunuzu çalıştırmayı planladığınız diğer tüm platformlar için tüm uyarıları gizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-168">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="af79e-169">Bunu yapmak için yalnızca proje dosyanızı düzenlemeniz ve `PlatformCompatIgnore` tüm platformları listeleyen özelliği yok sayılacak şekilde eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="af79e-169">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="af79e-170">Kabul edilen değerler şunlardır: `Linux` , `macOS` , ve `Windows` .</span><span class="sxs-lookup"><span data-stu-id="af79e-170">The accepted values are: `Linux`, `macOS`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;macOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="af79e-171">Kodunuz birden çok platformu hedefliyorsa ve bazılarında desteklenmeyen bir API 'nin avantajlarından yararlanmak istiyorsanız kodun bu bölümünü bir ifadesiyle koryükleyebilirsiniz `if` :</span><span class="sxs-lookup"><span data-stu-id="af79e-171">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="af79e-172">Ayrıca, hedef çerçeve/işletim sistemi için koşullu olarak derleyebilirsiniz, ancak şu anda [el ile](../frameworks.md#how-to-specify-a-target-framework)yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="af79e-172">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-a-target-framework).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="af79e-173">Desteklenen Tanılamalar</span><span class="sxs-lookup"><span data-stu-id="af79e-173">Supported diagnostics</span></span>

<span data-ttu-id="af79e-174">Şu anda, çözümleyici aşağıdaki durumları işler:</span><span class="sxs-lookup"><span data-stu-id="af79e-174">Currently, the analyzer handles the following cases:</span></span>

- <span data-ttu-id="af79e-175">(PC001) oluşturan .NET Standard API kullanımı <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="af79e-175">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
- <span data-ttu-id="af79e-176">.NET Framework 4.6.1 (PC002) üzerinde kullanılamayan bir .NET Standard API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="af79e-176">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
- <span data-ttu-id="af79e-177">UWP 'de mevcut olmayan bir yerel API kullanımı (PC003).</span><span class="sxs-lookup"><span data-stu-id="af79e-177">Usage of a native API that doesn't exist in UWP (PC003).</span></span>
- <span data-ttu-id="af79e-178">Delegate. BeginInvoke ve EndInvoke API 'Leri (PC004) kullanımı.</span><span class="sxs-lookup"><span data-stu-id="af79e-178">Usage of Delegate.BeginInvoke and EndInvoke APIs (PC004).</span></span>
- <span data-ttu-id="af79e-179">Kullanım dışı (DEXXXX) olarak işaretlenen bir API kullanımı.</span><span class="sxs-lookup"><span data-stu-id="af79e-179">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="af79e-180">CI makinesi</span><span class="sxs-lookup"><span data-stu-id="af79e-180">CI machine</span></span>

<span data-ttu-id="af79e-181">Tüm bu Tanılamalar yalnızca IDE 'de değil, aynı zamanda, CI sunucusunu içeren projenizi oluşturmanın bir parçası olarak komut satırında de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="af79e-181">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="af79e-182">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="af79e-182">Configuration</span></span>

<span data-ttu-id="af79e-183">Kullanıcı, tanılama nasıl ele alınacağına karar verir: uyarılar, hatalar, öneriler veya kapatılacak.</span><span class="sxs-lookup"><span data-stu-id="af79e-183">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="af79e-184">Örneğin, bir mimari olarak uyumluluk sorunlarının hata olarak değerlendirilip bazı kullanım dışı API 'lere yapılan çağrılar uyarı üretirken, diğerleri yalnızca öneriler üretmeye karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-184">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="af79e-185">Bunu, tanılama KIMLIĞI ve proje tarafından ayrı ayrı yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af79e-185">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="af79e-186">**Çözüm Gezgini**için, projenizin altındaki **Bağımlılıklar** düğümüne gidin.</span><span class="sxs-lookup"><span data-stu-id="af79e-186">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="af79e-187">**Dependencies**  >  **Analyzers**  >  **Microsoft. DotNet. çözümleyiciler. uyumluluğu**çözümleyicilerinin düğümleri bağımlılıklarını genişletin.</span><span class="sxs-lookup"><span data-stu-id="af79e-187">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="af79e-188">Tanılama KIMLIĞI ' ne sağ tıklayın, **kural kümesi önem derecesi ayarla**' yı seçin ve ardından istediğiniz seçeneği belirleyin.</span><span class="sxs-lookup"><span data-stu-id="af79e-188">Right-click on the diagnostic ID, select **Set Rule Set Severity**, and then pick the desired option.</span></span>

![Kural kümesi önem derecesine sahip tanılama ve açılır iletişim iletişimini gösteren Çözüm Gezgini ekran görüntüsü.](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="af79e-190">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af79e-190">See also</span></span>

- <span data-ttu-id="af79e-191">[API Çözümleyicisi blog gönderisine giriş](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) .</span><span class="sxs-lookup"><span data-stu-id="af79e-191">[Introducing API Analyzer](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) blog post.</span></span>
- <span data-ttu-id="af79e-192">YouTube 'da [API Çözümleyicisi](https://youtu.be/eeBEahYXGd0) tanıtım videosu.</span><span class="sxs-lookup"><span data-stu-id="af79e-192">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>
- [<span data-ttu-id="af79e-193">Platform uyumluluğu Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="af79e-193">Platform Compatibility Analyzer</span></span>](platform-compat-analyzer.md)
