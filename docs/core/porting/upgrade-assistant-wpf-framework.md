---
title: WPF uygulamalarını .NET 5 ' e yükseltme
description: .NET Framework mevcut bir WPF uygulamasını .NET 5 ' e yükseltmek için .NET Yükseltme Yardımcısı 'nı kullanın. .NET Yükseltme Yardımcısı, bir uygulamayı .NET Framework 'tan .NET 5 ' e geçirmeye yardımcı olan bir CLı aracıdır.
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: b0c9baa25be6da4e7849f28c875a1d8f5f5a5d07
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604846"
---
# <a name="upgrade-a-wpf-app-to-net-5-with-the-net-upgrade-assistant"></a><span data-ttu-id="b7cd9-104">.NET Yükseltme Yardımcısı ile bir WPF uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="b7cd9-104">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>

<span data-ttu-id="b7cd9-105">[.NET Yükseltme Yardımcısı](upgrade-assistant-overview.md) , .NET Framework WPF uygulamalarını .NET 5 ' e yükseltmeye yardımcı olabilecek bir komut satırı aracıdır.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-105">The [.NET Upgrade Assistant](upgrade-assistant-overview.md) is a command-line tool that can assist with upgrading .NET Framework WPF apps to .NET 5.</span></span> <span data-ttu-id="b7cd9-106">Bu makalede aşağıdakiler sunulmaktadır:</span><span class="sxs-lookup"><span data-stu-id="b7cd9-106">This article provides:</span></span>

- <span data-ttu-id="b7cd9-107">.NET Framework WPF uygulamasında aracın nasıl çalıştırılacağını gösteren bir gösterim</span><span class="sxs-lookup"><span data-stu-id="b7cd9-107">A demonstration of how to run the tool against a .NET Framework WPF app</span></span>
- <span data-ttu-id="b7cd9-108">Sorun giderme ipuçları</span><span class="sxs-lookup"><span data-stu-id="b7cd9-108">Troubleshooting tips</span></span>

## <a name="upgrade-net-framework-wpf-apps"></a><span data-ttu-id="b7cd9-109">WPF uygulamalarını .NET Framework yükseltme</span><span class="sxs-lookup"><span data-stu-id="b7cd9-109">Upgrade .NET Framework WPF apps</span></span>

<span data-ttu-id="b7cd9-110">Bu bölümde, 4.6.1 .NET Framework yeni oluşturulan WPF uygulamasında .NET Yükseltme Yardımcısı 'Nın çalıştırılması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-110">This section demonstrates running the .NET Upgrade Assistant against a newly created WPF app targeting .NET Framework 4.6.1.</span></span> <span data-ttu-id="b7cd9-111">Aracının nasıl yükleneceği hakkında daha fazla bilgi için bkz. [.NET Yükseltme Yardımcısı 'Na genel bakış](upgrade-assistant-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b7cd9-111">For more information on how to install the tool, see [Overview of the .NET Upgrade Assistant](upgrade-assistant-overview.md).</span></span>

### <a name="initial-demo-setup"></a><span data-ttu-id="b7cd9-112">İlk tanıtım kurulumu</span><span class="sxs-lookup"><span data-stu-id="b7cd9-112">Initial demo setup</span></span>

<span data-ttu-id="b7cd9-113">.NET Upgrade yardımcısını kendi .NET Framework uygulamanıza karşı çalıştırıyorsanız, bu adımı atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-113">If you're running the .NET Upgrade Assistant against your own .NET Framework app, you can skip this step.</span></span> <span data-ttu-id="b7cd9-114">Yalnızca nasıl çalıştığını görmek için denemek istiyorsanız, bu adım bir örnek .NET WPF projesini kullanmak üzere nasıl ayarlayabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-114">If you just want to try it out to see how it works, this step shows you how to set up a sample .NET WPF project to use.</span></span>

<span data-ttu-id="b7cd9-115">Visual Studio 'yu kullanarak .NET Framework kullanarak yeni bir WPF uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-115">Using Visual Studio, create a new WPF App using .NET Framework.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/new-project.png" alt-text="Visual Studio 'da yeni WPF projesi":::

<span data-ttu-id="b7cd9-117">Projeyi **Wpftest** olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-117">Name the project **WpfTest**.</span></span> <span data-ttu-id="b7cd9-118">Projeyi **.NET Framework 4.6.1** kullanacak şekilde yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-118">Configure the project to use **.NET Framework 4.6.1**.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/configure-project.png" alt-text="Visual Studio 'da Windows Forms projesi yapılandırma":::

<span data-ttu-id="b7cd9-120">Oluşturulan projeyi ve dosyalarını, özellikle de onun proje dosyalarını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-120">Review the created project and its files, especially its project file(s).</span></span>

### <a name="run-upgrade-assistant"></a><span data-ttu-id="b7cd9-121">Yükseltmeyi Çalıştır-Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="b7cd9-121">Run upgrade-assistant</span></span>

<span data-ttu-id="b7cd9-122">Bir Terminal açın ve hedef projenin veya çözümün bulunduğu klasöre gidin.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-122">Open a terminal and navigate to the folder where the target project or solution is located.</span></span> <span data-ttu-id="b7cd9-123">`upgrade-assistant`Hedeflemek istediğiniz projenin adını geçirerek komutunu çalıştırın (proje dosyasının yolu geçerli olduğu sürece komutu herhangi bir yerden çalıştırabilirsiniz).</span><span class="sxs-lookup"><span data-stu-id="b7cd9-123">Run the `upgrade-assistant` command, passing in the name of the project you're targeting (you can run the command from anywhere, as long as the path to the project file is valid).</span></span>

```console
upgrade-assistant .\WpfTest.csproj
```

<span data-ttu-id="b7cd9-124">Araç çalışır ve bunu yapacağız adımların bir listesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-124">The tool runs and shows you a list of the steps it will do.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/initial-run.png" alt-text=".NET Yükseltme Yardımcısı başlangıç ekranı":::

<span data-ttu-id="b7cd9-126">Her adım tamamlandığında, araç, kullanıcının bir sonraki adımı uygulamaya veya atlamaya izin veren bir komut kümesi sağlar, daha fazla ayrıntı için bkz. daha fazla ayrıntı, günlüğü yapılandırma veya işlemden çıkma.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-126">As each step is completed, the tool provides a set of commands allowing the user to apply or skip the next step, see more details, configure logging, or exit the process.</span></span> <span data-ttu-id="b7cd9-127">Araç, bir adımın hiçbir eylem gerçekleştirmediğini algılarsa, bu adımı otomatik olarak atlar ve gerçekleştirilecek eylemlere sahip olana kadar bir sonraki adıma devam eder.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-127">If the tool detects that a step will perform no actions, it will automatically skip that step and continue to the next step until it reaches one that will have actions to perform.</span></span> <span data-ttu-id="b7cd9-128">Başka seçim yapılmayacak şekilde ENTER tuşuna basmak sonraki adımı gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-128">Pressing enter will perform the next step if no other selection is made.</span></span>

<span data-ttu-id="b7cd9-129">Bu örnekte, uygulanan adım her seferinde seçilir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-129">In this example, the apply step is chosen each time.</span></span> <span data-ttu-id="b7cd9-130">İlk adım projeyi yedeklemedir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-130">The first step is to back up the project.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/backup-project.png" alt-text=".NET Yükseltme Yardımcısı proje yedeklemesi":::

<span data-ttu-id="b7cd9-132">Araç, yedekleme için özel bir yol ister ve varsayılan olarak, proje yedeklemesini uzantılı aynı klasöre yerleştirir `.backup` .</span><span class="sxs-lookup"><span data-stu-id="b7cd9-132">The tool prompts for a custom path for the backup, or to use the default, which will place the project backup in the same folder with a `.backup` extension.</span></span> <span data-ttu-id="b7cd9-133">Aracın yaptığı sonraki adım proje dosyasını SDK stiline dönüştürmektedir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-133">The next step the tool performs is to convert the project file to SDK style.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/convert-project.png" alt-text=".NET Yükseltme Yardımcısı projeyi SDK stiline Dönüştür":::

<span data-ttu-id="b7cd9-135">Proje biçimi güncelleştirildikten sonra, bir sonraki adım projenin TFı 'sini güncelleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-135">Once the project format has been updated, the next step is to update the TFM of the project.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-tfm.png" alt-text=".NET Yükseltme Yardımcısı güncelleştirme tfd":::

<span data-ttu-id="b7cd9-137">Ardından araç, projenin NuGet paketlerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-137">Next, the tool updates the project's NuGet packages.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-nuget-packages.png" alt-text=".NET Yükseltme Yardımcısı güncelleştirme NuGet paketleri":::

<span data-ttu-id="b7cd9-139">Paketler güncelleştirildikten sonra, bir sonraki adım, varsa şablon dosyaları eklemektir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-139">Once the packages are updated, the next step is to add template files, if any.</span></span> <span data-ttu-id="b7cd9-140">Bu durumda, eklenmesi gereken hiçbir şablon dosyası yoktur.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-140">In this case, there are no template files that need to be added.</span></span> <span data-ttu-id="b7cd9-141">Bu adım, uygulama yapılandırma dosyalarını ve güncelleştirme C# kaynağını aşağıda gösterildiği gibi düzeltmeleri uygulamak için devam ettirir ve geçirir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-141">This step continues and migrates app config files and updates C# source to apply fixes, as shown below.</span></span> <span data-ttu-id="b7cd9-142">Bu proje herhangi bir yapılandırma dosyası veya kaynak kodu değişikliğine ihtiyaç duymadı, bu nedenle bu adımlar otomatik olarak devam eder.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-142">This project didn't need any config file or source code changes, so these steps proceeded automatically.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/add-template-files.png" alt-text=".NET Yükseltme Yardımcısı şablon dosyaları Ekle ve yapılandırmayı geçir":::

<span data-ttu-id="b7cd9-144">Bu son proje olduğundan, sonraki adım "sonraki projeye geç", çözümün tamamını geçirme sürecini tamamlamayı ister.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-144">Since this is the last project, the next step, "Move to next project", prompts to complete the process of migrating the entire solution.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/complete-solution.png" alt-text="Çözümü tamamlayan .NET Yükseltme Yardımcısı":::

<span data-ttu-id="b7cd9-146">Bu işlem tamamlandıktan sonra, geçirilen WPF projesi şuna benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="b7cd9-146">Once this process has completed, the migrated WPF project will look something like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <OutputType>WinExe</OutputType>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <UseWPF>true</UseWPF>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
    <PackageReference Include="Microsoft.DotNet.UpgradeAssistant.Extensions.Default.Analyzers" Version="0.2.211942">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="5.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="b7cd9-147">.NET Yükseltme Yardımcısı 'Nın Ayrıca, yükseltme işlemine devam eden bir projeye çözümleyiciler eklediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-147">Notice that the .NET Upgrade Assistant also adds analyzers to the project that assist with continuing the upgrade process.</span></span>

## <a name="troubleshooting-tips"></a><span data-ttu-id="b7cd9-148">Sorun giderme ipuçları</span><span class="sxs-lookup"><span data-stu-id="b7cd9-148">Troubleshooting tips</span></span>

<span data-ttu-id="b7cd9-149">.NET Yükseltme Yardımcısı kullanılırken oluşabilecek birçok bilinen sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-149">There are several known problems that can occur when using the .NET Upgrade Assistant.</span></span> <span data-ttu-id="b7cd9-150">Bazı durumlarda, bunlar .NET Yükseltme Yardımcısı 'Nın dahili olarak kullandığı [TRY-Convert aracı](https://github.com/dotnet/try-convert) ile ilgili sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-150">In some cases, these are problems with the [try-convert tool](https://github.com/dotnet/try-convert) that the .NET Upgrade Assistant uses internally.</span></span> <span data-ttu-id="b7cd9-151">Bu araç daha fazla senaryoyu ele almak için sık sık güncelleştiriliyor, bu nedenle son sürümü kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-151">This tool is being frequently updated to address more scenarios, so make sure you're using a recent version.</span></span>

- <span data-ttu-id="b7cd9-152">TRY-Convert aracının yüklü olması ve en az sürüm _0.7.21201_'e güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-152">The try-convert tool must be installed and updated to at least version _0.7.21201_.</span></span>
- <span data-ttu-id="b7cd9-153">TRY-Convert aracının önceki sürümleri özel hedef veya özellik dosyalarını desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-153">Earlier versions of the try-convert tool didn't support custom target or props files.</span></span> <span data-ttu-id="b7cd9-154">En son sürüme yükseltirsiniz, bu sorunları el ile ele almanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-154">If you can't upgrade to the latest version, you may need to manually address these issues.</span></span> <span data-ttu-id="b7cd9-155">Hedef proje dosyası özel hedeflere veya props dosyalarına başvurular içeriyorsa, .NET Yükseltme Yardımcısı tarafından çalıştırılmadan önce bu başvuruların dosyadan el ile silinmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-155">If the target project file includes references to custom targets or props files, these references may need to be manually deleted from the file before the .NET Upgrade Assistant is run against it.</span></span>

<span data-ttu-id="b7cd9-156">[Aracın GitHub deposunda,](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) daha fazla sorun giderme ipuçları ve bilinen sorunlar vardır.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-156">[The tool's GitHub repository](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) has more troubleshooting tips and known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7cd9-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7cd9-157">See also</span></span>

- [<span data-ttu-id="b7cd9-158">.NET Yükseltme Yardımcısı ile bir Windows Forms uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="b7cd9-158">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="b7cd9-159">.NET Yükseltme Yardımcısı ile bir ASP.NET MVC uygulamasını .NET 5 ' e yükseltme</span><span class="sxs-lookup"><span data-stu-id="b7cd9-159">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-aspnetmvc.md)
- [<span data-ttu-id="b7cd9-160">.NET Yükseltme Yardımcısı 'na genel bakış</span><span class="sxs-lookup"><span data-stu-id="b7cd9-160">Overview of the .NET Upgrade Assistant</span></span>](upgrade-assistant-overview.md)
- [<span data-ttu-id="b7cd9-161">.NET Yükseltme Yardımcısı GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="b7cd9-161">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
