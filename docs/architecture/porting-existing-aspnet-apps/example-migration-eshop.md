---
title: ASP.NET Core için eShop 'ın örnek geçişi
description: Bir başvuru olarak örnek bir çevrimiçi mağaza uygulaması kullanarak, mevcut bir ASP.NET MVC uygulamasını ASP.NET Core 'e geçirmeye yönelik yönergeler.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 8175e24cbc82c8ce36d302c9e5f6376994668171
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639296"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a><span data-ttu-id="cf2ed-103">ASP.NET Core için eShop 'ın örnek geçişi</span><span class="sxs-lookup"><span data-stu-id="cf2ed-103">Example migration of eShop to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cf2ed-104">Bu bölümde, bir .NET Framework uygulamasının .NET Core 'a nasıl geçirileceği göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-104">In this chapter, you'll see how to migrate a .NET Framework app to .NET Core.</span></span> <span data-ttu-id="cf2ed-105">Bu bölümde, ASP.NET 5,0 için yazılmış bir örnek çevrimiçi mağaza uygulaması incelenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-105">The chapter examines a sample online store app written for ASP.NET 5.0.</span></span> <span data-ttu-id="cf2ed-106">Uygulama, bu kitapta daha önce açıklanan kavramların ve araçların birçoğunu kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-106">The app will use many of the concepts and tools described earlier in this book.</span></span> <span data-ttu-id="cf2ed-107">Başlangıç noktası uygulamasını [ *Eshopmodernize* GitHub deposunda](https://github.com/dotnet-architecture/eShopModernizing)bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-107">You'll find the starting point app in the [*eShopModernizing* GitHub repository](https://github.com/dotnet-architecture/eShopModernizing).</span></span> <span data-ttu-id="cf2ed-108">Birçok farklı başlangıç noktası uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-108">There are several different starting point apps.</span></span> <span data-ttu-id="cf2ed-109">Bu bölüm *Eshoplegacymvcsolution*' a odaklanır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-109">This chapter focuses on the *eShopLegacyMVCSolution*.</span></span>

<span data-ttu-id="cf2ed-110">Projenin ilk sürümü Şekil 4-1 ' de gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-110">The initial version of the project is shown in Figure 4-1.</span></span> <span data-ttu-id="cf2ed-111">Bu, oldukça standart bir ASP.NET MVC 5 uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-111">It's a fairly standard ASP.NET MVC 5 app.</span></span>

![Şekil 4-1](media/Figure4-1.png)

<span data-ttu-id="cf2ed-113">**Şekil 4-1.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-113">**Figure 4-1.**</span></span> <span data-ttu-id="cf2ed-114">MVC örnek proje yapısı *Eshopmodernize* .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-114">The *eShopModernizing* MVC sample project structure.</span></span>

## <a name="run-apiport-to-identify-problematic-apis"></a><span data-ttu-id="cf2ed-115">Sorunlu API 'Leri tanımlamak için *Apiport* çalıştırma</span><span class="sxs-lookup"><span data-stu-id="cf2ed-115">Run *ApiPort* to identify problematic APIs</span></span>

<span data-ttu-id="cf2ed-116">Geçirmeye hazırlanın ilk adımı, *Apiport* aracını çalıştırıyordu.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-116">The first step in preparing to migrate is to run the *ApiPort* tool.</span></span> <span data-ttu-id="cf2ed-117">Araç, uygulamanın kaç .NET Framework API 'sini ve bunların kaç tane .NET Standard veya .NET Core eşdeğerlerine sahip olduğunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-117">The tool identifies how many .NET Framework APIs the app calls and how many of these have .NET Standard or .NET Core equivalents.</span></span> <span data-ttu-id="cf2ed-118">Birincil olarak kendi uygulamanızın mantığına odaklanın, üçüncü taraf bağımlılıklara değil, ve `System.Web` bu yana, bir arada olması gereken bağımlılıklara dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-118">Focus primarily on your own app's logic, not third-party dependencies, and pay attention to `System.Web` dependencies that will need to be ported.</span></span> <span data-ttu-id="cf2ed-119">ApiPort Aracı, son bölümde [bağımlılıkları anlama ve güncelleştirme](/understand-update-dependencies.md)konusunda sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-119">The ApiPort tool was introduced in the last chapter on [understanding and updating dependencies](/understand-update-dependencies.md).</span></span>

<span data-ttu-id="cf2ed-120">[ *Apiport* aracını yükledikten ve yapılandırdıktan](https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer)sonra, Şekil 4-2 ' de gösterildiği gibi Analizi Visual Studio içinden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-120">After [installing and configuring the *ApiPort* tool](https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer), run the analysis from within Visual Studio, as shown in Figure 4-2.</span></span>

![Şekil 4-2](media/Figure4-2.png)

<span data-ttu-id="cf2ed-122">**Şekil 4-2.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-122">**Figure 4-2.**</span></span> <span data-ttu-id="cf2ed-123">Visual Studio 'da bütünleştirilmiş kod taşınabilirliği çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-123">Analyze assembly portability in Visual Studio.</span></span>

<span data-ttu-id="cf2ed-124">Şekil 4-3 ' de gösterildiği gibi, projenin *bin* klasöründen Web projesinin derlemesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-124">Choose the web project's assembly from the project's *bin* folder, as shown in Figure 4-3.</span></span>

![Şekil 4-3](media/Figure4-3.png)

<span data-ttu-id="cf2ed-126">**Şekil 4-3.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-126">**Figure 4-3.**</span></span> <span data-ttu-id="cf2ed-127">Projenin Web derlemesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-127">Choose the project's web assembly.</span></span>

<span data-ttu-id="cf2ed-128">Çözümünüz birden çok proje içeriyorsa, bunların tümünü seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-128">If your solution includes several projects, you can choose all of them.</span></span> <span data-ttu-id="cf2ed-129">*EShop* örneği yalnızca tek bir MVC projesi içerir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-129">The *eShop* sample includes just a single MVC project.</span></span>

<span data-ttu-id="cf2ed-130">Rapor oluşturulduktan sonra dosyayı açın ve sonuçları gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-130">Once the report is generated, open the file and review the results.</span></span> <span data-ttu-id="cf2ed-131">Özet, uygulamanızın uyumlu sürüme sahip olduğu .NET Framework çağrısı yüzdesinin üst düzey bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-131">The summary provides a high-level view of what percentage of .NET Framework calls your app is making have compatible versions.</span></span> <span data-ttu-id="cf2ed-132">Şekil 4-4, *eShop* MVC projesinin özetini gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-132">Figure 4-4 shows the summary for the *eShop* MVC project.</span></span>

![Şekil 4-4](media/Figure4-4.png)

<span data-ttu-id="cf2ed-134">**Şekil 4-4.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-134">**Figure 4-4.**</span></span> <span data-ttu-id="cf2ed-135">ApiPort Özeti.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-135">ApiPort summary.</span></span>

<span data-ttu-id="cf2ed-136">Bu uygulama için .NET Framework çağrılarının yüzde 80 ' unun uyumlu olduğunu öğrenin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-136">For this app, about 80 percent of the .NET Framework calls are compatible.</span></span> <span data-ttu-id="cf2ed-137">taşıma işlemi sırasında çağrıların yüzde 20 ' si ile ilgilenilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-137">20 percent of the calls need to be addressed during the porting process.</span></span> <span data-ttu-id="cf2ed-138">Ayrıntıları görüntülemek, uyumsuz çağrıların tümünün bir parçası olduğunu `System.Web` ve beklenen bir uyumsuzluk olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-138">Viewing the details reveals that all of the incompatible calls are part of `System.Web`, which is an expected incompatibility.</span></span> <span data-ttu-id="cf2ed-139">`System.Web`Çağrılardaki bağımlılıklar, uygulamanın denetleyicileri ve ilgili sınıfları sonraki bir adımda geçirildiğinde değinilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-139">The dependencies on `System.Web` calls will be addressed when the app's controllers and related classes are migrated in a later step.</span></span> <span data-ttu-id="cf2ed-140">Şekil 4-5 araç tarafından bulunan belirli türlerden bazılarını listeler:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-140">Figure 4-5 lists some of the specific types found by the tool:</span></span>

![Şekil 4-5](media/Figure4-5.png)

<span data-ttu-id="cf2ed-142">**Şekil 4-5.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-142">**Figure 4-5.**</span></span> <span data-ttu-id="cf2ed-143">*Apiport* uyumsuz tür ayrıntıları.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-143">*ApiPort* incompatible type details.</span></span>

<span data-ttu-id="cf2ed-144">Uyumsuz türlerin çoğu, `Controller` ve ASP.NET Core eşdeğerleri olan çeşitli ilgili özniteliklere başvurur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-144">Most of the incompatible types refer to `Controller` and various related attributes that have equivalents in ASP.NET Core.</span></span>

## <a name="update-project-files-and-nuget-reference-syntax"></a><span data-ttu-id="cf2ed-145">Proje dosyalarını ve NuGet başvuru sözdizimini Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="cf2ed-145">Update project files and NuGet reference syntax</span></span>

<span data-ttu-id="cf2ed-146">Daha sonra, eski *. csproj* dosya yapısından .NET Core ile tanıtılan daha yeni, daha basit bir yapıya geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-146">Next, migrate from the older *.csproj* file structure to the newer, simpler structure introduced with .NET Core.</span></span> <span data-ttu-id="cf2ed-147">Bunu yaparken, proje dosyasındaki öğeleri kullanmak için NuGet başvuruları için bir *packages.config* dosyası kullanmaktan da geçiş yapabilirsiniz `<PackageReference>` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-147">In doing so, you'll also migrate from using a *packages.config* file for NuGet references to using `<PackageReference>` elements in the project file.</span></span>

<span data-ttu-id="cf2ed-148">Orijinal projenin *Eshoplegacymvc. csproj* dosyası 418 satır uzunluğundadır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-148">The original project's *eShopLegacyMVC.csproj* file is 418 lines long.</span></span> <span data-ttu-id="cf2ed-149">Şekil 4-6 ' de proje dosyasının bir örneği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-149">A sample of the project file is shown in Figure 4-6.</span></span> <span data-ttu-id="cf2ed-150">Genel boyutunun ve karmaşıklığının bir fikir sunmak için görüntünün sağ tarafı dosyanın tamamının küçük bir görünümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-150">To offer a sense of its overall size and complexity, the right side of the image contains a miniature view of the entire file.</span></span>

![Şekil 4-6](media/Figure4-6.png)

<span data-ttu-id="cf2ed-152">**Şekil 4-6.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-152">**Figure 4-6.**</span></span> <span data-ttu-id="cf2ed-153">*Eshoplegacymvc. csproj* dosya yapısı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-153">The *eShopLegacyMVC.csproj* file structure.</span></span>

<span data-ttu-id="cf2ed-154">Mevcut bir ASP.NET projesi için yeni bir proje dosyası oluşturmanın yaygın bir yolu, `dotnet new`   >    >  Visual Studio 'da yeni bir **Proje** kullanarak yeni bir ASP.NET Core uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-154">A common way to create a new project file for an existing ASP.NET project is to create a new ASP.NET Core app using `dotnet new` or **File** > **New** > **Project** in Visual Studio.</span></span> <span data-ttu-id="cf2ed-155">Ardından, geçiş işleminin tamamlanabilmesi için dosyalar eski projeden yeni birine kopyalanabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-155">Then files can be copied from the old project to the new one to complete the migration.</span></span>

<span data-ttu-id="cf2ed-156">C# proje dosyasına ek olarak, NuGet bağımlılıkları Şekil 4-7 ' de gösterildiği gibi ayrı bir 45 satırı *packages.config* dosyasında depolanır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-156">In addition to the C# project file, NuGet dependencies are stored in a separate 45-line *packages.config* file, as shown in Figure 4-7.</span></span>

![Şekil 4-7](media/Figure4-7.png)

<span data-ttu-id="cf2ed-158">**Şekil 4-7.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-158">**Figure 4-7.**</span></span> <span data-ttu-id="cf2ed-159">*packages.config* dosyası.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-159">The *packages.config* file.</span></span>

<span data-ttu-id="cf2ed-160">Yeni *. csproj* dosya biçimine yükselttikten sonra Visual Studio 'yu kullanarak sınıf kitaplığı projelerinde *packages.config* geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-160">After upgrading to the new *.csproj* file format, you can migrate *packages.config* in class library projects using Visual Studio.</span></span> <span data-ttu-id="cf2ed-161">Ancak, bu işlevsellik ASP.NET projeleriyle birlikte çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-161">This functionality doesn't work with ASP.NET projects, however.</span></span> <span data-ttu-id="cf2ed-162">[ *packages.config* `<PackageReference>` Visual Studio 'da ' a geçirme hakkında daha fazla bilgi edinin](https://docs.microsoft.com/nuget/consume-packages/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="cf2ed-162">[Learn more about migrating *packages.config* to `<PackageReference>` in Visual Studio](https://docs.microsoft.com/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span> <span data-ttu-id="cf2ed-163">Geçirilecek çok sayıda projeniz varsa, [Bu topluluk aracı yardımcı olabilir](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).</span><span class="sxs-lookup"><span data-stu-id="cf2ed-163">If you have a large number of projects to migrate, [this community tool may help](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).</span></span>

## <a name="create-new-aspnet-core-project"></a><span data-ttu-id="cf2ed-164">Yeni ASP.NET Core projesi oluştur</span><span class="sxs-lookup"><span data-stu-id="cf2ed-164">Create new ASP.NET Core project</span></span>

<span data-ttu-id="cf2ed-165">Çalışma dosyalarının çoğu Visual Studio 'nun **Çözüm Gezgini** içinden yapılabilmesini sağlamak için mevcut uygulamanın çözümüne yeni bir ASP.NET Core projesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-165">Add a new ASP.NET Core project to the existing app's solution to make moving files easier, as most of the work can be done from within Visual Studio's **Solution Explorer**.</span></span> <span data-ttu-id="cf2ed-166">Visual Studio 'da uygulamanızın çözümüne sağ tıklayın ve **Yeni Proje Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-166">In Visual Studio, right-click on your app's solution and choose **Add New Project**.</span></span> <span data-ttu-id="cf2ed-167">**ASP.NET Core Web uygulaması**' nı seçin ve Şekil 4-8 ' de gösterildiği gibi yeni projeye bir ad verin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-167">Choose **ASP.NET Core web application**, and give the new project a name as shown in Figure 4-8.</span></span>

![Şekil 4-8](media/Figure4-8.png)

<span data-ttu-id="cf2ed-169">**Şekil 4-8.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-169">**Figure 4-8.**</span></span> <span data-ttu-id="cf2ed-170">Yeni ASP.NET Core Web uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-170">Add new ASP.NET Core web application.</span></span>

<span data-ttu-id="cf2ed-171">Sonraki iletişim kutusunda hangi şablonun kullanılacağını seçmeniz istenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-171">The next dialog will ask you to choose which template to use.</span></span> <span data-ttu-id="cf2ed-172">**Boş** şablonu seçin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-172">Select the **Empty** template.</span></span> <span data-ttu-id="cf2ed-173">Ayrıca, açılan menüyü de **.NET Core** 'tan **.NET Framework** olarak değiştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-173">Be sure to also change the dropdown from **.NET Core** to **.NET Framework**.</span></span> <span data-ttu-id="cf2ed-174">Şekil 4-9 ' de gösterildiği gibi **ASP.NET Core 2,2**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-174">Select **ASP.NET Core 2.2**, as shown in Figure 4-9.</span></span>

![Şekil 4-9](media/Figure4-9.png)

<span data-ttu-id="cf2ed-176">**Şekil 4-9.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-176">**Figure 4-9.**</span></span> <span data-ttu-id="cf2ed-177">ASP.NET Core 2,2 ile .NET Framework Hedefleme boş bir proje şablonu seçin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-177">Choose an Empty project template targeting .NET Framework with ASP.NET Core 2.2.</span></span>

### <a name="migrating-nuget-packages"></a><span data-ttu-id="cf2ed-178">NuGet paketleri geçiriliyor</span><span class="sxs-lookup"><span data-stu-id="cf2ed-178">Migrating NuGet Packages</span></span>

<span data-ttu-id="cf2ed-179">*packages.config* geçirmek için yerleşik geçiş aracı `<PackageReference>` ASP.net projelerinde çalışmadıklarından, bunun yerine bir topluluk aracı kullanabilir veya el ile geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-179">Since the built-in migration tool for migrating *packages.config* to `<PackageReference>` doesn't work on ASP.NET projects, you can use a community tool instead, or migrate by hand.</span></span> <span data-ttu-id="cf2ed-180">[Kullandığım bir topluluk aracı](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) bir biçimden diğerine dönüştürmek IÇIN bir xsl dosyası kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-180">A [community tool I've used](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) uses an XSL file to transform from one format to the other.</span></span> <span data-ttu-id="cf2ed-181">Bunu kullanmak için önce *packages.config* dosyasını yeni oluşturulan ASP.NET Core proje klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-181">To use it, first copy the *packages.config* file to the newly created ASP.NET Core project folder.</span></span> <span data-ttu-id="cf2ed-182">Bu komut dosyası, komut dosyasını çalıştırdığınız tüm klasörlerden *packages.config* dosyasını kaldırdığında dosyalarınızın bir yedeğini alın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-182">Make a backup of your files, as this script removes the *packages.config* file from all folders under where you run the script.</span></span> <span data-ttu-id="cf2ed-183">Sonra bu komutları proje klasöründen (veya tercih ediyorsanız tüm çözüm için) çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-183">Then run these commands from the project folder (or for the entire solution if you prefer):</span></span>

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

<span data-ttu-id="cf2ed-184">İlk iki komut dosyaları yerel olarak mevcut olacak şekilde indirir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-184">The first two commands download files so that they exist locally.</span></span> <span data-ttu-id="cf2ed-185">Son satır betiği çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-185">The last line runs the script.</span></span> <span data-ttu-id="cf2ed-186">Çalıştırdıktan sonra yeni projeyi oluşturmayı deneyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-186">After running it, try to build the new project.</span></span> <span data-ttu-id="cf2ed-187">Büyük olasılıkla bazı hatalar alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-187">You'll most likely get some errors.</span></span> <span data-ttu-id="cf2ed-188">Bunları çözmek için bazı başvuruları ( `Microsoft.AspNet` ve paketlerin çoğu gibi `System` ) ortadan kaldırmak isteyeceksiniz ve bazı öznitelikleri kaldırmanız gerekebilir `xmlns` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-188">To resolve them, you'll want to eliminate some references (like most of the `Microsoft.AspNet` and `System` packages), and you may need to remove some `xmlns` attributes.</span></span>

<span data-ttu-id="cf2ed-189">Çoğu ASP.NET MVC uygulamasında, önyükleme ve jQuery gibi birçok istemci tarafı bağımlılığı NuGet paketleri kullanılarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-189">In most ASP.NET MVC apps, many client-side dependencies like Bootstrap and jQuery were deployed using NuGet packages.</span></span> <span data-ttu-id="cf2ed-190">ASP.NET Core, NuGet paketleri yalnızca sunucu tarafı işlevleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-190">In ASP.NET Core, NuGet packages are only used for server-side functionality.</span></span> <span data-ttu-id="cf2ed-191">İstemci dosyaları diğer yollarla yönetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-191">Client files should be managed through other means.</span></span> <span data-ttu-id="cf2ed-192">`<PackageReference>`Eklenen ve bulunan öğelerin listesini gözden geçirin ve aşağıdakiler dahil olmak üzere istemci kitaplıkları için olan öğeleri unutmayın:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-192">Review the list of `<PackageReference>` elements added and remove and make note of any that are for client libraries, including:</span></span>

- <span data-ttu-id="cf2ed-193">Bootstrap</span><span class="sxs-lookup"><span data-stu-id="cf2ed-193">Bootstrap</span></span>
- <span data-ttu-id="cf2ed-194">jQuery</span><span class="sxs-lookup"><span data-stu-id="cf2ed-194">jQuery</span></span>
- <span data-ttu-id="cf2ed-195">jQuery. Validation</span><span class="sxs-lookup"><span data-stu-id="cf2ed-195">jQuery.Validation</span></span>
- <span data-ttu-id="cf2ed-196">Modernize</span><span class="sxs-lookup"><span data-stu-id="cf2ed-196">Modernizr</span></span>
- <span data-ttu-id="cf2ed-197">popper.js</span><span class="sxs-lookup"><span data-stu-id="cf2ed-197">popper.js</span></span>
- <span data-ttu-id="cf2ed-198">Yanıtlama</span><span class="sxs-lookup"><span data-stu-id="cf2ed-198">Respond</span></span>

<span data-ttu-id="cf2ed-199">Bu paketler için NuGet tarafından yüklenen statik istemci dosyaları, yeni projenin *Wwwroot* klasörüne kopyalanacak ve oradan barındırılacak.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-199">The static client files installed by NuGet for these packages will be copied over to the new project's *wwwroot* folder and hosted from there.</span></span> <span data-ttu-id="cf2ed-200">Bu dosyaların uygulama için hala gerekli olup olmadığını ve bunun yerine bunları barındırmayı veya bir içerik teslim ağı (CDN) kullanmayı bir anlam taşıdığını düşünürken.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-200">It's worth considering whether these files are still needed by the app, and whether it makes sense to continue hosting them or to use a content delivery network (CDN) instead.</span></span> <span data-ttu-id="cf2ed-201">Bu kitaplık sürümleri, [Libman](https://docs.microsoft.com/aspnet/core/client-side/libman/) veya [NPM](https://www.npmjs.com/)gibi araçlar kullanılarak derleme zamanında yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-201">These library versions can be managed at build time using tools like [LibMan](https://docs.microsoft.com/aspnet/core/client-side/libman/) or [npm](https://www.npmjs.com/).</span></span> <span data-ttu-id="cf2ed-202">Şekil 4-10, gösterilen dönüştürme aracını kullanarak paket başvurularını geçirdikten sonra ve gereksiz paketleri kaldırarak tam *Esatlamalı. csproj* dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-202">Figure 4-10 shows the full *eShopPorted.csproj* file after migrating package references using the conversion tool shown and removing unnecessary packages.</span></span>

![Şekil 4-10](media/Figure4-10.png)

<span data-ttu-id="cf2ed-204">**Şekil 4-10.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-204">**Figure 4-10.**</span></span> <span data-ttu-id="cf2ed-205">*Eshopcat. csproj* dosyasındaki paket başvuruları.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-205">Package references in the *eShopPorted.csproj* file.</span></span>

<span data-ttu-id="cf2ed-206">Paket başvuruları, `<Version>1.0.0.0</Version>` öğesi üzerinde bir özniteliği yaparak daha sonra sıkıştırabilirsiniz `Version=1.0.0.0` `<PackageReference>` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-206">The package references can be further compacted by making the `<Version>1.0.0.0</Version>` element a `Version=1.0.0.0` attribute on `<PackageReference>`.</span></span>

### <a name="migrate-static-files"></a><span data-ttu-id="cf2ed-207">Statik dosyaları geçirme</span><span class="sxs-lookup"><span data-stu-id="cf2ed-207">Migrate static files</span></span>

<span data-ttu-id="cf2ed-208">Uygulamanın kullandığı, üçüncü taraf betikler ve çerçeveler de dahil olmak üzere, özel görüntüler ve stil sayfaları da dahil olmak üzere tüm statik dosyalar eski projeden yeni bir projeye kopyalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-208">Any static files the app uses, including third-party scripts and frameworks but also custom images and stylesheets, must be copied from the old project to the new one.</span></span> <span data-ttu-id="cf2ed-209">ASP.NET MVC uygulamalarında, dosyalar genellikle proje klasörü içindeki konumlarına göre erişilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-209">In ASP.NET MVC apps, files were typically accessed based on their location within the project folder.</span></span> <span data-ttu-id="cf2ed-210">ASP.NET Core uygulamalarda, bu statik dosyalara *Wwwroot* klasörü içindeki konumlarına göre erişilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-210">In ASP.NET Core apps, these static files will be accessed based on their location within the *wwwroot* folder.</span></span> <span data-ttu-id="cf2ed-211">*EShop* projesi için aşağıdaki klasörlerde statik dosyalar bulunur:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-211">For the *eShop* project, there are static files in the following folders:</span></span>

* <span data-ttu-id="cf2ed-212">*İçerik*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-212">*Content*</span></span>
* <span data-ttu-id="cf2ed-213">*tiplerini*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-213">*fonts*</span></span>
* <span data-ttu-id="cf2ed-214">*Görüntüler*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-214">*Images*</span></span>
* <span data-ttu-id="cf2ed-215">*PICS*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-215">*Pics*</span></span>
* <span data-ttu-id="cf2ed-216">*Betikleri*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-216">*Scripts*</span></span>

<span data-ttu-id="cf2ed-217">Önceki adımda kullanılan **boş** proje şablonu, varsayılan olarak bu klasörü veya bunun çalışması için gerekli olan ara yazılımı içermez.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-217">The **Empty** project template used in the previous step doesn't include this folder by default, or the middleware needed for it to work.</span></span> <span data-ttu-id="cf2ed-218">Bunları eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-218">You'll need to add them.</span></span>

<span data-ttu-id="cf2ed-219">Projenin köküne bir *Wwwroot* klasörü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-219">Add a *wwwroot* folder to the root of the project.</span></span>

<span data-ttu-id="cf2ed-220">NuGet paketinin sürüm 2.2.0 ekleyin `Microsoft.AspNetCore.StaticFiles` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-220">Add version 2.2.0 of the `Microsoft.AspNetCore.StaticFiles` NuGet package.</span></span>

<span data-ttu-id="cf2ed-221">*Startup.cs*' de yöntemine bir çağrı ekleyin `app.UseStaticFiles()` `Configure` :</span><span class="sxs-lookup"><span data-stu-id="cf2ed-221">In *Startup.cs*, add a call to `app.UseStaticFiles()` in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();

    // ...
}
```

<span data-ttu-id="cf2ed-222">ASP.NET MVC uygulamasındaki *içerik* klasörünü yeni projenin *Wwwroot* klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-222">Copy the *Content* folder from the ASP.NET MVC app to the new project's *wwwroot* folder.</span></span>

<span data-ttu-id="cf2ed-223">Uygulamayı çalıştırın ve statik dosyanın beklenen yoldan doğru şekilde sunulduğunu doğrulamak için */Content/Base.css* klasörüne gidin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-223">Run the app and navigate to its */Content/base.css* folder to verify that the static file is served correctly from its expected path.</span></span> <span data-ttu-id="cf2ed-224">Statik dosyaları içeren klasörlerin geri kalanını yeni projeye kopyalamaya devam edin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-224">Continue copying the rest of the folders containing static files to the new project.</span></span> <span data-ttu-id="cf2ed-225">Ayrıca, görevin kökündeki izin *simgesi. ico* dosyasını *Wwwroot* klasörüne kopyalamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-225">You'll also want to copy the *favicon.ico* file from the project's root to the *wwwroot* folder.</span></span> <span data-ttu-id="cf2ed-226">Şekil 4-11, bu dosyaların ve klasörlerinin tümünün kopyalandığı sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-226">Figure 4-11 shows the results after these files and their folders have all been copied.</span></span>

![Şekil 4-11](media/Figure4-11.png)

<span data-ttu-id="cf2ed-228">**Şekil 4-11.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-228">**Figure 4-11.**</span></span> <span data-ttu-id="cf2ed-229">*Wwwroot* klasörüne kopyalanmış statik klasörler.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-229">Static folders copied over to *wwwroot* folder.</span></span>

### <a name="migrate-c-files"></a><span data-ttu-id="cf2ed-230">C# dosyalarını geçirme</span><span class="sxs-lookup"><span data-stu-id="cf2ed-230">Migrate C# files</span></span>

<span data-ttu-id="cf2ed-231">Ardından, standart MVC klasörleri ve *denetleyiciler*, *modeller*, *ViewModel* ve *Hizmetler* gibi Içerikleri de dahil olmak üzere uygulama tarafından kullanılan C# dosyalarını kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-231">Next, copy over the C# files used by the app, including standard MVC folders and their contents like *Controllers*, *Models*, *ViewModel*, and *Services*.</span></span> <span data-ttu-id="cf2ed-232">Bu dosyalarda büyük olasılıkla bazı değişiklikler yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-232">There will most likely be some changes needed in these files.</span></span> <span data-ttu-id="cf2ed-233">Tek seferde bir klasör (veya alt klasör) kopyalamak ve ne zaman giteceğinden ilgilenilmesi gerektiğini görmek için derlemek en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-233">It's best to copy one folder (or subfolder) at a time and compile to see what errors need to be addressed as you go.</span></span>

<span data-ttu-id="cf2ed-234">*EShop* örneği için, geçiş için seçeceğim ilk klasör, C# varlıklarını ve Entity Framework sınıflarını içeren *modeller* klasörüdür.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-234">For the *eShop* sample, the first folder I choose to migrate is the *Models* folder, which includes C# entities and Entity Framework classes.</span></span> <span data-ttu-id="cf2ed-235">Bu klasörün sınıfları çoğu başkaları tarafından kullanılır, bu nedenle bu sınıflar kopyalanana kadar çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-235">This folder's classes are used by most of the others, so they won't work until these classes have been copied.</span></span> <span data-ttu-id="cf2ed-236">Klasörü kopyaladıktan ve oluşturduktan sonra, derleyici eksik ad alanıyla ilgili hatalar `System.Web.Hosting` , ile ilgili erişim ve başvuru olarak ortaya çıkartiliyor `HostingEnvironment` `ConfigurationManager.AppSettings` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-236">After copying the folder and building, the compiler revealed errors related to missing namespace `System.Web.Hosting`, related access to `HostingEnvironment`, and a reference to `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="cf2ed-237">Bu sorunlara yönelik çözüm, gerekli yol verilerini geçirmek olacaktır; Şimdilik, son satırlar için açıklama alınır ve `TODO:` her birine izlemek için bir açıklama eklenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-237">The solution to these issues will be to pass in the necessary path data; for now the breaking lines are commented out and a `TODO:` comment is added to each one to track it.</span></span> <span data-ttu-id="cf2ed-238">Beş satırı değiştirdikten sonra **görev listesi** beş öğeyi ve proje yapılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-238">After changing five lines, the **Task List** shows five items and the project builds.</span></span>

<span data-ttu-id="cf2ed-239">Daha sonra, bir sınıfı olan *ViewModel* klasörü üzerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-239">Next, the *ViewModel* folder, with its one class, is copied over.</span></span> <span data-ttu-id="cf2ed-240">Bu çok kolay bir işlemdir ve anında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-240">It's an easy one, and builds immediately.</span></span>

<span data-ttu-id="cf2ed-241">*Hizmetler* klasörü üzerine kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-241">The *Services* folder is copied over.</span></span> <span data-ttu-id="cf2ed-242">Bu klasörün sınıfları *modeller* klasöründen, bu klasörden sonra kopyalanması gereken Entity Framework sınıflara bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-242">This folder's classes depend on Entity Framework classes from the *Models* folder, which is why it needed to be copied after that folder.</span></span> <span data-ttu-id="cf2ed-243">Neyse ki, hata olmadan derleme Yapılımı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-243">Fortunately, it too builds without errors.</span></span>

<span data-ttu-id="cf2ed-244">Bu, *denetleyiciler* klasörünü ve iki sınıfını bırakır `Controller` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-244">That leaves the *Controllers* folder and its two `Controller` classes.</span></span> <span data-ttu-id="cf2ed-245">Klasörü yeni projeye kopyaladıktan ve derlemeden sonra yedi derleme hatası vardır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-245">After copying the folder to the new project and building, there are seven build errors.</span></span> <span data-ttu-id="cf2ed-246">Bunlardan dördü, erişim ile ilgilidir `ViewBag` ve hata bildirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-246">Four of them are related to `ViewBag` access and report an error of:</span></span>

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

<span data-ttu-id="cf2ed-247">Bu hatayı çözmek için C# öğesine bir NuGet paket başvurusu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-247">To resolve this error add a NuGet package reference to C#:</span></span>

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

<span data-ttu-id="cf2ed-248">Kalan üç hata, başvurulmayan bir derlemede tanımlanan türleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-248">The remaining three errors specify types that are defined in an assembly that isn't referenced.</span></span> <span data-ttu-id="cf2ed-249">Özellikle bu türler:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-249">Specifically these types:</span></span>

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

<span data-ttu-id="cf2ed-250">Her hatayı tek tek göz atalım.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-250">Let's look at each error one by one.</span></span> <span data-ttu-id="cf2ed-251">`Server`Öğesinin özelliğine başvurulmasına çalışırken ilk hata oluşur `Controller` , ancak artık mevcut değildir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-251">The first error occurs while trying to reference the `Server` property of `Controller`, which no longer exists.</span></span> <span data-ttu-id="cf2ed-252">İşlemin hedefi, uygulamadaki bir görüntü dosyasının yolunu almak olur:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-252">The goal of the operation is to get the path to an image file in the app:</span></span>

```csharp
if (item != null)
{
    var webRoot = Server.MapPath("~/Pics"); // compiler error on this line
    var path = Path.Combine(webRoot, item.PictureFileName);

    string imageFileExtension = Path.GetExtension(item.PictureFileName);
    string mimetype = GetImageMimeTypeFromImageFileExtension(imageFileExtension);

    var buffer = System.IO.File.ReadAllBytes(path);

    return File(buffer, mimetype);
}
```

<span data-ttu-id="cf2ed-253">Bu sorunun iki olası çözümü vardır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-253">There are two possible solutions to this problem.</span></span> <span data-ttu-id="cf2ed-254">Birincisi, işlevselliği olduğu gibi tutdır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-254">The first is to keep the functionality as it is.</span></span> <span data-ttu-id="cf2ed-255">Bu durumda, kullanmak yerine, `Server.MapPath` *Wwwroot* 'daki görüntü dosyalarının konumuna başvuran sabit bir yol kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-255">In this case, rather than using `Server.MapPath`, a fixed path referencing the image files' location in *wwwroot* should be used.</span></span> <span data-ttu-id="cf2ed-256">Alternatif olarak, bu eylem yönteminin tek amacı bir statik görüntü dosyası döndürmesidir, bu eyleme ilişkin başvurular, doğrudan statik dosyalara başvuracak şekilde, çalışma zamanı performansını artıran şekilde güncelleştirilemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-256">Alternately, since the only purpose of this action method is to return a static image file, the references to this action in view files can be updated to reference the static files directly, which improves runtime performance.</span></span> <span data-ttu-id="cf2ed-257">Bu eylemin bir parçası olarak herhangi bir işlem yapılmadığından, yalnızca dosyaları doğrudan sunmanıza bir neden yoktur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-257">Since no processing is being done as part of this action, there's no reason not to just serve the files directly.</span></span> <span data-ttu-id="cf2ed-258">Bu eyleme yapılan tüm başvuruları güncelleştirebilmezse, statik dosyanın konumuna yeniden yönlendirme oluşturmak için eylem yeniden yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-258">If it's not tenable to update all references to this action, the action could be rewritten to produce a redirect to the static file's location.</span></span>

<span data-ttu-id="cf2ed-259">Sonraki iki hata, aynı kod satırında aynı özel yöntemde oluşur:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-259">The next two errors both occur in the same private method in the same line of code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="cf2ed-260">Hem hem de `this.Url` `this.Request` derleyici hatalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-260">Both `this.Url` and `this.Request` cause compiler errors.</span></span> <span data-ttu-id="cf2ed-261">Bu kodun nasıl kullanıldığına bakarak, amacı `PicController` görüntü dosyalarını işleyen eyleme bir bağlantı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-261">Looking at how this code is used, its purpose is to build a link to the `PicController` action that renders image files.</span></span> <span data-ttu-id="cf2ed-262">Yeni bulduğumuz, büyük olasılıkla *Wwwroot*'da bulunan statik dosyaların doğrudan bağlantılarıyla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-262">The same one we just discovered could probably be replaced with direct links to the static files located in *wwwroot*.</span></span> <span data-ttu-id="cf2ed-263">Şimdilik, bu kodu yoruma ve bu kodun `TODO:` başka bir şekilde başvuruda bulunmak için bir açıklama eklemeye değecektir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-263">For now, it's worth commenting out this code and adding a `TODO:` comment to reference the pics another way.</span></span>

<span data-ttu-id="cf2ed-264">`Controller` `CatalogController` Bu, bu kodun göründüğü sınıf tarafından kullanılan temel sınıfın, hala öğesine başvurmakta olduğunu belirtmekte bir değer `System.Web.Mvc.Controller` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-264">It's worth noting that the base `Controller` class, used by the `CatalogController` class in which this code appears, is still referring to `System.Web.Mvc.Controller`.</span></span> <span data-ttu-id="cf2ed-265">Bunu, ASP.NET Core kullanmak için güncelleştirdiğimiz bir kez daha fazla hata çözeceğiz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-265">There will undoubtedly be more errors to fix once we update this to use ASP.NET Core.</span></span> <span data-ttu-id="cf2ed-266">İlk olarak, `using System.Web.Mvc;` içindeki deyim listesinden satırı kaldırın `using` `CatalogController` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-266">First, remove the `using System.Web.Mvc;` line from the list of `using` statements in `CatalogController`.</span></span> <span data-ttu-id="cf2ed-267">Sonra, NuGet paketini ekleyin `Microsoft.AspNetCore.Mvc` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-267">Next, add the NuGet package `Microsoft.AspNetCore.Mvc`.</span></span> <span data-ttu-id="cf2ed-268">Son olarak, bir `using Microsoft.AspNetCore.Mvc;` ifade ekleyin ve uygulamayı yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-268">Finally, add a `using Microsoft.AspNetCore.Mvc;` statement, and build the app again.</span></span>

<span data-ttu-id="cf2ed-269">Bu kez, 16 hata vardır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-269">This time, there are 16 errors:</span></span>

- <span data-ttu-id="cf2ed-270">`Include` geçerli bir adlandırılmış öznitelik bağımsız değişkeni değil (2)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-270">`Include` is not a valid named attribute argument (2)</span></span>
- <span data-ttu-id="cf2ed-271">`HttpStatusCodeResult` bulunamadı (3)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-271">`HttpStatusCodeResult` not found (3)</span></span>
- <span data-ttu-id="cf2ed-272">`HttpNotFound` yok (3)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-272">`HttpNotFound` does not exist (3)</span></span>
- <span data-ttu-id="cf2ed-273">`SelectList` bulunamadı (8)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-273">`SelectList` not found (8)</span></span>

<span data-ttu-id="cf2ed-274">Daha fazla bilgi için bu hataları tek tek gözden geçirelim.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-274">Once more, let's review these errors one by one.</span></span> <span data-ttu-id="cf2ed-275">İlk olarak, `SelectList` `using Microsoft.AspNetCore.Mvc.Rendering;` hatanın yarısını ortadan kaldıran ekleyerek düzeltilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-275">First, `SelectList` can be fixed by adding `using Microsoft.AspNetCore.Mvc.Rendering;`, which eliminates half of the errors.</span></span>

<span data-ttu-id="cf2ed-276">Öğesine yapılan tüm başvurular `return HttpNotFound();` ile değiştirilmelidir `return NotFound();` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-276">All references to `return HttpNotFound();` should be replaced with `return NotFound();`.</span></span>

<span data-ttu-id="cf2ed-277">Öğesine yapılan tüm başvurular `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` ile değiştirilmelidir `return BadRequest();` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-277">All references to `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` should be replaced with `return BadRequest();`.</span></span>

<span data-ttu-id="cf2ed-278">Bu, yalnızca `Include` `[Bind]` birkaç eylem yöntemi üzerinde aşağıdaki gibi bir özniteliği ile kullanımını bırakır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-278">That just leaves the use of `Include` with a `[Bind]` attribute on a couple of action methods that look like this:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="cf2ed-279">Yukarıdaki kod, model bağlamasını dizede listelenen özelliklerle kısıtlar `Include` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-279">The preceding code restricts model binding to the properties listed in the `Include` string.</span></span> <span data-ttu-id="cf2ed-280">ASP.NET Core MVC 'de `[Bind]` öznitelik hala var, ancak artık `Include =` bağımsız değişkene ihtiyaç yoktur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-280">In ASP.NET Core MVC, the `[Bind]` attribute still exists, but no longer needs the `Include =` argument.</span></span> <span data-ttu-id="cf2ed-281">Özellik listesini doğrudan `[Bind]` özniteliğine geçirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-281">Pass the list of properties directly to the `[Bind]` attribute:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="cf2ed-282">Bu değişikliklerle proje bir kez daha derlenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-282">With these changes, the project compiles once more.</span></span> <span data-ttu-id="cf2ed-283">Genellikle etki alanı modelinize veya veri modeli türlerine doğrudan model bağlamayı kullanmak yerine, denetleyici girişleri için ayrı model türleri kullanmak daha iyi bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-283">It's generally a better practice to use separate model types for controller inputs, rather than using model binding directly to your domain model or data model types.</span></span>

## <a name="migrate-views"></a><span data-ttu-id="cf2ed-284">Görünümleri geçirme</span><span class="sxs-lookup"><span data-stu-id="cf2ed-284">Migrate views</span></span>

<span data-ttu-id="cf2ed-285">Görünümlerle ilgili iki en büyük ASP.NET Core MVC özelliği [Razor Pages](https://docs.microsoft.com/aspnet/core/razor-pages/) ve [etiket yardımcılardır](https://docs.microsoft.com/aspnet/core/mvc/views/tag-helpers/built-in/).</span><span class="sxs-lookup"><span data-stu-id="cf2ed-285">The two biggest ASP.NET Core MVC features related to views are [Razor Pages](https://docs.microsoft.com/aspnet/core/razor-pages/) and [Tag Helpers](https://docs.microsoft.com/aspnet/core/mvc/views/tag-helpers/built-in/).</span></span> <span data-ttu-id="cf2ed-286">İlk geçiş için, her iki özelliği de kullanmayacağız.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-286">For the initial migration, we won't use either feature.</span></span> <span data-ttu-id="cf2ed-287">Ancak, geçiş yapıldıktan sonra uygulamayı desteklemeye devam ederseniz özellikleri aklınızda bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-287">You should, however, keep the features in mind if you continue supporting the app once it's been migrated.</span></span> <span data-ttu-id="cf2ed-288">Bir sonraki adım, *Görünümler* klasörünü özgün projeden yeni bir kopyaya kopyalamadır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-288">The next step is to copy the *Views* folder from the original project into the new one.</span></span> <span data-ttu-id="cf2ed-289">Derlemeden sonra dokuz hata vardır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-289">After building, there are nine errors:</span></span>

- <span data-ttu-id="cf2ed-290">HttpContext yok (2)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-290">HttpContext does not exist (2)</span></span>
- <span data-ttu-id="cf2ed-291">Betikler yok (5)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-291">Scripts does not exist (5)</span></span>
- <span data-ttu-id="cf2ed-292">Stiller yok (1)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-292">Styles does not exist (1)</span></span>
- <span data-ttu-id="cf2ed-293">HtmlString bulunamadı (1)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-293">HtmlString could not be found(1)</span></span>

<span data-ttu-id="cf2ed-294">Bu hataları araştırmak, büyük *_Layout. cshtml*'de, komut dosyası ve stil etiketlerinin işlenmesinin yanı sıra, uygulamayı barındıran sunucunun en son yeniden başlatılması sırasında görüntülenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-294">Investigating these errors finds that most of them are in the main *_Layout.cshtml*, with several related to rendering script and style tags, or displaying when the server hosting the app was last restarted.</span></span> <span data-ttu-id="cf2ed-295">Aşağıdaki kod listesi *_Layout. cshtml* dosyasındaki sorun bölgelerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-295">The following code listing shows problem areas in the *_Layout.cshtml* file:</span></span>

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

<span data-ttu-id="cf2ed-296">Modernizr başvurusu kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-296">The reference to Modernizr can be removed.</span></span> <span data-ttu-id="cf2ed-297">Önyükleme ve jQuery başvuruları, uygun sürüme yönelik CDN bağlantılarıyla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-297">The references to Bootstrap and jQuery can be replaced with CDN links to the appropriate version.</span></span>

<span data-ttu-id="cf2ed-298">`@Styles.Render`Satırı Değiştir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-298">Replace `@Styles.Render` line with:</span></span>

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

<span data-ttu-id="cf2ed-299">Son iki satırı şu `Scripts.Render` metinle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-299">Replace the last two `Scripts.Render` lines with:</span></span>

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

<span data-ttu-id="cf2ed-300">Son olarak, önyükleme sonrasında `<link>` , `<link>` uygulamanızın kullandığı yerel stiller için ek öğeler ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-300">Finally, after the Bootstrap `<link>`, add additional `<link>` elements for local styles your app uses.</span></span> <span data-ttu-id="cf2ed-301">*EShop* için sonuç burada gösterilir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-301">For *eShop*, the result is shown here:</span></span>

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

<span data-ttu-id="cf2ed-302">Öğelerin görünmesi için gereken sırayı öğrenmek için `<link>` , orijinal uygulamanızın IŞLENMIŞ HTML dosyasına bakın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-302">To determine the order in which the `<link>` elements should appear, look at your original app's rendered HTML.</span></span> <span data-ttu-id="cf2ed-303">Alternatif olarak, *eShop* örneği için, uygun sırayı belirten bu kodu içeren *BundleConfig.cs* öğesini gözden geçirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-303">Alternatively, review *BundleConfig.cs*, which for the *eShop* sample includes this code indicating the appropriate sequence:</span></span>

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

<span data-ttu-id="cf2ed-304">Yeniden oluşturma, *oluşturma* ve *düzenleme* görünümlerinde jQuery doğrulaması yüklenirken bir hata daha ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-304">Building again reveals one more error loading jQuery Validation on the *Create* and *Edit* views.</span></span> <span data-ttu-id="cf2ed-305">Bu kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-305">Replace it with this script:</span></span>

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

<span data-ttu-id="cf2ed-306">Görünümlerde düzeltilmek üzere en son şey `Session` , uygulamanın ne kadar süreyle çalıştığını ve hangi makinede olduğunu göstermek için başvuru içerir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-306">The last thing to fix in the views is the reference to `Session` to display how long the app has been running, and on which machine.</span></span> <span data-ttu-id="cf2ed-307">Bu verileri `Startup` statik değişkenler olarak toplayabiliriz ve değişkenleri Düzen sayfasında görüntüleriz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-307">We can collect this data in `Startup` as static variables and display the variables on the layout page.</span></span> <span data-ttu-id="cf2ed-308">Aşağıdaki özellikleri *Startup.cs* öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-308">Add the following properties to *Startup.cs*:</span></span>

```csharp
public static DateTime StartTime { get; } = DateTime.UtcNow;
public static string MachineName { get; } = Environment.MachineName;
```

<span data-ttu-id="cf2ed-309">Sonra, düzen içindeki altbilginin içeriğini aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-309">Then replace the content of the footer in the layout with the following code:</span></span>

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@eShopPorted.Startup.MachineName - @eShopPorted.Startup.StartTime.ToString() UTC</small>
</section>
```

<span data-ttu-id="cf2ed-310">Bu noktada, daha sonra uygulama başarıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-310">At this point, the app once more builds successfully.</span></span> <span data-ttu-id="cf2ed-311">Ancak, bunu çalıştırmaya çalışmak yalnızca Merhaba Dünya verir *!*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-311">However, trying to run it just yields *Hello World!*</span></span> <span data-ttu-id="cf2ed-312">**boş** ASP.NET Core şablonu yalnızca herhangi bir isteğe yanıt olarak görüntülenecek şekilde yapılandırıldığından.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-312">because the **Empty** ASP.NET Core template is only configured to display that in response to any request.</span></span> <span data-ttu-id="cf2ed-313">Sonraki bölümde, bağımlılığı ekleme ve yapılandırma dahil olmak üzere uygulamayı ASP.NET Core MVC kullanacak şekilde yapılandırarak geçişi tamamlayacağım.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-313">In the next section, I complete the migration by configuring the app to use ASP.NET Core MVC, including dependency injection and configuration.</span></span> <span data-ttu-id="cf2ed-314">Bu bir yerde, uygulamanın çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-314">Once that's in place, the app should run.</span></span> <span data-ttu-id="cf2ed-315">Daha sonra, `TODO:` daha önce oluşturulmuş görevlerin düzeltilmesi zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-315">Then it will be time to fix the `TODO:` tasks that were created earlier.</span></span>

## <a name="migrate-app-startup-components"></a><span data-ttu-id="cf2ed-316">Uygulama başlangıç bileşenlerini geçirme</span><span class="sxs-lookup"><span data-stu-id="cf2ed-316">Migrate app startup components</span></span>

<span data-ttu-id="cf2ed-317">Son geçiş adımı, uygulama başlangıç görevlerinin *Global. asax* ve çağrı yaptığı sınıflardan sürme ve bunları ASP.NET Core eşdeğerlerine geçirmekte.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-317">The last migration step is to take the app startup tasks from *Global.asax*, and the classes it calls, and migrate these to their ASP.NET Core equivalents.</span></span> <span data-ttu-id="cf2ed-318">Bu görevler, MVC 'nin yapılandırmasını, bağımlılık ekleme işlemini ayarlamayı ve yeni yapılandırma sistemiyle çalışmayı içerir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-318">These tasks include configuration of MVC itself, setting up dependency injection, and working with the new configuration system.</span></span> <span data-ttu-id="cf2ed-319">ASP.NET Core, bu görevler *Startup.cs* dosyasında işlenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-319">In ASP.NET Core, these tasks are handled in the *Startup.cs* file.</span></span>

### <a name="configure-mvc"></a><span data-ttu-id="cf2ed-320">MVC 'yi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cf2ed-320">Configure MVC</span></span>

<span data-ttu-id="cf2ed-321">Özgün ASP.NET MVC uygulaması, `Application_Start` uygulamanın başlatıldığı zaman çalışan *Global. asax* dosyasında aşağıdaki koda sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-321">The original ASP.NET MVC app has the following code in its `Application_Start` in *Global.asax*, which runs when the app starts up:</span></span>

```csharp
protected void Application_Start()
{
    container = RegisterContainer();
    AreaRegistration.RegisterAllAreas();
    FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
    BundleConfig.RegisterBundles(BundleTable.Bundles);
    ConfigDataBase();
}
```

<span data-ttu-id="cf2ed-322">Bu satırlara tek tek bakarak, `RegisterContainer` yöntemi aşağıda yer alacak bağımlılık ekleme işlemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-322">Looking at these lines one by one, the `RegisterContainer` method sets up dependency injection, which will be ported below.</span></span> <span data-ttu-id="cf2ed-323">Sonraki üç satır MVC 'nin farklı kısımlarını yapılandırır: bölgeler, filtreler ve rotalar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-323">The next three lines configure different parts of MVC: areas, filters, and routes.</span></span> <span data-ttu-id="cf2ed-324">Paketler, bağlantı verilen uygulamadaki statik dosyalarla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-324">Bundles are replaced by static files in the ported app.</span></span> <span data-ttu-id="cf2ed-325">Son satır, daha sonraki bir bölümde gösterilecek olan uygulama için veri erişimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-325">The last line sets up data access for the app, which will be shown in a later section.</span></span>

<span data-ttu-id="cf2ed-326">Bu uygulama aslında alanlar kullandığından, alan kayıt çağrısını geçirmek için yapılması gereken hiçbir şey yok.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-326">Since this app isn't actually using areas, there's nothing that needs to be done to migrate the area registration call.</span></span> <span data-ttu-id="cf2ed-327">Uygulamanızın alan geçirilmesi gerekiyorsa, [docs ASP.NET Core alanların nasıl yapılandırılacağını belirtir](https://docs.microsoft.com/aspnet/core/mvc/controllers/areas).</span><span class="sxs-lookup"><span data-stu-id="cf2ed-327">If your app does need to migrate areas, the [docs specify how to configure areas in ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/controllers/areas).</span></span>

<span data-ttu-id="cf2ed-328">Genel filtreleri kaydetme çağrısı, `FilterConfig` uygulamanın *App_Start* klasöründeki sınıfında bir yardımcı çağırır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-328">The call to register global filters invokes a helper on the `FilterConfig` class in the app's *App_Start* folder:</span></span>

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

<span data-ttu-id="cf2ed-329">Uygulamaya eklenen tek öznitelik ASP.NET MVC filtresidir `HandleErrorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-329">The only attribute added to the app is the ASP.NET MVC filter, `HandleErrorAttribute`.</span></span> <span data-ttu-id="cf2ed-330">Bu filtre, bir isteğin parçası olarak bir özel durum oluştuğunda, özel durum ayrıntıları yerine varsayılan bir eylem ve görünümün görüntülenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-330">This filter ensures that when an exception occurs as part of a request, a default action and view are displayed, rather than the exception details.</span></span> <span data-ttu-id="cf2ed-331">ASP.NET Core, bu işlevsellik, `UseExceptionHandler` Ara yazılım tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-331">In ASP.NET Core, this same functionality is performed by the `UseExceptionHandler` middleware.</span></span> <span data-ttu-id="cf2ed-332">Ayrıntılı hata iletileri varsayılan olarak etkinleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-332">The detailed error messages aren't enabled by default.</span></span> <span data-ttu-id="cf2ed-333">Bunlar, ara yazılım kullanılarak yapılandırılmalıdır `UseDeveloperExceptionPage` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-333">They must be configured using the `UseDeveloperExceptionPage` middleware.</span></span> <span data-ttu-id="cf2ed-334">Bu davranışı özgün uygulamayla eşleşecek şekilde yapılandırmak için, `Configure` *Startup.cs* içinde yönteminin başlangıcına aşağıdaki kod eklenmelidir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-334">To configure this behavior to match the original app, the following code must be added to the start of the `Configure` method in *Startup.cs*:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
    }
    // ...
}
```

<span data-ttu-id="cf2ed-335">Bu, eShop uygulaması tarafından kullanılan tek filtreyi ele alır ve bu durumda yerleşik ara yazılım kullanılarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-335">This takes care of the only filter used by the eShop app, and in this case it was done by using built-in middleware.</span></span> <span data-ttu-id="cf2ed-336">Uygulamanızda yapılandırılması gereken genel filtrelerinizin varsa, bu `ConfigureServices` bölümde daha sonra gösterilen YÖNTEME MVC eklendiğinde bu işlem yapılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-336">If you have global filters that must be configured in your app, this is done when MVC is added in the `ConfigureServices` method, which is shown later in this chapter.</span></span>

<span data-ttu-id="cf2ed-337">Bulunması gereken MVC ile ilgili mantık 'nin en son parçası uygulamanın varsayılan yollardır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-337">The last piece of MVC-related logic that needs to be migrated are the app's default routes.</span></span> <span data-ttu-id="cf2ed-338">`RouteConfig.RegisterRoutes(RouteTable.Routes)` `RegisterRoutes` Aşağıdaki kodun uygulama başlatıldığında YÜRÜTÜLDÜĞÜ, MVC yol tablosunu yardımcı yönteme geçirir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-338">The call to `RouteConfig.RegisterRoutes(RouteTable.Routes)` passes the MVC route table to the `RegisterRoutes` helper method, where the following code is executed when the app starts up:</span></span>

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.MapMvcAttributeRoutes();
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Catalog", action = "Index", id = UrlParameter.Optional }
    );
}
```

<span data-ttu-id="cf2ed-339">Bu kod satırı satır içine alınıyor, ilk satır öznitelik yolları için desteği ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-339">Taking this code line-by-line, the first line sets up support for attribute routes.</span></span> <span data-ttu-id="cf2ed-340">Bu ASP.NET Core yerleşik olarak bulunur, bu nedenle ayrı olarak yapılandırmak gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-340">This is built into ASP.NET Core, so it's unnecessary to configure it separately.</span></span> <span data-ttu-id="cf2ed-341">Benzer şekilde, *{Resource}. axd* dosyaları ASP.NET Core ile kullanılmaz, bu nedenle bu yolların yoksayılmasına gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-341">Likewise, *{resource}.axd* files aren't used with ASP.NET Core, so there's no need to ignore such routes.</span></span> <span data-ttu-id="cf2ed-342">`MapRoute`Yöntemi, tipik yol şablonunu kullanan MVC için varsayılanı yapılandırır `{controller}/{action}/{id}` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-342">The `MapRoute` method configures the default for MVC, which uses the typical `{controller}/{action}/{id}` route template.</span></span> <span data-ttu-id="cf2ed-343">Bu, `CatalogController` varsayılan denetleyicinin kullanıldığı ve `Index` yöntemi varsayılan eylem olduğu gibi, bu şablon için varsayılan değerleri de belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-343">It also specifies the defaults for this template, such that the `CatalogController` is the default controller used and the `Index` method is the default action.</span></span> <span data-ttu-id="cf2ed-344">Daha büyük uygulamalar genellikle `MapRoute` ek rotalar ayarlamak için daha fazla çağrı içerecektir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-344">Larger apps will frequently include more calls to `MapRoute` to set up additional routes.</span></span>

<span data-ttu-id="cf2ed-345">ASP.NET Core MVC [geleneksel yönlendirme ve öznitelik yönlendirmeyi](https://docs.microsoft.com/aspnet/core/mvc/controllers/routing?view=aspnetcore-2.2&preserve-view=true)destekler.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-345">ASP.NET Core MVC supports [conventional routing and attribute routing](https://docs.microsoft.com/aspnet/core/mvc/controllers/routing?view=aspnetcore-2.2&preserve-view=true).</span></span> <span data-ttu-id="cf2ed-346">Geleneksel yönlendirme, yol tablosunun `RegisterRoutes` daha önce listelenen yöntemde nasıl yapılandırıldığına benzer.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-346">Conventional routing is analogous to how the route table is configured in the `RegisterRoutes` method listed previously.</span></span> <span data-ttu-id="cf2ed-347">*EShop* uygulamasında kullanılan gibi varsayılan bir yol ile geleneksel yönlendirmeyi ayarlamak için, `Configure` *Startup.cs* içindeki yönteminin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-347">To set up conventional routing with a default route like the one used in the *eShop* app, add the following code to the bottom of the `Configure` method in *Startup.cs*:</span></span>

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> <span data-ttu-id="cf2ed-348">ASP.NET Core 3,0 ve üzeri ile, bu, uç noktaları kullanacak şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-348">With ASP.NET Core 3.0 and later, this is changed to use endpoints.</span></span> <span data-ttu-id="cf2ed-349">İlk bağlantı noktasının 2,2 ASP.NET Core için, geleneksel yolların eşlenmesiyle ilgili doğru sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-349">For the initial port to ASP.NET Core 2.2, this is the proper syntax for mapping conventional routes.</span></span>

<span data-ttu-id="cf2ed-350">Bu değişiklikler varken, `Configure` yöntemi neredeyse yapılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-350">With these changes in place, the `Configure` method is almost done.</span></span> <span data-ttu-id="cf2ed-351">Merhaba Dünya yazdıran orijinal şablonun `app.Run` yöntemi *!*</span><span class="sxs-lookup"><span data-stu-id="cf2ed-351">The original template's `app.Run` method that prints *Hello World!*</span></span> <span data-ttu-id="cf2ed-352">silinmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-352">should be deleted.</span></span> <span data-ttu-id="cf2ed-353">Bu noktada, yöntemi burada gösterildiği gibidir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-353">At this point, the method is as shown here:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    app.UseStaticFiles();

    app.UseMvc(routes =>
    {
        routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="cf2ed-354">Şimdi MVC hizmetlerini yapılandırmak ve ardından uygulamanın bağımlılık ekleme (DI) desteğinin geri kalanı tarafından sağlananı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-354">Now it's time to configure MVC services, followed by the rest of the app's support for dependency injection (DI).</span></span> <span data-ttu-id="cf2ed-355">Şimdiye kadar, *Esatlamalı* projenin `ConfigureServices` yöntemi boş kaldı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-355">So far, the *eShopPorted* project's `ConfigureServices` method has remained empty.</span></span> <span data-ttu-id="cf2ed-356">Şimdi doldurmaya başlama zamanı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-356">Now it's time to start populating it.</span></span>

<span data-ttu-id="cf2ed-357">İlk olarak, ASP.NET Core MVC 'nin düzgün şekilde çalışmasını sağlamak için, eklenmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-357">First, to get ASP.NET Core MVC to work properly, it needs to be added:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

<span data-ttu-id="cf2ed-358">Yukarıdaki kod, MVC özelliklerinin çalışmasını sağlamak için gereken en düşük yapılandırmadır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-358">The preceding code is the minimal configuration required to get MVC features working.</span></span> <span data-ttu-id="cf2ed-359">Bu çağrıdan yapılandırılanılabilecek birçok ek özellik vardır, ancak şimdilik uygulamayı derlemek yeterli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-359">There are many additional features that can be configured from this call, but for now this will suffice to build the app.</span></span> <span data-ttu-id="cf2ed-360">Bunu çalıştırmak artık varsayılan isteği doğru şekilde yönlendirdik, ancak henüz DI 'yi yapılandırdığımız için, henüz bir `CatalogController` uygulama türü sağlanmadığından bir hata oluştu `ICatalogService` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-360">Running it now routes the default request properly, but since we've not yet configured DI, an error occurs while activating `CatalogController`, because no implementation of type `ICatalogService` has been provided yet.</span></span> <span data-ttu-id="cf2ed-361">MVC 'yi bir süre sonra yapılandırmak için geri döneceğiz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-361">We'll return to configure MVC further in a moment.</span></span> <span data-ttu-id="cf2ed-362">Şimdilik uygulamanın bağımlılık ekleme işlemini geçirelim.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-362">For now, let's migrate the app's dependency injection.</span></span>

#### <a name="migrate-dependency-injection-configuration"></a><span data-ttu-id="cf2ed-363">Bağımlılık ekleme yapılandırmasını geçirme</span><span class="sxs-lookup"><span data-stu-id="cf2ed-363">Migrate dependency injection configuration</span></span>

<span data-ttu-id="cf2ed-364">Orijinal uygulamanın *Global. asax* dosyası, uygulama başladığında çağrılan aşağıdaki yöntemi tanımlar:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-364">The original app's *Global.asax* file defines the following method, called when the app starts up:</span></span>

```csharp
protected IContainer RegisterContainer()
{
  var builder = new ContainerBuilder();

  builder.RegisterControllers(typeof(MvcApplication).Assembly);

  var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
  builder.RegisterModule(new ApplicationModule(mockData));

  var container = builder.Build();
  DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

  return container;
}
```

<span data-ttu-id="cf2ed-365">Bu kod bir [Autofac](https://autofac.org/) kapsayıcısını yapılandırır, gerçek veya sahte verilerin kullanılması gerekip gerekmediğini belirleyecek bir yapılandırma ayarı okur ve bu ayarı bir Autofac modülüne (uygulamanın */modules* dizininde bulunur) geçirir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-365">This code configures an [Autofac](https://autofac.org/) container, reads a config setting to determine whether real or mock data should be used, and passes this setting into an Autofac module (found in the app's */Modules* directory).</span></span> <span data-ttu-id="cf2ed-366">Neyse ki, Autofac .NET Core 'u destekler, bu nedenle modül doğrudan geçirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-366">Fortunately, Autofac supports .NET Core, so the module can be migrated directly.</span></span> <span data-ttu-id="cf2ed-367">Klasörü yeni projeye kopyalayın ve sınıfın ad alanını ve derlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-367">Copy the folder into the new project and updates the class's namespace and it should compile.</span></span>

<span data-ttu-id="cf2ed-368">ASP.NET Core, bağımlılık ekleme için yerleşik desteğe sahiptir, ancak gerekirse Autofac gibi üçüncü taraf bir kapsayıcıyı daha kolay bir şekilde oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-368">ASP.NET Core has built-in support for dependency injection, but you can wire up a third-party container such as Autofac easily if necessary.</span></span> <span data-ttu-id="cf2ed-369">Bu durumda, uygulama zaten Autofac kullanmak üzere yapılandırılmış olduğundan, en basit çözüm kullanımını sürdürmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-369">In this case, since the app is already configured to use Autofac, the simplest solution is to maintain its usage.</span></span> <span data-ttu-id="cf2ed-370">Bunu yapmak için `ConfigureServices` yöntem imzasının bir döndürecek şekilde değiştirilmesi gerekir `IServiceProvider` ve Autofac kapsayıcı örneği yapılandırılmalı ve yönteminden döndürülmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-370">To do so, the `ConfigureServices` method signature must be modified to return an `IServiceProvider`, and the Autofac container instance must be configured and returned from the method.</span></span>

<span data-ttu-id="cf2ed-371">**Note:** .NET Core 3,0 ve üzeri sürümlerde, üçüncü taraf bir dı kapsayıcısını tümleştirme işlemi değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-371">**Note:** In .NET Core 3.0 and later, the process for integrating a third-party DI container has changed.</span></span>

<span data-ttu-id="cf2ed-372">Autofac yapılandırmasının bir bölümü için bir çağrısı gerekir `builder.Populate(services)` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-372">Part of configuring Autofac requires a call to `builder.Populate(services)`.</span></span> <span data-ttu-id="cf2ed-373">Bu uzantı, `Autofac.Extensions.DependencyInjection` kod derlemeden önce yüklenmesi gereken NuGet paketinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-373">This extension is found in the `Autofac.Extensions.DependencyInjection` NuGet package, which must be installed before the code will compile.</span></span>

<span data-ttu-id="cf2ed-374">`ConfigureServices`Bir Autofac kapsayıcısını yapılandırmak için değiştirdikten sonra, yeni yöntem burada gösterildiği gibidir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-374">After modifying `ConfigureServices` to configure an Autofac container, the new method is as shown here:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    bool useMockData = true; // TODO: read from config
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

<span data-ttu-id="cf2ed-375">Şimdilik ayarı `useMockData` olarak ayarlanır `true` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-375">For now, the setting for `useMockData` is set to `true`.</span></span> <span data-ttu-id="cf2ed-376">Bu ayar, bir süre sonra yapılandırmadan okunacak.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-376">This setting will be read from configuration in a moment.</span></span> <span data-ttu-id="cf2ed-377">Bu noktada uygulama, Şekil 4-12 ' de gösterildiği gibi, çalıştırıldığında derlenir ve başarıyla yüklenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-377">At this point, the app compiles and should load successfully when run, as shown in Figure 4-12.</span></span>

![Şekil 4-12](media/Figure4-12.png)

<span data-ttu-id="cf2ed-379">**Şekil 4-12.**</span><span class="sxs-lookup"><span data-stu-id="cf2ed-379">**Figure 4-12.**</span></span> <span data-ttu-id="cf2ed-380">Sahte verilerle yerel olarak çalışan bir bağlantı *noktası* uygulama.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-380">Ported *eShop* app running locally with mock data.</span></span>

#### <a name="migrate-app-settings"></a><span data-ttu-id="cf2ed-381">Uygulama ayarlarını geçirme</span><span class="sxs-lookup"><span data-stu-id="cf2ed-381">Migrate app settings</span></span>

<span data-ttu-id="cf2ed-382">ASP.NET Core yeni bir [yapılandırma sistemi](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/?view=aspnetcore-2.2&preserve-view=true)kullanır ve bu, varsayılan olarak dosya *üzerinde birappsettings.js* yararlanır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-382">ASP.NET Core uses a new [configuration system](https://docs.microsoft.com/aspnet/core/fundamentals/configuration/?view=aspnetcore-2.2&preserve-view=true), which by default leverages an *appsettings.json* file.</span></span> <span data-ttu-id="cf2ed-383">Program.cs ' `CreateDefaultBuilder` de kullanarak varsayılan yapılandırma uygulamada zaten ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-383">By using `CreateDefaultBuilder` in *Program.cs*, the default configuration is already set up in the app.</span></span> <span data-ttu-id="cf2ed-384">Yapılandırmaya erişmek için sınıfların yalnızca kendi kurucusunda istemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-384">To access configuration, classes just need to request it in their constructor.</span></span> <span data-ttu-id="cf2ed-385">`Startup`Sınıf özel durum değildir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-385">The `Startup` class is no exception.</span></span> <span data-ttu-id="cf2ed-386">İçindeki yapılandırmaya `Startup` ve uygulamanın geri kalanına erişmeye başlamak için oluşturucudan bir örneği isteyin `IConfiguration` :</span><span class="sxs-lookup"><span data-stu-id="cf2ed-386">To start accessing configuration in `Startup` and the rest of the app, request an instance of `IConfiguration` from its constructor:</span></span>

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

<span data-ttu-id="cf2ed-387">Özgün uygulamanın ayarlarını kullanarak başvurduğu `ConfigurationManager.AppSettings` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-387">The original app referenced its settings using `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="cf2ed-388">Bu terimin tüm başvuruları için hızlı arama, yeni uygulama gereksinimlerinin ayar kümesini verir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-388">A quick search for all references of this term yields the set of settings the new app needs.</span></span> <span data-ttu-id="cf2ed-389">Yalnızca iki tane vardır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-389">There are only two:</span></span>

- `UseMockData`
- `UseCustomizationData`

<span data-ttu-id="cf2ed-390">Uygulamanızda daha karmaşık bir yapılandırma varsa, özellikle özel yapılandırma bölümleri kullanılıyorsa, büyük olasılıkla nesneleri oluşturup uygulamanızın yapılandırmasının farklı bölümlerine bağlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-390">If your app has more complex configuration, especially if it's using custom configuration sections, you'll probably want to create and bind objects to different parts of your app's configuration.</span></span> <span data-ttu-id="cf2ed-391">Bu türlere daha sonra [Seçenekler deseninin](https://docs.microsoft.com/dotnet/core/extensions/options)kullanılması erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-391">These types can then be accessed using the [options pattern](https://docs.microsoft.com/dotnet/core/extensions/options).</span></span> <span data-ttu-id="cf2ed-392">Ancak, başvurulan belge ' de belirtildiği gibi bu düzenin içinde kullanılmaması gerekir `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-392">However, as noted in the referenced doc, this pattern shouldn't be used in `ConfigureServices`.</span></span> <span data-ttu-id="cf2ed-393">Bunun yerine, bağlantı verilen uygulama `UseMockData` yapılandırma değerine doğrudan başvuracaktır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-393">Instead the ported app will reference the `UseMockData` configuration value directly.</span></span>

<span data-ttu-id="cf2ed-394">İlk olarak, bağlantı verilen uygulamanın `appsettings.json` dosyasını değiştirin ve iki ayarı köke ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-394">First, modify the ported app's `appsettings.json` file and add the two settings in the root:</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "true",
  "UseCustomizationData" :  "true"
}
```

<span data-ttu-id="cf2ed-395">Şimdi, `ConfigureServices` özelliği özelliğinden erişmek için değiştirin `UseMockData` `Configuration` (daha önce değeri olarak ayarlarız `true` ):</span><span class="sxs-lookup"><span data-stu-id="cf2ed-395">Now, modify `ConfigureServices` to access the `UseMockData` setting from the `Configuration` property (where previously we set the value to `true`):</span></span>

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

<span data-ttu-id="cf2ed-396">Bu noktada, ayar yapılandırmadan çekilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-396">At this point, the setting is pulled from configuration.</span></span> <span data-ttu-id="cf2ed-397">Diğer ayarı, `UseCustomizationData` sınıfı tarafından kullanılır `CatalogDBInitializer` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-397">The other setting, `UseCustomizationData`, is used by the `CatalogDBInitializer` class.</span></span> <span data-ttu-id="cf2ed-398">Bu sınıfı ilk kez aldığınızda, erişimi size yorum yaptı `ConfigurationManager.AppSettings["UseCustomizationData"]` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-398">When you first ported this class, you commented out the access to `ConfigurationManager.AppSettings["UseCustomizationData"]`.</span></span> <span data-ttu-id="cf2ed-399">Şimdi de ASP.NET Core yapılandırma kullanmak için değiştirme zamanı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-399">Now it's time to modify it to use ASP.NET Core configuration.</span></span> <span data-ttu-id="cf2ed-400">Yapıcısını `CatalogDBInitializer` aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-400">Modify the constructor of `CatalogDBInitializer` as follows:</span></span>

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

<span data-ttu-id="cf2ed-401">Web uygulaması içindeki yapılandırmaya yapılan tüm erişim, yeni türü kullanmak için bu şekilde değiştirilmelidir `IConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-401">All access to configuration within the web app should be modified in this manner to use the new `IConfiguration` type.</span></span> <span data-ttu-id="cf2ed-402">.NET Framework yapılandırmasına erişim gerektiren bağımlılıklar, web projesine eklenen bir *app.config* dosyasında bu tür ayarları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-402">Dependencies that require access to .NET Framework configuration can include such settings in an *app.config* file added to the web project.</span></span> <span data-ttu-id="cf2ed-403">Bağımlı projeler `ConfigurationManager` , ayarlarına erişmek için ile çalışabilir ve bu yaklaşımı zaten kullanıyorsa herhangi bir değişiklik gerektirmemelidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-403">The dependent projects can work with `ConfigurationManager` to access settings, and shouldn't require any changes if they already use this approach.</span></span> <span data-ttu-id="cf2ed-404">Ancak, ASP.NET Core uygulamalar kendi yürütülebilir dosyası olarak çalıştığı için, *web.config* başvurmazlar, ancak bunun yerine *app.config*. Ayarları eski uygulamanın *web.config* dosyasından ASP.NET Core uygulamasındaki yeni bir *app.config* dosyasına geçirerek, `ConfigurationManager` ayarlarına erişmek için kullanılan bileşenler düzgün şekilde çalışmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-404">However, since ASP.NET Core apps run as their own executable, they don't reference *web.config* but rather *app.config*. By migrating settings from the legacy app's *web.config* file to a new *app.config* file in the ASP.NET Core app, components that use `ConfigurationManager` to access their settings will continue to function properly.</span></span>

<span data-ttu-id="cf2ed-405">Uygulamanın geçişi neredeyse tamamlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-405">The app's migration is nearly complete.</span></span> <span data-ttu-id="cf2ed-406">Kalan tek görev, veri erişim yapılandırması.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-406">The only remaining task is data access configuration.</span></span>
  
## <a name="data-access-considerations"></a><span data-ttu-id="cf2ed-407">Veri erişim konuları</span><span class="sxs-lookup"><span data-stu-id="cf2ed-407">Data access considerations</span></span>

<span data-ttu-id="cf2ed-408">.NET Framework çalıştıran ASP.NET Core uygulamalar Entity Framework (EF) ile yararlanmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-408">ASP.NET Core apps running on .NET Framework can continue to leverage Entity Framework (EF).</span></span> <span data-ttu-id="cf2ed-409">Artımlı geçiş gerçekleştirmede, uygulamanın veri erişiminin bağlantı noktasında kullanım için bağlantı kurmaya çalışmadan önce EF 6 ile çalışmaya alınması EF Core çalışıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-409">If performing an incremental migration, getting the app working with EF 6 before trying to port its data access to use EF Core may be worthwhile.</span></span> <span data-ttu-id="cf2ed-410">Bu şekilde, başka bir geçiş çabasında başlamadan önce uygulamanın geçişine ilişkin herhangi bir sorun belirlenebilir ve çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-410">In this way, any problems with the app's migration can be identified and addressed before another block of migration effort is begun.</span></span>

<span data-ttu-id="cf2ed-411">Bu durumda, bu iş Autofac içinde gerçekleştirildiğinden, eShop örnek geçişinin içindeki EF 6 ' ı yapılandırmak özel bir iş gerektirmez `ApplicationModule` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-411">As it happens, configuring EF 6 in the eShop sample migration doesn't require any special work, since this work was performed in the Autofac `ApplicationModule`.</span></span> <span data-ttu-id="cf2ed-412">Tek sorun şu anda `CatalogDBContext` sınıfın *web.config* bağlantı dizesini okumaya çalışacağı bir sorundur. Bunu çözmek için bağlantı ayrıntılarının *appsettings.js* için eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-412">The only problem is that currently the `CatalogDBContext` class tries to read its connection string from *web.config*. To address this, the connection details need to be added to *appsettings.json*.</span></span> <span data-ttu-id="cf2ed-413">Sonra bağlantı dizesinin oluşturulduğu sırada içine geçirilmesi gerekir `CatalogDBContext` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-413">Then the connection string must be passed into `CatalogDBContext` when it's created.</span></span>

<span data-ttu-id="cf2ed-414">Bağlantı dizesini içerecek şekilde *appsettings.js* güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-414">Update the *appsettings.json* to include the connection string.</span></span> <span data-ttu-id="cf2ed-415">Tam dosya burada listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-415">The full file is listed here:</span></span>

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=eShopPorted;Trusted_Connection=True;MultipleActiveResultSets=true"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "false",
  "UseCustomizationData": "true"
}
```

<span data-ttu-id="cf2ed-416">Bağlantı dizesinin oluşturulduğu sırada oluşturucuya geçirilmesi gerekir `DbContext` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-416">The connection string must be passed into the constructor when the `DbContext` is created.</span></span> <span data-ttu-id="cf2ed-417">Örnekler Autofac tarafından oluşturulduğundan, değişikliğin ' de yapılması gerekir `ApplicationModule` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-417">Since the instances are created by Autofac, the change needs to be made in `ApplicationModule`.</span></span> <span data-ttu-id="cf2ed-418">Modülünü oluşturucusunda bir içinde olacak şekilde değiştirin `connectionString` ve bir alana atayın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-418">Modify the module to take in a `connectionString` in its constructor and assign it to a field.</span></span> <span data-ttu-id="cf2ed-419">Sonra `CatalogDBContext` bağlantı dizesini parametre olarak eklemek için kaydını değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-419">Then modify the registration for `CatalogDBContext` to add connection string as a parameter:</span></span>

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

<span data-ttu-id="cf2ed-420">Parametresi ayrıca kendi kendine yeni bir Oluşturucu aşırı yüküne eklenmelidir `CatalogDBContext` :</span><span class="sxs-lookup"><span data-stu-id="cf2ed-420">The parameter must also be added to a new constructor overload in `CatalogDBContext` itself:</span></span>

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

<span data-ttu-id="cf2ed-421">Son olarak, `ConfigureServices` öğesinden bağlantı dizesini okumalı `Config` ve onu `ApplicationModule` örnekleyen zaman içine iletmelidir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-421">Finally, `ConfigureServices` must read the connection string from `Config` and pass it into the `ApplicationModule` when it instantiates it:</span></span>

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

<span data-ttu-id="cf2ed-422">Bu kodla birlikte, uygulama daha önce olduğu gibi çalışır, bir SQL Server veritabanına bağlanarak `UseMockData` `false` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-422">With this code in place, the app runs as it did before, connecting to a SQL Server database when `UseMockData` is `false`.</span></span>

<span data-ttu-id="cf2ed-423">Uygulama bu noktada dağıtılabilir ve çalıştırılabilir, ASP.NET Core dönüştürülür, ancak yine de .NET Framework ve EF 6 ' da çalışır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-423">The app can be deployed and run in production at this point, converted to ASP.NET Core but still running on .NET Framework and EF 6.</span></span> <span data-ttu-id="cf2ed-424">İsterseniz, uygulama .NET Core ve Entity Framework Core çalışmak üzere geçirilebilir ve bu, önceki bölümlerde açıklanan ek avantajları getirir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-424">If desired, the app can be migrated to run on .NET Core and Entity Framework Core, which will bring additional advantages described in earlier chapters.</span></span> <span data-ttu-id="cf2ed-425">Entity Framework özel olarak, [Bu belge EF Core ve EF 6](https://docs.microsoft.com/ef/efcore-and-ef6/) ' ı karşılaştırır ve hangi kitaplığın her bir onlarca ayrı özelliği desteklediğini gösteren bir kılavuz içerir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-425">Specific to Entity Framework, [this documentation compares EF Core and EF 6](https://docs.microsoft.com/ef/efcore-and-ef6/) and includes a grid showing which library supports each of dozens of individual features.</span></span>

### <a name="migrate-to-entity-framework-core"></a><span data-ttu-id="cf2ed-426">Entity Framework Core geçir</span><span class="sxs-lookup"><span data-stu-id="cf2ed-426">Migrate to Entity Framework Core</span></span>

<span data-ttu-id="cf2ed-427">EF Core geçirilecek bir kararın olduğu varsayıldığında, özellikle özgün uygulama kod tabanlı bir model yaklaşımı kullanıyorsa, adımlar oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-427">Assuming a decision is made to migrate to EF Core, the steps can be fairly straightforward, especially if the original app used a code-based model approach.</span></span> <span data-ttu-id="cf2ed-428">[EF 6 ' dan EF Core bağlantı noktasına hazırlarken](https://docs.microsoft.com/ef/efcore-and-ef6/porting/), kullanacağınız EF Core hedef sürümündeki özelliklerin kullanılabilirliğini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-428">When [preparing to port from EF 6 to EF Core](https://docs.microsoft.com/ef/efcore-and-ef6/porting/), review the availability of features in the destination version of EF Core you'll be using.</span></span> <span data-ttu-id="cf2ed-429">[Kod tabanlı bir modelden taşıma](https://docs.microsoft.com/ef/efcore-and-ef6/porting/port-code) [ve edmx tabanlı modelden taşıma ile](https://docs.microsoft.com/ef/efcore-and-ef6/porting/port-edmx) ilgili belgeleri gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-429">Review the documentation on [porting from and EDMX-based model](https://docs.microsoft.com/ef/efcore-and-ef6/porting/port-edmx) versus [porting from a code-based model](https://docs.microsoft.com/ef/efcore-and-ef6/porting/port-code).</span></span>

<span data-ttu-id="cf2ed-430">EF Core 2,2 ' ye yükseltmek için, ilgili temel adımlar uygun NuGet paketlerini ve güncelleştirme ad alanlarını eklemektir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-430">To upgrade to EF Core 2.2, the basic steps involved are to add the appropriate NuGet package(s) and update namespaces.</span></span> <span data-ttu-id="cf2ed-431">Sonra bağlantı dizesinin türüne nasıl geçtiğini `DbContext` ve bunların bağımlılık ekleme için nasıl bağlı olduklarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-431">Then adjust how the connection string is passed to the `DbContext` type and how they're wired up for dependency injection.</span></span>

<span data-ttu-id="cf2ed-432">EF Core, projeye bir paket başvurusu olarak eklenir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-432">EF Core is added as a package reference to the project:</span></span>

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

<span data-ttu-id="cf2ed-433">EF 6 başvurusu kaldırılır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-433">The reference to EF 6 is removed:</span></span>

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

<span data-ttu-id="cf2ed-434">Derleyici ve içindeki hataları rapor eder `CatalogDBContext` `CatalogDBInitializer` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-434">The compiler will report errors in `CatalogDBContext` and `CatalogDBInitializer`.</span></span> <span data-ttu-id="cf2ed-435">`CatalogDbContext` eski ad alanlarının kaldırılıp değiştirilmeleri gerekir `Microsoft.EntityFrameworkCore` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-435">`CatalogDbContext` needs to have the old namespaces removed and replaced with `Microsoft.EntityFrameworkCore`.</span></span> <span data-ttu-id="cf2ed-436">Oluşturucuları kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-436">Its constructors can be removed.</span></span> <span data-ttu-id="cf2ed-437">`DbModelBuilder` ile değiştirilmelidir `ModelBuilder` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-437">`DbModelBuilder` should be replaced with `ModelBuilder`.</span></span> <span data-ttu-id="cf2ed-438">Türleri yapılandırmaya yönelik yardımcı yöntemler, uygulayan ayrı sınıflara taşınır `IEntityTypeConfiguration<T>` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-438">The helper methods for configuring types are moved to separate classes implementing `IEntityTypeConfiguration<T>`.</span></span> <span data-ttu-id="cf2ed-439">Sonra `CatalogDBContext` sınıfın `OnModelCreating` yöntemi yalnızca şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-439">Then the `CatalogDBContext` class's `OnModelCreating` method simply becomes:</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

<span data-ttu-id="cf2ed-440">Dahil edilen diğer değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-440">Other changes involved include:</span></span>

- <span data-ttu-id="cf2ed-441">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` yenisiyle değiştirilmiş `ValueGeneratedNever()`</span><span class="sxs-lookup"><span data-stu-id="cf2ed-441">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` replaced with `ValueGeneratedNever()`</span></span>
- <span data-ttu-id="cf2ed-442">`HasRequired<T>` yenisiyle değiştirilmiş `HasOne<T>`</span><span class="sxs-lookup"><span data-stu-id="cf2ed-442">`HasRequired<T>` replaced with `HasOne<T>`</span></span>
- <span data-ttu-id="cf2ed-443">`Microsoft.EntityFrameworkCore.Relational`Paket yüklendi</span><span class="sxs-lookup"><span data-stu-id="cf2ed-443">Installed `Microsoft.EntityFrameworkCore.Relational` package</span></span>
- <span data-ttu-id="cf2ed-444">`CatalogDBContext` `DbContextOptions` Temel oluşturucuya almak ve iletmek için bir Oluşturucu ekleyin</span><span class="sxs-lookup"><span data-stu-id="cf2ed-444">Add a constructor to `CatalogDBContext` taking `DbContextOptions` and passing it to the base constructor</span></span>

<span data-ttu-id="cf2ed-445">İçin örnek bir yapılandırma sınıfı `CatalogType` aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-445">An example configuration class for `CatalogType` is shown here:</span></span>

```csharp
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata.Builders;

namespace eShopPorted.Models.Config
{
    public class CatalogTypeConfig : IEntityTypeConfiguration<CatalogType>
    {
        public void Configure(EntityTypeBuilder<CatalogType> builder)
        {
            builder.ToTable(nameof(CatalogType));

            builder.HasKey(ci => ci.Id);

            builder.Property(ci => ci.Id)
               .IsRequired();

            builder.Property(cb => cb.Type)
                .IsRequired()
                .HasMaxLength(100);
        }
    }
}
```

<span data-ttu-id="cf2ed-446">`CatalogDBInitializer`Ve temel sınıfı, `CreateDatabaseIfNotExists<T>` EF Core ile uyumsuzdur.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-446">The `CatalogDBInitializer` and its base class, `CreateDatabaseIfNotExists<T>`, are incompatible with EF Core.</span></span> <span data-ttu-id="cf2ed-447">Bu sınıfın amacı, veritabanını oluşturmak ve tohum sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-447">The purpose of this class is to create and seed the database.</span></span> <span data-ttu-id="cf2ed-448">EF Core kullanmak, bu yöntemleri kullanarak [bir `DbContext` için ilişkili veritabanını oluşturup bırakacak](https://docs.microsoft.com/ef/core/managing-schemas/ensure-created) :</span><span class="sxs-lookup"><span data-stu-id="cf2ed-448">Using EF Core will [create and drop the associated database for a `DbContext`](https://docs.microsoft.com/ef/core/managing-schemas/ensure-created) using these methods:</span></span>

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

<span data-ttu-id="cf2ed-449">EF Core içindeki sağlama verileri el ile betiklerle veya tür yapılandırmasının bir parçası olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-449">Seeding data in EF Core can be done with manual scripts, or as part of the type configuration.</span></span> <span data-ttu-id="cf2ed-450">Diğer varlık özellikleriyle birlikte, çekirdek veriler `IEntityTypeConfiguration` kullanılarak sınıflarda yapılandırılabilir `builder.HasData()` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-450">Along with other entity properties, seed data can be configured in `IEntityTypeConfiguration` classes by using `builder.HasData()`.</span></span> <span data-ttu-id="cf2ed-451">Özgün uygulama, *Kurulum* dizinindeki CSV dosyalarından çekirdek verileri yükledi.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-451">The original app loaded seed data from CSV files in the *Setup* directory.</span></span> <span data-ttu-id="cf2ed-452">Yalnızca birkaç öğe olduğu verildiğine göre, bu veri kayıtları varlık yapılandırmasının bir parçası olarak eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-452">Given that there are only a handful of items, these data records can instead be added as part of the entity configuration.</span></span> <span data-ttu-id="cf2ed-453">Bu yaklaşım, seyrek olarak değişen tablolardaki arama verileri için iyi sonuç verir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-453">This approach works well for lookup data in tables that change infrequently.</span></span> <span data-ttu-id="cf2ed-454">Aşağıdaki ' `CatalogTypeConfig` ın metodunu eklemek, `Configure` veritabanı oluşturulduğunda ilişkili satırların mevcut olmasını sağlar:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-454">Adding the following to `CatalogTypeConfig`'s `Configure` method ensures the associated rows are present when the database is created:</span></span>

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

<span data-ttu-id="cf2ed-455">İlk uygulama, `PreconfiguredData` ve için veri içeren bir sınıfı içerir `CatalogBrand` `CatalogType` , bu nedenle bu yöntemi kullanarak çağrı şu `HasData` şekilde azaltılır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-455">The initial app includes a `PreconfiguredData` class, which includes data for `CatalogBrand` and `CatalogType`, so using this method the `HasData` call reduces to:</span></span>

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

<span data-ttu-id="cf2ed-456">`CatalogItem`Verilerin de çekilmesi `PreconfiguredData` ve ilişkili görüntülerin kaynak denetimde tutulup tutulmalarından ve uygulamanın çalışması için gereken son tablo olduğu varsayıldığında.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-456">The `CatalogItem` data can also be pulled from `PreconfiguredData`, and assuming the associated images are kept in source control, that is the last table needed for the app to function.</span></span> <span data-ttu-id="cf2ed-457">`CatalogDBInitializer`Sınıfı, tüm başvuruları ile birlikte kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-457">The `CatalogDBInitializer` class can be removed, along with any references to it.</span></span> <span data-ttu-id="cf2ed-458">Bu `CatalogItemHiLoGenerator` sınıf ve DIZINDEKI SQL dosyaları `Infrastructure` , bunlara yapılan başvurularla birlikte da kaldırılır (içinde `CatalogService` `ApplicationModule` ).</span><span class="sxs-lookup"><span data-stu-id="cf2ed-458">The `CatalogItemHiLoGenerator` class and the SQL files in the `Infrastructure` directory are also removed, along with any references to them (in `CatalogService`, `ApplicationModule`).</span></span>

<span data-ttu-id="cf2ed-459">İçin özel anahtar Oluşturucu sınıflarının yok etme özelliğiyle `CatalogItem` , bu kod şu kaynaktan kaldırılmıştır `CatalogItemConfig` :</span><span class="sxs-lookup"><span data-stu-id="cf2ed-459">With the elimination of the special key generator classes for `CatalogItem`, this code now is removed from `CatalogItemConfig`:</span></span>

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

<span data-ttu-id="cf2ed-460">Bu değişikliklerle ASP.NET Core uygulaması oluşturulur, ancak yine de bağımlılık ekleme için yapılandırılması gereken EF Core çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-460">With these modifications, the ASP.NET Core app builds, but it doesn't yet work with EF Core, which must still be configured for dependency injection.</span></span> <span data-ttu-id="cf2ed-461">EF Core ile, yapılandırmanın en kolay yolu `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="cf2ed-461">With EF Core, the simplest way to configure it is in `ConfigureServices`:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    bool useMockData = Configuration.GetValue<bool>("UseMockData");
    if (!useMockData)
    {
        string connectionString = Configuration.GetConnectionString("DefaultConnection");

        services.AddDbContext<CatalogDBContext>(options =>
            options.UseSqlServer(connectionString)
        );
    }

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

<span data-ttu-id="cf2ed-462">Autofac 'in son sürümü `ApplicationModule` , uygulamanın sahte verileri kullanmak üzere yapılandırılıp yapılandırılmadığını bağlı olarak yalnızca bir tür yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-462">The final version of Autofac's `ApplicationModule` only configures one type, depending on whether the app is configured to use mock data:</span></span>

```csharp
public class ApplicationModule : Module
{
    private bool _useMockData;

    public ApplicationModule(bool useMockData)
    {
        _useMockData = useMockData;
    }

    protected override void Load(ContainerBuilder builder)
    {
        if (_useMockData)
        {
            builder.RegisterType<CatalogServiceMock>()
                .As<ICatalogService>()
                .SingleInstance();
        }
        else
        {
            builder.RegisterType<CatalogService>()
                .As<ICatalogService>()
                .InstancePerLifetimeScope();
        }
    }
}
```

<span data-ttu-id="cf2ed-463">Çapraz olmayan uygulama çalışır, ancak sahte verileri kullanmak üzere yapılandırıldıysa hiçbir veri görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-463">The ported app runs, but doesn't display any data if configured to use non-mock data.</span></span> <span data-ttu-id="cf2ed-464">Üzerinden eklenen çekirdek veriler `HasData` yalnızca geçişler uygulandığında eklenir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-464">The seed data added through `HasData` is only inserted when migrations are applied.</span></span> <span data-ttu-id="cf2ed-465">Kaynak uygulama geçişleri kullanmamıştı ve varsa, olarak geçirilmez.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-465">The source app didn't use migrations, and if it had, they wouldn't migrate as-is.</span></span> <span data-ttu-id="cf2ed-466">En iyi yaklaşım, yeni bir geçiş betiği ile başlamadır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-466">The best approach is to start with a new migration script.</span></span> <span data-ttu-id="cf2ed-467">Bunu yapmak için, için bir paket başvurusu ekleyin `Microsoft.EntityFrameworkCore.Design` ve proje kökünde bir Terminal penceresi açın.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-467">To do this, add a package reference for `Microsoft.EntityFrameworkCore.Design` and open a terminal window in the project root.</span></span> <span data-ttu-id="cf2ed-468">Ardından şunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-468">Then run:</span></span>

```dotnetcli
dotnet ef migrations add Initial
```

<span data-ttu-id="cf2ed-469">Varsa, var olan *Esatlamalı* veritabanını bırakın, ardından şunu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-469">Drop the existing *eShopPorted* database if it exists, then run:</span></span>

```dotnetcli
dotnet ef database update
```

<span data-ttu-id="cf2ed-470">Bu, veritabanını oluşturur ve ekler.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-470">This creates and seeds the database.</span></span> <span data-ttu-id="cf2ed-471">Şimdi, bir kaç küçük güncelleştirme bırakılmış olacak şekilde çalıştırılmaya hazır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-471">It's now ready to run, with a few small updates left to address.</span></span>

## <a name="fix-all-todo-tasks"></a><span data-ttu-id="cf2ed-472">Tüm TODO görevlerini düzeltir</span><span class="sxs-lookup"><span data-stu-id="cf2ed-472">Fix all TODO tasks</span></span>

<span data-ttu-id="cf2ed-473">Bu noktada, bağlantı verilen uygulamayı çalıştırmak sayfada hiçbir resmin gösterildiğine işaret edilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-473">Running the ported app at this point reveals that no pictures are shown on the page.</span></span> <span data-ttu-id="cf2ed-474">Bunun nedeni `PictureUri` öğesinin özelliğinin hiçbir şekilde `CatalogItem` ayarlanmayacağı.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-474">This is because the `PictureUri` property of `CatalogItem` is never set.</span></span> <span data-ttu-id="cf2ed-475">`TODO`Visual Studio 'nun **görev listesi** kullanarak oluşturduğumuz öğelerin listesine bakarak, `CatalogController` "Wwwroot 'dan başvuru PIC" notunda yer alan tek bir tane.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-475">Looking at the list of `TODO` items we created using Visual Studio's **Task List**, the only one that remains is in `CatalogController`, with a note to "Reference pic from wwwroot."</span></span> <span data-ttu-id="cf2ed-476">Söz konusu kod şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-476">The code in question is:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="cf2ed-477">En basit çözüm, sitenin genel *Wwwroot/PICS* dizinindeki ortak görüntü dosyalarına başvurmanız.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-477">The simplest fix is to reference the public image files in the site's public *wwwroot/Pics* directory.</span></span> <span data-ttu-id="cf2ed-478">Bu görev, yöntemi aşağıdaki kodla değiştirilerek gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-478">This task can be accomplished by replacing the method with the following code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

<span data-ttu-id="cf2ed-479">Bu değişiklik ile, uygulamayı çalıştırmak görüntüleri daha önce olduğu gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-479">With this change, running the app reveals the images work as before.</span></span>

## <a name="additional-mvc-customizations"></a><span data-ttu-id="cf2ed-480">Ek MVC özelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="cf2ed-480">Additional MVC customizations</span></span>

<span data-ttu-id="cf2ed-481">*Eshoplegacymvc* uygulaması oldukça basittir, bu nedenle varsayılan MVC davranışı açısından yapılandırılması çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-481">The *eShopLegacyMVC* app is fairly simple, so there isn't much to configure in terms of default MVC behavior.</span></span> <span data-ttu-id="cf2ed-482">Ancak, CORS, filtreler ve yol kısıtlamaları gibi ek MVC bileşenleri yapılandırmanız gerekiyorsa, genellikle bu bilgileri ' de sağlarsınız; `Startup.ConfigureServices` burada `UseMvc` çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-482">However, if you do need to configure additional MVC components, such as CORS, filters, and route constraints, you generally provide this information in `Startup.ConfigureServices`, where `UseMvc` is called.</span></span> <span data-ttu-id="cf2ed-483">Örneğin, aşağıdaki kod listesi [CORS](https://docs.microsoft.com/aspnet/core/security/cors?view=aspnetcore-2.2&preserve-view=true) 'yi yapılandırır ve genel eylem filtresi ayarlıyor:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-483">For example, the following code listing configures [CORS](https://docs.microsoft.com/aspnet/core/security/cors?view=aspnetcore-2.2&preserve-view=true) and sets up a global action filter:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy(MyAllowSpecificOrigins,
            builder =>
                builder.WithOrigins("http://example.com", "http://www.contoso.com")
                    .AllowAnyHeader()
                    .AllowAnyMethod());
    });

    services.AddMvc(options =>
    {
      options.Filters.Add(new SampleGlobalActionFilter());
    }).SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
}
```

> [!Note]
> <span data-ttu-id="cf2ed-484">CORS 'yi yapılandırmayı bitirebilmeniz için de ' de çağırmanız gerekir `app.UseCors()` `Configure` .</span><span class="sxs-lookup"><span data-stu-id="cf2ed-484">To finish configuring CORS, you must also call `app.UseCors()` in `Configure`.</span></span>

<span data-ttu-id="cf2ed-485">[Özel model ciltçileri](https://docs.microsoft.com/aspnet/core/mvc/advanced/custom-model-binding?view=aspnetcore-2.2&preserve-view=true), Formatters ve daha fazlasını ekleme gibi diğer gelişmiş senaryolar, ayrıntılı ASP.NET Core belgeleri kapsamında ele alınmıştır. Genellikle bunlar tek bir denetleyiciye veya eyleme göre veya bir önceki kod listesinde gösterilen aynı seçenek yaklaşımını kullanarak küresel olarak uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-485">Other advanced scenarios, like adding [custom model binders](https://docs.microsoft.com/aspnet/core/mvc/advanced/custom-model-binding?view=aspnetcore-2.2&preserve-view=true), formatters, and more are covered in the detailed ASP.NET Core docs. Generally these can be applied on an individual controller or action basis, or globally using the same options approach shown in the previous code listing.</span></span>

## <a name="other-dependencies"></a><span data-ttu-id="cf2ed-486">Diğer bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="cf2ed-486">Other dependencies</span></span>

<span data-ttu-id="cf2ed-487">WCF istemci türü ve izleme kodu gibi eski yapılandırma modeline bağımlılığı olan .NET Framework özellikleri kullanan bağımlılıklar, bu sırada değiştirilmeli.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-487">Dependencies that use .NET Framework features that had a dependency on the legacy configuration model, such as the WCF client type and tracing code, must be modified when ported.</span></span> <span data-ttu-id="cf2ed-488">Bu türlerin yapılandırma bilgilerini doğrudan çekmesini yerine, kod içinde yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-488">Rather than having these types pull in their configuration information directly, they should be configured in code.</span></span> <span data-ttu-id="cf2ed-489">Örneğin, bir ASP.NET uygulamasının kullanılmak üzere *web.config* YAPıLANDıRıLMıŞ bir WCF hizmetine bağlantı, `basicHttpBinding` bunun yerine aşağıdaki kodla programlı olarak yapılandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="cf2ed-489">For example, a connection to a WCF service that was configured in an ASP.NET app's *web.config* to use `basicHttpBinding` could instead be configured programmatically with the following code:</span></span>

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

<span data-ttu-id="cf2ed-490">Ayarları için yapılandırma dosyalarına güvenmek yerine, WCF istemcileri ve diğer .NET Framework türleri kodda belirtilen ayarlara sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-490">Rather than relying on config files for its settings, WCF clients and other .NET Framework types should have their settings specified in code.</span></span> <span data-ttu-id="cf2ed-491">Bu şekilde yapılandırıldığında, bu türler ASP.NET Core 2,2 uygulamalarında çalışmaya devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="cf2ed-491">Configured in this manner, these types can continue to work in ASP.NET Core 2.2 apps.</span></span>

## <a name="references"></a><span data-ttu-id="cf2ed-492">Başvurular</span><span class="sxs-lookup"><span data-stu-id="cf2ed-492">References</span></span>

- [<span data-ttu-id="cf2ed-493">GitHub deposu için Eshopmodernize</span><span class="sxs-lookup"><span data-stu-id="cf2ed-493">eShopModernizing GitHub repository</span></span>](https://github.com/dotnet-architecture/eShopModernizing)
- [<span data-ttu-id="cf2ed-494">API ve Viewmodelleriniz etki alanı modellerine başvurmamalıdır</span><span class="sxs-lookup"><span data-stu-id="cf2ed-494">Your API and ViewModels Should Not Reference Domain Models</span></span>](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [<span data-ttu-id="cf2ed-495">Geliştirici özel durum sayfası ara yazılımı</span><span class="sxs-lookup"><span data-stu-id="cf2ed-495">Developer Exception Page Middleware</span></span>](https://docs.microsoft.com/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [<span data-ttu-id="cf2ed-496">HasData EF Core derinlemesine bakış</span><span class="sxs-lookup"><span data-stu-id="cf2ed-496">Deep Dive into EF Core HasData</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
><span data-ttu-id="cf2ed-497">[Önceki](more-migration-scenarios.md) 
> [Sonraki](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="cf2ed-497">[Previous](more-migration-scenarios.md)
[Next](deployment-scenarios.md)</span></span>
