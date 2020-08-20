---
title: .NET Core 3.1’e geçiş örneği
description: .NET Framework Hedefleme örnek uygulamaların .NET Core 3,1 ' ye nasıl geçirileceği gösteriliyor.
ms.date: 05/12/2020
ms.openlocfilehash: 6a0311e9aaeb25ac39f3394d3a62e17046fe03d8
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656768"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="7339d-103">.NET Core 3.1’e geçiş örneği</span><span class="sxs-lookup"><span data-stu-id="7339d-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="7339d-104">Bu bölümde, var olan uygulamanızın .NET Framework .NET Core 'a geçişini gerçekleştirmenize yardımcı olacak pratik yönergeler sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="7339d-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="7339d-105">İzleyebileceğiniz bir işlem ve her adımda göz önünde bulundurmanız gereken en önemli noktalar sunuyoruz.</span><span class="sxs-lookup"><span data-stu-id="7339d-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="7339d-106">Ardından, hem WinForms hem de WPF sürümlerinden örnek bir masaüstü uygulaması için adım adım geçiş sürecini belgeliyoruz.</span><span class="sxs-lookup"><span data-stu-id="7339d-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="7339d-107">Geçiş işlemine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7339d-107">Migration process overview</span></span>

<span data-ttu-id="7339d-108">Geçiş işlemi dört sıralı adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="7339d-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="7339d-109">**Hazırlık**: projenin, nelerin ilerimize dair bir fikir sahibi olması için bağımlılıkları anlayın.</span><span class="sxs-lookup"><span data-stu-id="7339d-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="7339d-110">Bu adımda, geçerli projeyi geçiş için başlangıç noktasını basitleştiren bir duruma getirin.</span><span class="sxs-lookup"><span data-stu-id="7339d-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="7339d-111">**Proje dosyasını geçirme:** .NET Core PROJELERI yeni SDK stili proje biçimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7339d-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="7339d-112">Bu biçimle yeni bir proje dosyası oluşturun veya SDK stilini kullanmak için sahip olduğunuz güncelleştirmeyi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7339d-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="7339d-113">**Kodu ve derlemeyi onarma:** .NET Core 'da, .NET Framework ve .NET Core arasındaki API düzeyi farklılıklar hakkında kod oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7339d-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="7339d-114">Gerekirse, üçüncü taraf paketleri .NET Core 'u destekleyen olanlarla güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7339d-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="7339d-115">**Çalıştır ve test et:** Çalışma zamanına kadar gösterilmeyebilir farklılıklar olabilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="7339d-116">Bu nedenle, uygulamayı çalıştırmayı unutmayın ve her şeyin beklendiği gibi çalıştığından test edin.</span><span class="sxs-lookup"><span data-stu-id="7339d-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="7339d-117">Hazırlık</span><span class="sxs-lookup"><span data-stu-id="7339d-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="7339d-118">packages.config dosyayı geçir</span><span class="sxs-lookup"><span data-stu-id="7339d-118">Migrate packages.config file</span></span>

<span data-ttu-id="7339d-119">.NET Framework bir uygulamada, dış paketlere yapılan tüm başvurular *packages.config* dosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="7339d-120">.NET Core 'da artık *packages.config* dosyasını kullanma gereksinimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7339d-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="7339d-121">Bunun yerine, uygulamanızın NuGet paketlerini belirtmek için proje dosyasının içindeki [Packagereference](../../core/project-sdk/msbuild-props.md#packagereference) özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7339d-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="7339d-122">Bu nedenle, bir biçimden diğerine geçiş yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="7339d-123">*packages.config* dosyasında bulunan bağımlılıkları alarak ve bunları biçimiyle proje dosyasına geçirerek güncelleştirmeyi el ile yapabilirsiniz `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="7339d-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="7339d-124">Ya da, Visual Studio 'Nun işi sizin yerinize yapmasına izin verebilirsiniz: *packages.config* dosyasına sağ tıklayıp **packages.config Packagereference 'a geçir** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7339d-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="7339d-125">.NET Core 'da her bağımlılık uyumluluğunu doğrulama</span><span class="sxs-lookup"><span data-stu-id="7339d-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="7339d-126">Paket başvurularını geçirdikten sonra her bir başvuruyu uyumluluk için denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="7339d-127">Uygulamanızın [NuGet.org](https://www.nuget.org/)üzerinde kullandığı her bir NuGet paketinin bağımlılıklarını inceleyebilirsiniz. Pakette .NET Standard bağımlılıklar varsa, .NET Core 3,1 tüm .NET Standard sürümlerini [desteklediğinden](../../standard/net-standard.md#net-implementation-support) .NET Core üzerinde çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="7339d-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="7339d-128">Aşağıdaki görüntüde, paket için bağımlılıklar gösterilmektedir `Castle.Windsor` :</span><span class="sxs-lookup"><span data-stu-id="7339d-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Role. Wın_sor paketi için NuGet bağımlılıklarının ekran görüntüsü](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="7339d-130">Paket uyumluluğunu denetlemek için, <https://fuget.org> sürümler ve Bağımlılıklar hakkında daha ayrıntılı bilgi sunan aracı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="7339d-131">Proje, .NET Core 'u desteklemeyen eski paket sürümlerine başvuruyor, ancak bunu destekleyen daha yeni sürümleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="7339d-132">Bu nedenle, paketleri daha yeni sürümlere güncelleştirmek genellikle iyi bir öneriydi.</span><span class="sxs-lookup"><span data-stu-id="7339d-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="7339d-133">Ancak, paket sürümünün güncelleştirilmesi, kodunuzun güncelleştirilmesini zorlayan bazı önemli değişiklikler getirebileceğini göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="7339d-134">Uyumlu bir sürüm bulamazsanız ne olur?</span><span class="sxs-lookup"><span data-stu-id="7339d-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="7339d-135">Bu son değişiklikler nedeniyle bir paketin sürümünü güncelleştirmek istemiyorsanız ne yapmanız gerekir?</span><span class="sxs-lookup"><span data-stu-id="7339d-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="7339d-136">Endişelenmeyin çünkü bir .NET Core uygulamasından .NET Framework paketlerine bağlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="7339d-137">Dış paket .NET Core 'da kullanılamayan bir API 'YI çağırırsa, çalışma zamanı hatalarına neden olabileceğinden, bunu kapsamlı olarak sınamayı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7339d-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="7339d-138">Bu, güncelleştirileymeyen eski bir paket kullanırken ve yalnızca .NET Core üzerinde çalışacak şekilde yeniden hedefleyecekseniz için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="7339d-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="7339d-139">API uyumluluğunu denetle</span><span class="sxs-lookup"><span data-stu-id="7339d-139">Check for API compatibility</span></span>

<span data-ttu-id="7339d-140">.NET Framework ve .NET Core 'daki API yüzeyi benzer ancak özdeş olduğundan, .NET Core 'da hangi API 'Lerin kullanılabilir olduğunu ve hangilerinin olmadığını denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="7339d-141">.NET Core üzerinde mevcut olmayan kullanılan API 'Leri kullanarak .NET taşınabilirlik Çözümleyicisi aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="7339d-142">Uygulamanızın ikili düzeyine bakar, çağrılan tüm API 'Leri ayıklar ve hedef çerçeveinizdeki hangi API 'Lerin kullanılabilir olduğunu listeler (Bu durumda .NET Core 3,1).</span><span class="sxs-lookup"><span data-stu-id="7339d-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="7339d-143">Bu araçla ilgili daha fazla bilgiyi şurada bulabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7339d-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="7339d-144">Bu aracın ilginç bir yönü, yalnızca kendi kodunuzla gelen farkları değil, farklı bir şekilde değişiklik yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7339d-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="7339d-145">Bu paketlerin çoğunu .NET Core ile çalışacak şekilde güncelleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="7339d-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="7339d-146">Proje dosyasını geçir</span><span class="sxs-lookup"><span data-stu-id="7339d-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="7339d-147">Yeni .NET Core projesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="7339d-147">Create the new .NET Core project</span></span>

<span data-ttu-id="7339d-148">Çoğu durumda, mevcut projenizi yeni .NET Core biçimiyle güncellemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="7339d-149">Bununla birlikte, eskisini koruyarak da yeni bir proje oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="7339d-150">Eski projeyi güncelleştirmeden asıl dezavantajı, tasarımcı desteğini kaybetmeniz ve sizin için önemli olabilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="7339d-151">Tasarımcıyı kullanmaya devam etmek istiyorsanız, eski bir .NET Core projesi oluşturup eskisiyle ve paylaşma varlıklarıyla paralel olarak oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="7339d-152">Tasarımcıda Kullanıcı arabirimi öğelerini değiştirmeniz gerekiyorsa, bunu yapmak için eski projeye geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="7339d-153">Varlıklar bağlı olduğundan, .NET Core projesinde de güncelleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="7339d-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="7339d-154">.NET Core için [SDK stili proje](../../core/project-sdk/msbuild-props.md) , .NET Framework proje biçiminden daha basittir.</span><span class="sxs-lookup"><span data-stu-id="7339d-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="7339d-155">Daha önce bahsedilen `PackageReference` girdilerden ayrı olarak, çok daha fazlasını yapmanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="7339d-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="7339d-156">Yeni proje biçimi, [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects) `.cs` `.xaml` dosyaları proje dosyasına açıkça dahil etmek zorunda kalmadan, ve gibi belirli dosya uzantılarını varsayılan olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="7339d-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="7339d-157">Assembly.info konuları</span><span class="sxs-lookup"><span data-stu-id="7339d-157">Assembly.info considerations</span></span>

<span data-ttu-id="7339d-158">Öznitelikler .NET Core projelerinde otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7339d-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="7339d-159">Proje bir *AssemblyInfo.cs* dosyası içeriyorsa, tanımlar çoğaltılır ve bu da derleme çakışmalarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7339d-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="7339d-160">Eski *AssemblyInfo.cs* dosyasını silebilir veya aşağıdaki girişi .NET Core proje dosyasına ekleyerek, oto oluşturmayı devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7339d-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="7339d-161">Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="7339d-161">Resources</span></span>

<span data-ttu-id="7339d-162">Gömülü kaynaklar otomatik olarak dahil edilir ancak kaynaklar değildir, bu nedenle kaynakları yeni proje dosyasına geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="7339d-163">Paket başvuruları</span><span class="sxs-lookup"><span data-stu-id="7339d-163">Package references</span></span>

<span data-ttu-id="7339d-164">packages.config, **PackageReference 'A geçir** seçeneğiyle, dış paket başvurularınızı daha önce belirtildiği gibi yeni biçime kolayca taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="7339d-165">Paket başvurularını Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="7339d-165">Update package references</span></span>

<span data-ttu-id="7339d-166">Bulduğunuz paketlerin sürümlerini, önceki bölümde gösterildiği gibi güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="7339d-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="7339d-167">Kodu ve derlemeyi düzeltir</span><span class="sxs-lookup"><span data-stu-id="7339d-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="7339d-168">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="7339d-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="7339d-169">Uygulamanız, kayıt defteri, ACL 'Ler veya WCF gibi .NET Core üzerinde kullanılamayan API 'Lere bağımlıysa, `Microsoft.Windows.Compatibility` Bu Windows 'a özgü API 'leri eklemek için pakete bir başvuru eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="7339d-170">Bunlar .NET Core üzerinde çalışır, ancak platformlar arası olmadıkları sürece dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="7339d-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="7339d-171"><https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>Kodunuzla uyumlu olmayan API 'leri tanımanıza yardımcı olan API Çözümleyicisi () adlı bir araç vardır.</span><span class="sxs-lookup"><span data-stu-id="7339d-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="7339d-172">\#IF yönergeleri kullanın</span><span class="sxs-lookup"><span data-stu-id="7339d-172">Use \#if directives</span></span>

<span data-ttu-id="7339d-173">.NET Framework ve .NET Core 'u hedeflerken farklı yürütme yollarına ihtiyacınız varsa, derleme sabitleri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="7339d-174">\#Aynı kod tabanını her iki hedef için de tutmak üzere kodunuza bazı if yönergeleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7339d-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="7339d-175">.NET Core 'da sunulan teknolojiler</span><span class="sxs-lookup"><span data-stu-id="7339d-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="7339d-176">Bazı teknolojiler .NET Core üzerinde kullanılamaz, örneğin:</span><span class="sxs-lookup"><span data-stu-id="7339d-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="7339d-177">Uygulama</span><span class="sxs-lookup"><span data-stu-id="7339d-177">AppDomains</span></span>
* <span data-ttu-id="7339d-178">Uzaktan iletişim</span><span class="sxs-lookup"><span data-stu-id="7339d-178">Remoting</span></span>
* <span data-ttu-id="7339d-179">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7339d-179">Code Access Security</span></span>
* <span data-ttu-id="7339d-180">WCF sunucusu</span><span class="sxs-lookup"><span data-stu-id="7339d-180">WCF Server</span></span>
* <span data-ttu-id="7339d-181">Windows Iş akışı</span><span class="sxs-lookup"><span data-stu-id="7339d-181">Windows Workflow</span></span>

<span data-ttu-id="7339d-182">Bu nedenle, bunları uygulamanızda kullanıyorsanız bu teknolojilerin yerini bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="7339d-183">Daha fazla bilgi için bkz. [.NET Core 'da .NET Framework teknolojileri kullanılamıyor](../../core/porting/net-framework-tech-unavailable.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="7339d-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="7339d-184">Otomatik olarak oluşturulan istemcileri yeniden üret</span><span class="sxs-lookup"><span data-stu-id="7339d-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="7339d-185">Uygulamanız bir WCF istemcisi gibi otomatik olarak oluşturulmuş kod kullanıyorsa, .NET Core 'u hedeflemek için bu kodu yeniden oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="7339d-186">Bazen, bazı eksik başvuruları, varsayılan .NET Core derlemeleri kümesinin bir parçası olarak eklendiklerinden da bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="7339d-187">Gibi bir araç kullanarak <https://apisof.net/> , eksik başvurunun bulunduğu derlemeyi kolayca bulabilir ve NuGet 'ten ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="7339d-188">Paket sürümleri geri alınıyor</span><span class="sxs-lookup"><span data-stu-id="7339d-188">Rolling back package versions</span></span>

<span data-ttu-id="7339d-189">Genel bir kural olarak, .NET Core ile uyumlu olmak için her tek paket sürümünü daha iyi güncelleştirdiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="7339d-190">Bununla birlikte, bir derlemenin güncelleştirilmiş ve uyumlu bir sürümünü hedefleme için yalnızca ödeme yapmayın.</span><span class="sxs-lookup"><span data-stu-id="7339d-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="7339d-191">Değişiklik maliyeti kabul edilebilir değilse, paket sürümlerinin .NET Framework ' de kullandıklarınızı tutarak geri almasını düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="7339d-192">.NET Core hedeflenmese de, desteklenmeyen bazı API 'Ler çağrıdıkça iyi çalışmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7339d-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="7339d-193">Çalıştırma ve test etme</span><span class="sxs-lookup"><span data-stu-id="7339d-193">Run and test</span></span>

<span data-ttu-id="7339d-194">Uygulamanızın hatasız olarak oluşturulmasını sağlayarak, her işlevselliği test ederek geçişin son adımını başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="7339d-195">Bu son adımda, uygulamanızın karmaşıklığına ve kullanmakta olduğunuz bağımlılıklara ve API 'Lere bağlı olarak çeşitli farklı sorunlar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="7339d-196">Örneğin, yapılandırma dosyalarını (*app.config*) kullanıyorsanız, çalışma zamanında yapılandırma bölümlerinin olmadığı gibi bazı hatalar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="7339d-197">`Microsoft.Extensions.Configuration`NuGet paketinin kullanılması bu hatayı düzeltir.</span><span class="sxs-lookup"><span data-stu-id="7339d-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="7339d-198">Hatalar için bir diğer neden, `BeginInvoke` `EndInvoke` .NET Core üzerinde desteklenmediğinden ve yöntemlerinin kullanılmasının bir nedenidir.</span><span class="sxs-lookup"><span data-stu-id="7339d-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="7339d-199">.NET Core üzerinde mevcut olmayan bir uzaktan Iletişim bağımlılığı olduğundan, .NET Core üzerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7339d-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="7339d-200">Bu sorunu gidermek için `await` anahtar sözcüğünü (kullanılabilir olduğunda) veya yöntemini kullanmayı deneyin <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7339d-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7339d-201">Kodunuzda .NET Core ile çalışma zamanında sorunlara neden olabilecek API 'Leri ve kod düzenlerini tanımlamanızı sağlamak için uyumluluk Çözümleyicileri ' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="7339d-202"><https://github.com/dotnet/platform-compat>' A gidin ve projenizde .NET API Çözümleyicisi ' ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="7339d-202">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="7339d-203">Windows Forms uygulamasını geçirme</span><span class="sxs-lookup"><span data-stu-id="7339d-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="7339d-204">Bir Windows Forms uygulamasının tüm geçiş sürecini göstermek için, ' de bulunan eShop örnek uygulamasını geçirmeyi seçtik <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="7339d-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="7339d-205">Geçişin tüm sonucunu ' de bulabilirsiniz <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="7339d-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="7339d-206">Bu uygulama bir ürün kataloğu gösterir ve kullanıcının ürünlere gezinme, filtre uygulama ve arama yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="7339d-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="7339d-207">Bir mimari görünümünden uygulama, bir arka uç veritabanına façlade görevi gören bir dış WCF hizmetini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7339d-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="7339d-208">Ana uygulama penceresini aşağıdaki resimde görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7339d-208">You can see the main application window in the following picture:</span></span>

![Ana uygulama penceresi](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="7339d-210">*. Csproj* proje dosyasını açarsanız şuna benzer bir şey görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7339d-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![CSPROJ dosya içeriğinin ekran görüntüsü](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="7339d-212">Daha önce belirtildiği gibi, .NET Core projesi daha kompakt bir stile sahiptir ve proje yapısını yeni .NET Core SDK stiline geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="7339d-213">Çözüm Gezgini, Windows Forms projesine sağ tıklayın ve **Proje düzenlemeyi kaldır**' ı seçin  >  **Edit**.</span><span class="sxs-lookup"><span data-stu-id="7339d-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="7339d-214">Artık. csproj dosyasını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="7339d-215">İçeriğin tamamını silecek ve aşağıdaki kodla değiştirilecek:</span><span class="sxs-lookup"><span data-stu-id="7339d-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="7339d-216">Projeyi kaydedin ve yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7339d-216">Save and reload the project.</span></span> <span data-ttu-id="7339d-217">Artık proje dosyasını güncellemeyi tamamladınız ve proje .NET çekirdeğini hedefliyor.</span><span class="sxs-lookup"><span data-stu-id="7339d-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="7339d-218">Projeyi bu noktada derlerseniz, WCF istemci başvurusuyla ilgili bazı hatalar bulacaksınız.</span><span class="sxs-lookup"><span data-stu-id="7339d-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="7339d-219">Bu kod otomatik olarak oluşturulduğundan, .NET Core 'u hedeflemek için yeniden oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Visual Studio 'da derleme hatalarının ekran görüntüsü](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="7339d-221">*Reference.cs* dosyasını silin ve yeni bir hizmet istemcisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7339d-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="7339d-222">**Bağlı hizmetler** ' e sağ tıklayın ve **bağlı hizmet ekle** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7339d-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Bağlı hizmet ekle seçeneği belirlenmiş olan bağlı hizmetler menüsünün ekran görüntüsü](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="7339d-224">Bağlı hizmetler penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="7339d-224">The Connected Services window opens.</span></span> <span data-ttu-id="7339d-225">**MICROSOFT WCF Web hizmeti** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="7339d-225">Select the **Microsoft WCF Web Service** option.</span></span>

![Bağlı hizmetler penceresinin ekran görüntüsü](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="7339d-227">Bu örnekteki aynı çözümde WCF hizmeti varsa, bir hizmet URL 'SI belirtmek yerine **bulma** seçeneğini belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![WCF Web hizmeti başvurusunu Yapılandır penceresinin ekran görüntüsü](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="7339d-229">Hizmet konumlandırıldıktan sonra araç, hizmet tarafından uygulanan API sözleşmesini yansıtır.</span><span class="sxs-lookup"><span data-stu-id="7339d-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="7339d-230">Ad alanının adını `eShopServiceReference` aşağıdaki görüntüde gösterildiği gibi olacak şekilde değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7339d-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![API sözleşmesinin ve ad alanının değiştiği ekran görüntüsü](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="7339d-232">**Son** düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="7339d-232">Select the **Finish** button.</span></span> <span data-ttu-id="7339d-233">Bir süre sonra, üretilen kodu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="7339d-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="7339d-234">Üç adet otomatik olarak oluşturulan dosya görmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="7339d-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="7339d-235">*Başlarken*: WCF ile ilgili bazı bilgiler sağlamak için GitHub bağlantısı.</span><span class="sxs-lookup"><span data-stu-id="7339d-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="7339d-236">*ConnectedService.js*: hizmete bağlanmak için yapılandırma parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7339d-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="7339d-237">*Reference.cs*: gerçek WCF istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="7339d-237">*Reference.cs*: the actual WCF client code.</span></span>

![Otomatik olarak oluşturulan üç dosyayı içeren Çözüm Gezgini penceresinin ekran görüntüsü](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="7339d-239">Yeniden derlerseniz, *yardımcı* klasörü içindeki *. cs* dosyalarından gelen birçok hata görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="7339d-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="7339d-240">Bu klasör .NET Framework sürümünde vardı, ancak eski *. csproj*içinde yer almıyor.</span><span class="sxs-lookup"><span data-stu-id="7339d-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="7339d-241">Ancak, yeni SDK stili projeyle, proje dosyası konumu altında bulunan her kod dosyası varsayılan olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="7339d-242">Diğer bir deyişle, yeni .NET Core projesi, dosyaları *yardımcı* klasörü içinde derlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="7339d-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="7339d-243">Bu klasör gerekli olmadığından, güvenli bir şekilde silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="7339d-244">Projeyi yeniden derleyip çalıştırırsanız, ürün görüntülerini görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="7339d-245">Bu sorun, artık dosyaların yolunun daha az değişmiş olması.</span><span class="sxs-lookup"><span data-stu-id="7339d-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="7339d-246">Bu sorunu gidermek için, yolda aşağıdaki şekilde bir derinlik düzeyi eklemeniz gerekir `CatalogView.cs` :</span><span class="sxs-lookup"><span data-stu-id="7339d-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="7339d-247">şöyle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7339d-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="7339d-248">Bu değişiklikten sonra uygulamanın, .NET Core 'da beklenildiği ve çalıştığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="7339d-249">WPF uygulamasını geçirme</span><span class="sxs-lookup"><span data-stu-id="7339d-249">Migrating a WPF application</span></span>

<span data-ttu-id="7339d-250">`Shop.ClassicWPF`Geçiş işlemini gerçekleştirmek için örnek uygulamayı kullanacağız.</span><span class="sxs-lookup"><span data-stu-id="7339d-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="7339d-251">Aşağıdaki görüntüde geçişten önce uygulamanın ekran görüntüsü gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="7339d-251">The following image shows a screenshot of the app before migration:</span></span>

![Geçişten önceki örnek uygulama](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="7339d-253">Bu uygulama, ürün kataloğu bilgilerini tutmak için yerel bir SQL Server Express veritabanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7339d-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="7339d-254">Bu veritabanına doğrudan WPF uygulamasından erişilir.</span><span class="sxs-lookup"><span data-stu-id="7339d-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="7339d-255">İlk olarak, *. csproj* dosyasını .NET Core uygulamaları tarafından kullanılan yeni SDK stiline güncelleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7339d-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="7339d-256">Windows Forms geçişte açıklanan adımların aynısını kullanacaksınız: projeyi kaldıracaksınız, *. csproj* dosyasını açacak, içeriğini güncelleştirtireceksiniz ve projeyi yeniden yükleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="7339d-257">Bu durumda, *. csproj* dosyasının tüm içeriğini silin ve aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="7339d-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWpf>true</UseWpf>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="7339d-258">Projeyi yeniden yükler ve derlerseniz, şu hatayı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="7339d-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Visual Studio 'da derleme hatalarının ekran görüntüsü](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="7339d-260">Tüm *. csproj* içeriğini sildiyseniz, eski projede mevcut bir proje başvuru belirtimini kaybettiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="7339d-261">Proje başvurusunu geri eklemek için bu satırı *. csproj* dosyasına eklemeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="7339d-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="7339d-262">Ayrıca, **Bağımlılıklar** düğümüne sağ tıklayıp **proje başvurusu Ekle**' yi seçerek Visual Studio 'nun size yardımcı olmasına izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7339d-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="7339d-263">Çözümdeki projeyi seçin ve **Tamam**' a tıklayın:</span><span class="sxs-lookup"><span data-stu-id="7339d-263">Select the project from the solution and click **OK**:</span></span>

![EShop. SqlProvider projesi seçili olan başvuru Yöneticisi iletişim kutusunun ekran görüntüsü](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="7339d-265">Eksik proje başvurusunu ekledikten sonra uygulama, .NET Core 'da beklendiği gibi derlenir ve çalışır.</span><span class="sxs-lookup"><span data-stu-id="7339d-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7339d-266">[Önceki](windows-migration.md) 
> [Sonraki](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="7339d-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
