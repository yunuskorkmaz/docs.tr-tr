---
title: ASP.NET MVC uygulamalarını .NET 5 ' e yükseltme
description: Mevcut bir .NET Framework ASP.NET MVC uygulamasını .NET 5 ' e yükseltmek için .NET Yükseltme Yardımcısı 'nı kullanın. .NET Yükseltme Yardımcısı, bir uygulamayı .NET Framework 'tan .NET 5 ' e geçirmeye yardımcı olan bir CLı aracıdır.
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: 0c9af9e12b78df7c4a2aaed18155f7ee9f02870d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108710"
---
# <a name="upgrade-an-aspnet-mvc-app-to-net-5-with-the-net-upgrade-assistant"></a><span data-ttu-id="e86f3-104">.NET Yükseltme Yardımcısı ile bir ASP.NET MVC uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="e86f3-104">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>

<span data-ttu-id="e86f3-105">[.NET Yükseltme Yardımcısı](upgrade-assistant-overview.md) , .NET Framework ASP.NET MVC uygulamalarını .NET 5 ' e yükseltmeye yardımcı olabilecek bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-105">The [.NET Upgrade Assistant](upgrade-assistant-overview.md) is a command-line tool that can assist with upgrading .NET Framework ASP.NET MVC apps to .NET 5.</span></span> <span data-ttu-id="e86f3-106">Bu makalede aşağıdakiler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e86f3-106">This article provides:</span></span>

* <span data-ttu-id="e86f3-107">.NET Framework ASP.NET MVC uygulamasında aracın nasıl çalıştırılacağını gösteren bir gösterim</span><span class="sxs-lookup"><span data-stu-id="e86f3-107">A demonstration of how to run the tool against a .NET Framework ASP.NET MVC app</span></span>
* <span data-ttu-id="e86f3-108">Sorun giderme ipuçları</span><span class="sxs-lookup"><span data-stu-id="e86f3-108">Troubleshooting tips</span></span>

## <a name="upgrade-net-framework-aspnet-mvc-apps"></a><span data-ttu-id="e86f3-109">.NET Framework ASP.NET MVC uygulamalarını yükseltme</span><span class="sxs-lookup"><span data-stu-id="e86f3-109">Upgrade .NET Framework ASP.NET MVC apps</span></span>

<span data-ttu-id="e86f3-110">Bu bölümde, yeni oluşturulan bir ASP.NET MVC uygulaması için .NET Yükseltme Yardımcısı 'Nın .NET Framework 4.6.1 ile çalıştırılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-110">This section demonstrates running the .NET Upgrade Assistant against a newly created ASP.NET MVC app targeting .NET Framework 4.6.1.</span></span> <span data-ttu-id="e86f3-111">Aracının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [.NET Yükseltme Yardımcısı 'Na genel bakış](upgrade-assistant-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e86f3-111">For more information on how to install the tool, see [Overview of the .NET Upgrade Assistant](upgrade-assistant-overview.md).</span></span>

### <a name="initial-demo-setup"></a><span data-ttu-id="e86f3-112">İlk tanıtım kurulumu</span><span class="sxs-lookup"><span data-stu-id="e86f3-112">Initial demo setup</span></span>

<span data-ttu-id="e86f3-113">.NET Upgrade yardımcısını kendi .NET Framework uygulamanıza karşı çalıştırıyorsanız, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e86f3-113">If you're running the .NET Upgrade Assistant against your own .NET Framework app, you can skip this step.</span></span> <span data-ttu-id="e86f3-114">Bunu yalnızca nasıl çalıştığını görmek için denemek istiyorsanız, bu adımda kullanılacak örnek bir ASP.NET MVC ve Web API (.NET Framework) projesini nasıl ayarlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-114">If you just want to try it out to see how it works, this step shows you how to set up a sample ASP.NET MVC and Web API (.NET Framework) project to use.</span></span>

<span data-ttu-id="e86f3-115">Visual Studio 'yu kullanarak .NET Framework kullanarak yeni bir ASP.NET Web uygulaması projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e86f3-115">Using Visual Studio, create a new ASP.NET Web Application project using .NET Framework.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/new-project.png" alt-text="Visual Studio 'da yeni ASP.NET Web uygulaması projesi":::

<span data-ttu-id="e86f3-117">Projeyi **Aspnetmvctest** olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e86f3-117">Name the project **AspNetMvcTest**.</span></span> <span data-ttu-id="e86f3-118">Projeyi **.NET Framework 4.6.1** kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="e86f3-118">Configure the project to use **.NET Framework 4.6.1**.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/configure-project.png" alt-text="Visual Studio 'da ASP.NET projesini yapılandırma":::

<span data-ttu-id="e86f3-120">Sonraki iletişim kutusunda **MVC** uygulaması ' nı ve ardından **Oluştur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="e86f3-120">In the next dialog, choose **MVC** application, then select **Create**.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/create-mvc-webapi.png" alt-text="Visual Studio 'da ASP.NET MVC projesi oluşturma":::

<span data-ttu-id="e86f3-122">Oluşturulan projeyi ve dosyalarını, özellikle de onun proje dosyalarını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e86f3-122">Review the created project and its files, especially its project file(s).</span></span>

### <a name="run-upgrade-assistant"></a><span data-ttu-id="e86f3-123">Yükseltmeyi Çalıştır-Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="e86f3-123">Run upgrade-assistant</span></span>

<span data-ttu-id="e86f3-124">Bir Terminal açın ve hedef projenin veya çözümün bulunduğu klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="e86f3-124">Open a terminal and navigate to the folder where the target project or solution is located.</span></span> <span data-ttu-id="e86f3-125">`upgrade-assistant`Hedeflemek istediğiniz projenin adını geçirerek komutunu çalıştırın (proje dosyasının yolu geçerli olduğu sürece komutu herhangi bir yerden çalıştırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="e86f3-125">Run the `upgrade-assistant` command, passing in the name of the project you're targeting (you can run the command from anywhere, as long as the path to the project file is valid).</span></span>

```console
upgrade-assistant .\AspNetMvcTest.csproj
```

<span data-ttu-id="e86f3-126">Araç çalışır ve bunu yapacağız adımların bir listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-126">The tool runs and shows you a list of the steps it will do.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/initial-run.png" alt-text=".NET Yükseltme Yardımcısı başlangıç ekranı":::

<span data-ttu-id="e86f3-128">Her adım tamamlandığında, araç, kullanıcının bir sonraki adımı uygulamaya veya atlamaya izin veren bir komut kümesi sağlar, daha fazla ayrıntı için bkz. daha fazla ayrıntı, günlüğü yapılandırma veya işlemden çıkma.</span><span class="sxs-lookup"><span data-stu-id="e86f3-128">As each step is completed, the tool provides a set of commands allowing the user to apply or skip the next step, see more details, configure logging, or exit the process.</span></span> <span data-ttu-id="e86f3-129">Araç, bir adımın hiçbir eylem gerçekleştirmediğini algılarsa, otomatik olarak bu adımı atlar ve gerçekleştirilecek eylemleri olan birine ulaşana kadar sonraki adıma devam eder.</span><span class="sxs-lookup"><span data-stu-id="e86f3-129">If the tool detects that a step will perform no actions, it automatically skips that step and continues to the next step until it reaches one that has actions to perform.</span></span> <span data-ttu-id="e86f3-130">Başka seçim yapılmayacak şekilde <kbd>ENTER</kbd> tuşuna basmak sonraki adımı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-130">Pressing <kbd>Enter</kbd> will perform the next step if no other selection is made.</span></span>

<span data-ttu-id="e86f3-131">Bu örnekte, uygulanan adım her seferinde seçilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-131">In this example, the apply step is chosen each time.</span></span> <span data-ttu-id="e86f3-132">İlk adım projeyi yedeklemedir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-132">The first step is to back up the project.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/backup-project.png" alt-text=".NET Yükseltme Yardımcısı proje yedeklemesi":::

<span data-ttu-id="e86f3-134">Araç, yedekleme için özel bir yol ister ve varsayılan olarak, proje yedeklemesini uzantılı aynı klasöre yerleştirir `.backup` .</span><span class="sxs-lookup"><span data-stu-id="e86f3-134">The tool prompts for a custom path for the backup, or to use the default, which will place the project backup in the same folder with a `.backup` extension.</span></span> <span data-ttu-id="e86f3-135">Aracın bir sonraki adımı, proje dosyasını SDK stiline dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-135">The next step the tool does is to convert the project file to SDK style.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/convert-project.png" alt-text=".NET Yükseltme Yardımcısı projeyi SDK stiline Dönüştür":::

<span data-ttu-id="e86f3-137">Proje biçimi güncelleştirildikten sonra, bir sonraki adım projenin TFı 'sini güncelleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-137">Once the project format has been updated, the next step is to update the TFM of the project.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-tfm.png" alt-text=".NET Yükseltme Yardımcısı projeyi SDK stiline Dönüştür":::

<span data-ttu-id="e86f3-139">Ardından araç, projenin NuGet paketlerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-139">Next, the tool updates the project's NuGet packages.</span></span> <span data-ttu-id="e86f3-140">Birkaç pakete güncelleştirmeler gerekiyor ve yeni bir çözümleyici paketi ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="e86f3-140">Several packages need updates, and a new analyzer package is added.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-nuget-packages.png" alt-text=".NET Yükseltme Yardımcısı güncelleştirme NuGet paketleri":::

<span data-ttu-id="e86f3-142">Paketler güncelleştirildikten sonra, bir sonraki adım, varsa şablon dosyaları eklemektir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-142">Once the packages are updated, the next step is to add template files, if any.</span></span> <span data-ttu-id="e86f3-143">Araç notları, eklenmesi gereken dört beklenen şablon öğesi olduğunu ve sonra bunları eklemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e86f3-143">The tool notes there are four expected template items that must be added, and then adds them.</span></span> <span data-ttu-id="e86f3-144">Bunlar aşağıdaki dosyaları içerir:</span><span class="sxs-lookup"><span data-stu-id="e86f3-144">These include the following files:</span></span>

- `Program.cs`
- `Startup.cs`
- `appsettings.json`
- `appsettings.Development.json`

<span data-ttu-id="e86f3-145">Bu dosyalar, [uygulama başlatma](/aspnet/core/fundamentals/startup) ve [yapılandırma](/aspnet/core/fundamentals/configuration)için ASP.NET Core tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-145">These files are used by ASP.NET Core for [app startup](/aspnet/core/fundamentals/startup) and [configuration](/aspnet/core/fundamentals/configuration).</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/add-template-files.png" alt-text=".NET Yükseltme Yardımcısı şablon dosyaları Ekle":::

<span data-ttu-id="e86f3-147">Ardından araç, yapılandırma dosyalarını geçirir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-147">Next, the tool migrates config files.</span></span> <span data-ttu-id="e86f3-148">Araç, uygulama ayarlarını tanımlar ve desteklenmeyen yapılandırma bölümlerini devre dışı bırakır, sonra `appSettings` yapılandırma değerlerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-148">The tool identifies app settings and disables unsupported configuration sections, then migrates the `appSettings` configuration values.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config.png" alt-text=".NET Yükseltme Yardımcısı geçiş yapılandırması":::

<span data-ttu-id="e86f3-150">Araç, geçiş yaparak yapılandırma dosyalarının geçişini tamamlar `system.web.webPages.razor/pages/namespaces` .</span><span class="sxs-lookup"><span data-stu-id="e86f3-150">The tool completes the migration of config files by migrating `system.web.webPages.razor/pages/namespaces`.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config2.png" alt-text=".NET Yükseltme Yardımcısı geçiş yapılandırması":::

<span data-ttu-id="e86f3-152">Araç, C# başvurularını yeni karşılıklarına geçirmek için bilinen düzeltmeleri uygular.</span><span class="sxs-lookup"><span data-stu-id="e86f3-152">The tool applies known fixes to migrate C# references to their new counterparts.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-csharp.png" alt-text=".NET Yükseltme Yardımcısı C# kaynağını güncelleştir":::

<span data-ttu-id="e86f3-154">Bu son proje olduğundan, sonraki adım "sonraki projeye geç", çözümün tamamını geçirme sürecini tamamlamayı ister.</span><span class="sxs-lookup"><span data-stu-id="e86f3-154">Since this is the last project, the next step, "Move to next project", prompts to complete the process of migrating the entire solution.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/complete-solution.png" alt-text="Çözümü tamamlayan .NET Yükseltme Yardımcısı":::

<span data-ttu-id="e86f3-156">Bu işlem tamamlandıktan sonra proje dosyasını açın ve gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e86f3-156">Once this process has completed, open the project file and review it.</span></span> <span data-ttu-id="e86f3-157">Şu şekilde statik dosyaları arayın:</span><span class="sxs-lookup"><span data-stu-id="e86f3-157">Look for static files like these:</span></span>

```xml
  <ItemGroup>
    <Content Include="fonts\glyphicons-halflings-regular.woff2" />
    <Content Include="fonts\glyphicons-halflings-regular.woff" />
    <Content Include="fonts\glyphicons-halflings-regular.ttf" />
    <Content Include="fonts\glyphicons-halflings-regular.eot" />
    <Content Include="Content\bootstrap.min.css.map" />
    <Content Include="Content\bootstrap.css.map" />
    <Content Include="Content\bootstrap-theme.min.css.map" />
    <Content Include="Content\bootstrap-theme.css.map" />
    <Content Include="Scripts\jquery-3.4.1.slim.min.map" />
    <Content Include="Scripts\jquery-3.4.1.min.map" />
  </ItemGroup>
```

<span data-ttu-id="e86f3-158">Web sunucusu tarafından sunulması gereken statik dosyalar, adlı kök düzeyindeki bir klasör içinde uygun bir klasöre taşınmalıdır `wwwroot` .</span><span class="sxs-lookup"><span data-stu-id="e86f3-158">Static files that should be served by the web server should be moved to an appropriate folder within a root level folder named `wwwroot`.</span></span> <span data-ttu-id="e86f3-159">Ayrıntılar için [ASP.NET Core Içindeki statik dosyalara](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0) bakın.</span><span class="sxs-lookup"><span data-stu-id="e86f3-159">See [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0) for details.</span></span> <span data-ttu-id="e86f3-160">Dosyalar taşındıktan sonra, `<Content>` Proje dosyasındaki bu dosyalara karşılık gelen öğeler silinebilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-160">Once the files have been moved, the `<Content>` elements in the project file corresponding to these files can be deleted.</span></span> <span data-ttu-id="e86f3-161">Aslında, tüm `<Content>` öğeler ve kapsayan grupları kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-161">In fact, all `<Content>` elements and their containing groups can be removed.</span></span> <span data-ttu-id="e86f3-162">Ayrıca, `<PackageReference>` veya gibi bir istemci tarafı Kitaplığı `bootstrap` ve `jQuery` kaldırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-162">Also, any `<PackageReference>` to a client-side library like `bootstrap` or `jQuery` should be removed.</span></span>

<span data-ttu-id="e86f3-163">Varsayılan olarak, proje bir sınıf kitaplığı olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="e86f3-163">By default, the project will be converted as a class library.</span></span> <span data-ttu-id="e86f3-164">İlk satırın `Sdk` özniteliğini olarak değiştirin ve öğesini `Microsoft.NET.Sdk.Web` `<TargetFramework>` olarak ayarlayın `net5.0` .</span><span class="sxs-lookup"><span data-stu-id="e86f3-164">Change the first line's `Sdk` attribute to `Microsoft.NET.Sdk.Web` and set the `<TargetFramework>` to `net5.0`.</span></span> <span data-ttu-id="e86f3-165">Projeyi derleyin.</span><span class="sxs-lookup"><span data-stu-id="e86f3-165">Compile the project.</span></span> <span data-ttu-id="e86f3-166">Bu noktada, hata sayısı oldukça küçük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-166">At this point, the number of errors should be fairly small.</span></span> <span data-ttu-id="e86f3-167">Yeni bir ASP.NET 4.6.1 MVC projesi taşıma sırasında, kalan hatalar klasördeki dosyalara başvurur `App_Start` :</span><span class="sxs-lookup"><span data-stu-id="e86f3-167">When porting a new ASP.NET 4.6.1 MVC project, the remaining errors refer to files in the `App_Start` folder:</span></span>

- <span data-ttu-id="e86f3-168">BundleConfig.cs</span><span class="sxs-lookup"><span data-stu-id="e86f3-168">BundleConfig.cs</span></span>
- <span data-ttu-id="e86f3-169">FilterConfig.cs</span><span class="sxs-lookup"><span data-stu-id="e86f3-169">FilterConfig.cs</span></span>
- <span data-ttu-id="e86f3-170">RouteConfig.cs</span><span class="sxs-lookup"><span data-stu-id="e86f3-170">RouteConfig.cs</span></span>

<span data-ttu-id="e86f3-171">Bu dosyalar-ve tüm `App_Start` klasör-silinebilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-171">These files - and the entire `App_Start` folder - can be deleted.</span></span> <span data-ttu-id="e86f3-172">Benzer şekilde, `Global.asax` ve `Global.asax.cs` dosyaları da kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-172">Likewise, the `Global.asax` and `Global.asax.cs` files can be removed.</span></span>

<span data-ttu-id="e86f3-173">Bu noktada, kalan tek hata paketleme ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-173">At this point the only errors that remain are related to bundling.</span></span> <span data-ttu-id="e86f3-174">[ASP.NET Core içinde paketleme ve küçültmeye yönelik çeşitli yollar](/aspnet/core/migration/mvc?view=aspnetcore-5.0#configure-bundling-and-minification)vardır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-174">There are [several ways to configure bundling and minification in ASP.NET Core](/aspnet/core/migration/mvc?view=aspnetcore-5.0#configure-bundling-and-minification).</span></span> <span data-ttu-id="e86f3-175">Projeniz için en mantıklı şeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="e86f3-175">Choose whatever makes the most sense for your project.</span></span>

## <a name="troubleshooting-tips"></a><span data-ttu-id="e86f3-176">Sorun giderme ipuçları</span><span class="sxs-lookup"><span data-stu-id="e86f3-176">Troubleshooting tips</span></span>

<span data-ttu-id="e86f3-177">.NET Yükseltme Yardımcısı kullanılırken oluşabilecek birçok bilinen sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-177">There are several known problems that can occur when using the .NET Upgrade Assistant.</span></span> <span data-ttu-id="e86f3-178">Bazı durumlarda, bunlar .NET Yükseltme Yardımcısı 'Nın dahili olarak kullandığı [TRY-Convert aracı](https://github.com/dotnet/try-convert) ile ilgili sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-178">In some cases, these are problems with the [try-convert tool](https://github.com/dotnet/try-convert) that the .NET Upgrade Assistant uses internally.</span></span> <span data-ttu-id="e86f3-179">Bu araç daha fazla senaryoyu ele almak için sık sık güncelleştiriliyor, bu nedenle son sürümü kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e86f3-179">This tool is being frequently updated to address more scenarios, so make sure you're using a recent version.</span></span>

- <span data-ttu-id="e86f3-180">**TRY-Convert** aracının yüklü olması ve en az sürüm _0.7.212201_'e güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-180">The **try-convert** tool must be installed and updated to at least version _0.7.212201_.</span></span>
- <span data-ttu-id="e86f3-181">**TRY-Convert** aracının önceki sürümleri özel hedef veya özellik dosyalarını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="e86f3-181">Earlier versions of the **try-convert** tool didn't support custom target or props files.</span></span> <span data-ttu-id="e86f3-182">En son sürüme yükseltirsiniz, bu sorunları el ile ele almanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-182">If you can't upgrade to the latest version, you may need to manually address these issues.</span></span> <span data-ttu-id="e86f3-183">Hedef proje dosyası özel hedeflere veya props dosyalarına başvurular içeriyorsa, .NET Yükseltme Yardımcısı tarafından çalıştırılmadan önce bu başvuruların dosyadan el ile silinmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e86f3-183">If the target project file includes references to custom targets or props files, these references may need to be manually deleted from the file before the .NET Upgrade Assistant is run against it.</span></span>

```xml
<Import Project="packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props" Condition="Exists('packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props')" />
```

<span data-ttu-id="e86f3-184">[Aracın GitHub deposunda,](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) daha fazla sorun giderme ipuçları ve bilinen sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="e86f3-184">[The tool's GitHub repository](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) has more troubleshooting tips and known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="e86f3-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e86f3-185">See also</span></span>

- [<span data-ttu-id="e86f3-186">.NET Yükseltme Yardımcısı ile bir WPF uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="e86f3-186">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-wpf-framework.md)
- [<span data-ttu-id="e86f3-187">.NET Yükseltme Yardımcısı ile bir Windows Forms uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="e86f3-187">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="e86f3-188">.NET Yükseltme Yardımcısı 'na genel bakış</span><span class="sxs-lookup"><span data-stu-id="e86f3-188">Overview of the .NET Upgrade Assistant</span></span>](upgrade-assistant-overview.md)
- [<span data-ttu-id="e86f3-189">.NET Yükseltme Yardımcısı GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="e86f3-189">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
