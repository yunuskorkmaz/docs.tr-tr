---
title: .NET core Araçları Genel
description: .NET Core genel araçları nedir ve bunlar için kullanılabilen .NET Core CLI komutları genel bakış.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 3bbf1e7953482dc07f05570443cf640a9fab6258
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647752"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="23440-103">.NET core Araçları Genel genel bakış</span><span class="sxs-lookup"><span data-stu-id="23440-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="23440-104">.NET Core genel aracı bir konsol uygulaması içeren özel bir NuGet paketidir.</span><span class="sxs-lookup"><span data-stu-id="23440-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="23440-105">Genel bir aracı makinenizde yol ortam değişkeninde bulunan bir varsayılan konum ya da özel bir konuma yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="23440-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="23440-106">.NET Core genel bir aracı kullanmak istiyorsanız:</span><span class="sxs-lookup"><span data-stu-id="23440-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="23440-107">Aracı (genellikle bir Web sitesi veya GitHub sayfası) hakkında bilgiler bulun.</span><span class="sxs-lookup"><span data-stu-id="23440-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="23440-108">Giriş akış (genellikle NuGet.org) için istatistikleri ve yazar denetleyin.</span><span class="sxs-lookup"><span data-stu-id="23440-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="23440-109">Aracı'nı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="23440-109">Install the tool.</span></span>
* <span data-ttu-id="23440-110">Aracı'nı arayın.</span><span class="sxs-lookup"><span data-stu-id="23440-110">Call the tool.</span></span>
* <span data-ttu-id="23440-111">Aracı'nı güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="23440-111">Update the tool.</span></span>
* <span data-ttu-id="23440-112">Aracı'nı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="23440-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="23440-113">.NET core Araçları Genel path değişkeninize görünür ve tam güvende çalıştırma.</span><span class="sxs-lookup"><span data-stu-id="23440-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="23440-114">.NET Core Araçları Genel Yazar güvenmediğiniz sürece yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="23440-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="23440-115">.NET Core genel aracını bulun</span><span class="sxs-lookup"><span data-stu-id="23440-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="23440-116">Şu anda .NET Core komut satırı arabirimi (CLI) bir genel aracı arama özelliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="23440-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="23440-117">.NET Core Araçları Genel bulabilirsiniz [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="23440-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="23440-118">Ancak, NuGet henüz, özellikle .NET Core genel araçları için arama yapmanıza izin vermez.</span><span class="sxs-lookup"><span data-stu-id="23440-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="23440-119">Ayrıca araç önerilerinden blog gönderilerini veya bulabilirsiniz [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="23440-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="23440-120">Genel ASP.NET ekibi tarafından oluşturulan araçlar için kaynak kodunu da görebilirsiniz [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub deposu.</span><span class="sxs-lookup"><span data-stu-id="23440-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="23440-121">Yazar ve istatistikleri denetimi</span><span class="sxs-lookup"><span data-stu-id="23440-121">Check the author and statistics</span></span>

<span data-ttu-id="23440-122">.NET Core Araçları Genel tam güvende çalıştırmak ve path değişkeninize genellikle yüklü olmadığından, çok güçlü olabilir.</span><span class="sxs-lookup"><span data-stu-id="23440-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="23440-123">Araçlar güvenmediğiniz kişilerden yüklemeyin.</span><span class="sxs-lookup"><span data-stu-id="23440-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="23440-124">Araç, NuGet üzerinde barındırılıyorsa, aracı için arama yaparak yazar ve istatistikleri kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23440-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="23440-125">Genel bir aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="23440-125">Install a Global Tool</span></span>

<span data-ttu-id="23440-126">Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](dotnet-tool-install.md) .NET Core CLI komutu.</span><span class="sxs-lookup"><span data-stu-id="23440-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="23440-127">Aşağıdaki örnek, varsayılan konumu genel bir aracı yüklemek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="23440-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="23440-128">Aracı yüklü değilse, hata iletileri görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="23440-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="23440-129">Beklediğiniz akışları denetlendiği denetleyin.</span><span class="sxs-lookup"><span data-stu-id="23440-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="23440-130">Yayın öncesi bir sürümü ya da aracının belirli bir sürümü yüklemeye çalışıyorsanız, sürüm numarası şu biçimi kullanarak belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="23440-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="23440-131">Yükleme başarılı olursa, aracı ve yüklü sürümü çağırmak için kullanılan komut aşağıdaki örneğe benzer gösteren bir ileti görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="23440-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="23440-132">Varsayılan dizini veya belirli bir konuma genel araçları yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="23440-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="23440-133">Varsayılan dizinler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="23440-133">The default directories are:</span></span>

| <span data-ttu-id="23440-134">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="23440-134">OS</span></span>          | <span data-ttu-id="23440-135">Yol</span><span class="sxs-lookup"><span data-stu-id="23440-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="23440-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="23440-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="23440-137">Windows</span><span class="sxs-lookup"><span data-stu-id="23440-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="23440-138">SDK'yı ilk kez çalıştırdığınızda, genel araçları yüklü doğrudan çağrılabilir için bu konumları kullanıcının yoluna eklenir.</span><span class="sxs-lookup"><span data-stu-id="23440-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="23440-139">Genel araçları kullanıcıya özgü olduğuna dikkat edin, genel makine yok.</span><span class="sxs-lookup"><span data-stu-id="23440-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="23440-140">Kullanıcıya özel olan, makinenin tüm kullanıcıları için kullanılabilir olan bir genel aracı yükleyemezsiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="23440-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="23440-141">Aracı yalnızca, aracının yüklendiği her kullanıcı profili için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="23440-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="23440-142">Genel araçları Ayrıca belirli bir dizindeki yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="23440-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="23440-143">Belirli bir dizindeki yüklendiğinde, kullanıcı komutu kullanılabilir yolunda belirtilen dizinle komutunu çağırarak bu dizine ekleyerek emin olmanız gerekir veya belirtilen dizin içinde aracından çağırma.</span><span class="sxs-lookup"><span data-stu-id="23440-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="23440-144">Bu durumda, .NET Core CLI bu konum otomatik olarak PATH ortam değişkenine eklemez.</span><span class="sxs-lookup"><span data-stu-id="23440-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="23440-145">Aracını kullanma</span><span class="sxs-lookup"><span data-stu-id="23440-145">Use the tool</span></span>

<span data-ttu-id="23440-146">Aracı yüklendikten sonra komutu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23440-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="23440-147">Komut paket adı ile aynı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="23440-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="23440-148">Komut ise `dotnetsay`, beraber:</span><span class="sxs-lookup"><span data-stu-id="23440-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="23440-149">Aracı Yazar bağlamında görüntülenecek araç istiyordu, `dotnet` istemi yazıldığına bu şekilde olarak çağrı `dotnet <command>`, gibi:</span><span class="sxs-lookup"><span data-stu-id="23440-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="23440-150">Kullanarak yüklü paketleri listeleyerek, hangi Araçlar yüklü bir genel Aracı paketine dahil edilen bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="23440-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="23440-151">Kullanım yönergeleri Aracı'nın Web sitesinde veya aşağıdaki komutlardan birini yazarak da arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="23440-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="23440-152">Nerede sorun çıkabilir</span><span class="sxs-lookup"><span data-stu-id="23440-152">What could go wrong</span></span>

<span data-ttu-id="23440-153">Genel Araçları [framework bağımlı uygulamaları](../deploying/index.md#framework-dependent-deployments-fdd), güvenin makinenizde yüklü bir .NET Core çalışma zamanı üzerinde anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="23440-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="23440-154">Beklenen çalışma zamanı bulunamazsa bunlar gibi normal .NET Core çalışma zamanı sarma kuralları izleyin:</span><span class="sxs-lookup"><span data-stu-id="23440-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="23440-155">Bir uygulama belirtilen birincil ve ikincil sürüm en yüksek düzeltme eki sürümü için İleri yapar.</span><span class="sxs-lookup"><span data-stu-id="23440-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="23440-156">Bir eşleştirme büyük ve küçük versiyon numarasını ile eşleşen hiçbir çalışma zamanı varsa, daha yüksek bir sonraki alt sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="23440-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="23440-157">İleri Sarma Önizleme ve yayın sürümleri arasında veya çalışma zamanı Önizleme sürümleri arasında oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="23440-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="23440-158">Bu nedenle, genel Önizleme sürümleri kullanılarak oluşturulan araçları yeniden ve yazarı tarafından yeniden yayımlanması ve gerekir yeniden.</span><span class="sxs-lookup"><span data-stu-id="23440-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="23440-159">Genel .NET Core 2.1 önizleme 1'de oluşturulan Araçlar ek sorunlar ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="23440-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="23440-160">Daha fazla bilgi için [.NET Core 2.1 önizleme 2 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="23440-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="23440-161">Uygun bir çalışma zamanı bir uygulamayı bulamıyorsanız, çalıştırılacak başarısız olur ve bir hata bildirir.</span><span class="sxs-lookup"><span data-stu-id="23440-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="23440-162">Başka bir sorun olabilir, daha önceki bir önizleme sırasında oluşturulan bir genel aracı, şu anda yüklü .NET Core çalışma zamanlarını çalışmayabilir ' dir.</span><span class="sxs-lookup"><span data-stu-id="23440-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="23440-163">Hangi çalışma zamanları, makinenizde aşağıdaki komutu kullanarak yüklenen görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="23440-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="23440-164">Genel aracı yazarıyla iletişime geçin ve bunlar yeniden derleyin ve güncelleştirilmiş sürüm numarasına sahip NuGet için kendi araç paketi yeniden yayımlamanız durumunda bakın.</span><span class="sxs-lookup"><span data-stu-id="23440-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="23440-165">NuGet paketi güncelleştirdiniz mi sonra kopyanızı güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23440-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="23440-166">.NET Core CLI yol ortam değişkenine ilk kullanım için varsayılan konumları eklemek çalışır.</span><span class="sxs-lookup"><span data-stu-id="23440-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="23440-167">Ancak, birkaç senaryo burada konumu değil eklenecek yolu otomatik olarak vardır gibi:</span><span class="sxs-lookup"><span data-stu-id="23440-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="23440-168">Ayarladıysanız `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam değişkeni.</span><span class="sxs-lookup"><span data-stu-id="23440-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="23440-169">Macos'ta .NET Core SDK'sını kullanarak yüklediyseniz, *. tar.gz* dosyaları ve *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="23440-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="23440-170">Linux üzerinde yolu yapılandırmak için kabuk ortam dosyasını düzenlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="23440-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="23440-171">Başka CLI komutları</span><span class="sxs-lookup"><span data-stu-id="23440-171">Other CLI commands</span></span>

<span data-ttu-id="23440-172">.NET Core SDK'sı, .NET Core Araçları Genel destekleyen diğer komutlar içerir.</span><span class="sxs-lookup"><span data-stu-id="23440-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="23440-173">Dilediğinizi `dotnet tool` aşağıdaki seçeneklerden birini komutlarıyla:</span><span class="sxs-lookup"><span data-stu-id="23440-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="23440-174">`--global` veya `-g` komutu geniş kullanıcı için geçerli genel araçları olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="23440-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="23440-175">`--tool-path` Genel araçları için özel bir konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="23440-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="23440-176">Hangi komutları için genel Araçlar kullanılabilir olduğunu öğrenmek için:</span><span class="sxs-lookup"><span data-stu-id="23440-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="23440-177">En son kararlı sürüm ile kaldırılmadan ve genel bir aracı güncelleştirme içerir.</span><span class="sxs-lookup"><span data-stu-id="23440-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="23440-178">Genel bir aracı güncelleştirmek için [dotnet aracı güncelleştirme](dotnet-tool-update.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="23440-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="23440-179">Kullanarak bir genel Aracı kaldırma [dotnet Aracı kaldırma](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="23440-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="23440-180">Genel sürüm ve komutları birlikte makine üzerinde yüklü araçların tümünü görüntülemek için kullanın [dotnet araç listesi](dotnet-tool-list.md) komutu:</span><span class="sxs-lookup"><span data-stu-id="23440-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```