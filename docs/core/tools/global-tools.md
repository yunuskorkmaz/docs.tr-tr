---
title: .NET Core küresel araçları
description: .NET Core genel araçlarının ne olduğuna ve bunlara yönelik .NET Core CLI komutlarına genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 01c1463ceddcd64e5bab05b95a5ae4a91b6da838
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117457"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="3fad5-103">.NET Core genel araçlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="3fad5-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="3fad5-104">.NET Core küresel Aracı, konsol uygulaması içeren özel bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="3fad5-105">Bir genel araç, makinenizde, PATH ortam değişkenine veya özel bir konuma dahil olan varsayılan bir konumda yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="3fad5-106">.NET Core küresel aracı kullanmak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="3fad5-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="3fad5-107">Araçla ilgili bilgileri bulun (genellikle bir Web sitesi veya GitHub sayfası).</span><span class="sxs-lookup"><span data-stu-id="3fad5-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="3fad5-108">Akışın giriş sayfasındaki yazar ve istatistikleri denetleyin (genellikle NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="3fad5-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="3fad5-109">Aracı 'nı yükler.</span><span class="sxs-lookup"><span data-stu-id="3fad5-109">Install the tool.</span></span>
* <span data-ttu-id="3fad5-110">Aracı çağırın.</span><span class="sxs-lookup"><span data-stu-id="3fad5-110">Call the tool.</span></span>
* <span data-ttu-id="3fad5-111">Aracı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="3fad5-111">Update the tool.</span></span>
* <span data-ttu-id="3fad5-112">Aracı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3fad5-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3fad5-113">.NET Core küresel araçları yolunuzda görünür ve tam güvende çalışır.</span><span class="sxs-lookup"><span data-stu-id="3fad5-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="3fad5-114">Yazara güvenmediğiniz .NET Core küresel araçlarını yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="3fad5-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="3fad5-115">.NET Core küresel aracı bulma</span><span class="sxs-lookup"><span data-stu-id="3fad5-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="3fad5-116">Şu anda .NET Core komut satırı arabiriminde (CLı) genel bir araç arama özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="3fad5-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="3fad5-117">[NuGet](https://www.nuget.org)üzerinde .NET Core küresel araçları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="3fad5-118">Ancak, NuGet henüz .NET Core küresel araçları için arama yapmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="3fad5-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="3fad5-119">Ayrıca, blog gönderilerinde veya [natemcmaster/DotNet-Tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposunda araç önerileri de bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="3fad5-120">[ASPNET/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub deposunda ASP.NET ekibi tarafından oluşturulan genel araçların kaynak kodunu da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="3fad5-121">Yazarı ve istatistikleri denetleme</span><span class="sxs-lookup"><span data-stu-id="3fad5-121">Check the author and statistics</span></span>

<span data-ttu-id="3fad5-122">.NET Core küresel araçları tam güvende çalıştığı ve genellikle yolunuza yüklendiği için, bu, çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="3fad5-123">Güvenmediğiniz kişilerden araç indirmeyin.</span><span class="sxs-lookup"><span data-stu-id="3fad5-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="3fad5-124">Araç NuGet üzerinde barındırılıyorsa, aracı arayarak yazarı ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="3fad5-125">Küresel bir araç yükler</span><span class="sxs-lookup"><span data-stu-id="3fad5-125">Install a Global Tool</span></span>

<span data-ttu-id="3fad5-126">Küresel bir araç yüklemek için [DotNet aracı install](dotnet-tool-install.md) .NET Core CLI komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3fad5-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="3fad5-127">Aşağıdaki örnek, genel bir aracın varsayılan konuma nasıl yükleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="3fad5-127">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="3fad5-128">Araç yüklenemezse hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="3fad5-129">Beklediğiniz akışların denetlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3fad5-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="3fad5-130">Bir yayın öncesi sürüm veya aracın belirli bir sürümünü yüklemeye çalışıyorsanız, sürüm numarasını aşağıdaki biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fad5-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="3fad5-131">Yükleme başarılı olursa, aşağıdaki örneğe benzer şekilde, aracı ve yüklü sürümü çağırmak için kullanılan komutu gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="3fad5-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="3fad5-132">Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="3fad5-133">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3fad5-133">The default directories are:</span></span>

| <span data-ttu-id="3fad5-134">OS</span><span class="sxs-lookup"><span data-stu-id="3fad5-134">OS</span></span>          | <span data-ttu-id="3fad5-135">Yol</span><span class="sxs-lookup"><span data-stu-id="3fad5-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="3fad5-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="3fad5-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="3fad5-137">Windows</span><span class="sxs-lookup"><span data-stu-id="3fad5-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="3fad5-138">Bu konumlar, SDK ilk kez çalıştırıldığında kullanıcının yoluna eklenir, bu nedenle genel araçlar yüklenir, böylece doğrudan çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="3fad5-139">Genel araçların makineye genel değil, kullanıcıya özgü olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3fad5-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="3fad5-140">Kullanıcıya özel olması, makinenin tüm kullanıcıları için kullanılabilir olan küresel bir araç yükleyemeyeceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="3fad5-141">Araç yalnızca aracın yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="3fad5-142">Genel araçlar, belirli bir dizine de yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="3fad5-143">Belirli bir dizine yüklendiğinde, kullanıcının, yolu belirtilen dizin ile çağırarak veya aracı belirtilen dizin içinden çağırarak, bu dizini da dahil ederek komutun kullanılabilir olduğundan emin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="3fad5-144">Bu durumda .NET Core CLI, bu konumu otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="3fad5-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="3fad5-145">Aracı kullanma</span><span class="sxs-lookup"><span data-stu-id="3fad5-145">Use the tool</span></span>

<span data-ttu-id="3fad5-146">Araç yüklendikten sonra, komutunu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="3fad5-147">Komutun paket adı ile aynı olamayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3fad5-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="3fad5-148">Komut ise `dotnetsay`, şunu ile çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fad5-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="3fad5-149">Araç yazarı, aracın `dotnet` istem bağlamında görünmesini istiyorlarsa, bu, şöyle bir şekilde bir `dotnet <command>`şekilde yazmış olabilirler, örneğin:</span><span class="sxs-lookup"><span data-stu-id="3fad5-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="3fad5-150">Yüklü paketleri [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak listeleyerek, yüklü bir genel araç paketine hangi araçların ekleneceğini bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="3fad5-151">Ayrıca, aracın Web sitesinde veya aşağıdaki komutlardan birini yazarak kullanım yönergelerine bakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fad5-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="3fad5-152">Hatalı gidebilirler</span><span class="sxs-lookup"><span data-stu-id="3fad5-152">What could go wrong</span></span>

<span data-ttu-id="3fad5-153">Küresel araçlar, [çerçeveye bağlı uygulamalardır](../deploying/index.md#framework-dependent-deployments-fdd)ve bu, makinenizde yüklü bir .NET Core çalışma zamanına bağlı olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="3fad5-154">Beklenen çalışma zamanı bulunamazsa, normal .NET Core çalışma zamanı alma-iletme kurallarını izler:</span><span class="sxs-lookup"><span data-stu-id="3fad5-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="3fad5-155">Bir uygulama, belirtilen birincil ve ikincil sürümün en yüksek düzeltme eki sürümüne ileri kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="3fad5-156">Eşleşen bir ana ve alt sürüm numarasına sahip eşleşen bir çalışma zamanı yoksa, sonraki en düşük sürüm kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3fad5-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="3fad5-157">Çalışma zamanının veya önizleme sürümleri ile sürüm sürümlerinin önizleme sürümleri arasında ileri alma gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="3fad5-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="3fad5-158">Bu nedenle, önizleme sürümleri kullanılarak oluşturulan küresel araçların, yazar tarafından yeniden oluşturulması ve yeniden yayımlanması ve yeniden yüklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="3fad5-159">.NET Core 2,1 Preview 1 ' de oluşturulan genel araçlarla ilgili ek sorunlar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="3fad5-160">Daha fazla bilgi için bkz. [.NET Core 2,1 Preview 2 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="3fad5-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="3fad5-161">Bir uygulama uygun bir çalışma zamanı bulamazsa, çalışmaz ve bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="3fad5-162">Başka bir sorun ortaya çıkabilir, önceki önizleme sırasında oluşturulan küresel bir araç, şu anda yüklü olan .NET Core çalışma zamanları ile çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="3fad5-163">Makinenizde hangi çalışma zamanlarının yüklü olduğunu aşağıdaki komutu kullanarak görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3fad5-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="3fad5-164">Genel aracının yazarına başvurun ve araç paketlerini, güncelleştirilmiş bir sürüm numarasıyla NuGet 'e yeniden derleyip yeniden yayımlayabilecekleri konusunda bilgi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="3fad5-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="3fad5-165">NuGet üzerinde paketi güncelleştirdikten sonra kopyanızı güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="3fad5-166">.NET Core CLI, ilk kullanımındaki yol ortam değişkenine varsayılan konumları eklemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="3fad5-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="3fad5-167">Ancak, konumun otomatik olarak yola eklenebileceği birkaç senaryo vardır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="3fad5-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="3fad5-168">`DOTNET_SKIP_FIRST_TIME_EXPERIENCE` Ortam değişkenini ayarladıysanız.</span><span class="sxs-lookup"><span data-stu-id="3fad5-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="3fad5-169">MacOS üzerinde. *tar. gz* dosyalarını *. pkg*değil kullanarak .NET Core SDK yüklediyseniz.</span><span class="sxs-lookup"><span data-stu-id="3fad5-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="3fad5-170">Linux 'ta, yolu yapılandırmak için kabuk ortam dosyasını düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="3fad5-171">Diğer CLı komutları</span><span class="sxs-lookup"><span data-stu-id="3fad5-171">Other CLI commands</span></span>

<span data-ttu-id="3fad5-172">.NET Core SDK .NET Core küresel araçlarını destekleyen diğer komutları içerir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="3fad5-173">Aşağıdaki seçeneklerden biriyle komutlardan birini kullanın: `dotnet tool`</span><span class="sxs-lookup"><span data-stu-id="3fad5-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="3fad5-174">`--global`ya `-g` da komutun Kullanıcı genelindeki genel araçlara uygun olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="3fad5-175">`--tool-path`Küresel araçlar için özel bir konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="3fad5-176">Genel araçlar için hangi komutların kullanılabildiğini öğrenmek için:</span><span class="sxs-lookup"><span data-stu-id="3fad5-176">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="3fad5-177">Küresel bir aracın güncelleştirilmesi, en son kararlı sürümle kaldırılması ve yeniden yüklenmesi ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="3fad5-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="3fad5-178">Genel bir aracı güncelleştirmek için [DotNet Aracı güncelleştirme](dotnet-tool-update.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="3fad5-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="3fad5-179">[DotNet aracını kaldırma](dotnet-tool-uninstall.md)Işlemini kullanarak genel bir aracı kaldırma:</span><span class="sxs-lookup"><span data-stu-id="3fad5-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="3fad5-180">Makinede yüklü olan tüm genel araçları, sürüm ve komutlarıyla birlikte göstermek için [DotNet araç listesi](dotnet-tool-list.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="3fad5-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```
